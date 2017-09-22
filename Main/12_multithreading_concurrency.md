- [Multithreading and concurrency](#multithreading-and-concurrency)
	- [Основные понятия многопоточности](#основные-понятия-многопоточности)
	- [API для работы с многопоточностью и их альтернативы](#multithreading-api-alternatives)
		- [POSIX Threads](#posix-threads)
		- [NSThread](#nsthread)
		- [Run Loops](#run-loops)
		- [NSObject instance methods](#nsobject-instance-methods)
		- [GCD](#gcd)
		- [NSOperationQueue](#nsoperationqueue)
		- [Idle-time notifications](#idle-time-notifications)
		- [Asynchronous functions](#asynchronous-functions)
		- [Timers]((#timers)
		- [Separate processes](#separate-processes)
	- [Что такое мьютекс?](#мьютекс)
	- [Что такое deadlock?](#deadlock)
	- [Что такое livelock?](#livelock)
	- [Что такое семафор?](#семафор)
	- [Чем отличается dispatch_async от dispatch_sync?](#dispatch_sync-dispatch_async)
	- [Как многопоточность работает с UIKit?](#многопоточность-uikit)
	- [Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?](#atomic-vs-nonatomic)
	- [Что такое гонка условий?](#race-condition)

<a name="multithreading-and-concurrency"></a>
# Multithreading and concurrency
__Multithreading__

Depending on your application, there may still be times when you need to create custom threads. If you do create custom threads, you should strive to create as few threads as possible yourself and you should use those threads only for specific tasks that cannot be implemented any other way.
Threads are still a good way to implement code that must run in real time. Dispatch queues make every attempt to run their tasks as fast as possible but they do not address real time constraints. If you need more predictable behavior from code running in the background, threads may still offer a better alternative.

__Concurrency__

Concurrency is the notion of multiple things happening at the same time. Threads are subunits of processes, which can be scheduled independently by the operating system scheduler. Virtually all concurrency APIs are built on top of threads under the hood – that’s true for both Grand Central Dispatch and operation queues. You can either use the POSIX thread API, or the Objective-C wrapper around this API, `NSThread`, to create your own threads.



<a name="основные-понятия-многопоточности"></a>
## Основные понятия многопоточности


__thread__

Is used to refer to a separate path of execution for code. Inside each program, however, exists one or more threads of execution, which can be used to perform different tasks simultaneously or in a nearly simultaneous manner. The system itself actually manages these threads of execution, scheduling them to run on the available cores and preemptively interrupting them as needed to allow other threads to run. The threads we’ve been talking about so far have been software threads. They’re (generally) independent units of computation. The hardware threads are based on the number of cores on the computer.
At the application level, all threads behave in essentially the same way as on other platforms. After starting a thread, the thread runs in one of three main states: running, ready, or blocked. If a thread is not currently running, it is either blocked and waiting for input or it is ready to run but not scheduled to do so yet. The thread continues moving back and forth among these states until it finally exits and moves to the terminated state. When you create a new thread, you must specify an entry-point function (or an entry-point method in the case of Cocoa threads) for that thread. This entry-point function constitutes the code you want to run on the thread. When the function returns, or when you terminate the thread explicitly, the thread stops permanently and is reclaimed by the system. Because threads are relatively expensive to create in terms of memory and time, it is therefore recommended that your entry point function do a significant amount of work or set up a run loop to allow for recurring work to be performed.

__process__

Is used to refer to a running executable, which can encompass multiple threads. It keeps track of what needs to be done and delegates the tasks to the threads. A process can have one or multiple threads. The process is like a project manager and the thread is like a worker.

__task__

Is used to refer to the abstract concept of work that needs to be performed

<a name="multithreading-api-alternatives"></a>
## API для работы с многопоточностью и их альтернативы

<a name="posix-threads"></a>
### POSIX Threads
Usually referred to as Pthreads, is a POSIX standard for threads defines an API for creating and manipulating threads. Pthreads defines a set of C programming language types, functions and constants. It is implemented with a pthread.h header and a thread library. There are around 100 Pthreads procedures, all prefixed `pthread_` and they can be categorized into four groups:

* Thread management - creating, joining threads etc.
* Mutexes
* Condition variables
* Synchronization between threads using read/write locks and barriers

Implementations of the API are available on many Unix-like POSIX-conformant operating systems such as FreeBSD, NetBSD, OpenBSD, GNU/Linux, Mac OS X and Solaris. DR-DOS and Microsoft Windows implementations also exist.
Use POSIX calls if cross-platform portability is required. If you are writing networking code that runs exclusively in OS X and iOS, you should generally avoid POSIX networking calls, because they are harder to work with than higher-level APIs. However, if you are writing networking code that must be shared with other platforms, you can use the POSIX networking APIs so that you can use the same code everywhere.

<a name="nsthread"></a>
## NSThread
A simple Objective-C wrapper around pthreads. This makes the code look more familiar in a Cocoa environment. It is a relatively lightweight way to implement multiple paths of execution inside of an application. For example, you can define a thread as a subclass of `NSThread`, which encapsulates the code you want to run in the background.

Though Operation queues is the preferred way to perform tasks concurrently, depending on application there may still be times when you need to create custom threads.
Threads are still a good way to implement code that must run in real time.
Use threads for specific tasks that cannot be implemented in any other way.
If you need more predictable behavior from code running in the background, threads may still offer a better alternative.

<a name="run-loops"></a>
## Run Loops
Циклы выполнения – часть инфраструктуры, используемой для управления событиями, прибывающими асинхронно в потоке. Ждет данные от одного или нескольких источников, чтобы запустить код на исполнение. Циклы выполнения работают по мониторингу одного или нескольких источников событий для потока. Как только события прибыли, система пробуждает поток и отправляет события на цикл выполнения, который затем передает их указанным обработчикам. Если нет событий готовых быть обработанными, цикл выполнения ставит поток в режим сна.
Одна из опасностей потокового программирования, это конфликты ресурсов между несколькими потоками. Если несколько потоков пытаются использовать или модифицировать один и тот же ресурс в одно и то же время, то могут возникнуть проблемы. Один из способов решить проблему заключается в устранении общего ресурса в целом и убедиться, что каждый поток имеет свой собственный набор ресурсов, на котором он работает. Поддержание совершенно разных ресурсов, это не вариант, и для синхронизации доступа к ресурсу придется прибегать к помощи замков, условий, атомарных операций, и других методов.
Замки обеспечивают грубую форму силы для защиты кода, который может быть выполнен только одним потоком одновременно. Наиболее распространенный тип блокировки взаимного исключения блокировки, также известный как мьютекс. Кроме замков, система обеспечивает поддержку для условий, которые обеспечивают надлежащую последовательность задач в рамках вашего приложения. Условие действует как привратник, блокируя определенный поток до приведения определенного состояния в значение истина. Когда это произойдет, поток освобождается и продолжает выполняться. И POSIX и Foundation framework оба оказывают прямую поддержку условий.
Run loops are not technically a concurrency mechanism like GCD or operation queues, because they don’t enable the parallel execution of tasks. However, run loops tie in directly with the execution of tasks on the main dispatch/operation queue and they provide a mechanism to execute code asynchronously. Run loops can be a lot easier to use than operation queues or GCD, because you don’t have to deal with the complexity of concurrency and still get to do things asynchronously.
A run loop is always bound to one particular thread. The main run loop associated with the main thread has a central role in each Cocoa and CocoaTouch application, because it handles UI events, timers, and other kernel events. Whenever you schedule a timer, use a `NSURLConnection` or call `performSelector:withObject:afterDelay`:, the run loop is used behind the scenes in order to perform these asynchronous tasks. Whenever you use a method which relies on the run loop, it is important to remember that run loops can be run in different modes. Each mode defines a set of events the run loop is going to react to. This is a clever way to temporarily prioritize certain tasks over others in the main run loop. A typical example of this is scrolling on iOS. While you’re scrolling, the run loop is not running in its default mode, and therefore, it’s not going to react to, for example, a timer you have scheduled before. Once scrolling stops, the run loop returns to the default mode and the events which have been queued up are executed. If you want a timer to fire during scrolling, you need to add it to the run loop in the `NSRunLoopCommonModes` mode. The main thread always has the main run loop set up and running. Other threads though don’t have a run loop configured by default. You can set up a run loop for other threads too, but you will rarely need to do this. Most of the time it is much easier to use the main run loop. If you need to do heavier work that you don’t want to execute on the main thread, you can still dispatch it onto another queue after your code is called from the main run loop.
You can think of a Run Loop to be an event processing for-loop associated to a thread. This is provided by the system for every thread, but it's only run automatically for the main thread. Note that _running run loops and executing a thread are two distinct concepts_. You can execute a thread without running a run loop, when you're just performing long calculations and you don't have to respond to various events. If you want to respond to various events from a secondary thread, you retrieve the run loop associated to the thread by `[NSRunLoop currentRunLoop];` and run it. The events run loops can handle is called input sources. You can add input sources to a run loop.


<a name="gcd"></a>
## GCD
With GCD you don’t interact with threads directly anymore. Instead you add blocks of code to queues, and GCD manages a thread pool behind the scenes. GCD decides on which particular thread your code blocks are going to be executed on, and it manages these threads according to the available system resources. This alleviates the problem of too many threads being created, because the threads are now centrally managed and abstracted away from application developers. The other important change with GCD is that you as a developer think about work items in a queue rather than threads. This new mental model of concurrency is easier to work with. GCD exposes five different queues: the main queue running on the main thread, three background queues with different priorities, and one background queue with an even lower priority, which is I/O throttled. Furthermore, you can create custom queues, which can either be serial or concurrent queues. While custom queues are a powerful abstraction, all blocks you schedule on them will ultimately trickle down to one of the system’s global queues and its thread pool(s).
Dispatch queues are a C-based mechanism for executing custom tasks. A dispatch queue executes tasks either serially or concurrently but always in a first-in, first-out order. (In other words, a dispatch queue always dequeues and starts tasks in the same order in which they were added to the queue.) A serial dispatch queue runs only one task at a time, waiting until that task is complete before dequeuing and starting a new one. By contrast, a concurrent dispatch queue starts as many tasks as it can without waiting for already started tasks to finish.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_queues_scheme.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_functions_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_functions_2.png">

__Плюсы__

* Визуально — он самый короткий и простой в реализации. Он возоможен с использованием блоков. Этот подход тоже очень гибкий (хотя отменять блок поставленный в очередь нельзя стандартными способами). В GCD можно настраивать приоритеты, блоки захватывают переменные из окружения блока.

Types of dispatch queues

__Serial__

Serial queues (also known as private dispatch queues) execute one task at a time in the order in which they are added to the queue. The currently executing task runs on a distinct thread (which can vary from task to task) that is managed by the dispatch queue. Serial queues are often used to synchronize access to a specific resource.
You can create as many serial queues as you need, and each queue operates concurrently with respect to all other queues. In other words, if you create four serial queues, each queue executes only one task at a time but up to four tasks could still execute concurrently, one from each queue.

__Concurrent__

Concurrent queues (also known as a type of global dispatch queue) execute one or more tasks concurrently, but tasks are still started in the order in which they were added to the queue. The currently executing tasks run on distinct threads that are managed by the dispatch queue. The exact number of tasks executing at any given point is variable and depends on system conditions.
In iOS 5 and later, you can create concurrent dispatch queues yourself by specifying `DISPATCH_QUEUE_CONCURRENT` as the queue type. In addition, there are four predefined global concurrent queues for your application to use.

__Main dispatch queue__

The main dispatch queue is a globally available serial queue that executes tasks on the application’s main thread. This queue works with the application’s run loop (if one is present) to interleave the execution of queued tasks with the execution of other event sources attached to the run loop. Because it runs on your application’s main thread, the main queue is often used as a key synchronization point for an application.
Although you do not need to create the main dispatch queue, you do need to make sure your application drains it appropriately.

<a name="nsoperationqueue"></a>
## NSOperationQueue
Operation queues are a Cocoa abstraction of the queue model exposed by GCD. While GCD offers more low-level control, operation queues implement several convenient features on top of it, which often makes it the best and safest choice for application developers. The `NSOperationQueue` class has two different types of queues: the main queue and custom queues. The main queue runs on the main thread, and custom queues are processed in the background. In any case, the tasks which are processed by these queues are represented as subclasses of `NSOperation`. Whereas dispatch queues always execute tasks in first-in, first-out order, operation queues take other factors into account when determining the execution order of tasks. Because the `NSOperation` class is essentially an abstract base class, you typically define custom subclasses to perform your tasks. However, the Foundation framework does include some concrete subclasses that you can create and use as is to perform tasks.

__Плюсы__

* Можно для каждой очереди настраивать приоритет и количество одновременно выполняющихся операций. `NSOperationQueue` самостоятельно создает и поддерживает пул потоков, в которых исполняются `NSOperation`. Так же `NSOperation` предоставляет возможность отменять операции, приостанавливать всю очередь, запускать ее снова и много чего прочего.

<a name="nsobject-instance-methods"></a>
## NSObject instance methods
```objectivec
- (void)performSelector:(SEL)aSelector onThread:(NSThread *)thread withObject:(id)arg waitUntilDone:(BOOL)wait;
- (void)performSelector:(SEL)aSelector onThread:(NSThread *)thread withObject:(id)arg waitUntilDone:(BOOL)wait mo-des:(NSArray *)array;
- (void)performSelector:(SEL)aSelector withObject:(id)anArgument afterDelay:(NSTimeInterval)delay;
- (void)performSelector:(SEL)aSelector withObject:(id)anArgument afterDelay:(NSTimeInterval)delay inModes:(NSArray *)modes;
- (void)performSelectorInBackground:(SEL)aSelector withObject:(id)arg;
- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait;
- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait modes:(NSArray *)array;
```
Это один из самых простых и распространенных вариантов. Он требует только указать метод, который будет исполнять этот поток.

* Because these methods are running on their own threads, you must create an autorelease pool for Cocoa objects. The main autorelease pool is associated with the main thread.
* The methods must not return any values and must either take no arguments or have one object as an argument. In other words, the methods must have one of the following signatures:
```objectivec
- (void)myMethod;
- (void)myMethod:(id)myObject;
```
__Плюсы__

* Он подходит для простых задач

__Минусы__

* Нужно упаковывать все параметры для передачи, и бедные возможности по управлению очередностью, количеством одновременных задач, их приоритетом. На каждый вызов `performSelectorInBackground` будет создаваться отдельный поток. При быстром скролле большой таблицы можно довести число потоков до очень большой величины.

In general, you should use the highest level of abstraction that suits your needs. This means that you should usually use `NSOperationQueue` instead of GCD, unless you need to do something that `NSOperationQueue` doesn't support.

Use NSOperationQueue when you have more complex operations you want to run concurrently.
NSOperation allows for subclassing, dependencies, priorities, cancellation and a supports a number of other higher-level features.
NSOperation actually uses GCD under the hood so it is as multi-core, multi-thread capable as GCD.

<a name="мьютекс"></a>
### Что такое мьютекс?
`@synchronized`

Замки являются одним из наиболее часто используемых инструментов синхронизации. Вы можете использовать замки для защиты критической секции вашего кода, который является сегментом кода, к которому разрешен доступ только одному потоку одновременно. Взаимоисключающая (или мьютекс) блокировка действует как защитный барьер вокруг ресурса. Мьютекс является одним из видов семафора, который предоставляет доступ одновременно только одному потоку. Если мьютекс используется и другой поток пытается получить его, что поток блокируется до тех пор, пока мьютекс не освободится от своего первоначального владельца. Если несколько потоков соперничают за одни и те же мьютексы, только одному будет разрешен к нему доступ.

<a name="deadlock"></a>
### Что такое deadlock?
Каждый поток захватывает ресурс и ждет, пока другой не осводит второй ресурс. Таким образом, они ждут друг друга вечно. Deadlock is an unhappy condition in which two or more competing tasks are each waiting on the other to finish. You can observe this in real life when cars arrive simultaneously at a four-way stop.

<a name="livelock"></a>
### Что такое livelock?
Система не застревает, но занимается бесполезной работой. A livelock occurs when a request for an exclusive lock is repeatedly denied because a series of overlapping shared locks keep interfering. It is an endless loop in program execution. This could be a case when two threads exit allowing each other to write to or update record(s) in a database.

<a name="семафор"></a>
### Что такое семафор?
Семафор позволяет выполнять какой-либо участок кода одновременно только конкретному количеству потоков. В основе семафора лежит счетчик, который и определяет, можно ли выполнять участок кода текущему потоку или нет. Если счетчик больше нуля — поток выполняет код, в противном случае — нет. Семафор в GCD представлен типом `dispatch_semaphore_t`. Для создания семафора существует функция `dispatch_semaphore_create`, которая принимает один аргумент — число потоков, которые могут одновременно выполнять участок кода.

<a name="dispatch_sync-dispatch_async"></a>
### Чем отличается dispatch_async от dispatch_sync?
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

<a name="многопоточность-uikit"></a>
### Как многопоточность работает с UIKit?
In Cocoa Touch, the `UIApplication` i.e. the instance of your application is attached to the main thread because this thread is created by `UIApplicatioMain()`, the entry point function of Cocoa Touch. It sets up main event loop, including the application’s run loop, and begins processing events. Application's main event loop receives all the UI events i.e. touches, gestures etc. These application UI events are further forwarded to `UIResponder`'s following the chain of responders usually like `UIApplication->UIWindow->UIViewController->UIView->subviews (UIButton, etc...)` Responders handle events like button press, tap, pinch zoom, swipe etc. which get translated as change in the UI. Hence as you can see these chain of events occur on main thread which is why UIKit, the framework which contains the responders should operate on main thread.
One of the most common mistakes even experienced iOS/Mac developers make is accessing parts of UIKit/AppKit on background threads. It’s very easy to make the mistake of setting properties like image from a background thread, because their content is being requested from the network in the background anyway. Apple’s code is performance-optimized and will not warn you if you change properties from different threads. For the most part, UIKit classes should be used only from an application’s main thread. This is particularly true for classes derived from `UIResponder` or that involve manipulating your application’s user interface in any way.

<a name="atomic-vs-nonatomic"></a>
### Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?
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

<a name="race-condition"></a>
## Что такое гонка условий?
