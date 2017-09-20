- [Objective-C](#objective-c)
	- [Transparent and opaque data types](#transparent-and-opaque-data-types)
	- [Toll-Free Bridged Types](#toll-free-bridged-types)
	- [Директивы компилятора](#директивы-компилятора)

<a name="objective-c"></a>
# Objective-C
Компилируемый язык программирования, используемый корпорацией Apple, построенный на основе языка Си и парадигм Smalltalk. В частности, объектная модель построена в стиле Smalltalk — то есть объектам посылаются сообщения. Язык Objective-C является надмножеством языка Си, поэтому Си-код полностью понятен компилятору Objective-C. Компилятор Objective-C доступен на большинстве основных платформ. Язык используется в первую очередь для Mac OS X (Cocoa) и GNUstep — реализаций объектно-ориентированного интерфейса OpenStep. Также язык используется для iOS (Cocoa Touch). Objective-C был создан Брэдом Коксом в начале 1980-х в его компании Stepstone. Он искал возможность собирать программы из готовых компонентов (объектов), подобно тому как сложные электронные устройства могут быть легко собраны из набора готовых интегральных микросхем. При этом такой язык должен быть достаточно простым и основанным на языке Си, чтобы облегчить переход разработчиков на него. Таким образом, Objective-C является именно расширением языка Си — в язык Си просто добавлены новые возможности для объектно-ориентированного программирования. При этом любая программа на Си является программой и на Objective-C.
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

`@synthesize` Дает указание компилятору, что необходимо автоматически сгенерировать сеттеры и геттеры для данных (разделенных запятой) свойств. Сеттеры и геттеры автоматически создаются согласно указанным в объявлении свойства директивам. Если переменные экземпляра называ-ются не так, как указано после директивы `@property`, вы можете соединить их с помощью знака равенства

`@dynamic` Cообщает компилятору, что требуемые сеттеры и геттеры для данных свойств будут реализованы вручную или динамически во время выполнения. При доступе к таким свойствам, компилятор не будет выдавать предупреждений, даже если требуемые сеттеры и геттеры не реализованы. Вы можете использовать такие свойства, когда хотите, чтобы сеттеры и геттеры выполняли какойто специфичный для вас код.

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
