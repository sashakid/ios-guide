- [Multithreading and concurrency](#multithreading-and-concurrency)
  - [Основные понятия многопоточности](#основные-понятия-многопоточности)
  - [API для работы с многопоточностью и их альтернативы](#api-для-работы-с-многопоточностью-и-их-альтернативы)
    - [POSIX Threads](#posix-threads)
    - [NSThread](#nsthread)
    - [Run Loops](#run-loops)
    - [NSObject instance methods](#nsobject-instance-methods)
    - [GCD](#gcd)
      - [Swift 3 API](#swift-3-api)
    - [NSOperationQueue](#nsoperationqueue)
    - [async / await](#async--await)
    - [Idle-time notifications](#idle-time-notifications)
    - [Timers](#timers)
  - [Synchronization](#synchronization)
    - [Memory Barriers and Volatile Variables](#memory-barriers-and-volatile-variables)
    - [Atomic Operations](#atomic-operations)
    - [Lock](#lock)
    - [Semaphore](#semaphore)
    - [Mutex](#mutex)
    - [Performance](#performance)
    - [Differences](#differences)
  - [Что такое гонка условий?](#что-такое-гонка-условий)
    - [Deadlock](#deadlock)
    - [Livelock](#livelock)
    - [Starvation](#starvation)
    - [Priority inversion](#priority-inversion)
    - [Как избежать гонки условий](#как-избежать-гонки-условий)
- [Чем отличается dispatch\_async от dispatch\_sync?](#чем-отличается-dispatch_async-от-dispatch_sync)
- [Как многопоточность работает с UIKit?](#как-многопоточность-работает-с-uikit)
- [Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?](#atomic-vs-nonatomic-чем-отличаются-как-вручную-переопределить-atomicnonatomic-сеттер-в-не-arc-коде)
- [Можно ли отменить операцию в GCD? А в NSOperationQueue?](#можно-ли-отменить-операцию-в-gcd-а-в-nsoperationqueue)
- [Когда лучше использовать GCD, а когда NSOperationQueue?](#когда-лучше-использовать-gcd-а-когда-nsoperationqueue)
- [Difference between GCD and async/await](#difference-between-gcd-and-asyncawait)

<a name="multithreading-and-concurrency"></a>

# Multithreading and concurrency

<a name="основные-понятия-многопоточности"></a>

## Основные понятия многопоточности

__Multithreading__

The ability of a central processing unit (CPU) (or a single core in a multi-core processor) to provide multiple threads of execution concurrently, supported by the operating system. This approach differs from multiprocessing.

Depending on your application, there may still be times when you need to create custom threads. If you do create custom threads, you should strive to create as few threads as possible yourself and you should use those threads only for specific tasks that cannot be implemented any other way.
Threads are still a good way to implement code that must run in real time. Dispatch queues make every attempt to run their tasks as fast as possible but they do not address real time constraints. If you need more predictable behavior from code running in the background, threads may still offer a better alternative.

__Concurrency__

The ability of different parts or units of a program, algorithm, or problem to be executed out-of-order or in partial order, without affecting the outcome. This allows for parallel execution of the concurrent units, which can significantly improve overall speed of the execution in multi-processor and multi-core systems. In more technical terms, concurrency refers to the decomposability of a program, algorithm, or problem into order-independent or partially-ordered components or units of computation.

Concurrency is the notion of multiple things happening at the same time. Threads are subunits of processes, which can be scheduled independently by the operating system scheduler. Virtually all concurrency APIs are built on top of threads under the hood – that’s true for both Grand Central Dispatch and operation queues. You can either use the `POSIX` thread API, or the Objective-C wrapper around this API, `NSThread`, to create your own threads.

__Parallelism__

Refers to techniques to make programs faster by performing several computations at the same time. This requires hardware with multiple processing units.

> Explanation 1:
Concurrency is the composition of independently executing computations, and concurrency is not parallelism: concurrency is about dealing with lots of things at once but parallelism is about doing lots of things at once. Concurrency is about structure, parallelism is about execution, concurrency provides a way to structure a solution to solve a problem that may (but not necessarily) be parallelizable.

> Explanation 2:
Say you have a program that has two threads. The program can run in two ways:

```
Concurrency                 Concurrency + parallelism
(Single-Core CPU)           (Multi-Core CPU)
 ___                         ___ ___
|th1|                       |th1|th2|
|   |                       |   |___|
|___|___                    |   |___
    |th2|                   |___|th2|
 ___|___|                    ___|___|
|th1|                       |th1|
|___|___                    |   |___
    |th2|                   |   |th2|
```

> In both cases we have concurrency from the mere fact that we have more than one thread running. If we ran this program on a computer with a single CPU core, the OS would be switching between the two threads, allowing one thread to run at a time. If we ran this program on a computer with a multi-core CPU then we would be able to run the two threads in parallel - side by side at the exact same time.

__queue__

В Swift (и в iOS вообще) под queue обычно подразумевается GCD (Grand Central Dispatch) очередь — это способ организации выполнения задач асинхронно или синхронно, с управлением многопоточностью через очереди задач, а не напрямую через потоки.

DispatchQueue — это абстракция очереди задач, за которой скрыта пул потоков (thread pool). Вместо ручного создания потоков, ты просто ставишь задачу в очередь, а GCD сам решает, когда и где её выполнять.

```swift
DispatchQueue.global().async {
    print("Это выполняется в фоновом потоке")
}
```

⚙️ Что под капотом

•	DispatchQueue = очередь задач, реализованная на базе GCD (libdispatch)

•	Задачи добавляются в очередь (FIFO), а GCD сам назначает их на свободные потоки

•	iOS/macOS поддерживают глобальный пул потоков

•	Используется кооперативная модель (не 1:1 к ядрам) и оптимизация загрузки процессора

🔄 Потоки и пул

GCD использует thread pool, то есть набор рабочих потоков. Когда ты добавляешь задачу, GCD:

1.	Ставит задачу в очередь

2.	Проверяет, есть ли свободный поток

3.	Если есть — выполняет задачу

4.	Если нет — ждёт или создаёт поток при необходимости

🔍 Объяснение:

•	Вы добавляете задачи в DispatchQueue (например, DispatchQueue.global().async { ... })

•	GCD ставит их в очередь (FIFO — “первым пришёл — первым выполнен”)

•	Затем выбирается доступный поток из пула

•	GCD сам решает, когда и какой поток использовать (и может переиспользовать потоки)

•	Когда поток освобождается — он может взять следующую задачу из очереди

🎯 Что важно понимать

•	GCD не создаёт новый поток под каждую задачу, а использует переиспользуемый пул

•	У каждой задачи нет жёсткой привязки к конкретному потоку

•	main-очередь всегда однопоточная и работает на главном потоке UI

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_queue.png">

__thread__

Is used to refer to a separate path of execution of tasks.

Inside each program, however, exists always one (Main Thread) or more threads of execution, which can be used to perform different tasks simultaneously or in a nearly simultaneous manner. The system itself actually manages these threads of execution, scheduling them to run on the available cores and preemptively interrupting them as needed to allow other threads to run. The threads we’ve been talking about so far have been `software threads`. They’re (generally) independent units of computation. The `hardware threads` are based on the number of cores on the computer. A `hardware thread` is a physical CPU or core. So, a 4 core CPU can genuinely support 4 `hardware threads` at once - the CPU really is doing 4 things at the same time.
After starting a thread, the thread runs in one of three main states: `running`, `ready`, or `blocked`. If a thread is `not currently running`, it is either `blocked` and waiting for input or it is `ready` to run but not scheduled to do so yet. The thread continues moving back and forth among these states until it finally exits and moves to the terminated state. When you create a new thread, you must specify an entry-point function for that thread. This entry-point function constitutes the code you want to run on the thread. When the function returns, or when you terminate the thread explicitly, the thread stops permanently and is reclaimed by the system. Because threads are relatively expensive to create in terms of memory and time, it is therefore recommended that your entry point function do a significant amount of work or set up a `run loop` to allow for recurring work to be performed.

Общая структура: Software vs Hardware Threads

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/thread1.png">

🔄 Как работает планировщик и context switch

Context switch (переключение контекста) — это процесс, при котором ОС:

1.	Сохраняет состояние текущего потока (регистры, стек, счетчик инструкций и т.д.)

2.	Загружает состояние следующего потока

3.	CPU продолжает выполнение другого потока

📉 Пример: 10 software threads на 1 hardware thread

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/thread2.png">

•	Только один софтварный поток работает в момент времени.

•	Остальные — в очереди или в ожидании.

•	Планировщик ОС через короткие интервалы переключает потоки.

•	Это создает иллюзию параллелизма, хотя в реальности всё по очереди.

💡 Краткий вывод:

•	Да, много софтварных потоков могут использовать один хардварный поток — просто по очереди.

•	Context switch позволяет делить время между ними, но это не бесплатно: он требует времени и ресурсов.

•	Чем больше переключений — тем выше нагрузка на CPU и кеши.

___

__Зачем тогда создавать много софтварных тредов если в итоге они работают один за одним и задачи выполняются одна за одной?__

✅ 1. Ожидание (waiting) — не блокирует CPU

Многие потоки не заняты вычислениями, а ждут:

•	сеть (запрос к серверу)

•	диск (чтение файла)

•	пользовательский ввод

•	блокировки (mutex, semaphore)

❗ Когда поток ждет, он не занимает CPU, и ОС может дать время другим потокам.

➡ Это позволяет эффективно использовать процессор: пока один ждет, другие работают.

✅ 2. Параллелизм на многоядерных CPU

Если есть несколько hardware threads (например, 8 ядер), то несколько потоков действительно работают одновременно.

➡ Чем больше потоков, тем выше шанс загрузить все ядра.

✅ 3. Изоляция задач

•	Разные потоки могут обслуживать разные клиенты, задачи, сервисы.

•	Потоки — удобный способ изолировать выполнение: каждый поток — своя “мини-программа”.

```
Thread 1 — загрузка данных из сети
Thread 2 — парсинг JSON
Thread 3 — обновление UI
Thread 4 — логгирование
```

✅ 4. Планировщик ОС сам управляет — не надо самому

•	Потоки абстрагируют от ручного управления временем.

•	Ты просто создаешь потоки, а ОС уже решает, когда и как их запускать.

⸻

✅ 5. Потоки — основа многих библиотек и фреймворков

•	GCD, OperationQueue, async/await — всё это под капотом использует потоки.

•	Даже если ты не создаешь их напрямую — они всё равно есть.

⸻

🔥 Краткий вывод:

Создание множества потоков полезно, потому что:

•	они ждут, не занимая CPU

•	используют многоядерность

•	разделяют логику приложения

•	делают код проще и реактивнее

•	ОС эффективно ими управляет

__process__

Is used to refer to a running executable, which can encompass multiple threads. It keeps track of what needs to be done and delegates the tasks to the threads. A process can have one or multiple threads. The process is like a project manager and the thread is like a worker.

__task__

Is used to refer to the abstract concept of work that needs to be performed

__Difference between `queue` and `thread`__

A message queue is a data structure for holding messages from the time they're sent until the time the receiver retrieves and acts on them. Generally queues are used as a way to 'connect' producers (of data) & consumers (of data).
A thread pool is a pool of threads that do some sort of processing. A thread pool will normally have some sort of thread-safe queue (refer message queue) attached to allow you to queue up jobs to be done. Here the queue would usually be termed 'task-queue'.
So in a way thread pool could exist at your producer end (generating data) or consumer end (processing the data). And the way to 'pass' that data would be through queues. Why the need for this "middleman" - It decouples the systems. Producers do not know about consumers & vice versa.
The Consumers are not bombarded with data if there is a spike in Producer data. The queue length would increase but the consumers are safe.

Example:

_In iOS the main thread, also called the UI thread, is very important because it is in charge of dispatching the events to the appropriate widget and this includes the drawing events, basically the UI that the user sees & interacts. If you touch a button on screen, the UI thread dispatches the touch event to the app, which in turn sets its pressed state and posts an request to the event queue. The UI thread dequeues the request and notifies the widget to redraw itself._

Queues are cheaper. They reduce the memory cost for storing thread stacks in the application’s memory space. Tappings into the kernel are done when absolutely necessary. They eliminate the code needed to create and configure the threads. They eliminate the code needed to manage and schedule work on threads. They simplify the code we have to write. We focus on the work to be performed without having to worry about thread creation and management including thread communication. And so the underlying queueing software handles all of the thread creation and management for us and the benefit is that it manages threads much more efficiently than the corresponding threaded code.

__Difference between `main queue` and `main thread`__

The main thread is the one that starts our program, and it’s also the one where all our UI work must happen. However, there is also a main queue, and although sometimes we use the terms `main thread` and `main queue` interchangeably, they aren’t quite the same thing. It’s a subtle distinction, but it can sometimes matter: although your `main queue` will always execute on the `main thread` (and is therefore where you’ll be doing your UI work!), it’s also possible that other queues might sometimes run on the `main thread` – the system is free to move things around in whatever way is most efficient. So, if you’re on the `main queue` then you’re definitely on the `main thread`, but being on the `main thread` doesn’t automatically mean you’re on the `main queue` – a different queue could temporarily be running on the `main thread`.

<a name="multithreading-api-alternatives"></a>

## API для работы с многопоточностью и их альтернативы

<a name="posix-threads"></a>

### POSIX Threads

Usually referred to as Pthreads, is a POSIX standard for threads defines an API for creating and manipulating threads. Pthreads defines a set of C programming language types, functions and constants. It is implemented with a pthread.h header and a thread library. There are around 100 Pthreads procedures, all prefixed `pthread_` and they can be categorized into four groups:

- Thread management - creating, joining threads etc.
- Mutexes
- Condition variables
- Synchronization between threads using read/write locks and barriers

Implementations of the API are available on many Unix-like POSIX-conformant operating systems such as FreeBSD, NetBSD, OpenBSD, GNU/Linux, Mac OS X and Solaris. DR-DOS and Microsoft Windows implementations also exist.
Use POSIX calls if cross-platform portability is required. If you are writing networking code that runs exclusively in OS X and iOS, you should generally avoid POSIX networking calls, because they are harder to work with than higher-level APIs. However, if you are writing networking code that must be shared with other platforms, you can use the POSIX networking APIs so that you can use the same code everywhere.

<a name="nsthread"></a>

### NSThread

A simple Objective-C wrapper around pthreads. This makes the code look more familiar in a Cocoa environment. It is a relatively lightweight way to implement multiple paths of execution inside of an application. For example, you can define a thread as a subclass of `NSThread`, which encapsulates the code you want to run in the background.

Though Operation queues is the preferred way to perform tasks concurrently, depending on application there may still be times when you need to create custom threads.
Threads are still a good way to implement code that must run in real time.
Use threads for specific tasks that cannot be implemented in any other way.
If you need more predictable behavior from code running in the background, threads may still offer a better alternative.

_Inter-thread Communication_

- Direct messaging
- Global variables, shared memory, and objects
- Conditions
- Run loop sources
- Ports and sockets
- Message queues
- Cocoa distributed objects

<a name="run-loops"></a>

### Run Loops

Циклы выполнения – часть инфраструктуры, используемой для управления событиями, прибывающими асинхронно в потоке. Ждет данные от одного или нескольких источников, чтобы запустить код на исполнение. Циклы выполнения работают по мониторингу одного или нескольких источников событий для потока. Как только события прибыли, система пробуждает поток и отправляет события на цикл выполнения, который затем передает их указанным обработчикам. Если нет событий готовых быть обработанными, цикл выполнения ставит поток в режим сна.
Одна из опасностей потокового программирования, это конфликты ресурсов между несколькими потоками. Если несколько потоков пытаются использовать или модифицировать один и тот же ресурс в одно и то же время, то могут возникнуть проблемы. Один из способов решить проблему заключается в устранении общего ресурса в целом и убедиться, что каждый поток имеет свой собственный набор ресурсов, на котором он работает.
Run loops are not technically a concurrency mechanism like GCD or operation queues, because they don’t enable the parallel execution of tasks. However, run loops tie in directly with the execution of tasks on the main dispatch/operation queue and they provide a mechanism to execute code asynchronously.
A run loop is always bound to one particular thread. The main run loop associated with the main thread has a central role in each application, because it handles UI events, timers, and other kernel events. Whenever you schedule a timer, use a `NSURLConnection` or call `performSelector:withObject:afterDelay`:, the run loop is used behind the scenes in order to perform these asynchronous tasks. Whenever you use a method which relies on the run loop, it is important to remember that run loops can be run in different modes. Each mode defines a set of events the run loop is going to react to. This is a clever way to temporarily prioritize certain tasks over others in the main run loop.
A typical example of this is scrolling on iOS. While you’re scrolling, the run loop is not running in its default mode, and therefore, it’s not going to react to, for example, a timer you have scheduled before. Once scrolling stops, the run loop returns to the default mode and the events which have been queued up are executed. If you want a timer to fire during scrolling, you need to add it to the run loop in the `NSRunLoopCommonModes` mode. The main thread always has the main run loop set up and running. Other threads though don’t have a run loop configured by default. You can set up a run loop for other threads too, but you will rarely need to do this. Most of the time it is much easier to use the main run loop. If you need to do heavier work that you don’t want to execute on the main thread, you can still dispatch it onto another queue after your code is called from the main run loop.
You can think of a Run Loop to be an event processing for-loop associated to a thread. This is provided by the system for every thread, but it's only run automatically for the main thread. Note that _running run loops and executing a thread are two distinct concepts_. You can execute a thread without running a run loop, when you're just performing long calculations and you don't have to respond to various events. If you want to respond to various events from a secondary thread, you retrieve the run loop associated to the thread by `[NSRunLoop currentRunLoop];` and run it.
A run loop receives events from two different types of sources. Input sources deliver asynchronous events, usually messages from another thread or from a different application. Timer sources deliver synchronous events, occurring at a scheduled time or repeating interval. Both types of source use an application-specific handler routine to process the event when it arrives.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/runloop.jpg">

<https://suelan.github.io/2021/02/13/20210213-dive-into-runloop-ios/>

<a name="nsobject-instance-methods"></a>

### NSObject instance methods

Group of `performSelector` methods and `cancelPreviousPerformRequests` methods

```objectivec
- (void)performSelectorInBackground:(SEL)aSelector withObject:(id)arg;
```

This method creates a new thread in your application, putting your application into multithreaded mode if it was not already. The method represented by aSelector must set up the thread environment just as you would for any other new thread in your program.

<a name="gcd"></a>

### GCD

With GCD you don’t interact with threads directly anymore. Instead you add blocks of code to queues, and GCD manages a thread pool behind the scenes. GCD decides on which particular thread your code blocks are going to be executed on, and it manages these threads according to the available system resources. This alleviates the problem of too many threads being created, because the threads are now centrally managed and abstracted away from application developers. The other important change with GCD is that you as a developer think about work items in a queue rather than threads. This new mental model of concurrency is easier to work with. GCD exposes five different queues: the main queue running on the main thread, three background queues with different priorities, and one background queue with an even lower priority, which is I/O throttled. Furthermore, you can create custom queues, which can either be serial or concurrent queues. While custom queues are a powerful abstraction, all blocks you schedule on them will ultimately trickle down to one of the system’s global queues and its thread pool(s).

__Dispatch Queue__

Dispatch queues are a C-based mechanism for __executing custom tasks__. A dispatch queue executes tasks either serially or concurrently but __always in a FIFO order__. A serial dispatch queue runs only one task at a time, waiting until that task is complete before dequeuing and starting a new one. By contrast, a concurrent dispatch queue starts as many tasks as it can without waiting for already started tasks to finish.

- Serial

Serial queues (also known as private dispatch queues) execute one task at a time in the order in which they are added to the queue. The currently executing task runs on a distinct thread (which can vary from task to task) that is managed by the dispatch queue. Serial queues are often used to synchronize access to a specific resource.
You can create as many serial queues as you need, and each queue operates concurrently with respect to all other queues. In other words, if you create four serial queues, each queue executes only one task at a time but up to four tasks could still execute concurrently, one from each queue.

- Concurrent

Concurrent queues (also known as a type of global dispatch queue) execute one or more tasks concurrently, but tasks are still started in the order in which they were added to the queue. The currently executing tasks run on distinct threads that are managed by the dispatch queue. The exact number of tasks executing at any given point is variable and depends on system conditions.
In iOS 5 and later, you can create concurrent dispatch queues yourself by specifying `DISPATCH_QUEUE_CONCURRENT` as the queue type. In addition, there are four predefined global concurrent queues for your application to use.

- Main dispatch queue

The main dispatch queue is a globally available serial queue that executes tasks on the application’s main thread. This queue works with the application’s run loop (if one is present) to interleave the execution of queued tasks with the execution of other event sources attached to the run loop. Because it runs on your application’s main thread, the main queue is often used as a key synchronization point for an application. Although you do not need to create the main dispatch queue, you do need to make sure your application drains it appropriately.

__Dispatch Source__

Dispatch sources are a C-based mechanism __for processing specific types of system events asynchronously__. A dispatch source encapsulates information about a particular type of system event and submits a specific block object or function to a dispatch queue whenever that event occurs. You can use dispatch sources to monitor the following types of system events:

- Timers
- Signal handlers
- Descriptor-related events
- Process-related events
- Mach port events
- Custom events that you trigger

- async - concurrent: the code runs on a background thread. Control returns immediately to the main thread (and UI). The block can't assume that it's the only block running on that queue
- async - serial: the code runs on a background thread. Control returns immediately to the main thread. The block can assume that it's the only block running on that queue
- sync - concurrent: the code runs on a background thread but the main thread waits for it to finish, blocking any updates to the UI. The block can't assume that it's the only block running on that queue (I could have added another block using async a few seconds previously)
- sync - serial: the code runs on a background thread but the main thread waits for it to finish, blocking any updates to the UI. The block can assume that it's the only block running on that queue

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_queues_scheme.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_functions_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_functions_2.png">

__Плюсы__

- Визуально — он самый короткий и простой в реализации. Он возможен с использованием блоков. Этот подход тоже очень гибкий (хотя отменять блок поставленный в очередь нельзя стандартными способами). В GCD можно настраивать приоритеты, блоки захватывают переменные из окружения блока.

<a name="swift-3-api"></a>

#### Swift 3 API

The QoS classes are:

- __User-interactive__: This represents tasks that need to be done immediately in order to provide a nice user experience. Use it for UI updates, event handling and small workloads that require low latency. The total amount of work done in this class during the execution of your app should be small. This should run on the main thread.
- __User-initiated__: The represents tasks that are initiated from the UI and can be performed asynchronously. It should be used when the user is waiting for immediate results, and for tasks required to continue user interaction. This will get mapped into the high priority global queue.
- __Default__: Default tasks have a lower priority than user-initiated and user-interactive tasks, but a higher priority than utility and background tasks. Assign this class to tasks or queues that your app initiates or uses to perform active work on the user’s behalf.
- __Utility__: This represents long-running tasks, typically with a user-visible progress indicator. Use it for computations, I/O, networking, continous data feeds and similar tasks. This class is designed to be energy efficient. This will get mapped into the low priority global queue.
- __Background__: This represents tasks that the user is not directly aware of. Use it for prefetching, maintenance, and other tasks that don’t require user interaction and aren’t time-sensitive. This will get mapped into the background priority global queue.

```swift
DispatchQueue.global(attributes: [.qosDefault]).async {
  // Background thread
  DispatchQueue.main.async(execute: {
    // UI Updates
  })
}
```

| Тип очереди            | Как создаётся                                              | По умолчанию     | Пояснение                                                                 |
|------------------------|------------------------------------------------------------|------------------|---------------------------------------------------------------------------|
| Main Queue             | DispatchQueue.main                                         | serial           | Главная очередь UI. Только 1 задача за раз, используется для UI-работы.  |
| Global Queue (по QoS)  | DispatchQueue.global(qos: .userInitiated)                  | concurrent       | Параллельная, шарится системой. Не нужно создавать вручную.              |
| Global Queue (default) | DispatchQueue.global()                                     | concurrent       | То же, что global(qos: .default).                                        |
| Custom Serial Queue    | DispatchQueue(label: "my.queue")                           | serial           | Последовательная пользовательская очередь.                               |
| Custom Concurrent Queue| DispatchQueue(label: "my.queue", attributes: .concurrent)  | concurrent       | Параллельная пользовательская очередь.                                   |

<a name="nsoperationqueue"></a>

### NSOperationQueue

Operation queues are a Cocoa abstraction of the queue model exposed by GCD. While GCD offers more low-level control, operation queues implement several convenient features on top of it, which often makes it the best and safest choice for application developers. The `NSOperationQueue` class has two different types of queues: the main queue and custom queues. The main queue runs on the main thread, and custom queues are processed in the background. In any case, the tasks which are processed by these queues are represented as subclasses of `NSOperation`. Whereas dispatch queues always execute tasks in first-in, first-out order, operation queues __take other factors into account when determining the execution order of tasks__. Primary among these factors is whether a given task depends on the completion of other tasks. You configure dependencies when defining your tasks and can use them to create complex execution-order graphs for your tasks. Because the `NSOperation` class is essentially an abstract base class, you typically define custom subclasses to perform your tasks. However, the Foundation framework does include some concrete subclasses that you can create and use as is to perform tasks.

`NSBlockOperation` exectues a block. `NSInvocationOperation` executes a `NSInvocation` (or a method defined by target, selector, object). `NSOperation` must be subclassed, it offers the most flexibility but requires the most code. `NSBlockOperation` and `NSInvocationOperation` are both subclasses of `NSOperation`. They are provided by the system so you don't have to create a new subclass for simple tasks. Using `NSBlockOperation` and `NSInvocationOperation` should be enough for most tasks.

After an operation begins executing, it continues performing its task until it is finished or until your code explicitly cancels the operation. Cancellation can occur at any time, even before an operation begins executing. Although the NSOperation class provides a way for clients to cancel an operation, recognizing the cancellation event is voluntary by necessity. If an operation were terminated outright, there might not be a way to reclaim resources that had been allocated. As a result, operation objects are expected to check for cancellation events and to exit gracefully when they occur in the middle of the operation.

__Плюсы__

- Можно для каждой очереди настраивать приоритет и количество одновременно выполняющихся операций. `NSOperationQueue` самостоятельно создает и поддерживает пул потоков, в которых исполняются `NSOperation`. Так же `NSOperation` предоставляет возможность отменять операции, приостанавливать всю очередь, запускать ее снова и много чего прочего.

<a name="async-await"></a>

### async / await

`async` означает асинхронный, и его можно рассматривать как атрибут метода, показывающий, что метод выполняет асинхронную работу. Чтобы вызвать такой метод, нужно использовать аттрибут `await`.

Плюсы:

- визуальная эстетичность кода. Читать код стало на порядок легче, отчасти от того, что мы избегаем callback hell’ов. Это, в свою очередь, снижает вероятность допустить ошибку - забыть вызвать `completionHandler`, из-за нарушить логику работы программы, теперь нельзя. Да и что тут говорить, код, с закосом под синхронный, стал намного элегантнее. Вот это:

```swift
func obtainFirstCarsharing(completionHandler: @escaping (CarsharingCarDetail?) -> Void) {
    fetchCars { [weak self] cars in
        guard let self = self, let firstCar = cars.first else {
            completionHandler(nil)
            return
        }
        self.fetchCarDetail(withId: firstCar.id) { detail in
            completionHandler(detail)
        }
    }
}
```

Теперь может выглядеть так:

```swift
func obtainFirstCarsharing() async throws -> CarsharingCarDetail {
    let allCars = try await fetchCars()
    guard let firstCarId = allCars.first?.id else { throw NSError() }
    return try await fetchCarDetail(with: firstCarId)
}
```

Асинхронная функция, помимо результирующей модели, может вернуть ошибку - это нормальное поведение, которое разработчик может закладывать. В таком случае у нас есть возможность обрабатывать ошибки посредством try/catch.

`async/await` является неблокирующим механизмом. Сразу отмечу, что неблокирующий тут не равно непрерывный / синхронный. На это слово надо взглянуть под другим ракурсом - неблокирующим механизм является для потока. Что это значит?

Взглянем на примеры:

```swift
let queue = DispatchQueue(label: "citymobil.queue.com")
queue.sync { /* Execute WorkItem */ }
// ----------------------------
let semaphore = DispatchSemaphore(value: 0)
semaphore.wait()
// ----------------------------
let _ = try await service.fetchCars()
```

Рассмотрим поведение потока с очередью, которая вызывает sync-метод — синхронно выполняет какую-нибудь WorkItem-задачу. В месте вызова sync поток блокируется и доступ к нему возвращается только после исполнения sync-замыкания. С семафорами ситуация схожа, если не хуже: они, очевидно, находятся вне философии очередей - могут заблокировать какой-либо поток, в котором выполняется WorkItem, отданный очереди.
В случае с async/await синхронное выполнение метода приостанавливается: точкой приостановки является await, при этом сам поток не простаивает в ожидании.

Тут стоит держать в голове пару моментов:

- Поток, в котором выполнялся код до await, и который подхватил дальнейшее выполнение после, не обязательно будет одним и тем же.
- Несмотря на то, что в сниппете кода нет коллбеков, глобальное состояние приложения во время приостановки (там, где await), может кардинально поменяться - это обязательно нужно держать в голове.

Хочется дополнить механизм работы еще одним примером и сравнить разницу в поведении между новым и старых механизмом.

```swift
let syncQueue = DispatchQueue(label: "queue.sync.com", attributes: .concurrent)
for i in 1...32 {
  DispatchQueue.global().async {
    syncQueue.sync { /* do some work */ }
  }
}
```

Здесь включаются в работу большое количество потоков. При этом каждое переключение между ними (context switch) становится все более ресурсоемким для системы при большом его количестве. Несмотря на то, что чего-то критичного в этих переключениях нет - context switch внутри одного процесса в общем то происходит достаточно быстро, и в большинстве случаев мы можем себе позволить не задумываться о нем - заблокированный поток, де факто, держит свой стек и занимает память. В довесок, мы можем легко воспроизвести ситуацию, где исчерпаем рабочие потоки, тем самым воссоздав thread explosion (взрыв потоков). Мы можем избежать такой ситуации, грамотно спроектировав работу с многопоточным кодом - например, использовать здесь concurrentPerform или ненулевые семафоры. Но Apple, кажется, "встроил" подобные оптимизации в систему:

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/continuation.png">

Аналогичный код, переписанный с async/await, на условном двухъядерном устройстве будет гонять по одному потоку, которые не станут простаивать в ожидании, а стало быть и переключения между ними не будет. Вместо этого, переключение будет происходить преимущественно внутри одного потока между continuation—объектами, и будет сводиться к переключению между методами.

Swift Concurrency works with a cooperative thread pool, meaning that the system actively tries to match the number of threads to the number of available cores. This approach eliminates the issues related to thread explosion, but they require a different approach to dispatch work items. 
 
Instead of using the same work items that GCD uses, Swift concurrency uses a construct called a ”continuation” for asynchronous code. It stores all information needed to suspend and resume an individual task, pushing the suspension point down the hierarchy. This structure means that when a particular method needs to wait for a resource, the thread can pick up another task instead. 

__Актор (actor)__

Сущность, редназначенная для предотвращения состояний гонки (race conditions) в асинхронных классов. Хотя это не новая концепция, акторы являются частью гораздо более крупного замысла. Да, теоретически вы можете реализовать все, что делает актор, просто добавив `NSLock` в свойства/методы ваших классов, но на практике у них есть несколько важных бонусов. Во-первых, механизм синхронизации, используемый акторами, — это не известные нам блокировки, а новая Cooperative Threading Model (модель кооперативной потоковой обработки) async/await в которой потоки могут плавно «изменять» контексты для выполнения других фрагментов кода, чтобы избежать простаивающих потоков, а во-вторых, наличие акторов позволяет компилятору проверить многие проблемы параллелизма прямо во время компиляции, давая вам сразу знать если есть какая-либо потенциальная опасность.

Actor isolation is how actors protect their mutable state. For actors, the primary mechanism for this protection is by only allowing their stored instance properties to be accessed directly on self. For example, here is a method that attempts to transfer money from one account to another:

```swift
actor BankAccount {
  let accountNumber: Int
  var balance: Double

  init(accountNumber: Int, initialDeposit: Double) {
    self.accountNumber = accountNumber
    self.balance = initialDeposit
  }
}

extension BankAccount {
  enum BankError: Error {
    case insufficientFunds
  }
  
  func transfer(amount: Double, to other: BankAccount) throws {
    if amount > balance {
      throw BankError.insufficientFunds
    }

    print("Transferring \(amount) from \(accountNumber) to \(other.accountNumber)")

    balance = balance - amount
    other.balance = other.balance + amount  // error: actor-isolated property 'balance' can only be referenced on 'self'
  }
}
```

__AsyncSequence__

A type that provides asynchronous, sequential, iterated access to its elements.

__Executors__

- The compiler splits async code into jobs. A job roughly corresponds to the code from one await (= potential suspension point) to the next.
- The runtime submits each job to an executor. The executor is the object that decides in which order and in which context (i.e. which thread or dispatch queue) to run the jobs.

Swift ships with two built-in executors: the default concurrent executor, used for “normal”, non-actor-isolated async functions, and a default serial executor. Every actor instance has its own instance of this default serial executor and runs its code on it. Since the serial executor, like a serial dispatch queue, only runs a single job at a time, this prevents concurrent accesses to the actor’s state.

---

__Structured concurrency__

is a programming paradigm aimed at improving the clarity, quality, and development time of a computer program by using a structured approach to concurrent programming. The core concept is the encapsulation of concurrent threads of execution (here encompassing kernel and userland threads and processes) by way of control flow constructs that have clear entry and exit points and that ensure all spawned threads have completed before exit. Such encapsulation allows errors in concurrent threads to be propagated to the control structure's parent scope and managed by the native error handling mechanisms of each particular computer language. It allows control flow to remain readily evident by the structure of the source code despite the presence of concurrency. To be effective, this model must be applied consistently throughout all levels of the program – otherwise concurrent threads may leak out, become orphaned, or fail to have runtime errors correctly propagated. Structured concurrency is analogous to structured programming, which introduced control flow constructs that encapsulated sequential statements and subroutines.

```swift
let x = await calculateFirstNumber()
let y = await calculateSecondNumber()
let z = await calculateThirdNumber()
print(x + y + z)
```

Каждая строка выполняется после того, как предыдущая строка завершает свою работу. Мы создаем три потенциальные точки приостановки и ждем, пока процессор не получит достаточно мощности для выполнения и завершения каждой задачи. Все это происходит в последовательном порядке. А что если мы хотим выполнить эти задачи параллельно, и нам не важны отдельные результаты, но нам нужны все (x,y,z) так быстро, как мы можем?

```swift
async let x = calculateFirstNumber()
async let y = calculateSecondNumber()
async let z = calculateThirdNumber()

let res = await x + y + z
print(res)
```

С концепцией структурированного параллелизма в языке появилось два новых типа данных: `Task` и `TaskGroup`, которые позволяют выполнять параллельные операции индивидуально или скоординировано.

```swift
func runMultipleCalculations() async throws {
  let taskOne = Task {
    (0..<50).map(fibonacci)
  }

  let taskTwo = Task {
    try await getWeatherReadings(for: "Rome")
  }

  let resultOne = await taskOne.value
  let resultTwo = try await taskTwo.value
  print("The first 50 numbers in the Fibonacci sequence are: \(resultOne)")
  print("Rome weather readings are: \(resultTwo)")
}
```

В приведенном выше примере приоритет не задан, поэтому он будет выставлен по умолчанию, но при необходимости его можно задать следующим образом: `Task(priority: .high)`.
Помимо выполнения операций, Task также предоставляет нам несколько статических методов для управления вызовами:

- Вызов `Task.sleep()` переводит текущую задачу спящий режим на определенное количество наносекунд. `1_000_000_000` (миллиард) наносекунд равняется 1 секунде.
- Вызов `Task.checkCancellation()` проверяет не был ли вызван для отмены метод `cancel()`, и если был, то выбросит `CancellationError`.
- Вызов `Task.yield()` приостанавливает текущую задачу на несколько мгновений, чтобы дать некоторое время другим задачам, которые могут ожидать свой очереди. Это особенно важно, если вы выполняете высоко-нагруженную работу в цикле.

<https://docs.swift.org/swift-book/LanguageGuide/Concurrency.html>

<https://developer.apple.com/videos/play/wwdc2021/10254/>

<a name="idle-time-notifications"></a>

### Idle-time notifications

- [Idle-time notifications](#idle-time-notifications)

`NSNotification`
A container for information broadcast through a notification center to all registered observers.

`NSNotificationCenter`
A notification dispatch mechanism that enables the broadcast of information to registered observers.

`NSNotificationQueue`
A notification center buffer.

`NSDistributedNotificationCenter`
A notification dispatch mechanism that enables the broadcast of notifications across task boundaries.

<a name="timers"></a>

### Timers

3 ways to create a timer:

1. Scheduling a timer with the current run loop;
2. Creating a timer that you later register with a run loop;
3. Initializing a timer with a given fire date.

Because the run loop maintains the timer, from the perspective of object lifetimes there’s typically no need to keep a reference to a timer after you’ve scheduled it. (Because the timer is passed as an argument when you specify its method as a selector, you can invalidate a repeating timer when appropriate within that method.) In many situations, however, you also want the option of invalidating the timer—perhaps even before it starts. In this case, you do need to keep a reference to the timer, so that you can stop it whenever appropriate. If you create an unscheduled timer (see Unscheduled Timers), then you must maintain a strong reference to the timer so that it is not deallocated before you use it.

<a name="synchronization"></a>

## Synchronization

<a name="memory-barriers"></a>

### Memory Barriers and Volatile Variables

A memory barrier is a type of nonblocking synchronization tool used to ensure that memory operations occur in the correct order.

Volatile variables apply another type of memory constraint to individual variables. The compiler often optimizes code by loading the values for variables into registers. For local variables, this is usually not a problem. If the variable is visible from another thread however, such an optimization might prevent the other thread from noticing any changes to it. Applying the volatile keyword to a variable forces the compiler to load that variable from memory each time it is used. You might declare a variable as volatile if its value could be changed at any time by an external source that the compiler may not be able to detect.

<a name="atomic"></a>

### Atomic Operations

`/usr/include/libkern/OSAtomic.h`

Atomic operations let you perform simple mathematical and logical operations on 32-bit or 64-bit values. These operations rely on special hardware instructions (and an optional memory barrier) to ensure that the given operation completes before the affected memory is accessed again. In the multithreaded case, you should always use the atomic operations that incorporate a memory barrier to ensure that the memory is synchronized correctly between threads.

Operation types: Add, Increment, Decrement, Logical OR, Logical AND, Logical XOR, Compare and swap, Test and set, Test and clear

<a name="lock"></a>

### Lock

Mechanism for enforcing limits on access to a resource in an environment where there are many threads of execution. A lock is designed to enforce a mutual exclusion concurrency control policy.

A mutually exclusive (or mutex) lock acts as a protective barrier around a resource. A mutex is a type of semaphore that grants access to only one thread at a time. If a mutex is in use and another thread tries to acquire it, that thread blocks until the mutex is released by its original holder. If multiple threads compete for the same mutex, only one at a time is allowed access to it.

---

__POSIX Mutex Lock__

```c
pthread_mutex_t mutex;
void MyInitFunction() {
  pthread_mutex_init(&mutex, NULL);
}

void MyLockingFunction() {
  pthread_mutex_lock(&mutex);
  // Do work.
  pthread_mutex_unlock(&mutex);
}
```

---

__NSLock__

```objectivec
BOOL moreToDo = YES;
NSLock *theLock = [[NSLock alloc] init];
...
while (moreToDo) {
  /* Do another increment of calculation */
  /* until there’s no more to do. */
  if ([theLock tryLock]) {
    /* Update display used by all threads. */
    [theLock unlock];
  }
}
```

The `NSLock` class uses `POSIX` threads to implement its locking behavior. When sending an unlock message to an `NSLock` object, you must be sure that message is sent from the same thread that sent the initial lock message. Unlocking a lock from a different thread can result in undefined behavior.

---

__@synchronized__

```objectivec
- (NSString *)myString {
  @synchronized(self) {
    return [[myString retain] autorelease];
  }
}
```

is transformed into:

```objectivec
- (NSString *)myString {
  NSString *retval = nil;
  pthread_mutex_t *self_mutex = LOOK_UP_MUTEX(self);
  pthread_mutex_lock(self_mutex);
  retval = [[myString retain] autorelease];
  pthread_mutex_unlock(self_mutex);
  return retval;
}
```

As a precautionary measure, the `@synchronized` block implicitly adds an exception handler to the protected code. This handler automatically releases the mutex in the event that an exception is thrown. This means that in order to use the `@synchronized` directive, you must also enable Objective-C exception handling in your code. If you do not want the additional overhead caused by the implicit exception handler, you should consider using the lock classes.

---

__Recursive lock__

A recursive lock is a variant on the mutex lock. A recursive lock allows a single thread to acquire the lock multiple times before releasing it. Other threads remain blocked until the owner of the lock releases the lock the same number of times it acquired it. Recursive locks are used during recursive iterations primarily but may also be used in cases where multiple methods each need to acquire the lock separately. As its name implies, this type of lock is commonly used inside a recursive function to prevent the recursion from blocking the thread. You could similarly use it in the non-recursive case to call functions whose semantics demand that they also take the lock.

```objectivec
NSRecursiveLock *theLock = [[NSRecursiveLock alloc] init];
void MyRecursiveFunction(int value) {
  [theLock lock];
    if (value != 0) {
      --value;
      MyRecursiveFunction(value);
    }
  [theLock unlock];
}
MyRecursiveFunction(5);
```

If you did not use an `NSRecursiveLock` object for this code, the thread would deadlock when the function was called again.

__Read-write lock__

A read-write lock is also referred to as a shared-exclusive lock. This type of lock is typically used in larger-scale operations and can significantly improve performance if the protected data structure is read frequently and modified only occasionally.

__pthread_rwlock__

```c
thread_rwlock_rdlock(p);
newx = ACCESS_ONCE(x);
thread_rwlock_unlock(p);
...
thread_rwlock_wrlock(p);
ACCESS_ONCE(x)++;
thread_rwlock_unlock(p);
```

__GCD dispatch barrier__

Add a `.barrier` flag to mark the added job as a barrier task. It will prevent any other tasks from running in parallel with it, so any tasks added later will wait until this task finishes work. This is useful if you have some tasks that can mostly be run concurrently, but a subset of those tasks requires exclusive access to some resource (e.g. a database for writing) and other tasks can't run until the resource is released.

```c
dispatchQueue.async(qos: .userInitiated, flags: .barrier) {
    // do some work
}
```

__NSOperationQueue Barrier Task__

Call `addBarrierBlock()` on an `OperationQueue`. It works exactly like the `DispatchQueue` version.

```swift
operationQueue.addBarrierBlock {
    // do some work
}
```

_Are sync/async the same thing as barrier?_

Sync/async and barriers are two completely different issues. The sync/async dictates the flow or behavior of the calling thread (i.e. does it wait or not). Barriers dictate the behavior of the queue to which it it was dispatched (whether it’s allowed to run concurrently with any other dispatched blocks to that queue). Note, though, that barriers do not work on global queues; they only affect private concurrent queues that you created. As the docs say about barriers:

> The queue you specify should be a concurrent queue that you create yourself... If the queue you pass to this function is a serial queue or one of the global concurrent queues, this function behaves [as if it were dispatched without the barrier].

---

__Distributed lock__

A distributed lock provides mutually exclusive access at the process level. Unlike a true mutex, a distributed lock does not block a process or prevent it from running. It simply reports when the lock is busy and lets the process decide how to proceed.

---

__Spin lock__

A spin lock polls its lock condition repeatedly until that condition becomes true. Spin locks are most often used on multiprocessor systems where the expected wait time for a lock is small. In these situations, it is often more efficient to poll than to block the thread, which involves a context switch and the updating of thread data structures.

`OSSpinLock` is an integer type.  The convention is that unlocked is zero, and locked is nonzero.  Locks
must be naturally aligned and cannot be in cache-inhibited memory.

`OSSpinLockLock()` will spin if the lock is already held, but employs various strategies to back off, making it immune to most priority-inversion livelocks.  But because it can spin, it may be inefficient
in some situations.

`OSSpinLockTry()` immediately returns false if the lock was held, true if it took the lock.  It does not spin.

`OSSpinLockUnlock()` unconditionally unlocks the lock by zeroing it.

---

__Double-checked lock__

A double-checked lock is an attempt to reduce the overhead of taking a lock by testing the locking criteria prior to taking the lock. Because double-checked locks are potentially unsafe, the system does not provide explicit support for them and their use is discouraged.

---

__Condition lock__

An `NSConditionLock` object defines a mutex lock that can be locked and unlocked with specific values. You should not confuse this type of lock with a condition. The behavior is somewhat similar to conditions, but is implemented very differently. Typically, you use an `NSConditionLock` object when threads need to perform tasks in a specific order, such as when one thread produces data that another consumes. While the producer is executing, the consumer acquires the lock using a condition that is specific to your program. (The condition itself is just an integer value that you define.) When the producer finishes, it unlocks the lock and sets the lock condition to the appropriate integer value to wake the consumer thread, which then proceeds to process the data.

<a name="semaphore"></a>

### Semaphore

_Is the number of free identical toilet keys. Example, say we have four toilets with identical locks and keys. The semaphore count - the count of keys - is set to 4 at beginning (all four toilets are free), then the count value is decremented as people are coming in. If all toilets are full, ie. there are no free keys left, the semaphore count is 0. Now, when eq. one person leaves the toilet, semaphore is increased to 1 (one free key), and given to the next person in the queue._

Variable or abstract data type used to control access to a common resource by multiple processes in a concurrent system. A trivial semaphore is a plain variable that is changed (for example, incremented or decremented, or toggled) depending on programmer-defined conditions. The variable is then used as a condition to control access to some system resource. A useful way to think of a semaphore as used in the real-world systems is as a record of how many units of a particular resource are available, coupled with operations to adjust that record safely (i.e. to avoid race conditions) as units are required or become free, and, if necessary, wait until a unit of the resource becomes available. Semaphores are a useful tool in the prevention of race conditions; however, their use is by no means a guarantee that a program is free from these problems. Semaphores which allow an arbitrary resource count are called __counting semaphores__, while semaphores which are restricted to the values 0 and 1 (or locked/unlocked, unavailable/available) are called __binary semaphores__ and are used to implement locks.

Семафор позволяет выполнять какой-либо участок кода одновременно только конкретному количеству потоков. В основе семафора лежит счетчик, который и определяет, можно ли выполнять участок кода текущему потоку или нет. Если счетчик больше нуля — поток выполняет код, в противном случае — нет.Семафор в GCD представлен типом `dispatch_semaphore_t`. Для создания семафора существует функция `dispatch_semaphore_create`, которая принимает один аргумент — число потоков, которые могут одновременно выполнять участок кода.

__How to implement max concurrent functionality__

```c
dispatch_semaphore_t concurrencyLimitingSemaphore = dispatch_semaphore_create(limit);
//do this part once per task, for example in a loop
dispatch_semaphore_wait(concurrencyLimitingSemaphore, DISPATCH_TIME_FOREVER);
dispatch_async(someConcurrentQueue, ^{
    /* work goes here */
    dispatch_semaphore_signal(concurrencyLimitingSemaphore);
}
```

__Conditions__

A condition is another type of semaphore that allows threads to signal each other when a certain condition is true. Conditions are typically used to indicate the availability of a resource or to ensure that tasks are performed in a specific order. When a thread tests a condition, it blocks unless that condition is already true. It remains blocked until some other thread explicitly changes and signals the condition. The difference between a condition and a mutex lock is that multiple threads may be permitted access to the condition at the same time. The condition is more of a gatekeeper that lets different threads through the gate depending on some specified criteria.

1. POSIX Conditions
2. NSCondition

<a name="mutex"></a>

### Mutex

_Is a key to a toilet. One person can have the key - occupy the toilet - at the time. When finished, the person gives (frees) the key to the next person in the queue._

Мьютекс является одним из видов семафора, который предоставляет доступ одновременно только одному потоку. Если мьютекс используется и другой поток пытается получить его, что поток блокируется до тех пор, пока мьютекс не освободится от своего первоначального владельца. Если несколько потоков соперничают за одни и те же мьютексы, только одному будет разрешен к нему доступ.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/mutex.png">

<a name="performance"></a>

### Performance

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/lock_performance.png">

`@synchronized` is very heavy weight because it has to set up an exception handler, and it actually ends up taking a few internal locks on its way there.  So instead of a simple cheap lock, you’re paying for a couple locks/unlocks just to acquire your measly lock.  Those take time.

`OSSpinLock`, on the other hand, doesn’t even enter the kernel — it just keeps reloading the lock, hoping that it’s unlocked.  This is terribly inefficient if locks are held for more than a few nanoseconds, but it saves a costly system call and a couple context switches. Pthread mutexes actually use an `OSSpinLock` first, to keep things running smoothly where there’s no contention.  When there is, it resorts to heavier, kernel-level locking/tasking stuff.

So, if you’ve got hotly-contested locks, OSSpinLock probably isn’t for you (unless your critical sections are really fast). Pthread mutexes are a tiny bit more expensive, but they avoid the power-wasting effects of `OSSpinLock`.

`NSLock` is a pretty wrapper on pthread mutexes. They don’t provide much else, so there’s not much point in using them over pthread mutexes.

<a name="diff"></a>

### Differences

__semaphore vs. mutex vs. lock__

__Explanation 1__

A mutex is essentially the same thing as a binary semaphore and sometimes uses the same basic implementation. The differences between them are in how they are used. While a binary semaphore may be used as a mutex, a mutex is a more specific use-case, in that only the thread that locked the mutex is supposed to unlock it.
A mutex is a synchronization object. You acquire a lock on a mutex at the beginning of a section of code, and release it at the end, in order to ensure that no other thread is accessing the same data at the same time. A mutex typically has a lifetime equal to that of the data it is protecting, and that one mutex is accessed by multiple threads.
A lock object is an object that encapsulates that lock. When the object is constructed it acquires the lock on the mutex. When it is destructed the lock is released. You typically create a new lock object for every access to the shared data.

__Explanation 2__

A mutex is an object which can be locked. A lock is the object which maintains the lock. To create a lock, you need to pass it a mutex.

__Explanation 3__

A Mutex is different than a semaphore as it is a locking mechanism while a semaphore is a signalling mechanism. A binary semaphore can be used as a Mutex but a Mutex can never be used as a semaphore

<a name="race-condition"></a>

## Что такое гонка условий?

Can always happen if multiple threads access a shared resource without making sure that one thread is finished operating on a resource before another one begins accessing it.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/race_condition.png">

<a name="deadlock"></a>

### Deadlock

Two or more competing tasks are each waiting on the other to finish. You can observe this in real life when cars arrive simultaneously at a four-way stop.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/deadlock.png">

```swift
let queue = DispatchQueue(label: "my-queue")
queue.sync {
  print("print this")

  queue.sync {
    print("deadlocked")
  }
}
```

Putting this code anywhere in your app will immediately result in a crash before the second print statement runs. The queue is running code synchronously. The second closure can't run until the first one completes. The first closure can't complete until the second closure is run since its dispatched synchronously.

<a name="livelock"></a>

### Livelock

Система не застревает, но занимается бесполезной работой. A livelock occurs when a request for an exclusive lock is repeatedly denied because a series of overlapping shared locks keep interfering. It is an endless loop in program execution. This could be a case when two threads exit allowing each other to write to or update record(s) in a database.

Here's a very simple Java example of livelock where a husband and wife are trying to eat soup, but only have one spoon between them. Each spouse is too polite, and will pass the spoon if the other has not yet eaten.

```java
public class Livelock {
    static class Spoon {
        private Diner owner;
        public Spoon(Diner d) { owner = d; }
        public Diner getOwner() { return owner; }
        public synchronized void setOwner(Diner d) { owner = d; }
        public synchronized void use() {
            System.out.printf("%s has eaten!", owner.name);
        }
    }

    static class Diner {
        private String name;
        private boolean isHungry;

        public Diner(String n) { name = n; isHungry = true; }       
        public String getName() { return name; }
        public boolean isHungry() { return isHungry; }

        public void eatWith(Spoon spoon, Diner spouse) {
            while (isHungry) {
                // Don't have the spoon, so wait patiently for spouse.
                if (spoon.owner != this) {
                    try { Thread.sleep(1); }
                    catch(InterruptedException e) { continue; }
                    continue;
                }                       

                // If spouse is hungry, insist upon passing the spoon.
                if (spouse.isHungry()) {                    
                    System.out.printf(
                        "%s: You eat first my darling %s!%n",
                        name, spouse.getName());
                    spoon.setOwner(spouse);
                    continue;
                }

                // Spouse wasn't hungry, so finally eat
                spoon.use();
                isHungry = false;               
                System.out.printf(
                    "%s: I am stuffed, my darling %s!%n",
                    name, spouse.getName());                
                spoon.setOwner(spouse);
            }
        }
    }

    public static void main(String[] args) {
        final Diner husband = new Diner("Bob");
        final Diner wife = new Diner("Alice");

        final Spoon s = new Spoon(husband);

        new Thread(new Runnable() {
            public void run() { husband.eatWith(s, wife); }   
        }).start();

        new Thread(new Runnable() {
            public void run() { wife.eatWith(s, husband); }
        }).start();
    }
}
```

Run the program and you'll get:

```
Bob: You eat first my darling Alice!
Alice: You eat first my darling Bob!
Bob: You eat first my darling Alice!
Alice: You eat first my darling Bob!
Bob: You eat first my darling Alice!
Alice: You eat first my darling Bob!
...
```

This will go on forever if uninterrupted. This is a livelock because both Alice and Bob are repeatedly asking each other to go first in an infinite loop (hence live). In a deadlock situation, both Alice and Bob would simply be frozen waiting on each other to go first — they won't be doing anything except wait (hence dead).

<a name="starvation"></a>

### Starvation

Locking shared resources can result in the readers-writers problem. Taking a reading lock is allowed as long as there is no writing lock on the resource. In this situation, a thread that is waiting to acquire a write lock can be starved by more read locks occurring in the meantime.

<a name="priority-inversion"></a>

### Priority inversion

The problem can occur when you have a high-priority and a low-priority task share a common resource. When the low-priority task takes a lock to the common resource, it is supposed to finish off quickly in order to release its lock and to let the high-priority task execute without significant delays. Since the high-priority task is blocked from running as long as the low-priority task has the lock, there is a window of opportunity for medium-priority tasks to run and to preempt the low-priority task, because the medium-priority tasks have now the highest priority of all currently runnable tasks. At this moment, the medium-priority tasks hinder the low-priority task from releasing its lock, therefore effectively gaining priority over the still waiting, high-priority tasks.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/priority_inversion.png">

<a name="как-избежать-гонки-условий"></a>

### Как избежать гонки условий

The best way to avoid both deadlock and livelock situations is to take only one lock at a time. If you must acquire more than one lock at a time, you should make sure that other threads do not try to do something similar.

- Avoid Synchronization Altogether

The best way to implement concurrency is to reduce the interactions and inter-dependencies between your concurrent tasks. If each task operates on its own private data set, it does not need to protect that data using locks. Even in situations where two tasks do share a common data set, you can look at ways of partitioning that set or providing each task with its own copy.

- Understand the Limits of Synchronization

Synchronization tools are effective only when they are used consistently by all threads in an application. If you create a mutex to restrict access to a specific resource, all of your threads must acquire the same mutex before trying to manipulate the resource. Failure to do so defeats the protection offered by the mutex and is a programmer error.

- Watch Out for Deadlocks and Livelocks

The best way is to take only one lock at a time. If you must acquire more than one lock at a time, you should make sure that other threads do not try to do something similar.

- Use Volatile Variables Correctly

<a name="dispatch_sync-dispatch_async"></a>

# Чем отличается dispatch_async от dispatch_sync?

Когда это возможно, асинхронное выполнение с использованием `dispatch_async` и `dispatch_async_f` функций предпочтительнее, чем синхронный вариант. При добавлении объекта блока или функции в очередь, нет никакого способа узнать, когда этот код будет выполняться. В результате, добавляя блоки или функции асинхронно позволяет запланировать выполнение кода и продолжать делать другую работу из вызывающего потока. Это особенно важно, если вы планировали выполнить задачу из основного потока приложения, возможно, в ответ на некоторые пользовательские события.
Хотя вы должны добавлять задачи асинхронно по мере возможности, все же могут быть случаи, когда вам нужно добавить задачу синхронно, чтобы предотвратить гонку условий или другие ошибки синхронизации. В этих случаях можно использовать функции `dispatch_sync` и `dispatch_sync_f` для добавления задачи в очередь. Эти функции блокируют текущий поток исполнения до завершения выполнения указанной задачи.

__Важно:__ Вы никогда не должны вызывать функции `dispatch_sync` или `dispatch_sync_f` из задачи, которая выполняется в той же очереди, в которой вы планируете переход к функции. Это особенно важно для последовательных очередей, которые гарантированно приведут к deadlock, но также следует избегать одновременных очередей.

Следующий пример показывает, как использовать блочные варианты для отправки задачи асинхронно и синхронно:

```objectivec
dispatch_queue_t myCustomQueue;
myCustomQueue = dispatch_queue_create("com.example.MyCustomQueue", NULL);

dispatch_async(myCustomQueue, ^{
  printf("Сделайте некую работу здесь.\n");
});
printf("Первый блок может работать или может не работать.\n");

dispatch_sync(myCustomQueue, ^{
  printf("Сделайте еще некую работу здесь.\n");
});
printf("Оба блока были завершены.\n");
```

| Очередь         | async                     | sync                                           |
|-----------------|---------------------------|------------------------------------------------|
| serial          | Не блокирует вызывающий   | Блокирует вызывающий, задачи выполняются по порядку |
| concurrent      | Не блокирует вызывающий, задачи могут идти параллельно | Блокирует вызывающий, задачи по-прежнему идут по порядку (для этого потока), но очередь может выполнять другие задачи параллельно |
| main (главная)  | Не блокирует, если из фонового потока | Deadlock, если вызвать из самой main очереди! |

<a name="многопоточность-uikit"></a>

# Как многопоточность работает с UIKit?

In Cocoa Touch, the `UIApplication` i.e. the instance of your application is attached to the main thread because this thread is created by `UIApplicatioMain()`, the entry point function of Cocoa Touch. It sets up main event loop, including the application’s run loop, and begins processing events. Application's main event loop receives all the UI events i.e. touches, gestures etc. These application UI events are further forwarded to `UIResponder`'s following the chain of responders usually like `UIApplication->UIWindow->UIViewController->UIView->subviews (UIButton, etc...)` Responders handle events like button press, tap, pinch zoom, swipe etc. which get translated as change in the UI. Hence as you can see these chain of events occur on main thread which is why UIKit, the framework which contains the responders should operate on main thread.
One of the most common mistakes even experienced iOS/Mac developers make is accessing parts of UIKit/AppKit on background threads. It’s very easy to make the mistake of setting properties like image from a background thread, because their content is being requested from the network in the background anyway. Apple’s code is performance-optimized and will not warn you if you change properties from different threads. For the most part, UIKit classes should be used only from an application’s main thread. This is particularly true for classes derived from `UIResponder` or that involve manipulating your application’s user interface in any way.

<a name="atomic-vs-nonatomic"></a>

# Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?

Cинхронизировать чтение/запись между потоками или нет.
Atomic – thread safe.
Тут все сложнее и неоднозначнее, есть ряд способов как сделать threadsafe аксессоры к пропертям. Самый простой способ это сделать – добавить конструкцию `@synchronized`:

```objectivec
- (NSString *)foo {
  @synchronized(self) {
    return foo;
  }
}

- (void)setFoo:(NSString)newFoo {
  @synchronized(self) {
    if (foo != newFoo) {
      [foo release];
      foo = [newFoo retain];
    }
  }
}
```

Таким образом используя `@synchronized` мы лочим по ключу `self` доступ к `foo`, однако у такого метода есть очевидный недостаток, если в классе будет две переменные (или 100500) к которым нужен одновременный доступ с разных потоков, то они будут лочиться и друг относительно друга, т.к `self` для них один и тот же, в таких случаях нужно использовать другие методы лока, как `NSLock`, `NSRecursiveLock`,...

<a name="отмена-операций"></a>

# Можно ли отменить операцию в GCD? А в NSOperationQueue?

__GCD (Grand Central Dispatch)__

•	GCD не поддерживает полноценную отмену задач после их запуска.

•	Можно использовать DispatchWorkItem, у которого есть методы:

•	.cancel() — отменяет блок до его выполнения.

•	.isCancelled — проверяется внутри блока для ручной отмены.

•	Нельзя отменить уже выполняющийся async-блок.

•	Приостановка (suspend/resume) возможна только для пользовательских очередей, не для .main или глобальных.

```swift
let workItem = DispatchWorkItem {
    if workItem.isCancelled { return }
    print("Работа началась")
}

DispatchQueue.global().async(execute: workItem)

// Позднее...
workItem.cancel()
```

__NSOperationQueue (или OperationQueue в Swift)__

Поддерживает:

•	.cancelAllOperations() — отмена всех операций в очереди.

•	.cancel() — отмена конкретной Operation.

•	Класс Operation (или BlockOperation) имеет флаг isCancelled, который можно проверять в коде.

•	Очередь можно приостановить с помощью queue.isSuspended = true.

•	Можно задавать зависимости между операциями и контролировать их выполнение.

```swift
let queue = OperationQueue()
let operation = BlockOperation {
    if operation.isCancelled { return }
    print("Операция выполняется")
}

queue.addOperation(operation)

// Позднее...
operation.cancel()
```


<a name="gcd-vs-nsoperationqueue"></a>

# Когда лучше использовать GCD, а когда NSOperationQueue?

`NSOperationQueue` can be more suitable for long-running operations that may need to be cancelled or have complex dependencies.

GCD dispatch queues are better for short tasks that should have minimum performance and memory overhead.

| Возможность                     | GCD (`DispatchQueue`)                      | NSOperationQueue (`OperationQueue`)          |
|---------------------------------|--------------------------------------------|----------------------------------------------|
| Отмена до начала выполнения     | ✅ `DispatchWorkItem.cancel()`             | ✅ `operation.cancel()`                       |
| Отмена во время выполнения      | ✅ Только вручную через `isCancelled`      | ✅ При проверке `isCancelled` внутри блока    |
| Приостановка очереди            | ✅ `queue.suspend()` (только custom)       | ✅ `queue.isSuspended = true`                 |
| Возобновление очереди           | ✅ `queue.resume()`                        | ✅ `queue.isSuspended = false`                |
| Ограничение параллелизма        | ⚠️ Только serial/concurrent                | ✅ `maxConcurrentOperationCount`              |
| Задание приоритета (QoS)        | ✅ `DispatchQoS` при создании очереди      | ✅ `qualityOfService`                         |
| Зависимости между задачами      | ❌                                          | ✅ `addDependency()`                          |
| Повторное использование         | ⚠️ Только вручную через блоки              | ✅ Через наследование от `Operation`          |
| Проверка отмены в задаче        | ✅ `isCancelled` у `DispatchWorkItem`      | ✅ `isCancelled` у `Operation`                |
| Асинхронная операция со статусами | ❌ Нет                                   | ✅ Да (isExecuting, isFinished)              |


<a name="gcd-vs-async-await"></a>

# Difference between GCD and async/await

**How GCD works**

Since a concurrent queue can handle multiple work items at once, the system will bring up several threads until we have saturated all the CPU cores. If a thread blocks and there is more work to be done on the concurrent queue, GCD will bring up more threads to drain the remaining work items. In GCD, it's easy to have excessive concurrency:

- Overcommitting the system with more threads than CPU cores (e.g., Apple Watch only has 2 cores)
- Risk of thread explosion

Too many threads come with performance costs:

- Memory overhead - as each blocked thread is holding onto valuable memory and resources while waiting to run again
- Scheduling overhead - as new threads are brought up, the CPU need to perform a full thread context switch in order to switch away from the old thread to start executing the new thread

> In computing, a context switch is the process of storing the state of a process or of a thread, so that it can be restored and execution resumed from the same point later. This allows multiple processes to share a single CPU, and is an essential feature of a multitasking operating system.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/context_switch.png">

**How async/await works**

- have one thread running on each cpu core - create only as many threads as there are CPU cores
- replace blocked threads with lightweight objects called continuations to track resumption of work - this way threads are be able to cheaply and efficiently switch between work items when they are blocked
- no context switches - instead of a full thread context switch, swapping continuations comes has the cost of a function call

*How sync functions work*

- Every thread in a running program has one stack, which it uses to store state for function calls
- When the thread executes a function call, a new frame is pushed onto its stack
- This newly created stack frame can be used by the function to store parameters, local variables, the return address, and any other information that is needed
- Once the function finishes executing and returns, its stack frame is popped

*How async functions work*

- like for non-async functions, the stack frame stores local variables that do not need to be available across suspension points (a.k.a. await calls)
- async functions will also have an associated frame stored in the heap
- async frames (a.k.a. the async function frame in the heap) store information that does need to be available across suspension points
instead of adding new stack frames across function calls, the top most stack frame is replaced when any variables that will be needed in the future will already have been stored in the list of async frames
- suppose the execution of an async function is suspended, and the thread is reused to do some other useful work instead of being blocked
- since all information that is maintained across a suspension point is stored on the heap, it can be used to continue execution at a later stage
- this also means that the stack frame can be (and is) safely destroyed
- this list of async frames is the runtime representation of a `continuation`
- once we resume (in the same or another thread), we create again its stack frame and continue its execution with the info from the heap