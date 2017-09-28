- [Multithreading and concurrency](#multithreading-and-concurrency)
	- [Основные понятия многопоточности](#основные-понятия-многопоточности)
	- [API для работы с многопоточностью и их альтернативы](#multithreading-api-alternatives)
		- [POSIX Threads](#posix-threads)
		- [NSThread](#nsthread)
		- [Run Loops](#run-loops)
		- [NSObject instance methods](#nsobject-instance-methods)
		- [GCD](#gcd)
			- [Swift 3 API](#swift-3-api)
		- [NSOperationQueue](#nsoperationqueue)
		- [Idle-time notifications](#idle-time-notifications)
		- [Timers](#timers)
	- [Synchronization](#synchronization)
		- [Semaphore](#semaphore)
		- [Lock](#lock)
		- [Mutex](#mutex)
		- [Средства синхронизации в iOS](#synchronization-ios)
	- [Гонка условий](#race-condition)
		- [Deadlock](#deadlock)
		- [Livelock](#livelock)
		- [Starvation](#starvation)
		- [Priority inversion](#priority-inversion)
		- [Как избежать гонки условий](#как-избежать-гонки-условий)
	- [Чем отличается dispatch_async от dispatch_sync?](#dispatch_sync-dispatch_async)
	- [Как многопоточность работает с UIKit?](#многопоточность-uikit)
	- [Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?](#atomic-vs-nonatomic)
	- [Можно ли отменить операцию в GCD? А в NSOperationQueue?](#отмена-операций)
	- [Когда лучше использовать GCD, а когда NSOperationQueue](#gcd-vs-nsoperationqueue)

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

_Inter-thread Communication_
* Direct messaging
* Global variables, shared memory, and objects
* Conditions
* Run loop sources
* Ports and sockets
* Message queues
* Cocoa distributed objects

<a name="run-loops"></a>
## Run Loops
Циклы выполнения – часть инфраструктуры, используемой для управления событиями, прибывающими асинхронно в потоке. Ждет данные от одного или нескольких источников, чтобы запустить код на исполнение. Циклы выполнения работают по мониторингу одного или нескольких источников событий для потока. Как только события прибыли, система пробуждает поток и отправляет события на цикл выполнения, который затем передает их указанным обработчикам. Если нет событий готовых быть обработанными, цикл выполнения ставит поток в режим сна.
Одна из опасностей потокового программирования, это конфликты ресурсов между несколькими потоками. Если несколько потоков пытаются использовать или модифицировать один и тот же ресурс в одно и то же время, то могут возникнуть проблемы. Один из способов решить проблему заключается в устранении общего ресурса в целом и убедиться, что каждый поток имеет свой собственный набор ресурсов, на котором он работает.
Run loops are not technically a concurrency mechanism like GCD or operation queues, because they don’t enable the parallel execution of tasks. However, run loops tie in directly with the execution of tasks on the main dispatch/operation queue and they provide a mechanism to execute code asynchronously.
A run loop is always bound to one particular thread. The main run loop associated with the main thread has a central role in each application, because it handles UI events, timers, and other kernel events. Whenever you schedule a timer, use a `NSURLConnection` or call `performSelector:withObject:afterDelay`:, the run loop is used behind the scenes in order to perform these asynchronous tasks. Whenever you use a method which relies on the run loop, it is important to remember that run loops can be run in different modes. Each mode defines a set of events the run loop is going to react to. This is a clever way to temporarily prioritize certain tasks over others in the main run loop.
A typical example of this is scrolling on iOS. While you’re scrolling, the run loop is not running in its default mode, and therefore, it’s not going to react to, for example, a timer you have scheduled before. Once scrolling stops, the run loop returns to the default mode and the events which have been queued up are executed. If you want a timer to fire during scrolling, you need to add it to the run loop in the `NSRunLoopCommonModes` mode. The main thread always has the main run loop set up and running. Other threads though don’t have a run loop configured by default. You can set up a run loop for other threads too, but you will rarely need to do this. Most of the time it is much easier to use the main run loop. If you need to do heavier work that you don’t want to execute on the main thread, you can still dispatch it onto another queue after your code is called from the main run loop.
You can think of a Run Loop to be an event processing for-loop associated to a thread. This is provided by the system for every thread, but it's only run automatically for the main thread. Note that _running run loops and executing a thread are two distinct concepts_. You can execute a thread without running a run loop, when you're just performing long calculations and you don't have to respond to various events. If you want to respond to various events from a secondary thread, you retrieve the run loop associated to the thread by `[NSRunLoop currentRunLoop];` and run it.
A run loop receives events from two different types of sources. Input sources deliver asynchronous events, usually messages from another thread or from a different application. Timer sources deliver synchronous events, occurring at a scheduled time or repeating interval. Both types of source use an application-specific handler routine to process the event when it arrives.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/runloop.jpg">

<a name="nsobject-instance-methods"></a>
## NSObject instance methods

Group of `performSelector` methods and `cancelPreviousPerformRequests` methods

```objectivec
- (void)performSelectorInBackground:(SEL)aSelector withObject:(id)arg;
```
This method creates a new thread in your application, putting your application into multithreaded mode if it was not already. The method represented by aSelector must set up the thread environment just as you would for any other new thread in your program.

<a name="gcd"></a>
## GCD
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

* Timers
* Signal handlers
* Descriptor-related events
* Process-related events
* Mach port events
* Custom events that you trigger

- async - concurrent: the code runs on a background thread. Control returns immediately to the main thread (and UI). The block can't assume that it's the only block running on that queue
- async - serial: the code runs on a background thread. Control returns immediately to the main thread. The block can assume that it's the only block running on that queue
- sync - concurrent: the code runs on a background thread but the main thread waits for it to finish, blocking any updates to the UI. The block can't assume that it's the only block running on that queue (I could have added another block using async a few seconds previously)
- sync - serial: the code runs on a background thread but the main thread waits for it to finish, blocking any updates to the UI. The block can assume that it's the only block running on that queue

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_queues_scheme.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_functions_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_functions_2.png">

__Плюсы__

* Визуально — он самый короткий и простой в реализации. Он возоможен с использованием блоков. Этот подход тоже очень гибкий (хотя отменять блок поставленный в очередь нельзя стандартными способами). В GCD можно настраивать приоритеты, блоки захватывают переменные из окружения блока.

<a name="swift-3-api"></a>
#### Swift 3 API

The QoS classes are:
* User-interactive: This represents tasks that need to be done immediately in order to provide a nice user experience. Use it for UI updates, event handling and small workloads that require low latency. The total amount of work done in this class during the execution of your app should be small. This should run on the main thread.
* User-initiated: The represents tasks that are initiated from the UI and can be performed asynchronously. It should be used when the user is waiting for immediate results, and for tasks required to continue user interaction. This will get mapped into the high priority global queue.
* Utility: This represents long-running tasks, typically with a user-visible progress indicator. Use it for computations, I/O, networking, continous data feeds and similar tasks. This class is designed to be energy efficient. This will get mapped into the low priority global queue.
* Background: This represents tasks that the user is not directly aware of. Use it for prefetching, maintenance, and other tasks that don’t require user interaction and aren’t time-sensitive. This will get mapped into the background priority global queue.
```swift
DispatchQueue.global(attributes: [.qosDefault]).async {
  // Background thread
  DispatchQueue.main.async(execute: {
    // UI Updates
  })
}
```

<a name="nsoperationqueue"></a>
## NSOperationQueue
Operation queues are a Cocoa abstraction of the queue model exposed by GCD. While GCD offers more low-level control, operation queues implement several convenient features on top of it, which often makes it the best and safest choice for application developers. The `NSOperationQueue` class has two different types of queues: the main queue and custom queues. The main queue runs on the main thread, and custom queues are processed in the background. In any case, the tasks which are processed by these queues are represented as subclasses of `NSOperation`. Whereas dispatch queues always execute tasks in first-in, first-out order, operation queues __take other factors into account when determining the execution order of tasks__. Primary among these factors is whether a given task depends on the completion of other tasks. You configure dependencies when defining your tasks and can use them to create complex execution-order graphs for your tasks. Because the `NSOperation` class is essentially an abstract base class, you typically define custom subclasses to perform your tasks. However, the Foundation framework does include some concrete subclasses that you can create and use as is to perform tasks.

`NSBlockOperation` exectues a block. `NSInvocationOperation` executes a `NSInvocation` (or a method defined by target, selector, object). `NSOperation` must be subclassed, it offers the most flexibility but requires the most code. `NSBlockOperation` and `NSInvocationOperation` are both subclasses of `NSOperation`. They are provided by the system so you don't have to create a new subclass for simple tasks. Using `NSBlockOperation` and `NSInvocationOperation` should be enough for most tasks.

After an operation begins executing, it continues performing its task until it is finished or until your code explicitly cancels the operation. Cancellation can occur at any time, even before an operation begins executing. Although the NSOperation class provides a way for clients to cancel an operation, recognizing the cancellation event is voluntary by necessity. If an operation were terminated outright, there might not be a way to reclaim resources that had been allocated. As a result, operation objects are expected to check for cancellation events and to exit gracefully when they occur in the middle of the operation.

__Плюсы__

* Можно для каждой очереди настраивать приоритет и количество одновременно выполняющихся операций. `NSOperationQueue` самостоятельно создает и поддерживает пул потоков, в которых исполняются `NSOperation`. Так же `NSOperation` предоставляет возможность отменять операции, приостанавливать всю очередь, запускать ее снова и много чего прочего.

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

<a name="semaphore"></a>
### Semaphore
_Is the number of free identical toilet keys. Example, say we have four toilets with identical locks and keys. The semaphore count - the count of keys - is set to 4 at beginning (all four toilets are free), then the count value is decremented as people are coming in. If all toilets are full, ie. there are no free keys left, the semaphore count is 0. Now, when eq. one person leaves the toilet, semaphore is increased to 1 (one free key), and given to the next person in the queue._

Variable or abstract data type used to control access to a common resource by multiple processes in a concurrent system. A trivial semaphore is a plain variable that is changed (for example, incremented or decremented, or toggled) depending on programmer-defined conditions. The variable is then used as a condition to control access to some system resource. A useful way to think of a semaphore as used in the real-world systems is as a record of how many units of a particular resource are available, coupled with operations to adjust that record safely (i.e. to avoid race conditions) as units are required or become free, and, if necessary, wait until a unit of the resource becomes available. Semaphores are a useful tool in the prevention of race conditions; however, their use is by no means a guarantee that a program is free from these problems. Semaphores which allow an arbitrary resource count are called __counting semaphores__, while semaphores which are restricted to the values 0 and 1 (or locked/unlocked, unavailable/available) are called __binary semaphores__ and are used to implement locks.

Семафор позволяет выполнять какой-либо участок кода одновременно только конкретному количеству потоков. В основе семафора лежит счетчик, который и определяет, можно ли выполнять участок кода текущему потоку или нет. Если счетчик больше нуля — поток выполняет код, в противном случае — нет.

<a name="lock"></a>
### Lock
Mechanism for enforcing limits on access to a resource in an environment where there are many threads of execution. A lock is designed to enforce a mutual exclusion concurrency control policy.

<a name="mutex"></a>
### Mutex
_Is a key to a toilet. One person can have the key - occupy the toilet - at the time. When finished, the person gives (frees) the key to the next person in the queue._

Мьютекс является одним из видов семафора, который предоставляет доступ одновременно только одному потоку. Если мьютекс используется и другой поток пытается получить его, что поток блокируется до тех пор, пока мьютекс не освободится от своего первоначального владельца. Если несколько потоков соперничают за одни и те же мьютексы, только одному будет разрешен к нему доступ.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/mutex.png">

__semaphore vs. mutex vs. lock__

__Explanation 1__

A mutex is essentially the same thing as a binary semaphore and sometimes uses the same basic implementation. The differences between them are in how they are used. While a binary semaphore may be used as a mutex, a mutex is a more specific use-case, in that only the thread that locked the mutex is supposed to unlock it.
A mutex is a synchronization object. You acquire a lock on a mutex at the beginning of a section of code, and release it at the end, in order to ensure that no other thread is accessing the same data at the same time. A mutex typically has a lifetime equal to that of the data it is protecting, and that one mutex is accessed by multiple threads.
A lock object is an object that encapsulates that lock. When the object is constructed it acquires the lock on the mutex. When it is destructed the lock is released. You typically create a new lock object for every access to the shared data.

__Explanation 2__

A mutex is an object which can be locked. A lock is the object which maintains the lock. To create a lock, you need to pass it a mutex.

<a name="synchronization-ios"></a>
### Средства синхронизации в iOS
***
__Atomic Operations__

`/usr/include/libkern/OSAtomic.h`

Atomic operations let you perform simple mathematical and logical operations on 32-bit or 64-bit values. These operations rely on special hardware instructions (and an optional memory barrier) to ensure that the given operation completes before the affected memory is accessed again. In the multithreaded case, you should always use the atomic operations that incorporate a memory barrier to ensure that the memory is synchronized correctly between threads.

Operation types: Add, Increment, Decrement, Logical OR, Logical AND, Logical XOR, Compare and swap, Test and set, Test and clear
***
__Memory Barriers and Volatile Variables__

A memory barrier is a type of nonblocking synchronization tool used to ensure that memory operations occur in the correct order.

Volatile variables apply another type of memory constraint to individual variables. The compiler often optimizes code by loading the values for variables into registers. For local variables, this is usually not a problem. If the variable is visible from another thread however, such an optimization might prevent the other thread from noticing any changes to it. Applying the volatile keyword to a variable forces the compiler to load that variable from memory each time it is used. You might declare a variable as volatile if its value could be changed at any time by an external source that the compiler may not be able to detect.
***
__Locks__

Замки являются одним из наиболее часто используемых инструментов синхронизации. Вы можете использовать замки для защиты критической секции вашего кода, который является сегментом кода, к которому разрешен доступ только одному потоку одновременно. Взаимоисключающая (или мьютекс) блокировка действует как защитный барьер вокруг ресурса.

- Mutex

A mutually exclusive (or mutex) lock acts as a protective barrier around a resource. A mutex is a type of semaphore that grants access to only one thread at a time. If a mutex is in use and another thread tries to acquire it, that thread blocks until the mutex is released by its original holder. If multiple threads compete for the same mutex, only one at a time is allowed access to it.

1. POSIX Mutex Lock
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

2. `NSLock`
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

3. `@synchronized`
```objectivec
- (void)myMethod:(id)anObj {
  @synchronized(anObj) {
    // Everything between the braces is protected by the @synchronized directive.
  }
}
```
As a precautionary measure, the `@synchronized` block implicitly adds an exception handler to the protected code. This handler automatically releases the mutex in the event that an exception is thrown. This means that in order to use the `@synchronized` directive, you must also enable Objective-C exception handling in your code. If you do not want the additional overhead caused by the implicit exception handler, you should consider using the lock classes.

- Recursive lock

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

- Read-write lock

A read-write lock is also referred to as a shared-exclusive lock. This type of lock is typically used in larger-scale operations and can significantly improve performance if the protected data structure is read frequently and modified only occasionally.

1. `pthread_rwlock`
2. dispatch barrier

- Distributed lock

A distributed lock provides mutually exclusive access at the process level. Unlike a true mutex, a distributed lock does not block a process or prevent it from running. It simply reports when the lock is busy and lets the process decide how to proceed.

- Spin lock

A spin lock polls its lock condition repeatedly until that condition becomes true. Spin locks are most often used on multiprocessor systems where the expected wait time for a lock is small. In these situations, it is often more efficient to poll than to block the thread, which involves a context switch and the updating of thread data structures.

`OSSpinLock` is an integer type.  The convention is that unlocked is zero, and locked is nonzero.  Locks
must be naturally aligned and cannot be in cache-inhibited memory.

`OSSpinLockLock()` will spin if the lock is already held, but employs various strategies to back off, making it immune to most priority-inversion livelocks.  But because it can spin, it may be inefficient
in some situations.

`OSSpinLockTry()` immediately returns false if the lock was held, true if it took the lock.  It does not spin.

`OSSpinLockUnlock()` unconditionally unlocks the lock by zeroing it.

- Double-checked lock

A double-checked lock is an attempt to reduce the overhead of taking a lock by testing the locking criteria prior to taking the lock. Because double-checked locks are potentially unsafe, the system does not provide explicit support for them and their use is discouraged.

- Condition lock

An `NSConditionLock` object defines a mutex lock that can be locked and unlocked with specific values. You should not confuse this type of lock with a condition. The behavior is somewhat similar to conditions, but is implemented very differently. Typically, you use an `NSConditionLock` object when threads need to perform tasks in a specific order, such as when one thread produces data that another consumes. While the producer is executing, the consumer acquires the lock using a condition that is specific to your program. (The condition itself is just an integer value that you define.) When the producer finishes, it unlocks the lock and sets the lock condition to the appropriate integer value to wake the consumer thread, which then proceeds to process the data.

- Semaphore

Семафор в GCD представлен типом `dispatch_semaphore_t`. Для создания семафора существует функция `dispatch_semaphore_create`, которая принимает один аргумент — число потоков, которые могут одновременно выполнять участок кода.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/lock_performance.png">

`@synchronized` is very heavy weight because it has to set up an exception handler, and it actually ends up taking a few internal locks on its way there.  So instead of a simple cheap lock, you’re paying for a couple locks/unlocks just to acquire your measly lock.  Those take time.

`OSSpinLock`, on the other hand, doesn’t even enter the kernel — it just keeps reloading the lock, hoping that it’s unlocked.  This is terribly inefficient if locks are held for more than a few nanoseconds, but it saves a costly system call and a couple context switches. Pthread mutexes actually use an `OSSpinLock` first, to keep things running smoothly where there’s no contention.  When there is, it resorts to heavier, kernel-level locking/tasking stuff.

So, if you’ve got hotly-contested locks, OSSpinLock probably isn’t for you (unless your critical sections are really fast). Pthread mutexes are a tiny bit more expensive, but they avoid the power-wasting effects of `OSSpinLock`.

`NSLock` is a pretty wrapper on pthread mutexes. They don’t provide much else, so there’s not much point in using them over pthread mutexes.
***
Conditions

A condition is another type of semaphore that allows threads to signal each other when a certain condition is true. Conditions are typically used to indicate the availability of a resource or to ensure that tasks are performed in a specific order. When a thread tests a condition, it blocks unless that condition is already true. It remains blocked until some other thread explicitly changes and signals the condition. The difference between a condition and a mutex lock is that multiple threads may be permitted access to the condition at the same time. The condition is more of a gatekeeper that lets different threads through the gate depending on some specified criteria.

1. POSIX Conditions
2. `NSCondition`
***
Signals

Signals are a low-level BSD mechanism that can be used to deliver information to a process or manipulate it in some way.
***

<a name="race-condition"></a>
## Что такое гонка условий?
Can always happen if multiple threads access a shared resource without making sure that one thread is finished operating on a resource before another one begins accessing it.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/race_condition.png">

<a name="deadlock"></a>
### Deadlock
Two or more competing tasks are each waiting on the other to finish. You can observe this in real life when cars arrive simultaneously at a four-way stop.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/deadlock.png">

<a name="livelock"></a>
### Livelock
Система не застревает, но занимается бесполезной работой. A livelock occurs when a request for an exclusive lock is repeatedly denied because a series of overlapping shared locks keep interfering. It is an endless loop in program execution. This could be a case when two threads exit allowing each other to write to or update record(s) in a database.

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

* Avoid Synchronization Altogether

The best way to implement concurrency is to reduce the interactions and inter-dependencies between your concurrent tasks. If each task operates on its own private data set, it does not need to protect that data using locks. Even in situations where two tasks do share a common data set, you can look at ways of partitioning that set or providing each task with its own copy.

* Understand the Limits of Synchronization

Synchronization tools are effective only when they are used consistently by all threads in an application. If you create a mutex to restrict access to a specific resource, all of your threads must acquire the same mutex before trying to manipulate the resource. Failure to do so defeats the protection offered by the mutex and is a programmer error.

* Watch Out for Deadlocks and Livelocks

The best way is to take only one lock at a time. If you must acquire more than one lock at a time, you should make sure that other threads do not try to do something similar.

* Use Volatile Variables Correctly

<a name="dispatch_sync-dispatch_async"></a>
## Чем отличается dispatch_async от dispatch_sync?
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
## Как многопоточность работает с UIKit?
In Cocoa Touch, the `UIApplication` i.e. the instance of your application is attached to the main thread because this thread is created by `UIApplicatioMain()`, the entry point function of Cocoa Touch. It sets up main event loop, including the application’s run loop, and begins processing events. Application's main event loop receives all the UI events i.e. touches, gestures etc. These application UI events are further forwarded to `UIResponder`'s following the chain of responders usually like `UIApplication->UIWindow->UIViewController->UIView->subviews (UIButton, etc...)` Responders handle events like button press, tap, pinch zoom, swipe etc. which get translated as change in the UI. Hence as you can see these chain of events occur on main thread which is why UIKit, the framework which contains the responders should operate on main thread.
One of the most common mistakes even experienced iOS/Mac developers make is accessing parts of UIKit/AppKit on background threads. It’s very easy to make the mistake of setting properties like image from a background thread, because their content is being requested from the network in the background anyway. Apple’s code is performance-optimized and will not warn you if you change properties from different threads. For the most part, UIKit classes should be used only from an application’s main thread. This is particularly true for classes derived from `UIResponder` or that involve manipulating your application’s user interface in any way.

<a name="atomic-vs-nonatomic"></a>
## Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?
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

To suspend a dispatch queue, it's simply `dispatch_suspend(queue)` or `queue.suspend()` in Swift 3. That doesn't affect any tasks currently running, but merely prevents new tasks from starting on that queue. Also, you obviously only suspend queues that you created (not global queues, not main queue). To resume a dispatch queue, it's `dispatch_resume(queue)` or `queue.resume()`. There's no concept of "auto resume", so you'd just have to manually resume it when appropriate.

In terms of canceling tasks queued on dispatch queues, this is a new feature of iOS 8 and you'd call `dispatch_block_cancel(block)` with your `dispatch_block_t`. This cancels queued blocks/items that have not started, but does not stop ones that are underway. If you want to be able to interrupt a dispatched block/item, you have to periodically examine `dispatch_block_testcancel()` or `item.isCancelled` in Swift 3.

If you want to cancel tasks, you might also consider using operation queues, `NSOperationQueue`. It also supports constraining the degree of concurrency with `maxConcurrentOperationCount` (whereas with dispatch queues you can only choose between serial and concurrent, and controlling concurrency more than that requires a tiny bit of effort on your part). If using operation queues, you suspend and resume by changing the suspended property of the queue. And to pass it around, you just pass the `NSOperationQueue` object you instantiated.

<a name="gcd-vs-nsoperationqueue"></a>
# Когда лучше использовать GCD, а когда NSOperationQueue?
`NSOperationQueue` can be more suitable for long-running operations that may need to be cancelled or have complex dependencies.

GCD dispatch queues are better for short tasks that should have minimum performance and memory overhead.
