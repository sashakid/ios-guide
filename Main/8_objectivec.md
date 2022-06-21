- [OBJECTIVE-C](#objective-c)
	- [Transparent and opaque data types](#transparent-and-opaque-data-types)
	- [Toll-Free Bridged Types](#toll-free-bridged-types)
	- [Директивы компилятора](#директивы-компилятора)
- [MEMORY MANAGEMENT](#memory-management)
	- [Память в стеке и в куче](#память-в-стеке-и-в-куче)
	- [Manual retain-release](#manual-retain-release)
	- [Automatic Reference Counting](#automatic-reference-counting)
	- [Модификаторы](#модификаторы)
	- [Что такое property](#что-такое-property)
	- [Написать сеттер и геттер для свойства, с ARC и без](#написать-сеттер-и-геттер)
	- [В каких случаях лучше использовать strong, а в каких copy для NSString? Почему?](#copy-strong-nsstring)
	- [autorelease vs release](#autorelease-vs-release)
	- [Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC](#arc-nonarc)
	- [Владение объектами в массиве](#владение-объектами-в-массиве)
	- [Вопрос о циклах в графах владения, и почему свойства delegate обычно задаются как assign?](#retain-cycle)
	- [Нужно ли ретейнить делегат для CAAnimation?](#caanimation-retain)
	- [Если я вызову performSelector:withObject:afterDelay: объекту пошлется сообщение retain?](#performselectorwithobject)
	- [Что происходит когда вы посылаете объекту сообщение autorelease?](#сообщение-autorelease)
	- [Что такое retain count?](#retain-count)
- [КОЛЛЕКЦИИ В Objective-C](#коллекции-в-objective-c)
	- [Разница между NSSet и NSArray](#разница-между-set-и-array)
	- [Difference between NSArray and CFArray](#difference-between-nsarray-and-cfarray)
	- [Enumeration](#enumeration)
	- [Filtering](#filtering)
	- [Sorting](#sorting)
	- [Зачем нужен NSCache? В чем от реализации кэша на NSDictionary?](#nscache-vs-nsdictionary)
- [RUNTIME](#runtime)
	- [Что такое указатель isa? Для чего он нужен?](#isa)
	- [Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?](#метод-объекта)
	- [Что такое классы в Objective-C, структура классов?](#классы)
	- [Чем объект Objective-c отличается от структуры С, что такое структура в C?](#объект)
	- [Вопрос о методах isKindOfClass, isMemberOfClass](#вisKindOfClass)
	- [Тип id](#тип-id)
	- [Dynamic method resolution](#dynamic-method-resolution)
- [БЛОКИ](#блоки)
	- [Типы блоков](#типы-блоков)
	- [When and why block captures self and when they don't?](#block-captures-self)
	- [Примеры объявления и использования блоков](#примеры)
	- [В чем отличие блока от лямбды и замыкания](#блок-лямбда-замыкание)
	- [Обратный вызов](#обратный-вызов)
	- [Когда использовать блоки, делегаты, KVO и уведомления?](#блоки-делегаты-kvo-уведомления)

<a name="objective-c"></a>
# OBJECTIVE-C
Objective-C — это компилируемый язык программирования, используемый корпорацией Apple, построенный на основе языка Си и парадигм Smalltalk. В частности, объектная модель построена в стиле Smalltalk — то есть объектам посылаются сообщения. Язык Objective-C является надмножеством языка Си, поэтому Си-код полностью понятен компилятору Objective-C. Компилятор Objective-C доступен на большинстве основных платформ. Язык используется в первую очередь для Mac OS X (Cocoa) и GNUstep — реализаций объектно-ориентированного интерфейса OpenStep. Также язык используется для iOS (Cocoa Touch). Objective-C был создан Брэдом Коксом в начале 1980-х в его компании Stepstone. Он искал возможность собирать программы из готовых компонентов (объектов), подобно тому как сложные электронные устройства могут быть легко собраны из набора готовых интегральных микросхем. При этом такой язык должен быть достаточно простым и основанным на языке Си, чтобы облегчить переход разработчиков на него. Таким образом, Objective-C является именно расширением языка Си — в язык Си просто добавлены новые возможности для объектно-ориентированного программирования. При этом любая программа на Си является программой и на Objective-C.
* Мультипарадигма́льный язы́к программи́рования — как правило, язык программирования, который был разработан специально как инструмент мультипарадигмального программирования, то есть изобразительные возможности которого изначально предполагалось унаследовать от нескольких, чаще всего неродственных языков. Иногда термин мультипарадигмальный язык программирования определяют как «язык, который поддерживает больше чем одну парадигму программирования». Цель разработки мультипарадигмальных языков программирования состоит, как правило, в том, чтобы позволить программистам использовать лучший инструмент для работы, признавая, что никакая парадигма не решает все проблемы самым лёгким или самым эффективным способом.
* Рефлексивно-ориентированный – в информатике отражение или рефлексия (синоним интроспекция, англ. reflection) означает процесс, во время которого программа может отслеживать и модифицировать собственную структуру и поведение во время выполнения. Парадигма программирования, положенная в основу отражения, называется рефлексивным программированием. An object refers to its class to get various information about itself, particularly what code to run to handle each action.
* Message-oriented – вызовы метода интерпретируются не как вызов функции (хотя к этому обычно все сводится), а именно как посылка сообщения (с именем и аргументами) объекту, подобно тому, как это происходит в Smalltalk-е. Такой подход дает целый ряд плюсов — так, любому объекту можно послать любое сообщение. Объект может вместо обработки сообщения просто переслать его другому объекту для обработки (так называемое делегирование), в частности именно так можно легко реализовать распределенные объекты (то есть объекты, находящиеся в различных адресных пространствах и даже на разных компьютерах). The receiver is an object, and the message tells it what to do. In source code, the message is simply the name of a method and any arguments that are passed to it. When a message is sent, the runtime system selects the appropriate method from the receiver’s repertoire and invokes it. Object can contain state, which in practical terms means that they can contain data and references to other objects. In implementation and use, state usually consists of member variables, instance data, or whatever terminology you use. Can receive messages sent from other objects. Can send messages to other objects.
* Runtime-oriented – динамичность, целый ряд решений, обычно принимаемых на этапе компиляции, здесь откладывается непосредственно до этапа выполнения. Примеры использования библиотеки рантайма - не рефлексии напрямую - получения списка всех наследников класса, маппинг объекта в словарь, динамическое добавление свойства в объект для динамических баз данных (это уже совсем рефлексия), свиззлинг для добавления дополнительной логики для методов системных фреймворков.
* Dynamic Typing – The id type is completely nonrestrictive. By itself, it yields no information about an object, except that it is an object. At some point, a program needs to find more specific information about the objects it contains—what the object’s instance variables are, what methods it can perform, and so on. Since the id type designator can’t supply this information to the compiler, each object has to be able to supply it at runtime. This is possible because every object carries with it an isa instance variable that identifies the object’s class—what kind of object it is. Objects are thus dynamically typed at runtime. Whenever it needs to, the runtime system can find the exact class that an object belongs to, just by asking the object. Dynamic typing in Objective-C serves as the foundation for dynamic binding. A crucial difference between function calls and messages is that a function and its arguments are joined together in the compiled code, but a message and a receiving object aren’t united until the program is running and the message is sent. Therefore, the exact method that’s invoked to respond to a message can only be determined at runtime, not when the code is compiled. This dynamic binding of methods to messages works hand-in-hand with polymorphism to give object-oriented programming much of its flexibility and power. Since each object can have its own version of a method, a program can achieve a variety of results, not by varying the message itself, but by varying just the object that receives the message. This can be done as the program runs; receivers can be decided “on the fly” and can be made dependent on external factors such as user actions. The compiler creates just one accessible object for each class, a class object that knows how to build new objects belonging to the class. (For this reason it’s traditionally called a “factory object.”) The class object is the compiled version of the class; the objects it builds are instances of the class. The objects that do the main work of your program are instances created by the class object at runtime. Утиная типизация – границы использования объекта определяются его текущим набором методов и свойств, в противоположность наследованию от определённого класса. То есть считается, что объект реализует интерфейс, если он содержит все методы этого интерфейса, независимо от связей в иерархии наследования и принадлежности к какому-либо конкретному классу. «Если нечто выглядит как утка, плавает как утка и крякает как утка, то это, наверное, и есть утка»

<a name="transparent-and-opaque-data-types"></a>
## Transparent and opaque data types
In computer science, an opaque data type is a data type whose concrete data structure is not defined in an interface. This enforces information hiding, since its values can only be manipulated by calling subroutines that have access to the missing information. The concrete representation of the type is hidden from its users, and the visible implementation is incomplete. A data type whose representation is visible is called transparent. Opaque data types are frequently used to implement abstract data types.
Some languages, such as C, allow the declaration of opaque records (structs), whose size and fields are hidden from the client. The only thing that the client can do with an object of such a type is to take its memory address, to produce an opaque pointer. If the information provided by the interface is sufficient to determine the type's size, then clients can declare variables, fields, and arrays of that type, assign their values, and possibly compare them for equality. This is usually the case for opaque pointers.

<a name="toll-free-bridged-types"></a>
## Toll-Free Bridged Types
There are a number of data types in the Core Foundation framework and the Foundation framework that can be used interchangeably. Data types that can be used interchangeably are also referred to as toll-free bridged data types. This means that you can use the same data structure as the argument to a Core Foundation function call or as the receiver of an Objective-C message invocation. But not all data types are toll-free bridged, even though their names might suggest that they are. Through toll-free bridging, in a method where you see for example an `NSLocale *parameter`, you can pass a `CFLocaleRef`, and in a function where you see a `CFLocaleRef` parameter, you can pass an `NSLocale` instance. You also have to provide other information for the compiler: first, you have to cast one type to the other; in addition, you may have to indicate the object lifetime semantics. The compiler understands Objective-C methods that return Core Foundation types and follow the historical Cocoa naming conventions. For example, the compiler knows that, in iOS, the `CGColor` returned by the `CGColor` method of `UIColor` is not owned. You must still use an appropriate type cast, as illustrated by this example:
```objectivec
NSMutableArray *colors = [NSMutableArray arrayWithObject:(id)[[UIColor darkGrayColor] CGColor]];
[colors addObject:(id)[[UIColor lightGrayColor] CGColor]];
```
The compiler does not automatically manage the lifetimes of Core Foundation objects. You tell the compiler about the ownership semantics of objects using either a cast (defined in `objc/runtime.h`) or a Core Foundation-style macro (defined in `NSObject.h`):
* `__bridge` transfers a pointer between Objective-C and Core Foundation with no transfer of ownership
* `__bridge_retained` or `CFBridgingRetain` casts an Objective-C pointer to a Core Foundation pointer and also transfers ownership to you. You are responsible for calling `CFRelease` or a related function to relinquish ownership of the object.
* `__bridge_transfer` or CFBridgingRelease moves a non-Objective-C pointer to Objective-C and also transfers ownership to ARC. ARC is responsible for relinquishing ownership of the object.

<a name="директивы-компилятора"></a>
## Директивы компилятора
`@implementation` Определяет начало определения (реализации) класса или категории.

`@class` Используется для предварительного объявления класса. При использовании этой директивы класс помечается как известный, даже без загрузки заголовочного файла.

`@protocol` Используются для объявления протокола. Кроме того, протокол может адаптировать другие протоколы.

`@required` (по-умолчанию) Определяет методы, которые следуют после директивы как обязательные.

`@optional` Определяет методы, которые следуют после директивы как необязательные. Классы, которые поддерживают протокол, могут сами решать — реализовывать эти методы или нет. Классы, которые используют необязательные методы протокола, должны делать проверку на существование.

`@public` Определяет, что переменные экземпляра, следующие за директивой будут доступны публично. Публичные переменные могут быть прочтены и изменены с помощью следующей конструкции: `someObject->aPublicVariable = 10;`

`@package` Определяет, что переменные экземпляра, следующие за директивой будут публично доступны в библиотеке, которая определяет класс, но закрытыми за пределами этой библиотеки. Важное замечание, это справедливо только для 64-разрядных систем. На 32-разрядных системах имеет то же значение, что и `@public`

`@protected` (по умолчанию) Определяет, что переменные экземпляра, следующие за директивой, будут доступны только для класса и его потомков.

`@private` Определяет, что переменные экземпляра, следующие за директивой, будут доступны только в пределах данного класса

`@property` Определяет свойство, которое может быть использовано с помощью точечной нотации. За директивой `@property` могут следовать необязательные круглые скобки, которые содержат дополнительные ключевые слова (модификаторы), которые определяют поведение свойства.

`@synthesize` Дает указание компилятору, что необходимо автоматически сгенерировать сеттеры и геттеры для данных (разделенных запятой) свойств. Сеттеры и геттеры автоматически создаются согласно указанным в объявлении свойства директивам. Если переменные экземпляра называются не так, как указано после директивы `@property`, вы можете соединить их с помощью знака равенства

`@dynamic` Cообщает компилятору, что требуемые сеттеры и геттеры для данных свойств будут реализованы вручную или динамически во время выполнения. При доступе к таким свойствам, компилятор не будет выдавать предупреждений, даже если требуемые сеттеры и геттеры не реализованы. Вы можете использовать такие свойства, когда хотите, чтобы сеттеры и геттеры выполняли какой-то специфичный для вас код.

`@try` Defines a block of code that will be tested to determine if an exception should be thrown.

`@catch()` Defines a block of code for handling a thrown exception. Takes an argument, typically of type `NSException`, but can be of other types.

`@finally` Defines a block of code that gets executed whether an exception is thrown or not. This code will always be executed.

`@throw` Throws an exception. Earlier, we mentioned that you can throw exceptions from objects other than `NSException` instances, but that you should avoid doing so. The reason is that not every Cocoa framework catches exceptions thrown by objects other than `NSException`. To ensure that Cocoa works right with your exceptions, you should throw `NSException` objects only. Think of it like the old saying that you don’t have to floss all your teeth, just the ones you want to keep. You’ll typically use `@try`, `@catch`, and `@finally` together in one structure. It goes a little something like this:
```objectivec
@try {
  // code you want to execute that might throw an exception.
}
@catch (NSException *exception)
{
  // code to execute that handles exception
}
@finally {
  // code that will always be executed. Typically for cleanup.
}
```
`@synchronized` Заключает блок кода в мьютекс. Обеспечивает гарантию того, что блок кода и объект блокировки будут доступны только из одного потока в момент времени.

`@autoreleasepool` В тех приложения, в которых вы используете автоматический подсчет ссылок (ARC), вы должны использовать `@autoreleasepool` как замену для `NSAutoreleasePool`. И вообще, `@autoreleasepool` примерно в 6 раз быстрее, чем `NSAutoreleasePool`, поэтому Apple рекомендует использовать его даже для не-ARC приложений. Кроме того, вы не должны определять переменную внутри блока `@autoreleasepool` и затем продолжать использовать ее после. Подобный код должен быть исключен.

`@selector` Возвращает специальный тип селекторов SEL выбранного метода Objective-C. Генерирует предупреждение компилятора, если метода не объявлен или не существует. Это имя метода закодированное специальным образом, используемым Objective-C для быстрого поиска. Указание компилятору на селектор происходит при помощи директивы `@selector(methodName)`

`@encode` Возвращает кодировку типа.

`@compatibility_alias` Позволяет вам задать псевдоним для существующего класса. Первый параметр — имя псевдонима для имени класса, класса с таким именем не должно существовать. Второй параметр — имя существующего класса, для которого создается псевдоним.

`@"some text";` Объявляет константный объект класса NSString. Для таких строк не требуется вызывать `retain` или `release`.

`@import` Модуль прекомпилированных заголовков, позволяющий экономить время по сравнению с компиляцией заголовков при `#import`. Не надо линковать фреймворк.

```objectivec
#import <Cocoa/Cocoa.h> //is the same as
@import Cocoa;
```

<a name="memory-management"></a>
# MEMORY MANAGEMENT
Memory management – процесс выделения памяти под объекты, и освобождение ее после использования.
* __Manual Retain-Release__ (ручное сохранение-освобождение) или MRR – вы явно управляете памятью, отслеживая объекты, которые у вас есть. Это реализуется с помощью модели, известной как подсчет ссылок, что Foundation класса NSObject обеспечивает совместно со средой выполнения.
* В __Automatic Reference Counting__ (автоматическом подсчете ссылок), или ARC, система использует тот же подсчет ссылок, что и система MRR, но он вставляет соответствующий вызов метода управления памятью за вас во время компиляции.
* В __Garbage Collection__ (сборе мусора), система автоматически отслеживает, какие объекты владеют другими объектами. Затем она автоматически освобождает (или собирает мусор) объекты, на которые больше не ссылаются. Метод использует другой механизм, нежели, чем у используемых в MRR и ARC, и поддерживается только в среде выполнения на Mac OS X, а не IOS.

_Отличие ARC от GC:_

GC работает во время выполнения программы с помощью кода, который периодически запускается и проверяет объекты. ARC работает во время компиляции и вставляет retain и release автоматически в код.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/memory_management.png">

<a name="память-в-стеке-и-в-куче"></a>
## Память в стеке и в куче

__Stack__

The stack is a region of memory which contains storage for local variables, as well as internal temporary values and housekeeping. On a modern system, there is one stack per thread of execution. When a function is called, a stack frame is pushed onto the stack, and function-local data is stored there. When the function returns, its stack frame is destroyed. All of this happens automatically, without the programmer taking any explicit action other than calling a function.

__Heap__

The heap is, essentially, everything else in memory. (Yes, there are things other than the stack and heap, but let's ignore that for this discussion.) Memory can be allocated on the heap at any time, and destroyed at any time. You have to explicitly request for memory to be allocated from the heap, and if you aren't using garbage collection, explicitly free it as well. This is where you store things that need to outlive the current function call. The heap is what you access when you call `malloc` and `free`.

__Stack vs Heap Objects__

Given that, what's a stack object, and what's a heap object?
First, we must understand what an object is in general. In Objective-C (and many other languages), an object is simply a contiguous blob of memory with a particular layout.
The precise location of that memory is less important. As long as you have some memory somewhere with the right contents, it's a working Objective-C object. In Objective-C, objects are usually created on the heap:
```objectivec
NSObject *obj = [[NSObject alloc] init];
```
The storage for the obj variable itself is on the stack, but the object it points to is in the heap. The `[NSObject alloc]` call allocates a chunk of heap memory, and fills it out to match the layout needed for an NSObject.

A stack object is just an object where the memory for that object is allocated on the stack. Objective-C doesn't have any support for this directly, but you can construct one manually without too much trouble:
```objectivec
struct {
  Class isa;
} fakeNSObject;

fakeNSObject.isa = [NSObject class];

NSObject *obj = (NSObject *)&fakeNSObject;
NSLog(@"%@", [obj description]);
```
This works fine, although you shouldn't depend on it, as it depends on replicating the internal layout of the class.

__Advantages of Stack Objects__

It's obviously possible to have stack objects in general. Aside from the above hack, real languages like C++ have language support for stack objects. In C++, you can create objects on the stack or the heap:
```c++
std::string stackString;
std::string *heapString = new std::string;
```
Stack objects have two compelling advantages:

* Speed: Allocating memory on the stack is really fast. All of the bookkeeping is done by the compiler when you build your program. At runtime, the function prolog just carves out the amount of space it needs for all local variables, and the code knows what goes where because it was all computed in advance. Stack allocations are essentially free, whereas heap allocations can be quite expensive.
* Simplicity: Stack objects have a defined lifetime. You can never leak one, because it always gets destroyed at the end of the scope where it was declared.

__Disadvantages of Stack Objects__

The strictly defined lifetime of a stack object is a disadvantage as well, and a major one. In Objective-C (and C++, and many other languages), it is impossible to move an object after it's created. The reason for this is because there may be many pointers to that object, and those pointers are not tracked. They would all need to be updated to track the move, but there's no way to accomplish this.
(Note: it's not an impossibility in general, and many languages move objects around as a matter of course, often as part of garbage collection schemes. However, this requires more runtime smarts and a stricter type system than you get in Objective-C.)
As used in Cocoa, Objective-C uses a reference counting system for memory management. The advantage of this system is that any single object can have multiple "owners", and the system won't allow the object to be destroyed until all owners have relinquished ownership.
Stack allocated objects inherently have a single owner, the function which created them. If Objective-C had stack objects, what would happen if you passed it to some other code which then tried to keep it around by retaining it? There's no way to prevent the object from being destroyed when the function which created it returns, so the retain can't work. The code which tries to keep the object around will fail, end up with a dangling reference, and will crash.
Another problem is that stack objects are not very flexible. It's not uncommon in Objective-C to implement an initializer which destroys the original object and returns a new one instead. How could you do that with a stack object? You really couldn't. Much of the runtime flexibility of Objective-C depends on having heap objects.

__Actual Stack Objects in Objective-C__

It turns out that Objective-C does have stack objects, truly and officially, as of 10.6!
Don't get too excited, though. It's only supported for a single kind of object: blocks. When you write a block inside a function using the `^{}` syntax, the result of that expression is a stack object!

## Manual retain-release
Используйте методы доступа, чтобы сделать управление памятью проще. Рассмотрим счетчик объекта, количество которого вы хотите установить.
```objectivec
@interface Counter : NSObject {
	NSNumber *_count;
}
@property (nonatomic, retain) NSNumber *count;
@end;
```
В свойстве объявляется два метода доступа. Как правило, вы должны попросить компилятор для синтезации методов, однако, поучительно посмотреть, как они могли бы быть реализованы. В `get` методе, вы просто возвращаете переменную экземпляра, так что нет необходимости в `retain` или `release`:
```objectivec
- (NSNumber *)count {
	return _count;
}
```
В `set` методе, если все остальные играют по тем же правилам, вы должны принять новое значение счетчика, которое может быть удалено в любое время, поэтому вам придется взять на себя ответственность объектно, отправив ему `retain` сообщение, чтобы убедиться что его не будет. Вы должны также отказаться от права владения на старый объект, отправив ему `release` сообщение. (Отправка сообщения к `nil` допускается в Objective-C, так что реализация все равно будет работать, если `_count` до сих пор не установлена.) Вы должны послать это после `[newCount retain]` на случай, если два и более объекта захотят, ненароком ее освободить.
```objectivec
- (void)setCount:(NSNumber *)newCount {
	[newCount retain];
	[_count release];
	// Make the new assignment.
	_count = newCount;
}
```

__Использование методов доступа для установки значений свойств__

Предположим, вы хотите реализовать метод для сброса счетчика. У вас есть несколько вариантов. Первая реализация создает экземпляр `NSNumber` с `alloc`, который вы балансируете `release`ом.
```objectivec
- (void)reset {
	NSNumber *zero = [[NSNumber alloc] initWithInteger:0];
	[self setCount:zero];
	[zero release];
}
```
Второй использует удобство конструктора для создания нового объекта `NSNumber`. Он уже существует поэтому нет необходимости в `retain` или `release`
```objectivec
- (void)reset {
	NSNumber *zero = [NSNumber numberWithInteger:0];
	[self setCount:zero];
}
```
Обратите внимание, что оба используют `set` метод доступа.
Следующий код почти наверняка работает правильно для простых случаев, но как заманчиво бы это не выглядело, чтобы отказаться от методов доступа, сделав это почти наверняка в будущем приведет к ошибке на определенном этапе (например, если вы забыли сохранить или освободить, или если изменится семантика управления памятью для переменной экземпляра).
```objectivec
- (void)reset {
	NSNumber *zero = [[NSNumber alloc] initWithInteger:0];
	[_count release];
	_count = zero;
}
```
Отметим также, что если вы используете методику ключ-значение (`KVO`), то изменение переменной, таким путем, не совместимо с `KVO`.
* Не используйте методы доступа в методах инициализаторов и `dealloc`
Единственные места, где вы не должны использовать методы доступа для установки переменной экземпляра находятся в методах - инициализаторе и dealloc. Для инициализации счетчика объекта со значением нуль, вы можете реализовать метод инициализации следующим образом:
```objectivec
- init {
	self = [super init];
	if (self) {
		_count = [[NSNumber alloc] initWithInteger:0];
	}
	return self;
}
```
Чтобы позволить счетчику при инициализации принимать значение отличное от нуля, вы можете реализовать метод `initWithCount:` следующим образом:
```objectivec
- initWithCount:(NSNumber *)startingCount {
	self = [super init];
	if (self) {
		_count = [startingCount copy];
	}
	return self;
}
```
Так как переменная счетчика класса - экземпляр объекта, необходимо также реализовать `dealloc` метод. Следует отказаться от владения любыми переменными экземпляра, отправив им сообщение `release`, и в конечном счете он должен вызывать реализацию супер класса:
```objectivec
- (void)dealloc {
	[_count release];
	[super dealloc];
}
```
* Используйте `weak` (слабые) ссылки чтобы избежать сохранения циклов. Сохранение объекта создает сильную ссылку на этот объект. Объект не может быть освобожден, пока все его сильные ссылки не будут освобождены. Проблема, известная как сохранность цикла, может возникнуть, если два объекта имеют циклические ссылки, то есть, у них есть сильные ссылки друг на друга (либо непосредственно, либо через цепочку других объектов, каждый из которых имеет сильную ссылку на следующую ведущую к первой).
* Не освобождайте объекты, которые используете
* Не используйте dealloc для управления ограниченными ресурсами
Вы должны управлять как правило, не ограниченными ресурсами, такими как дескрипторы файлов, сетевые подключения, и буферы или кэш в `dealloc` методе. В частности, вы не должны проектировать классы так, чтобы `dealloc` был вызван, когда вы думаете, он будет вызван. Вызов `dealloc`, может быть отложен или обойден, либо из-за ошибки или из-за падения приложения.

__Коллекции собственных объектов__

При добавлении объекта в коллекцию (например, массив, словарь, или набор), коллекция становится его владельцем. Коллекция откажется от владения объектом, когда объект удаляется из коллекции или коллекция будет освобождена. Так, например, если вы хотите создать массив чисел вы можете выполнить одно из следующих действий:
```objectivec
NSMutableArray *array = <#Получаем изменяемый массив#>;
NSUInteger i;
// ...
for (i = 0; i < 10; i++) {
	NSNumber *convenienceNumber = [NSNumber numberWithInteger:i];
	[array addObject:convenienceNumber];
}
```
В этом случае вы не вызываете `alloc`, так что нет необходимости вызывать `release`. Значит нет необходимости вызова retain для новых номеров (`convenienceNumber`), так как массив это сделает.
Базовая модель используемая для управления памятью со счетчиком ссылок обеспечивается сочетанием методов, определенных в протоколе `NSObject` и стандартными методами именования. Класс `NSObject` также определяет метод `dealloc`, который вызывается автоматически, когда объект будет освобожден.
Вы владеете каким-либо объектом вами созданным:

* Вы можете создать объект, используя метод, имя которого начинается с `alloc`, `new`, `copy`, или `mutableCopy`.
* Вы можете стать владельцем объекта, используя `retain`: Полученный объект, как правило, гарантированно остается в силе в течение выполнения метода, в котором он был получен, и этот метод также может безопасно вернуть объект к вызвавшему его методу. Вы используете `retain` в двух случаях:
1. В реализации метода доступа или инициализации метода, чтобы стать владельцем объекта, который нужно сохранить как значение свойства
2. Для предотвращения освобождения объекта как побочного эффекта от некоторых других операций

_Если объект вам больше не нужен, вы должны отказаться от права собственности на него:_
Вы отказываетесь от права собственности на объект, послав ему сообщение `release` или `autorelease` сообщение. В Cocoa терминологии, из отказа от права владения объектом, как правило следует, "освобождение" объекта.
_Вы не должны отказаться от права владения объектом, которого у вас нет:_ Это всего лишь следствие предыдущих правил политики, заявленных в явном виде.
Используйте `autorelease` для отправки отложенного `release`.
_Вы не являетесь владельцем объектов, возвращаемых по ссылке:_
Некоторые методы в Cocoa указывают, что объект возвращается по ссылке (то есть, они не имеют аргумента типа `ClassName **` или `id *`). Данная закономерность заключается в использовании `NSError` объекта, который содержит информацию об ошибках, если они происходит, о чем свидетельствуют `initWithContentsOfURL:options:error:` (`NSData`) и `initWithContentsOfFile:encoding:error:` (`NSString`). В этих случаях применяются те же правила, как уже было описано. При вызове любого из этих методов, вы не создаете `NSError` объект, так что вы не являетесь его владельцем.
_Реализация `dealloc` для отказа от права владения объектами:_
Класс `NSObject` определяет метод `dealloc`, который вызывается автоматически, когда объект не имеет владельцев и его память будет утилизирована, в терминологии Cocoa это называется "освободил" или "освобождена". Роль `dealloc` метода заключается в освобождении собственной памяти объекта, и распоряжением любыми ресурсами которыми он располагает, в том числе любыми переменными экземпляра объекта, которыми он владеет.
Важно:

* Вы никогда не должны ссылаться на dealloc метод другого объекта непосредственно.
* Вы должны вызвать реализацию суперкласса в конце вашей реализации.
* Вы не должны привязывать управление системными ресурсами, как к объектам контролируемым временем жизни.

<a name="automatic-reference-counting"></a>
## Automatic Reference Counting
Автоматический подсчет ссылок является компиляторной функцией, которая обеспечивает автоматическое управление памятью в Objective-C объектах. Вместо того, чтобы думать о сохранении и освобождении объектов, ARC позволяет сосредоточиться на непосредственном ко-де Вашего приложения. ARC работает путем добавления кода во время компиляции, чтобы время жизни объекта было ровно столько, сколько необходимо, но не более того. Концептуально, это то же управление памятью, что и ручной подсчет ссылок (описанное в практическом управлении памятью) путем добавления соответствующего кода управления памятью, за вас. ARC поддерживается начиная с Xcode 4.2 для Mac OS X v10.6 и v10.7 (64-bit applications), а также iOS 4 и iOS 5. Слабые (`weak`) ссылки не поддерживаются в Mac OS X v10.6 и iOS 4 и более ранних.
Существует несколько ограничений на использование механизма ARC.
* Нельзя использовать свойство, имя которого начинается со слова `new`. Например, не допускается объявление
```objectivec
@property NSString *newString;
```
* Нельзя использовать свойство только для чтения без атрибутов управления памятью. Если вы не используете механизм ARC, то можете использовать объявление
```objectivec
@property (readonly) NSString *title;
```
Но если вы используете механизм ARC, то должны указать, кто управляет памятью, так что достаточно просто вставить ключевое слово unsafe_unretained, потому что по умолчанию используется атрибут `assign`.
ARC only works with retainable object pointers (ROPs). There are three kinds of retainable object pointers:

1. Block pointers
2. Objective-C object pointers
3. Typedefs marked with `__attribute__((NSObject))`

All other pointer types, such as `char *` and CF objects such as `CFStringRef`, are not ARC compatible. If you use pointers that aren’t handled by ARC, you’ll have to manage them yourself. That’s OK, because ARC interoperates with manually managed memory.

<a name="модификаторы"></a>
## Модификаторы
__Для свойств__

`readwrite` (по-умолчанию) и `readonly`
* генерируются одновременно сеттеры и геттеры (setters/getters) или только геттеры

`assign` (по-умолчанию)
просто присваивает переданное значение.
* assign is the default and simply performs a variable assignment
* assign is a property attribute that tells the compiler how to synthesize the property's setter implementation
* I would use assign for C primitive properties and weak for weak references to Objective-C ob-jects.

`retain`
посылает release текущему значению переменной экземпляра, потом посылает retain новому объекту, и присваивает новое значение переменной экземпляра.
* it is retained, old value is released and it is assigned retain specifies the new value should be sent
* retain on assignment and the old value sent -release
* retain is the same as strong.
* apple says if you write retain it will auto converted/work like strong only.
* methods like alloc include an implicit retain

`copy`
посылает `release` текущему значению переменной экземпляра, затем copy новому объекту и присваивает новый объект переменной экземпляра. В последних двух случаях, вы должны послать `release` (или присвоить `nil`) свойству при `dealloc`. Атрибут сору создает копию объекта и переводит на нее указатель. Атрибут сору чаще всего используется с объектными типами, имеющими изменяемые субклассы. Например, `NSString` имеет субкласс с именем `NSMutаblеString`.

`assign` (по-умолчанию), `retain`, `copy` — применяются только для свойств, которые могут быть безопасно приведены к `id`.

`atomic` (по-умолчанию) и `nonatomic`
свойства с ключевым словом atmoic — потокобезопасны, с nonatomic — могут быть проблемы при многопоточном доступе. Доступ к nonatomic свойствам обычно быстрее чем к atomic, поэтому они часто используются в однопоточных приложениях.

`strong` (ARC)
это синоним для `retain`
* it says "keep this in the heap until I don't point to it anymore"
* in other words "I'am the owner, you cannot dealloc this before aim fine with that same as re-tain"
* you use strong only if you need to retain the object.
* by default all instance variables and local variables are strong pointers.
* we generally use strong for `UIViewController` (UI item's parents)
* strong is used with ARC and it basically helps you, by not having to worry about the retain count of an object. ARC automatically releases it for you when you are done with it. Using the keyword strong means that you own the object.

`weak` (ARC)
синоним `assign`, с одним лишь исключением, что свойство с `weak` автоматически устанавливается в `nil` когда объект уничтожается. Также следует учитывать, что ключ `weak` доступен только начиная с iOS 5 и Mac OS X 10.7 (Lion). Если переменная указатель сохраняет адрес объекта, этот объект является активным и имеет владельца – сильная ссылка (`strong`). Если переменная не принимает владения объектом – слабая ссылка (`weak`, `__weak`). Родитель может владеть своим потомком, но потомок – родителем не должен.
* it says "keep this as long as someone else points to it strongly"
* the same thing as assign, no retain or release
* a weak reference is a reference that you do not retain.
* we generally use weak for `IBOutlets` (`UIViewController`'s Childs). This works because the child object only needs to exist as long as the parent object does.
* a weak reference is a reference that does not protect the referenced object from collection by a garbage collector.
* `weak` is essentially `assign`, a unretained property. Except the when the object is deallocated the weak pointer is automatically set to `nil`

`unsafe_unretained` (по умолчанию)
всегда используется для свойств, содержащих необъектные значения. Что делать, если вы хотите использовать механизм ARC в более старых операционных системах, в которых обнуляемые слабые ссылки недоступны? Компания Apple предлагает использовать ключевое слово `__unsafe_unretained` и атрибут `unsafe_unretained`, которые сообщают механизму ARC, что указанная ссылка является слабой.

_Strong & Weak Explanation_

_It may be helpful to think about strong and weak references in terms of balloons. A balloon will not fly away as long as at least one person is holding on to a string attached to it. The number of people holding strings is the retain count. When no one is holding on to a string, the ballon will fly away (dealloc). Many people can have strings to that same balloon. You can get/set properties and call methods on the referenced object with both strong and weak references. A strong reference is like holding on to a string to that balloon. As long as you are holding on to a string attached to the balloon, it will not fly away. A weak reference is like looking at the balloon. You can see it, access it's properties, call it's methods, but you have no string to that balloon. If everyone holding onto the string lets go, the balloon flies away, and you cannot access it anymore._

__Для переменных__

Generally speaking, these extra qualifiers don’t need to be used very often. You might first encounter these qualifiers and others when using the migration tool. For new projects however, you generally you won’t need them and will mostly use strong/weak with your declared properties.

`__strong`
по умолчанию. Объект остается "живым", если на него есть сильный указатель. This means any object created using alloc/init is retained for the lifetime of its current scope. The “current scope” usually means the braces in which the variable is declared (i.e. a method, for loop, if block, etc…)

`__weak`
указывается (слабая) ссылка, которая не сохраняет указанный объект живым. Слабая ссылка устанавливается в `nil`, когда на объект нет сильных ссылок. This is only useful if the object is somehow strongly referenced somewhere else. When destroyed, a variable with `__weak` is set to `nil`. Будьте осторожны с применением `__weak` слабых ссылок, так, если Вы создадите объект только со слабой ссылкой, то нет никакой гарантии, что он доживет до своего применения и не освободится.

`__unsafe_unretained`
указывается ссылка, которая не сохраняет указанный объект живым и не устанавливается в `nil`, когда нет сильных ссылок на объект. Если объект, на который она ссылается, будет освобожден, то указатель остается болтаться со значением, которого уже нет. Можете использовать `__unsafe_unretained` вместо `__weak`. Это создаст слабую ссылку, которая НЕ будет обнулена. Но вы должны быть уверены, что не используете этот указатель (предпочтительно, чтобы вы обнулили его вручную) ПОСЛЕ того, как объект, на который он указывает, был уничтожен. Используется только тогда, когда недоступен `weak`.

`__autoreleasing`
используется для обозначения аргументов, которые передаются по ссылке `(id *)` и autoreleased по возвращении. not to be confused with calling autorelease on an object before returning it from a method, this is used for passing objects by reference, for example when passing `NSError` objects by reference such as
```objectivec
[myObject performOperationWithError:&tmp];
```
Absolutely not. The key difference in the two definitions that you've pointed out is the "as long as someone else". It's the "someone else" that is important.

_Consider the following:_
```objectivec
__strong id strongObject = <some_object>;
__weak id weakObject = strongObject;
```
_Now we've got a two pointers to `<some_object>`, one `strong` and one `weak`. If we set_ `strongObject` to `nil` like so:
```objectivec
strongObject = nil;
```
_Then if you go through the rules you outlined then you'll ask yourself these questions:_

__Strong: "keep this in the heap until I don't point to it anymore"__

_`strongObject` doesn't point to `<some_object>` any more. So we don't need to keep it._

__Weak: "keep this as long as someone else points to it strongly"__

_`weakObject` still points to `<some_object>`. But since nobody else points to it, this rule also means that we don't need to keep it.
The result is that `<some_object>` is deallocated and if your runtime supports it (Lion and iOS 5 upwards) then weakObject will automatically be set to nil._

_Now consider what happens if we set `weakObject` to `nil` like so:_
```objectivec
weakObject = nil;
```
_Then if you go through the rules you outlined then you'll ask yourself these questions:_

__Strong: "keep this in the heap until I don't point to it anymore"__

_strongObject does point to <some_object>. So we do need to keep it._

__Weak: "keep this as long as someone else points to it strongly"__

_`weakObject` doesn't point to `<some_object>`.
The result is that `<some_object>` is not deallocated, but `weakObject` will be the `nil` pointer._

_[Note that all that is assuming `<some_object>` is not pointed to by another strong reference somewhere else / some other means of being "held"]_

<a name="что-такое-property"></a>
## Что такое property?
Упрощенный способ для определения и создания методов доступа, обращающихся к существующим переменным экземплярам. Классы, которые подставляют переменные экземпляра, могут использовать обозначение свойства вместо того, чтобы использовать синтаксис getter и setter.

<a name="написать-сеттер-и-геттер"></a>
## Написать сеттер и геттер для свойства, с ARC и без
__ARC__
```objectivec
- (void)setNumerator:(int)n {
	numerator = n;
}

- (int)numerator {
	return numerator;
}
```
__MRR__
```objectivec
- (NSArray *)sushiTypes {
	return _sushiTypes;
}

- (void)setSushiTypes:(NSArray *)sushiTypes {
	[sushiTypes retain];
	[_sushiTypes release];
	_sushiTypes = sushiTypes;
}

- (void)dealloc {
	[super dealloc];
	[sushiTypes release];
}
```
<a name="copy-strong-nsstring"></a>
## В каких случаях лучше использовать strong, а в каких copy для NSString? Почему?
```objectivec
@property (nonatomic, strong) NSString *someString;
@property (nonatomic, copy) NSString *anotherString;
```
`сopy` используется только для объектов, реализующих протокол `<NSCopying>`. Обычно его используют с mutable объектами или со свойствами, представляющими какое-то значение (value).

<a name="autorelease-vs-release"></a>
## `autorelease` vs `release`?
Autorelease pool это — механизм отложенного отказа от ответственности. Это означает что вы больше не хотите владеть объектом и он вам в общем-то не нужен, но не хотите чтобы он удалился прямо сейчас. Зачастую вам не нужно создавать свой пул, просто используется NSAutoreleasePool и то даже не напрямую. Чтобы поместить объект в autorelease pool нужно отправить ему сообщение autorelease (один объект может быть добавлен в пул несколько раз) и на следующем цикле сообщений autorelease pool отправит всем этим объектам сообщение release, так как сам получит dealloc после чего будет создан новый autorelease pool. Таким образом Cocoa ожидает, что как минимум один autorelease pool будет всегда, и автоматически создает его в main.
Autorelease pool добавляются по принципу стека, самый последний добавленный пул будет в самом верху стека авторелиз пулов в текущем потоке. Создание пула осуществляется стандартным alloc и init, удаление drain. Если послать сообщение drain не самому верхнему пулу, то все пулы над ним тоже получат это сообщение и соответственно удалят все из себя. Официальная документация показывает нам вот такой пример использования своего пула:
```objectivec
NSArray *urls = <# An array of file URLs #>;
for (NSURL *url in urls) {
	NSAutoreleasePool *loopPool = [[NSAutoreleasePool alloc] init];
	NSError *error = nil;
	NSString *fileContents = [[[NSString alloc] initWithContentsOfURL:url encoding:NSUTF8StringEncoding error:&error] autorelease];
	/* Process the string, creating and autoreleasing more objects. */
	[loopPool drain];
}
```
Мы тут видим, что был создан свой пул (он разместился вверху стека пулов и будет освобожден первым), в него добавляются `NSString *fileContents` и потом пул освобождается (а так как он самый верхний — освобождается только он).

<a name="arc-nonarc"></a>
## Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC?
1 способ: Edit – Refactor – Convert to ObjC ARC

2 способ: App – Targets – Build Phases – Compile Sources – поставить флаг `-fno-objc-arc`

<a name="владение-объектами-в-массиве"></a>
## Владение объектами
* Что случится если вы добавите только что созданный объект в `NSMutableArray`, и пошлете ему сообщение `release`?

//объект останется в массиве

* Что случится если послать сообщение `release` массиву?

//массив удалится

* Что случится если вы удалите объект из массива и попытаетесь его использовать?

//объект удалится из массива, использовать объект дальше можно

<a name="retain-cycle"></a>
## Вопрос о циклах удержания, и почему свойства delegate обычно задаются как assign?
```
A creates B;
A sets itself as B’s delegate;
[A release];
if B retained A => leak;
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/retain_cycle.png">

<a name="caanimation-retain"></a>
## Нужно ли ретейнить делегат для CAAnimation?
Да. Это одно из редких исключений в политике управления памятью. Specific task that has some sort of “finished” state. Также нужно ритейнить `NSURLConnection`.

<a name="performselectorwithobject"></a>
## Если я вызову performSelector:withObject:afterDelay: объекту пошлется сообщение retain?
Да. Это создает таймер который вызывает селектор в RunLoop'е текущего потока (thread).

<a name="сообщение-autorelease"></a>
## Вы можете объяснить, что происходит когда вы посылаете объекту сообщение autorelease?
Когда вы посылаете объекту сообщение `autorelease`, его счетчик ссылок уменьшится на 1 в определенный момент в будущем. Объект будет добавлен в autorelease pool (пул автоосвобождения) в текущем потоке (thread). Цикл главного потока (main thread loop `NSRunLoop`) создает autorelease pool в начале функции и освобождает его в конце. Это устанавливает pool на время выполнения задачи. Это также означает что авторелизные (объекты помещенные в пул) объекты созданные в течение выполнения задачи не будут уничтожены пока задача не завершится. Это может привести к излишнему потреблению памяти для задачи (объекты будут уже не нужны но освободятся только в конце задачи). Вы также можете попробовать создать вложенный пул и освободить его раньше, или использовать NSOperationQueue с его собственным пулом.

<a name="retain-count"></a>
## Объясните что такое retain count?
Подсчет ссылок (retain count) — это механизм с помощью которого в Objective-C реализовано управление памятью. Когда вы создаете объект, его счетчик ссылок (retain count) установлен на `1`. Когда вы посылаете объекту сообщение `retain` , его счетчик ссылок увеличивается на `1`. Когда вы посылаете объекту сообщение `release` , его счетчик ссылок уменьшается на `1`. Когда вы посылаете объекту сообщение autorelease , его счетчик ссылок уменьшится на `1` в определенный момент в будущем. Когда счетчик ссылок объекта становится равным `0` то объект уничтожается (`dealloc`).

<a name="коллекции-в-objective-c"></a>
# КОЛЛЕКЦИИ В Objective-C
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/objc_collections.png">

__Mutability__

Most collection classes exist in two versions: mutable and immutable (default). What’s the big advantage? Thread safety. Immutable collections are fully thread safe and can be iterated from multiple threads at the same time, without any risk of mutation exceptions. Of course there’s a cost when going from immutable and mutable and back - the object has to be copied twice, and all objects within will be retained/released. Sometimes it’s more efficient to hold an internal mutable collection and return a copied, immutable object on access. Notably, some of the more modern collection classes like `NSHashTable`, `NSMapTable`, and `NSPointerArray` are mutable by default and don’t have immutable counterparts.

__Массив в СИ__

Количество элементов массива определено заранее при объявлении массива. Все элементы упорядочены – каждому присвоен порядковый номер, который называется индексом. Доступ к конкретному элементу массива осуществляется с помощью индекса. В языке Cи все массивы располагаются в отдельной непрерывной области памяти. Первый элемент массива имеет наименьший адрес, а последний – наибольший. Элементы массива могут быть как простыми переменными, так и составными. Элемент массива может иметь несколько индексов. Количество индексов переменной определяет размерность массива. Размерность массивов в языке Cи не ограничена, но чаще используются одномерные и двумерные массивы. Начальное значение индекса элемента массива для каждого измерения в Cи — нуль.
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/c_array.jpg">

## Core Foundation:
* `CFArray / CFMutableArray`

An object of opaque type `CFArray` — is an ordered, compact container of values. The values are in sequential order and the key for accessing these values is their index, an integer specifying a value’s position in the sequence. The range of indexes is from 0 to `n-1` where n is the number of values in the array. An index of `0` identifies the first value in the array. You can think of arrays as numbered slots. An array is said to be compact because, with mutable arrays, deleting a value does not leave a gap in the array.

* `CFDictionary / CFMutableDictionary`

An object of the `CFDictionary` type — is a hashing-based collection whose keys for accessing its values are arbitrary, program-defined pieces of data (or pointers to data). Although the key is usually a string (or, in Core Foundation, a `CFString` object), it can be anything that can fit into the size of a pointer—an integer, a reference to a Core Foundation object, even a pointer to a data structure (unlikely as that might be). The keys of dictionaries are unlike the keys of the other collection objects in that, conceptually, they are also contained by the collection along with the values. Dictionaries are primarily useful for holding and organizing data that can be labeled, such as values extracted from text fields in the user interface.
In Core Foundation, a dictionary differs from an array in that the key used to access a particular value in the dictionary remains the same as values are added to or removed from the dictionary—that is, until a value associated with a particular key is replaced or removed. In an array, the key (that is, the index) that is used to retrieve a particular value can change over time as values are added to or deleted from the array. Also, unlike an array, a dictionary does not put its values in any order. To enable later retrieval of a value, the key of the key-value pair should be constant (or be treated as constant); if the key changes after being used to put a value in the dictionary, the value might not be retrievable. The keys of a dictionary form a set; in other words, keys are guaranteed to be unique in a dictionary.
The access time for a value in the dictionary is guaranteed to be at worst `O(N)` for any implementation, current and future, but will often be `O(1)` (constant time). Insertion or deletion operations will typically be constant time as well, but are `O(N^2)` in the worst case in some implementations. Access of values through a key is faster than accessing values directly (if there are any such operations). Dictionaries will tend to use significantly more memory than a array with the same number of values.

* `CFSet / CFMutableSet`

A set, both in its mathematical sense and in the implementation of `CFSet`, is an unordered collection of distinct elements. `CFSet` creates static sets and `CFMutableSet` creates dynamic sets.

* `CFBag / CFMutableBag`

Sets and bags are related types of collections. What they have in common is that the key for accessing a value in the collection is the value itself. The difference between sets and bags is the membership “rule” for values. With sets, if the value already exists in the collection, an identical value cannot be added to the set; conversely, you can add any value to a bag even if the bag already holds that value.
This “uniquing” functionality (or lack thereof) can have many uses. Say, for example, that your program is searching the Internet and you want to keep all qualifying URLs but don’t want duplicates; a set would work nicely for this purpose. A bag could be useful for statistical sampling; you could put all collected values in it and after you finish collecting data, you could query it for the frequency of each value.

* `CFBinaryHeap`

Implements a container that stores values sorted using a binary search algorithm. All binary heaps are mutable; there is not a separate immutable variety. Binary heaps can be useful as priority queues.

* `CFBitVector / CFMutableBitVector`

For managing bit vectors - ordered collections of bit values, which are either `0` or `1`

* `CFTree / CFMutableTree`

You use `CFTree` to create tree structures that represent hierarchical organizations of information. In such structures, each tree node has exactly one parent tree (except for the root tree, which has no parent) and can have multiple children.

## Foundation:
__Ordered Collections__
* `NSArray / NSMutableArray`

Управляет упорядоченной коллекцией элементов, называемой массивом. Вы можете использовать объекты этого класса для создания неизменяемых массивов. Это значит, что все элементы объектов класса `NSArray` доступны только для чтения. Имеется возможность доступа к элементам массива по индексу. Массивы могут хранить элементы различных типов. Массивы поддерживают сортировку и поиск элементов, а также сравнение самих массивов между собой.
The most interesting part is that Apple doesn’t guarantee `O(1)` access time on individual object access - as you can read in the note about Computational Complexity in the `CFArray.h` `CoreFoundation` header: The access time for a value in the array is guaranteed to be at worst `O(lg N)` for any implementation, current and future, but will often be `O(1)` (constant time). Linear search operations similarly have a worst case complexity of `O(Nlg N)`, though typically the bounds will be tighter, and so on. Insertion or deletion operations will typically be linear in the number of values in the array, but may be `O(Nlg N)` clearly in the worst case in some implementations. There are no favored positions within the array for performance; that is, it is not necessarily faster to access values with low indices, or to insert or delete values with high indices, or whatever.

__Collections of Keys and Values__
* `NSDictionary / NSMutableDictionary`

Следует использовать когда требуется удобный и эффективный способ хранения данных, ассоциированных с ключом. Объекты класса `NSDictionary` позволяют хранить неизменяемые пары объектов “ключ/значение” различных типов. Ключи в словаре `NSDictionary` не могут дублироваться, повторение значений допускается. Типы ключей и значений могут, но не обязаны совпадать. Особенно эффективными по скорости будут операции поиска по ключу, так как словарь специально оптимизирован для них. Because the dictionary copies each key, keys must conform to the NSCopying protocol. Bear this in mind when choosing what objects to use as keys. Although you can use any object that adopts the `NSCopying` protocol and implements the hash and isEqual: methods, it is typically bad design to use large objects, such as instances of `NSImage`, because doing so may incur performance penalties.

__Unordered Collections of Objects__
* `NSSet / NSMutableSet`

Объекты представляют неупорядоченные множества различных объектов. Вы можете использовать множества в качестве альтернативы массивам, когда порядок элементов не важен, но требуется быстрое определение `O(1)` принадлежности объекта множеству. Операция определения принадлежности выполняется значительно быстрее в сравнении с массивами. `NSSet` can only work efficiently if the hashing method used is balanced; if all objects are in the same hash bucket, then `NSSet` is not much faster in object-existence checking than `NSArray`. Variants of `NSSet` are also `NSCountedSet`, and the non-toll-free counter-variant `CFBag / CFMutableBag`.

* `NSOrderedSet / NSMutableOrderedSet`

Объявляет программный интерфейс для упорядоченного множества объектов. Вы задаёте записи неизменяемого множества на этапе его создания, после этого записи не могут быть изменены. Вы можете использовать упорядоченные множества как альтернативу массивам, когда порядок элементов является важным и требуется высокая скорость поиска элементов в коллекции. Класс `NSMutableOrderedSet` объявляет программный интерфейс к изменяемому упорядоченному множеству различных объектов. Объекты класса `NSMutableOrderedSet` объекты не похожи на массивы языка Си. Во время создания такого множества вы можете указать размер, но реальный размер всё равно будет равен `0`.

* `NSCountedSet`

Объявляет программный интерфейс к изменяемой, неупорядоченной коллекции нечетких объектов. Счётное множество также известно как `Bag`. Каждый отдельный объект, вставленный в `NSCountedSet`, имеет счётчик, связанный с ним. Объект `NSCountedSet` отслеживает количество раз, когда объекты были вставлены, и требует, чтобы объекты были удалены такое же количество раз. В то же время, внутри объекта `NSSet` существует только один экземпляр вставляемого объекта, даже если этот объект был добавлен в множество несколько раз.

__Storing Indexes into an Array__
* `NSIndexSet / NSMutableIndexSet`

Represents an immutable collection of unique unsigned integers, known as indexes because of the way they are used. This collection is referred to as an index set. You use index sets in your code to store indexes into some other data structure. For example, given an `NSArray` object, you could use an index set to identify a subset of objects in that array. You should not use index sets to store an arbitrary collection of integer values because index sets store indexes as sorted ranges. This makes them more efficient than storing a collection of individual integers. It also means that each index value can only appear once in the index set. The designated initializers of the `NSIndexSet` class are: `init`, `initWithIndexesInRange:`, and `initWithIndexSet:`. You must not subclass the `NSIndexSet` class. The mutable subclass of `NSIndexSet` is `NSMutableIndexSet`.

* `NSIndexPath`

Представляет путь к конкретному узлу в виде дерева вложенных массивов коллекций. Этот путь известен как индексный путь. Каждый индекс в индексном пути представляет индекс в массиве дочерних элементов от одного узла в дереве к другому.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/complexity.png">

__Pointer collection classes__

The pointer collection classes allow you to further customize the collection to tailor it to your memory and storage needs. The options specified by `NSPointerFunctionsOptions` provide a convenient interface for customizing how the collection manages the pointers it contains.

* `NSPointerArray`

Mutable collection modeled after `NSArray` but it can also hold `NULL` values, which can be inserted or extracted (and which contribute to the object’s count). Moreover, unlike traditional arrays, you can set the count of the array directly. You can use an `NSPointerArray` object when you want an ordered collection that uses weak references. For example, suppose you have a global array that contains some objects. Because global objects are never collected, none of its contents can be deallocated unless they are held weakly. Pointer arrays configured to hold objects weakly do not own their contents. If there are no strong references to objects within such a pointer array, those objects can be deallocated.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/pointerarray.png">

* `NSMapTable`

Is a general-purpose analogue of `NSDictionary`. Contrasted with the behavior of `NSDictionary / NSMutableDictionary`, `NSMapTable` has the following characteristics:
- `NSDictionary` / `NSMutableDictionary` copies keys, and holds strong references to values.
- `NSMapTable` is mutable, without an immutable counterpart.
- `NSMapTable` can hold keys and values with weak references, in such a way that entries are removed when either the key or value is deallocated.
- `NSMapTable` can copy its values on input.
- `NSMapTable` can contain arbitrary pointers, and use pointer identity for equality and hashing checks.

* `NSHashTable`

В отличие от NSSet, поддерживает слабые ссылки. Он может содержать слабые ссылки на объекты. Объекты класса NSHashTable могут содержать произвольные указатели, хранимые объекты не ограничиваются объектами классов. Можно настроить экземпляр `NSHashTable` для работы с произвольными указателями, а не только с объектами классов. Благодаря своим свойствам, класс `NSHashTable` это не множество, потому что он может вести себя по-другому.

_`NSArray` is the best choice to use for a list of items if you're going to iterate over them in sequence, or access directly by index. They are also efficient to use as a queue or stack, as adding or removing items from either the beginning or is `O(1)`. Checking to see if an object exists in the array using `containsObject:` is an `O(N)` operation, as it may take up to `N` comparisons to find the match._
_`NSSet` is a great choice for checking `containsObject:` due to efficient hashing algorithms. Adding/removing items is always `O(1)`. In addition, you have fast set arithmetic operations._
_`NSDictionary` is a great choice if you have a natural key you can use to access objects. This has no inherent order, but if you know the key you can retrieve any object as `O(1)`._

<a name="разница-между-set-и-array"></a>
## Разница между NSSet и NSArray
`NSArray` является упорядоченным массивом, в нем хранятся значения одного и того же типа в упорядоченном списке. Одно и то же значение может появляться в массиве несколько раз в разных положениях.
`NSSet` является неупорядоченным массивом, в нем хранятся отдельные значения одного и того же типа без определенного порядка. Вы можете использовать множество вместо массива, когда порядок элементов не важен, или когда вам нужно убедиться, что элемент появляется только один раз.
Добавить дубликат элемента в `NSMutableSet` у вас также не получится. Для создания неупорядоченного массива, в котором можно использовать неуникальные элементы, можно использовать `NSCountedSet`. Основным преимуществом `NSCountedSet` перед использованием классического массива `NSArray` является то, что элемент может быть продублирован огромное количество раз и при этом занимать памяти как один элемент. Это объясняется тем, что `NSCountedSet` хранит в памяти только одну копию элемента и запоминает сколько раз этот элемент встречается. Если для вас не важен порядок элементов внутри массива и вы используете действительно большие объемы информации, то использование `NSSet` повысит производительность приложения за счет снижения потребляемой памяти. Несмотря на то, что количество элементов хранящихся в памяти будет одинаковым, `NSSet` не тратит память на то, чтобы помнить в какой последовательности хранятся элементы.

<a name="difference-between-nsarray-and-cfarray"></a>
## Difference between NSArray and CFArray
What's the point of them both existing? There are a few reasons.

* If you want to provide a C API, like the Carbon API, and you need things like arrays and dictionaries of referenced-counted objects, you want a library like Core Foundation (which provides CFArray), and of course it needs to have a C API.
* If you want to write libraries for third-parties to use on Windows (for example), you need to provide a C API.
* If you want to write a low-level library, say for interfacing with your operating system's kernel, and you want avoid the overhead of Objective-C messaging, you need a C API.

So those are good reasons for having Core Foundation, a pure C library.

But if you want to provide a higher-level, more pleasant API in Objective-C, you want Objective-C objects that represent arrays, dictionaries, reference-counted objects, and so on. So you need Foundation, which is an Objective-C library.

When should you use one or the other? Generally, you should use the Objective-C classes (e.g. `NSArray`) whenever you can, because the Objective-C interface is more pleasant to use: `myArray.count` (or `[myArray count]`) is easier to read and write than `CFArrayGetCount(myArray)`. You should use the Core Foundation API only when you really need to: when you're on a platform that doesn't have Objective-C, or when you need features that the Core Foundation API provides but the Objective-C objects lack. For example, you can specify callbacks when creating a `CFArray` or a `CFDictionary` that let you store non-reference-counted objects. The `NSArray` and `NSDictionary` classes don't let you do that - they always assume you are storing reference-counted objects.
Are the CF objects just legacy objects? Not at all. In fact, Nextstep existed for years with just the Objective-C Foundation library and no Core Foundation library. When Apple needed to support both the Carbon API and the Cocoa API on top of the same lower-level operating system facilities, they created Core Foundation support both.

<a name="enumeration"></a>
## Enumeration
Enumeration is where computation gets interesting. It's one thing to encode logic that's executed once, but applying it across a collection – that's what makes programming so powerful.
* Procedural increments a pointer within a loop
* Object Oriented applies a function or block to each object in a collection
* Functional works through a data structure recursively

Cocoa содержит три основных способа перечисления содержимого коллекции. К ним относятся классический луп "for", быстрое перечисление и блочное перечисление. Существует также `NSEnumerator` класс, хотя в целом был замещен быстрым перечислением.

__C Loops (for/while)__

for and while loops are the "classic" method of iterating over a collection. Anyone who's taken Computer Science 101 has written code like this before:
```objectivec
for (NSUInteger i = 0; i < [array count]; i++) {
	id object = array[i];
	NSLog(@"%@", object);
}
```
But as anyone who has used C-style loops knows, this method is prone to off-by-one errors—particularly when used in a non-standard way. Fortunately, Smalltalk significantly improved this state of affairs with an idea called list comprehensions, which are commonly known today as for/in loops.

__List Comprehension (for/in)__

By using a higher level of abstraction, declaring the intention of iterating through all elements of a collection, not only are we less prone to error, but there's a lot less to type:
```objectivec
for (id object in array) {
	NSLog(@"%@", object);
}
```
Поведение для быстрого перечисления немного отличается в зависимости от типа коллекции. Массивы и наборы перечисляют их содержимое, а словари перечисляют свои ключи. `NSIndexSet` и `NSIndexPath` не поддерживают быстрое перечисление.
```objectivec
NSString *key;
for (key in someDictionary) {
	NSLog(@"Key: %@, Value %@", key, [someDictionary objectForKey: key]);
}
```
In Cocoa, comprehensions are available to any class that implements the `NSFastEnumeration` protocol, including `NSArray`, `NSSet`, and `NSDictionary`.
Быстрое перечисление является предпочтительным методом перечисления содержимого коллекции, поскольку оно обеспечивает следующие преимущества:

* Перечисление является более эффективным, чем использование NSEnumerator напрямую.
* Синтаксис краток
* Перечислитель вызывает исключение, если вы измените коллекции при перечислении.
* Вы можете выполнять несколько перечислений одновременно.

__Блочное перечисление__

Для перечисления с блоком, вызовите соответствующий метод и укажите блок для использования.
```objectivec
NSArray *anArray = [NSArray arrayWithObjects:@"A", @"B", @"D", @"M", nil];
NSString *string = @"c";
[anArray enumerateObjectsUsingBlock:^(id obj, NSUInteger index, BOOL *stop) {
	if ([obj localizedCaseInsensitiveCompare:string] == NSOrderedSame) {
		NSLog(@"Object Found: %@ at index: %i", obj, index);
		*stop = YES;
	}
}];
```
Для перечисления `NSArray`, параметр `index` полезен для одновременного перечисления. Без этого параметра, единственный способ получить доступ к индексу был бы использованием метода `indexOfObject:`, который является неэффективным. `stop` параметр важен для производительности, так как он позволяет остановить перечисление раньше, на основе некоторого условия, определяемого в пределах блока. Методы перечисления на основе блока в других коллекциях, немного отличаются по названию.

__Использование перечислителя NSEnumerator__

Абстрактный класс, экземпляры подклассов которого перечисляют коллекции других объектов, таких как массивы и словари. Все методы создания определены в классах коллекций, таких как `NSArray`, `NSSet` и `NSDictionary`, которые обеспечивают специальные объекты `NSEnumerator` для перечисления их содержимого. Например, класс `NSArray` имеет два метода, которые возвращают объект `NSEnumerator`: `objectEnumerator` и `reverseObjectEnumerator`. `NSDictionary` также имеет два метода, которые возвращают объект `NSEnumerator`: `keyEnumerator` и `objectEnumerator`. Эти методы позволяют перечислить содержимое словаря по ключу или по значению, соответственно. Вы отправляете `nextObject`, чтобы вновь созданный объект `NSEnumerator` возвращал следующий объект в оригинальной коллекции. Когда коллекция будет исчерпана, то возвращается `nil`. Вы не можете "сбросить" перечислитель после того, как он исчерпал свои коллекции. Подклассы `NSEnumerator`, используемые `NSArray`, `NSDictionary` и `NSSet` сохраняют коллекцию во время перечисления. Когда перечисление закончено, временные коллекции освобождаются.
_Примечание:_ не безопасно изменение коллекции во время её перечисления. Некоторые коллекции в настоящее время поддерживают такие операции, но такое поведение не гарантировано в будущем.
Для перечисления коллекции, вы должны создать новый перечислитель:
```objective-c
NSMutableDictionary *myMutableDictionary = ... ;
NSMutableArray *keysToDeleteArray = [NSMutableArray arrayWithCapacity:[myMutableDictionary count]];
NSString *aKey;
NSEnumerator *keyEnumerator = [myMutableDictionary keyEnumerator];
while (aKey = [keyEnumerator nextObject]) {
	if (/* Проверка критериев для ключа или значения */) {
		[keysToDeleteArray addObject:aKey];
	}
}
[myMutableDictionary removeObjectsForKeys:keysToDeleteArray];
```

__Array__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/array_performance.png">


__Dictionary__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/dictionary_performance.png">

Why is `NSFastEnumeration` so slow here? Iterating the dictionary usually requires both key and object; fast enumeration can only help for the key, and we have to fetch the object every time ourselves. Using the block-based `enumerateKeysAndObjectsUsingBlock:` is more efficient since both objects can be more efficiently prefetched.

<a name="filtering"></a>
## Filtering
If you look at an arbitrary code base, chances are you’ll sooner or later run into a piece of code similar to this one:
```objectivec
NSMutableArray *oldSkoolFiltered = [[NSMutableArray alloc] init];
for (Book *book in bookshelf) {
	if ([book.publisher isEqualToString:@"Apress"]) {
		[oldSkoolFiltered addObject:book];
	}
}
```
It’s a straight-forward approach to filtering an array of items (in this case, we’re talking about books) using a rather simple if-statement. Nothing wrong with this, but despite the fact we’re using a fairly simple expression here, the code is rather verbose. We can easily imagine what will happen in case we need to use more complicated selection criteria or a combination of filtering criteria.

__Simple filtering with NSPredicate__

Thanks to Cocoa, we can simplify the code by using NSPredicate. NSPredicate is the object representation of an if-statement, or, more formally, a predicate. Predicates are expressions that evaluate to a truth value, i.e. true or false. We can use them to perform validation and filtering. In Cocoa, we can use `NSPredicate` to evaluate single objects, filter arrays and perform queries against Core Data data sets. Let’s have a look at how our example looks like when using `NSPredicate`:
```objectivec
NSPredicate *predicate = [NSPredicate predicateWithFormat:@"publisher == %@", @"Apress"];
NSArray *filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
```

__Filtering with Regular Expressions__

Regular Expressions can be used to solve almost any problem, so it’s good to know you can use them in `NSPredicates` as well. To use regular expressions in your `NSPredicate`, you need to use the `MATCHES` operator. Let’s filter all books that are about iPad or iPhone programming:
```objectivec
predicate = [NSPredicate predicateWithFormat:@"title MATCHES '.*(iPhone|iPad).*'"];
filtered = [bookshelf filteredArrayUsingPredicate:predicate];
NSLog(@"Books that contain 'iPad' or 'iPhone' in their title", filtered);
```
You need to obey some rules when using regular expressions in `NSPredicate`: most importantly, you cannot use regular expression metacharacters inside a pattern set.

__Filtering using set operations__

Let’s for a moment assume you want to filter all books that have been published by your favorite publishers. Using the `IN` operator, this is rather simple: first, we need to set up a set containing the publishers we’re interested in. Then, we can create the predicate and finally perform the filtering operation:
```objectivec
NSArray *favoritePublishers = [NSArray arrayWithObjects:@"Apress", @"O'Reilly", nil];
predicate = [NSPredicate predicateWithFormat:@"publisher IN %@", favoritePublishers];
filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
NSLog(@"Books published by my favorite publishers", filtered);
```

__Advanced filtering thanks to KVC goodness__

NSPredicate relies on key-value coding to achieve its magic. On one hand this means your classes need to be KVC compliant in order to be queried using `NSPredicate` (at least the attributes you want to query). On the other hand, this allows us to perform some very interesting things with very little lines of code. Let’s for example retrieve a list of books written by authors with the name “Mark”:
```objectivec
predicate = [NSPredicate predicateWithFormat:@"authors.lastName CONTAINS %@", @"Mark" ];
filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
```
In case we’d want to return the value of one of the aggregate functions, we don’t need to use NSPredicate itself, but instead use KVC directly. Let’s retrieve the average price of all books on our shelf:
```objectivec
NSNumber *average = [bookshelf valueForKeyPath:@"@avg.price"];
```

<a name="sorting"></a>
## Sorting

Вам может потребоваться разместить несколько созданных пользователем строк в алфавитном порядке, либо вам потребуется разместить номера в убыванию или по возрастанию – используйте дескрипторы блоков и селекторов. Дескрипторы сортировки (экземпляры NSSortDescriptor) обеспечивают удобный и абстрактный способ описания порядка сортировки.
Простая сортировка по алфавиту:
```objectivec
NSArray *myArray = @[@"v", @"a", @"c", @"b", @"z"];
NSLog(@"%@", [myArray sortedArrayUsingSelector:@selector(caseInsensitiveCompare:)]);
```
`sortedArrayUsingDescriptors:` или `sortUsingDescriptors:`
```objectivec
//Сначала создадим массив из словарей
NSString *LAST = @"lastName";
NSString *FIRST = @"firstName";
NSMutableArray *array = [NSMutableArray array];
NSArray *sortedArray;
NSDictionary *dict;
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Jo", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Joe", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Joe", FIRST, @"Smythe", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Joanne", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Robert", FIRST, @"Jones", LAST, nil];
[array addObject:dict];
//Далее сортируем содержимое массива по last name затем first name
//Результаты могут быть показаны пользователю
//Обратите внимание на использование localizedCaseInsensitiveCompare:selector
NSSortDescriptor *lastDescriptor = [[NSSortDescriptor alloc] initWithKey:LAST ascending:YES selector:@selector(localizedCaseInsensitiveCompare:)];
NSSortDescriptor *firstDescriptor = [[NSSortDescriptor alloc] initWithKey:FIRST ascending:YES selector:@selector(localizedCaseInsensitiveCompare:)];
NSArray *descriptors = [NSArray arrayWithObjects:lastDescriptor, firstDescriptor, nil];
sortedArray = [array sortedArrayUsingDescriptors:descriptors];
```

__Сортировка с помощью функции__

Такой подход значительно менее гибкий.
```objectivec
NSInteger lastNameFirstNameSort(id person1, id person2, void *reverse) {
	NSString *name1 = [person1 valueForKey:LAST];
	NSString *name2 = [person2 valueForKey:LAST];
	NSComparisonResult comparison = [name1 localizedCaseInsensitiveCompare:name2];
	if (comparison == NSOrderedSame) {
		name1 = [person1 valueForKey:FIRST];
		name2 = [person2 valueForKey:FIRST];
		comparison = [name1 localizedCaseInsensitiveCompare:name2];
	}
	if (*(BOOL *)reverse == YES) {
		return 0 - comparison;
	}
	return comparison;
}
BOOL reverseSort = YES;
sortedArray = [array sortedArrayUsingFunction:lastNameFirstNameSort context:&reverseSort];
```

__Сортировка с блоками__

```objectivec
NSArray *sortedArray = [array sortedArrayUsingComparator: ^(id obj1, id obj2) {
	if ([obj1 integerValue] > [obj2 integerValue]) {
		return (NSComparisonResult)NSOrderedDescending;
	}
	if ([obj1 integerValue] < [obj2 integerValue]) {
		return (NSComparisonResult)NSOrderedAscending;
	}
	return (NSComparisonResult)NSOrderedSame;
}];
```

__Сортировка с помощью функций и селекторов__

Следующий листинг иллюстрирует использование методов `sortedArrayUsingSelector:`, `sortedArrayUsingFunction:context:`, и `sortedArrayUsingFunction:context:hint:`. Самым сложным из этих методов является `sortedArrayUsingFunction:context:hint:`. Он наиболее эффективен, когда у вас есть большой массив (`N` записей), которые вам надо отсортировать раз и затем лишь слегка изменить (`P` добавлений и удалений, где `P` гораздо меньше, чем `N`). Вы можете использовать работу, которую вы сделали в оригинальной сортировке, и сделать своего рода слияние между `N` "старых" предметов и `Р` "новых" предметов. Чтобы получить соответствующую подсказку, вы используете sortedArrayHint когда исходный массив был отсортирован, и держите его, пока вам это нужно (если вы хотите, отсортировать массив после того, как он был изменен).
```objectivec
NSInteger alphabeticSort(id string1, id string2, void *reverse) {
	if (*(BOOL *)reverse == YES) {
		return [string2 localizedCaseInsensitiveCompare:string1];
	}
	return [string1 localizedCaseInsensitiveCompare:string2];
}
NSMutableArray *anArray = [NSMutableArray arrayWithObjects:
@"aa", @"ab", @"ac", @"ad", @"ae", @"af", @"ag", @"ah", @"ai", @"aj", @"ak", @"al", @"am", @"an", @"ao", @"ap", @"aq", @"ar", @"as", @"at", @"au", @"av", @"aw", @"ax", @"ay", @"az", @"ba", @"bb", @"bc", @"bd", @"bf", @"bg", @"bh", @"bi", @"bj", @"bk", @"bl", @"bm", @"bn", @"bo", @"bp", @"bq", @"br", @"bs", @"bt", @"bu", @"bv", @"bw", @"bx", @"by", @"bz", @"ca", @"cb", @"cc", @"cd", @"ce", @"cf", @"cg", @"ch", @"ci", @"cj", @"ck", @"cl", @"cm", @"cn", @"co", @"cp", @"cq", @"cr", @"cs", @"ct", @"cu", @"cv", @"cw", @"cx", @"cy", @"cz", nil];
// внимание: anArray отсортирован
NSData *sortedArrayHint = [anArray sortedArrayHint];
[anArray insertObject:@"be" atIndex:5];
NSArray *sortedArray;
// сортировка используя селектор
sortedArray = [anArray sortedArrayUsingSelector:@selector(localizedCaseInsensitiveCompare:)];
// сортировка используя функцию
BOOL reverseSort = NO;
sortedArray = [anArray sortedArrayUsingFunction:alphabeticSort context:&reverseSort];
// сортировка с подсказкой
sortedArray = [anArray sortedArrayUsingFunction:alphabeticSort context:&reverseSort hint:sortedArrayHint];
```
Sorting 1,000,000 elements:
```
selector: 4947.90[ms]
function: 5618.93[ms]
block: 5082.98[ms]
```

<a name="nscache-vs-nsdictionary"></a>
## Зачем нужен NSCache? В чем от реализации кэша на NSDictionary?

`NSCache` objects differ from other mutable collections in a few ways:

* The NSCache class incorporates various auto-removal policies, which ensure that it does not use too much of the system’s memory. The system automatically carries out these policies if memory is needed by other applications. When invoked, these policies remove some items from the cache, minimizing its memory footprint.
* You can add, remove, and query items in the cache from different threads without having to lock the cache yourself.
* Retrieving something from an `NSCache` object returns an autoreleased result.
* Unlike an `NSMutableDictionary` object, a cache does not copy the key objects that are put into it.
* These features are necessary for the `NSCache` class, as the cache may decide to automatically mutate itself asynchronously behind the scenes if it is called to free up memory.

<a name="runtime"></a>
# RUNTIME
The heart of this power is the Objective-C runtime, provided by libobjc. The Objective-C runtime is a collection of functions that provides the dynamic features of Objective-C. It includes such core functions
As `objc_msgSend`, which is called every time you use the `[object message];` syntax. It also includes functions to allow you to inspect and modify the class hierarchy at runtime, including creating new classes and methods. Библиотека времени выполнения. Objective-C is a runtime-oriented language. Now the question that arises is, what is a runtime language? A runtime language is a language that decides what to implement in a function and other decisions during the runtime of the applications. Is Objective-C a runtime language? NO. It is a runtime-oriented language, which means that whenever it is possible, it defers decisions from compile and link time to the time when the code in the application is actually being executed. Функции и структуры Runtime-библиотеки определены в нескольких заголовочных файлах: `NSObjCRuntime.h`, `objc.h`, `runtime.h` и `message.h`.
Система вызова методов в Objective-C реализована через посылку сообщений объекту. Каждый вызов метода транслируется в соответствующий вызов функции `objc_msgSend`:
```objectivec
// Вызов метода
[array insertObject:foo atIndex:1];
// Соответствующий ему вызов Runtime-функции
objc_msgSend(array, @selector(insertObject:atIndex:), foo, 1);
```
Вызов `objc_msgSend` инициирует процесс поиска реализации метода, соответствующего селектору, переданному в функцию. Реализация метода ищется в так называемой таблице диспетчеризации класса. Поскольку этот процесс может быть достаточно продолжительным, с каждым классом ассоциирован кеш методов. После первого вызова любого метода, результат поиска его реализации будет закеширован в классе. Если реализация метода не найдена в самом классе, дальше поиск продолжается вверх по иерархии наследования — в суперклассах данного класса. Если же и при поиске по иерархии результат не достигнут, в дело вступает механизм динамического поиска — вызывается один из специальных методов: `resolveInstanceMethod` или `resolveClassMethod` (динамическое переопределение методов).

<a name="isa"></a>
## Что такое указатель isa? Для чего он нужен?
Каждый объект Objective-C содержит в себе атрибут `isa` - указатель на class object для данного объекта. class object автоматически создается компилятором и существует как один экземпляр, на который через `isa` ссылаются все экземпляры данного класса.
First there is a pointer to your class definition. Then each of your superclasses’ ivars (instance variables) are laid out as struct properties, and then your class’s ivars are laid out as struct properties. This structure is called `objc_object`, and a pointer to it is called `id`:
```objectivec
typedef struct objc_object {
  Class isa;
} *id;
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/isa.png">

<a name="метод-объекта"></a>
## Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?

_Форвардинг_

So if you pass a `doSomething` message to an object `[object doSomething]`
1. It will first check whether it has a `doSomething` method
2. Then it will check its superclasses
3. It'll try dynamic method resolution (`resolveInstanceMethod` for instance)
see [Dynamic method resolution](#dynamic-method-resolution)
4. It'll look for a forwarding target (`forwardingTargetForSelector:`)

> This method gives an object a chance to redirect an unknown message sent to it before the much more expensive forwardInvocation: machinery takes over. This is useful when you simply want to redirect messages to another object and can be an order of magnitude faster than regular forwarding. It is not useful where the goal of the forwarding is to capture the NSInvocation, or manipulate the arguments or return value during the forwarding.

5. Finally, if everything else fails, it'll create an invocation (using `methodSignatureForSelector:` and put to `forwardInvocation:`. By default, `forwardInvocation:` just calls doesNotRecognizeSelector: which crashes you on iOS (or terminates the current thread on OS X). But you can override it to do something else (like they have here).

The `NSInvocation` object encapsulates the original message and the arguments that were passed with it. You can implement a `forwardInvocation:` method to give a default response to the message, or to avoid the error in some other way. As its name implies, `forwardInvocation:` is commonly used to forward the message to another object.

<a name="классы"></a>
## Что такое классы в Objective-C, структура классов?
```objectivec
#import <objc/objc.h>
/*
*	Class Template
*/
struct objc_class {			
  struct objc_class *isa;
  struct objc_class *super_class;
  const char *name;		
  long version;
  long info;
  long instance_size;
  struct objc_ivar_list *ivars;

  #if defined(Release3CompatibilityBuild)
  struct objc_method_list *methods;
  #else
  struct objc_method_list **methodLists;
  #endif

  struct objc_cache *cache;
  struct objc_protocol_list *protocols;
};
```

<a name="объект"></a>
## Чем объект Objective-c отличается от структуры С, что такое структура в C?
Структура – специальный тип данных языка C, который содержит в себе другие типы данных в одном блоке и группирует их под одним именем.
```c
struct point {
  int x;
  int у;
};
```
Объекты в ObjС представляют собой структуры cо своими данными и в которых имеется ссылка isa на объект класса.

<a name="isKindOfClass"></a>
## Вопрос о методах isKindOfClass, isMemberOfClass
Протокол `<NSObject>`, методы тестирования наследования:

1. `isKindOfClass:`
2. `isMemberOfClass:`
3. `respondsToSelector:`
4. `conformsToProtocol:`

`isKindOfClass:`

Возвращает логическое значение, указывающее, является ли приемник экземпляром заданного класса или экземпляром любого класса, который наследует от этого класса (обязательный):
```objectivec
`- (BOOL)isKindOfClass:(Class)aClass`
```
Аргументы:

`aClass` Объект класс, представляющий Objective-C класс для тестирования.

Возвращаемое значение:

`YES`, если получатель является экземпляром `aClass` или экземпляром любого класса, который наследует от `aClass`, в противном случае `NO`.

`isMemberOfClass:`

Возвращает логическое значение, указывающее, является ли приемник экземпляром заданного класса (обязательный).
```objectivec
- (BOOL)isMemberOfClass:(Class)aClass
```
Аргументы:

`aClass` Объект класс, представляющий Objective-C класс для тестирования.

Возвращаемое значение:

`YES`, если получатель является экземпляром `aClass`, в противном случае `NO`.

`respondsToSelector:`

Возвращает логическое значение, указывающее, что приемник реализует или наследует метод, который может реагировать на указанное сообщение. (обязательный).
```objectivec
- (BOOL)respondsToSelector:(SEL)aSelector
```
Аргументы:

`aSelector` Селектор, который идентифицирует сообщение.

Возвращаемое значение:

`YES`, если приемник реализует или наследует метод, который может реагировать на `aSelector`, в противном случае `NO`.

`conformsToProtocol:`

Возвращает логическое значение, указывающее, что приемник соответствует заданному протоколу. (обязательный).
```objectivec
- (BOOL)conformsToProtocol:(Protocol *)aProtocol
```
Аргументы:

`aProtocol` Объект протокола, который представляет определенный протокол.

Возвращаемое значение:

`YES`, если приемник поддерживает `aProtocol`, в противном случае `NO`.

Рассмотрение:

Этот метод работает идентично методу класса `conformsToProtocol`: объявленному в `NSObject`. Это сделано для удобства, так чтобы вам не нужно было получать объект класса, чтобы узнать, может ли экземпляр ответить на заданный набор сообщений.

<a name="тип-id"></a>
## Тип id

__id__

```c
typedef struct objc_class *Class;
typedef struct objc_object {
    Class isa;
} *id;
```
`id` is a pointer to any Objective-C object (`objc_object`). It is not just a `void` pointer and you should not treat it as so. It references an object that should have a valid `isa` pointer. The values that can be stored in `id` are also not just limited to `NSObject` and its descendants, which starts to make sense of the existence of the `NSObject` protocol as well as the `NSProxy` class which does not even inherit from `NSObject`. The compiler will allow you to assign an object referenced by type `id` to any object type, assign any object type to `id`, as well as send it any message (that the compiler has seen) without warning.

Thus “id” type is polymorphic. This is very powerful as it doesn’t require a cast to use such a value:
```objectivec
id data = ...;
NSString *host = [data host]; // assume NSURL
```
Sure enough `id` usage can lead to bugs, because the availability of the method is determined at runtime. This is called “dynamic (or late) binding”. Nevertheless if used carefully it is very useful and lets you write parts of the code faster as if using a scripting language.

Unfortunately this doesn’t work with property syntax:
```objectivec
id data = ...;
NSString *host = data.host; // error: "Property 'host' not found"
data.host = @"dobegin.com"; // same error
```

__instancetype__

> Use the `instancetype` keyword as the return type of methods that return an instance of the class they are called on (or a subclass of that class). These methods include `alloc`, `init`, and class factory methods. Using `instancetype` instead of `id` in appropriate places improves type safety in your Objective-C code.

* Что случится во время компиляции если мы посылаем сообщение объекту типа id?

With a variable typed `id`, you can send it any known message and the compiler will not complain. With a variable typed `NSObject *`, you can only send it messages declared by `NSObject` (not methods of any subclass) or else it will generate a warning.

* Что произойдет здесь?
```objectivec
NSString *s = [NSNumber numberWithInt:3];
int i = [s intValue];
```
Переменная типа `id` фактически является указателем на произвольный объект. Для обозначения нулевого указателя на объект используется константа `nil` (= `NULL`). При этом вместо `id` можно использовать и более привычное обозначение с явным указанием класса. В частности последнее позволяет компилятору осуществлять некоторую проверку поддержки сообщения объектами — если компилятор из типа переменной не может сделать вывод о поддержке объектом данного сообщения, то он выдаст предупреждение. Тем самым язык поддерживает проверку типов, но в нестрогой форме (то есть найденные несоответствия возвращаются как предупреждения, а не ошибки).
```objectivec
MyArray *array = [MyArray arrayWithObjects:@(1), @(2), nil];
```
Теперь вы видите, почему возвращаемый тип `arrayWithObjects:` должен быть `id`. Если бы это был `(NSArray *)`, то подклассы потребует, чтобы они были приведены к необходимому классу.

* В чем разница между `void` и `void *`?

The `void` type, in several programming languages derived from C and Algol68, is the type for the result of a function that returns normally, but does not provide a result value to its caller. Usually such functions are called for their side effects, such as performing some task or writing to their output parameters.
C and C++ also support the pointer to `void` type (specified as `void *`), but this is an unrelated notion. Variables of this type are pointers to data of an unspecified type, so in this context (but not the others) `void *` acts roughly like a universal or top type. A program can probably convert a pointer to any type of data (except a function pointer) to a pointer to `void` and back to the original type without losing information, which makes these pointers useful for polymorphic functions. The C language standard does not guarantee that the different pointer types have the same size.

In C and C++

A function with `void` result type ends either by reaching the end of the function or by executing a return statement with no returned value. The `void` type may also appear as the sole argument of a function prototype to indicate that the function takes no arguments. Note that despite the name, in all of these situations, the `void` type serves as a unit type, not as a zero or bottom type (which is sometimes confusingly is also called the "void type"), even though unlike a real unit type which is a singleton, the `void` type lacks a way to represent it's a value and the language does not provide any way to declare an object or represent a value with type `void`.

* Можно ли создать структуру и привести к id?

`NSValue`

> A simple container for a single C or Objective-C data item. An `NSValue` object can hold any of the scalar types such as `int`, `float`, and `char`, as well as pointers, structures, and object `id` references. Use this class to work with such data types in collections (such as `NSArray` and `NSSet`), Key-value coding, and other APIs that require Objective-C objects. `NSValue` objects are always immutable.

```objectivec
[NSValue valueWithBytes:&struct objCType:@encode(MyStruct)];
```
And to get the value back out:
```objectivec
MyStruct struct;
[value getValue:&struct];
```

<a name="dynamic-method-resolution"></a>
## Dynamic method resolution

There are situations where you might want to provide an implementation of a method dynamically. For example, the Objective-C declared properties feature includes the `@dynamic` directive, which tells the compiler that the methods associated with the property will be provided dynamically. You can implement the methods `resolveInstanceMethod:` and `resolveClassMethod:` to dynamically provide an implementation for a given selector for an instance and class method respectively.

An Objective-C method is simply a C function that take at least two arguments — `self` and `_cmd`. You can add a function to a class as a method using the function `class_addMethod`. Therefore, given the following function:
```c
void dynamicMethodIMP(id self, SEL _cmd) {
  // implementation ....
}
```
you can dynamically add it to a class as a method (called `resolveThisMethodDynamically`) using `resolveInstanceMethod:` like this:
```objectivec
@implementation MyClass
+ (BOOL)resolveInstanceMethod:(SEL)aSEL {
  if (aSEL == @selector(resolveThisMethodDynamically)) {
    class_addMethod([self class], aSEL, (IMP) dynamicMethodIMP, "v@:");
      return YES;
    }
  return [super resolveInstanceMethod:aSEL];
}
@end
```
A class has the opportunity to dynamically resolve a method before the forwarding mechanism kicks in. If `respondsToSelector:` or `instancesRespondToSelector:` is invoked, the dynamic method resolver is given the opportunity to provide an `IMP` for the selector first. If you implement `resolveInstanceMethod:` but want particular selectors to actually be forwarded via the forwarding mechanism, you return `NO` for those selectors.

__Dynamic Loading__

An Objective-C program can load and link new classes and categories while it’s running. The new code is incorporated into the program and treated identically to classes and categories loaded at the start. Dynamic loading can be used to do a lot of different things. For example, the various modules in the System Preferences application are dynamically loaded. In the Cocoa environment, dynamic loading is commonly used to allow applications to be customized. Others can write modules that your program loads at runtime—much as Interface Builder loads custom palettes and the OS X System Preferences application loads custom preference modules. The loadable modules extend what your application can do. They contribute to it in ways that you permit but could not have anticipated or defined yourself. You provide the framework, but others provide the code.

<a name="блоки"></a>
# БЛОКИ

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/blocks.png">

Objective-C blocks introduce a new class of language-level types to represent block types. They match the standard (but tricky) syntax for C function pointer types, but with a `^` in place of the `*`:
```c
void (*)(int) // function pointer taking int and returning void
void (^)(int) // block taking int and returning void
```
As with function and method definitions, the braces indicate the start and end of the block. In this example, the block doesn’t return any value, and doesn’t take any arguments. In the same way that you can use a function pointer to refer to a C function, you can declare a variable to keep track of a block, like this:
```objectivec
void (^simpleBlock)(void);

simpleBlock = ^{
    NSLog(@"This is a block");
};
```
Once you’ve declared and assigned a block variable, you can use it to invoke the block:
```objectivec
simpleBlock();
```
Blocks are Objective-C objects. When you write a block in code, that is an expression of object type, much like the `@"..."` constant string syntax gives you an expression of object type. You can then use this object like you would any other Objective-C object, by sending it messages that it responds to, putting it into containers, passing it as a parameter, returning it, etc.

There is a major difference from the constant string syntax. Unlike constant strings, blocks are not exactly the same each time through a piece of code. This is because blocks capture their enclosing scope, and that scope is different every time they're called. In short, each time code execution hits a `^{...}` construct, a new object is created.

Allocating a new object every time would be kind of slow, so blocks take an unusual approach: the object you get from a `^{...}` construct is a stack object. The cost of calling a block is therefore about the same as the cost of calling a C function. This means that it has the same lifetime as local variables, and will be destroyed automatically upon leaving the current scope.

It's frequently useful for a block to outlive the scope where it was created. For example, you may want to return a block, or save it for later. For this to work, you must copy the block. You can do this like any other Objective-C object by sending it the `copy` message. And like any other Objective-C object, if you aren't running under Garbage Collection then you own the resulting object and must eventually dispose of it using `release` or `autorelease`.

Any reference to `self` is a reference to a local object variable, causing `self` to be retained. Any reference to an instance variable is an implicit reference to `self` and causes the same thing.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/block_capturing.png">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/blocks_structure.png">

```c
struct Block_literal_1 {
    void *isa; // initialized to &_NSConcreteStackBlock or &_NSConcreteGlobalBlock
    int flags;
    int reserved;
    void (*invoke)(void *, ...);
    struct Block_descriptor_1 {
    unsigned long int reserved;         // NULL
        unsigned long int size;         // sizeof(struct Block_literal_1)
        // optional helper functions
        void (*copy_helper)(void *dst, void *src);     // IFF (1<<25)
        void (*dispose_helper)(void *src);             // IFF (1<<25)
        // required ABI.2010.3.16
        const char *signature;                         // IFF (1<<30)
    } *descriptor;
    // imported variables
};

enum {
    BLOCK_HAS_COPY_DISPOSE =  (1 << 25),
    BLOCK_HAS_CTOR =          (1 << 26), // helpers have C++ code
    BLOCK_IS_GLOBAL =         (1 << 28),
    BLOCK_HAS_STRET =         (1 << 29), // IFF BLOCK_HAS_SIGNATURE
    BLOCK_HAS_SIGNATURE =     (1 << 30),
};
```

Objective-C blocks are objects which contain an embedded function pointer. A block call translates to a call to that function pointer, passing the block as an implicit parameter:
```objectivec
block();
// equivalent to:
block->impl(block);
```
It's slightly higher due to the need to look up the implementation pointer first, but just slightly.

It's actually fairly straightforward and described in Clang's Block Implementation Spec, in the "Imported Variables" section.

When the compiler encounters a Block like:
```objectivec
^{ if( numBalloons > numClowns) abort(); }
```
it creates a literal structure that includes -- among other things -- two elements that are important here. There's a function pointer to the executable code in the Block, and a const field for each variable that's referred to inside the Block. Something like this:
```c
struct __block_literal_1 {
    /* other fields */
    void (*invoke)(struct __block_literal_1 *);
    /* ... */
    const int numBalloons;
    const int numClowns;
};
```
Notice that the invoke function will take a pointer to a struct of the kind that's being defined right here; that is, the Block passes itself in when executing its code. Thus, the code gets access to the members of the structure.

Right after the declaration, the compiler creates a definition of the Block, which simply uses the referenced variables to initialize the correct fields in the struct:
```c
struct __block_literal_1 __block_literal_1 = {
    /* Other fields */
    __block_invoke_2, /* This function was also created by the compiler. */
    /* ... */
    numBalloons, /* These two are the exact same variables as */
    numClowns /* those referred to in the Block literal that you wrote. */
};
```
Then, inside the invoke function, references to the captured variables are made like any other member of a struct, `the_block->numBalloons`.

<a name="типы-блоков"></a>
## Типы блоков

* Global block (_NSConcreteGlobalBlock, NSGlobalBlock)

Normally, the `Block_literal` data appears on the stack (like a regular struct would in its surrounding function). With no references to the surrounding scope, clang configures the `Block_literal` as a global block instead. This causes the block to appear in a fixed global location instead of on the stack (the flags value has the `BLOCK_IS_GLOBAL` flag set to indicate this at runtime but it's not immediately clear to me if this is ever used).
The implication of this is that global blocks are never actually copied or disposed, even if you invoke the functions to do so. This optimisation is possible because without any references to the surrounding scope, no part of the block (neither its code nor its `Block_literal`) will ever change — it becomes a shared constant value.
```objectivec
Class class = [^{
} class];
NSLog(@"%@", NSStringFromClass(class));
//__NSGlobalBlock__
```

* Stack block (_NSConcreteStackBlock, NSStackBlock)

It is a stack allocated Objective-C object. If you have ever tried to allocate an Objective-C object on the stack (not as a pointer but statically allocated) you'll know that the compiler normally forbids this.
```objectivec
int foo = 3;
Class class = [^{
		int foo1 = foo + 1;
} class];
NSLog(@"%@", NSStringFromClass(class));
//__NSStackBlock__
```

* Malloc block (NSMallocBlock)

Copying a block doesn't really give you a copy of the block — if the block is already an `NSMallocBlock`, a copy simply increases the retain count of the block (this retain count is an internal reserved field — the retainCount returned from the object will remain at 1). This is perfectly appropriate since the scope of the block cannot change after it is created (therefore the block is constant) but it does mean that invoking copy on a block is not the same thing as recreating it.
```objectivec
int foo = 3;
Class class = [[^{
		int foo1 = foo + 1;
} copy] class];
NSLog(@"%@", NSStringFromClass(class));
//__NSMallocBlock__
```

Как видно, если блок не захватывает внешние переменные, то мы получаем `__NSGlobalBlock__`. Если же блок захватывает внешние переменные, то блок `__NSStackBlock__` (на стеке). Однако если же послать блоку `copy`, то блок будет скопирован в кучу (`__NSMallocBlock__`).

<a name="block-captures-self"></a>
## When and why block captures `self` and when they don't?

_Example:_
```objectivec
- (void)makeAsyncNetworkCall {
    [self.networkService performAsyncNetworkCallWithCompletion:^{
        dispatch_async(dispatch_get_main_queue(), ^{
                [self.activityIndicatorView stopAnimating];
            }
        });
    }];
}
```
I think the issue is that the `networkService` may keep a strong reference to the block. And the view controller may have a strong reference to the `networkService`. So the possible cycle of `VC->NetworkService->block->VC` could exist. However, in this case, it's usually safe to assume that the block will be released after it has run, in which case the cycle is broken. So, in this case, it isn't necessary.

Where it is necessary is if the block is not released. Say, instead of having a block that runs once after a network call, you have a block that is used as a callback. i.e. the `networkService` object maintains a strong reference to the block and uses it for all callbacks. In this case, the block will have a strong reference to the VC, and this will create a strong cycle, so a weak reference is preferred.

__Case 1: using the keyword self inside a block:__

If the block is retained by a property, a retain cycle is created between `self` and the block and both objects can’t be destroyed anymore. If the block is passed around and copied by others, `self` is retained for each copy.

The situation for object-type variables is a little more complicated, but the same principle applies.

__Case 2: declaring a `__weak` reference to `self` outside the block and use it inside the block:__

There is no retain cycle and no matter if the block is retained or not by a property. If the block is passed around and copied by others, when executed, `weakSelf` can have been turned `nil`. The execution of the block can be preempted and different subsequent evaluations of the `weakSelf` pointer can lead to different values (i.e. `weakSelf` can become `nil` at a certain evaluation).
```objectivec
__weak typeof(self) weakSelf = self;
dispatch_block_t block =  ^{
	[weakSelf doSomething]; // weakSelf != nil
	// preemption, weakSelf turned nil
	[weakSelf doSomethingElse]; // weakSelf == nil
};
```

__Case 3: declaring a `__weak` reference to `self` outside the block and use a `__strong` reference inside the block:__

There is no retain cycle and, again, no matter if the block is retained or not by a property. If the block is passed around and copied by others, when executed, `weakSelf` can have been turned `nil`. When the strong reference is assigned and it is not `nil`, we are sure that the object is retained for the entire execution of the block if preemption occurs and therefore subsequent evaluations of `strongSelf` will be consistent and will lead to the same value since the object is now retained. If `strongSelf` evaluates to `nil` usually the execution is returned since the block cannot execute properly.
```objectivec
__weak typeof(self) weakSelf = self;
myObj.myBlock = ^{
	__strong typeof(self) strongSelf = weakSelf;
	if (strongSelf) {
		[strongSelf doSomething]; // strongSelf != nil
		// preemption occurs, strongSelf still not nil
		[strongSelf doSomethingElse]; // strongSelf != nil
	} else {
		// Probably nothing...
		return;
	}
};
```
Dereferencing a `__weak` pointer is not allowed due to possible `null` value caused by race condition, assign it to a strong variable first. It can be shown with the following code:
```objectivec
__weak typeof(self) weakSelf = self;
myObj.myBlock =  ^{
    id localVal = weakSelf->someIVar;
};
```
_Case 1 should be used only when the block is not assigned to a property, otherwise it will lead to a retain cycle._

_Case 2 should be used when the block is assigned to a property and self is referenced only once and the block has a single statement._

_Case 3 should be used when the block is assigned to a property and self is referenced more the once and the block has more than a statement._

<a name="примеры"></a>
## Примеры объявления и использования блоков
```objectivec
#import "NSArray+Map.h"

@implementation NSArray (Map)

- (NSArray *)map:(id (^)(id))block {
	// takes an id, returns an id
	NSMutableArray *ret = [NSMutableArray array];
	for (id obj in self) {
		[ret addObject:block(obj)];
	}
	return ret;
}

- (NSArray *)select:(BOOL (^)(id obj))block {
	NSMutableArray *new = [NSMutableArray array];
	for (id obj in self) {
		if (block(obj)) {
			[new addObject: obj];
		}
	}
	return new;
}

@end

NSArray *array = @[@1, @2, @3, @4, @5];
NSArray *mappedArray = [array map:^id(id element) {
	NSNumber *current = (NSNumber *)element;
	return [NSNumber numberWithInt:[current intValue] * [current intValue]];
}];

NSArray *longStrings = [strings select:^BOOL (id obj) { return [obj length] > 5; }];
```

As a local variable:
```objectivec
returnType (^blockName)(parameterTypes) = ^returnType(parameters) {...};
```
As a property:
```objectivec
@property (nonatomic, copy) returnType (^blockName)(parameterTypes);
```
As a method parameter:
```objectivec
- (void)someMethodThatTakesABlock:(returnType (^)(parameterTypes))blockName;
````
As an argument to a method call:
```objectivec
[someObject someMethodThatTakesABlock:^returnType (parameters) {...}];
```
As a typedef:
```objectivec
typedef returnType (^TypeName)(parameterTypes);
TypeName blockName = ^returnType(parameters) {...};
```

## В чем отличие блока от лямбды и замыкания
Замыкание (англ. closure) в программировании — функция, в теле которой присутствуют ссылки на переменные, объявленные вне тела этой функции и не в качестве её параметров (а в окружающем коде). Говоря другим языком, замыкание — функция, которая ссылается на свободные переменные в своём контексте. Замыкание, так же как и экземпляр объекта, есть способ представления функциональности и данных, связанных и упакованных вместе.

Examples:
```python
def func(): return h
def anotherfunc(h):
	return func()
```   
This will cause an error, because `func` does not close over the environment in `anotherfunc` - `h` is undefined. `func` only closes over the global environment. This will work:
```python
def anotherfunc(h):
	def func(): return h
    return func()
```
Because here, `func` is defined in `anotherfunc`, and in python 2.3 and greater (or some number like this) when they almost got closures correct (mutation still doesn't work), this means that it closes over `anotherfunc`'s environment and can access variables inside of it. In Python 3.1+, mutation works too when using the `nonlocal` keyword.

Another important point - `func` will continue to close over `anotherfunc`'s environment even when it's no longer being evaluated in `anotherfunc`. This code will also work:
```python
def anotherfunc(h):
    def func(): return h
    return func

print anotherfunc(10)()
```
This will print `10`.

This, as you notice, has nothing to do with lambda's - they are two different (although related) concepts.

Лямбда-выражение — это специальный синтаксис для объявления анонимных функторов по месту их использования. Используя лямбда-выражения, можно объявлять функции в любом месте кода. Обычно лямбда-выражение допускает замыкание на лексический контекст, в котором это выражение использовано. Лямбда-выражения поддерживаются во многих языках программирования (C, Common Lisp, Python, PHP, C#, F#, Visual Basic .NET, C++, Java и других).
Нестандартное расширение синтаксиса языков программирования C/C++/Objective-C, позволяющее инкапсулировать код и данные в один объект. Блоковые объекты это C-уровневые синтаксические функции. Они похожи на стандартные функции C, но в дополнение к исполняемому коду они также могут содержать переменные привязанные к автоматической (стеку) или управляемой (куче) памяти. Поэтому блок может поддерживать набор состояний (данные), которые он может использовать, чтобы повлиять на поведение при выполнении. Блоки особенно полезны в качестве обратного вызова, потому что блок несет как код, который будет выполняться на обратном вызове, так и данные, необходимые во время этого выполнения.
A lambda is just an anonymous function - a function defined with no name. In some languages, such as Scheme, they are equivalent to named functions. In fact, function definition is rewritten as binding a lambda to a variable internally. In other languages, like Python, there are some (rather needless) distinctions between them, but they behave the same way otherwise.

As lower level languages, C and C++ had no concept of anonymous functions. To add them, new syntax had to be created. Because of this, Objective-C blocks and C++0x lambdas ended up with somewhat different syntax. An empty Objective-C block looks like this:
```
^{}
```
Whereas an empty C++0x lambda looks like this:
```
[]{}
```
So far not much different. They both use the standard C `{}` symbols to separate a block of code, with a special symbol to indicate that this is a block or lambda, not a normal C block. In both cases, the `{}` section takes normal code.
The anonymous function can take arguments by writing them in parentheses, in the style of function arguments, after the leading bit:
```objectivec
^(int x, NSString *y){} // ObjC, take int and NSString*
```
```c++
[](int x, std::string y){} // C++, take int and std::string
```
In both languages, a value can be returned, and the return type can be inferred from the return statement:
```objectivec
^{ return 42; } // ObjC, returns int
```
```c++
[]{ return 42; } // C++, returns int
```
Here, the two features begin to diverge. With C++0x lambdas, the return type can only be inferred if the lambda contains a single statement, and that statement is a return statement. So while the above is valid, this is not:
```c++
[]{ if(something) return 42; else return 43; }
```
In a more complicated lambda with an inferred return type, the return type is always inferred to be `void`. The code above will therefore produce an error, because it's invalid to return `42` from something with a return type of `void`.

Замыкание — процедура, которая ссылается на свободные переменные в своём лексическом контексте. На примере лямбда это анонимный метод который допускает замыкание.
```c#
//oldArray 1, 2, 5, 10, 20
var newArray = oldArray.Select(x=>x > 5); // замыкание не используется

int y = 1;
var newArray = oldArray.Select(x=>x * y); // замыкание используется
```
Таким образом, лямбда-функция это жаргонное название анонимной функции, то есть функции у которой нет имени.
Замыкание, строго говоря, никак не связано с анонимностью. Замыкание - это по сути вложенная функция, которая может обращаться к переменным в функции, в которую она вложена. Поэтому можно говорить, что замыкание - это функция, у которой есть состояние. При этом замыкающаяся функция может быть анонимной (то есть лямбдой), а может и не быть. Лямбда-функция, аналогично, может быть замыканием, а может и не быть (если она не обращается к переменным, объявленным вне её).

<a name="обратный-вызов"></a>
## Обратный вызов
Ситуация, в которой код ожидает внешних событий, называется обратным вызовом. Для программистов Objective-C существуют три основных формы обратного вызова.

1. Приемник/действие: перед началом ожидания вы говорите: «Когда произойдет Х, отправь это конкретное сообщение этому конкретному объекту». Объект, получающий сообщение, называется приемником. Селектор сообщения и есть действие.
2. Вспомогательные объекты: перед началом ожидания вы говорите: «Здесь имеется вспомогательный объект, поддерживающий твой протокол. Когда что-нибудь произойдет, отправляй ему сообщения. Вспомогательные объекты часто называются делегатами или источниками данных.
3. Оповещения: имеется объект, называемый центром оповещений. Перед началом ожидания вы говорите ему: «Этот объект ожидает таких-то оповещений. При поступлении одного из них отправь объекту это сообщение». Когда происходит Х, объект отправляет оповещение центру оповещений, а последний пересылает его вашему объекту.
4. Блоки

__Example 1__

There is no "callback" in C - not more than any other generic programming concept. They're implemented using function pointers. Here's an example:
```c
void populate_array(int *array, size_t arraySize, int (*getNextValue)(void)) {
    for (size_t i=0; i<arraySize; i++)
        array[i] = getNextValue();
}

int getNextRandomValue(void) {
    return rand();
}

int main(void) {
    int myarray[10];
    populate_array(myarray, 10, getNextRandomValue);
    ...
}
```
Here, the `populate_array` function takes a function pointer as its third parameter, and calls it to get the values to populate the array with. We've written the callback `getNextRandomValue`, which returns a randomish value, and passed a pointer to it to `populate_array`. `populate_array` will call our callback function 10 times and assign the returned values to the elements in the given array.

__Example 2__

Let's say you want to write some code that allows registering callbacks to be called when some event occurs. First define the type of function used for the callback:
```c
typedef void (*event_cb_t)(const struct event *evt, void *userdata);
```
Now, define a function that is used to register a callback:
```c
int event_cb_register(event_cb_t cb, void *userdata);
```
This is what code would look like that registers a callback:
```c
static void my_event_cb(const struct event *evt, void *data) {
    /* do stuff and things with the event */
}

...
event_cb_register(my_event_cb, &my_custom_data);
...
```
In the internals of the event dispatcher, the callback may be stored in a struct that looks something like this:
```c
struct event_cb {
    event_cb_t cb;
    void *data;
};
```
This is what the code looks like that executes a callback.
```c
struct event_cb *callback;
...

/* Get the event_cb that you want to execute */

callback->cb(event, callback->data);
```

<a name="блоки-делегаты-kvo-уведомления"></a>
## Когда использовать блоки, делегаты, KVO и уведомления?
__Block__

* 1–3 callbacks
* Single observer

__Delegate__

* Many callbacks
* Single observer
* Formal interface

__KVO__

* Any number of observers
* Just want to be notified of changes to state of an object
* Simplistic updates, unrelated to behavior

__Notifications__

* Multiple observers
* Observer 'far away' from observee

http://albertodebortoli.com/blog/2013/04/21/objective-c-blocks-under-the-hood/

http://albertodebortoli.com/blog/2013/08/03/objective-c-blocks-caveat/

https://www.mikeash.com/pyblog/friday-qa-2009-08-14-practical-blocks.html

http://rypress.com/tutorials/objective-c/blocks

https://clang.llvm.org/docs/Block-ABI-Apple.html
