
- [Swift](#swift)
  - [Memory management](#memory-management)
  - [Сlosures and functions](#сlosures-and-functions)
  - [How Do I Declare a Closure in Swift?](#how-do-i-declare-a-closure-in-swift)
  - [Generics](#generics)
  - [Что такое протокол-ориентированное программирование? Как оно связано со Swift? Чем протоколы Swift отличаются от протоколов Objective-C?](#что-такое-протокол-ориентированное-программирование-как-оно-связано-со-swift-чем-протоколы-swift-отличаются-от-протоколов-objective-c)
  - [Difference between Array VS NSArray VS \[AnyObject\]](#difference-between-array-vs-nsarray-vs-anyobject)
  - [Objective-C id is Swift Any or AnyObject](#objective-c-id-is-swift-any-or-anyobject)
  - [ValueType vs. ReferenceType](#valuetype-vs-referencetype)
  - [What is copy on write mechanism](#what-is-copy-on-write-mechanism)
  - [RxSwift](#rxswift)
  - [SwiftUI](#swiftui)
  - [Combine](#combine)
  - [Publishers](#publishers)
  - [Subscribers](#subscribers)
  - [Operators](#operators)
  - [Metod Dispatching](#metod-dispatching)
  - [Чем отличается Generic от Protocol?](#чем-отличается-generic-от-protocol)
  - [Какие бывают анимации?](#какие-бывают-анимации)
  - [Что такое type erasure?](#что-такое-type-erasure)
  - [Разница между map, compactMap и flatMap?](#разница-между-map-compactmap-и-flatmap)
  - [Что такое opaque type?](#что-такое-opaque-type)
  - [Что такое Sendable?](#что-такое-sendable)

<a name="swift"></a>

# Swift

* Multi-paradigm: protocol-oriented, object-oriented, functional, imperative, block structured
- Designed by Chris Lattner and Apple Inc.
- First appeared: June 2, 2014
- Stable release: 5.6.1 / April 8, 2022
- Typing discipline: Static, strong, inferred
- OS: Darwin, Linux, FreeBSD
- Influenced by C#, CLU, D, Haskell, Objective-C, Python, Ruby, Rust

Swift is a multi-paradigm, compiled programming language created by Apple Inc. for iOS, OS X, watchOS and tvOS development. Swift is designed to work with Apple's Cocoa and Cocoa Touch frameworks and the large body of existing Objective-C code written for Apple products. Swift is in-tended to be more resilient to erroneous code ("safer") than Objective-C and also more concise. It is built with the LLVM compiler and later and uses the Objective-C runtime, allowing C, Objective-C, C++ and Swift code to run within a single program.

Swift supports the core concepts that made Objective-C flexible, notably dynamic dispatch, wide-spread late binding, extensible programming, and similar features. These features also have well known performance and safety trade-offs, which Swift was designed to address. For safety, Swift introduced a system that helps address common programming errors like null pointers, as well as introducing syntactic sugar to avoid the pyramid of doom that can result. For performance issues, Apple has invested considerable effort in aggressive optimization that can flatten out method calls and accessors to eliminate this overhead. More fundamentally, Swift has added the concept of protocol extensibility, an extensibility system that can be applied to types, structs and classes, Apple promotes this as a real change in programming paradigms they refer to as "protocol-oriented programming".

__Плюсы__

- It has less overhead and syntax requirements, and you can often achieve the same line of code using less characters.
- Swift is a functional programming language, which means you can do neat tricks like passing functions as variables. This means you can write highly generic code that can do a lot of different things, reducing repetition.
- Swift is 'safer' - there's less memory management to worry about (basically none, compared to C).
- API Swift легко читать и поддерживать. Предполагаемые типы делают ваш код более чистым и менее подверженным ошибкам. Модули удаляют заголовки и предоставляют пространства имен.
- Swift поддерживает все платформы Apple, Linux, Windows и Ubuntu.
- Динамические библиотеки существуют вне вашего кода и загружаются при необходимости. Библиотеки интегрированы в каждую версию устройства.
- Swift имеет одно из самых активных и богатых сообществ с открытым исходным кодом. Кроме того, есть много ресурсов, которые помогут вам выучить язык.

__Минусы__

- Относительно новый язык: Swift все еще молодой язык. Это означает, что некоторые из его возможностей и ресурсов не так надежны, как другие языки программирования.
- Слабая кроссплатформенная поддержка: хотя Swift поддерживает все платформы Apple, Linux и Windows, он лучше всего подходит для разработки под iOS.
- Частые обновления: Swift — более новый язык, и у него частые обновления. Это может затруднить поиск подходящих инструментов для решения определенных задач.
- Поддержка IDE: Xcode, официальная среда разработки Apple, не соответствует требованиям в некоторых областях поддержки, включая выделение синтаксиса, автозаполнение, рефакторинг и компиляцию.

<a name="memory-management"></a>

## Memory management

At hardware level, memory is just a long list of bytes. We treat it as if it were organized into three virtual parts:

- Stack, where all local variables go.
- Global data, where static variables, constants and type metadata go.
- Heap, where all dynamically allocated objects go. Basically, everything that has a lifetime is stored here.

Memory management is the process of controlling program’s memory. Memory management is tightly connected with the concept of Ownership. Ownership is the responsibility of some piece of code to eventually cause an object to be destroyed. `Automatic reference counting (ARC)` is Swift ownership system, which implicitly imposes a set of conventions for managing and transferring ownership. The name by which an object can be pointed is called a `reference`. Swift references have two levels of strength: `strong` and `weak`. Additionally, `weak` references have a flavor, called `unowned`.

The essence of Swift memory management is: Swift preserves an object if it is strongly referenced and deallocates it otherwise. The rest is just an implementation detail.

__Understanding Strong, Weak and Unowned__

The purpose of a strong reference is to keep an object alive. Strong referencing might result in several non-trivial problems:

- Retain cycles. Considering that Swift language is not cycle-collecting, a reference R to an object which holds a strong reference to the object R (possibly indirectly), results in a reference cycle. We must write lots of boilerplate code to explicitly break the cycle.
- It is not always possible to make strong references valid immediately on object construction, e.g. with delegates.

Weak references address the problem of back references. An object can be destroyed if there are weak references pointing to it. A weak reference returns nil, when an object it points to is no longer alive. This is called `zeroing`.

Unowned references are different flavor of weak, designed for tight validity invariants. Unowned references are `non-zeroing`. When trying to read a non-existent object by an unowned reference, a program will crash with assertion error. They are useful to track down and fix consistency bugs.

__Defining Swift Runtime__

The mechanism of ARC is implemented in a library called Swift Runtime. It implements such core features as the runtime type system, including dynamic casting, generics, and protocol conformance registration. Swift Runtime represents every dynamically allocated object with `HeapObject` struct. It contains all the pieces of data which make up an object in Swift: reference counts and type metadata. Internally every Swift object has three reference counts: one for each kind of reference. At the SIL generation phase, swift compiler inserts calls to the methods `swift_retain()` and `swift_release()`, wherever it’s appropriate. This is done by intercepting initialization and destruction of HeapObjects. Compilation is one of the steps of Xcode Build System. If you are an old school Objective-C programmer and wonder where is autorelease, then I have some news for you: there is no such thing for pure Swift objects. Now let’s move on to the weak references. The way they are implemented is closely connected with the concept of side tables.

__Introducing Side Tables__

Side tables are mechanism for implementing Swift weak references. Typically objects don’t have any weak references, hence it is wasteful to reserve space for weak reference count in every object. This information is stored externally in side tables, so that it can be allocated only when it’s really needed. Instead of directly pointing to an object, weak reference points to the side table, which in its turn points to the object. This solves two problems: saves memory for weak reference count, until an object really needs it; allows to safely zero out weak reference, since it does not directly point to an object, and no longer a subject to race conditions. Side table is just a reference count + a pointer to an object. They are declared in Swift Runtime as follows (C++ code):

```c++
class HeapObjectSideTableEntry {
  std::atomic<HeapObject*> object;
  SideTableRefCounts refCounts;
  // Operations to increment and decrement reference counts
}
```

__Swift Object Life Cycle__

Swift objects have their own life cycle, represented by a finite state machine on the figure below. Square brackets indicate a condition that triggers transition from state to state.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/heap-object-lifecycle.svg">

In `live` state an object is alive. Its reference counts are initialized to 1 `strong`, 1 `unowned` and 1 `weak` (side table starts at +1). `Strong` and `unowned` reference access work normally. Once there is a `weak` reference to the object, the side table is created. The `weak` reference points to the side table instead of the object.

From the `live` state, the object moves into the `deiniting` state once `strong` reference count reaches zero. The `deiniting` state means that `deinit()` is in progress. At this point `strong` ref operations have no effect. `Weak` reference reads return `nil`, if there is an associated side table (otherwise there are no `weak` refs). `Unowned` reads trigger assertion failure. New `unowned` references can still be stored. From this state, the object can take two routes:

- A shortcut in case there no `weak`, `unowned` references and the side table. The object transitions to the dead state and is removed from memory immediately.
- Otherwise, the object moves to `deinited` state.

In the `deinited` state `deinit()` has been completed and the object has outstanding `unowned` references (at least the initial +1). `Strong` and `weak` stores and reads cannot happen at this point. `Unowned` stores also cannot happen. `Unowned` reads trigger assertion error. The object can take two routes from here:

- In case there are no `weak` references, the object can be deallocated immediately. It transitions into the `dead` state.
- Otherwise, there is still a side table to be removed and the object moves into the freed state.

In the `freed` state the object is fully deallocated, but its side table is still alive. During this phase the `weak` reference count reaches zero and the side table is destroyed. The object transitions into its final state. In the dead state there is nothing left from the object, except for the pointer to it. The pointer to the `HeapObject` is freed from the Heap, leaving no traces of the object in memory.

__Reference Count Invariants__

During their life cycle, the objects maintain following invariants:

- When the `strong` reference count becomes zero, the object is `deinited`. Unowned reference reads raise assertion errors, `weak` reference reads become `nil`.
- The `unowned` reference count adds +1 to the `strong` one, which is decremented after object’s `deinit` completes.
- The `weak` reference count adds +1 to the `unowned` reference count. It is decremented after the object is freed from memory.

<https://github.com/apple/swift/blob/main/stdlib/public/SwiftShims/RefCount.h>

<a name="closures-and-functions"></a>

## Сlosures and functions

```swift
()->()
```

Closures in Swift are similar to blocks in C and Objective-C.
Closures are first-class objects, so that they can be nested and passed around (as do blocks in Objective-C). In Swift, functions are just a special case of closures.

_Defining a function:_

You define a function with the `func` keyword. Functions can take and return none, one or multiple parameters (tuples).
Return values follow the `->` sign.

```swift
func jediGreet(name: String, ability: String) -> (farewell: String, mayTheForceBeWithYou: String) {
 return ("Good bye, \(name).", " May the \(ability) be with you.")
}
```

_Calling a function:_

```swift
let retValue = jediGreet("old friend", "Force")
println(retValue)
println(retValue.farewell)
println(retValue.mayTheForceBeWithYou)
```

_Function types_

Every function has its own function type, made up of the parameter types and the return type of the function itself.
For example the following function:

```swift
func sum(x: Int, y: Int) -> (result: Int) { return x + y }
```

has a function type of:

```swift
(Int, Int) -> (Int)
```

Function types can thus be used as parameters types or as return types for nesting functions.

_Passing and returning functions_

The following function is returning another function as its result which can be later assigned to a variable and called.

```swift
func jediTrainer() -> ((String, Int) -> String) {
 func train(name: String, times: Int) -> (String) {
  return "\(name) has been trained in the Force \(times) times"
   }
   return train
}
let train = jediTrainer()
train("Obi Wan", 3)
```

_Variadic functions_

Variadic functions are functions that have a variable number of arguments (indicated by `...` after the argument's type) that can be accessed into their body as an array.

```swift
func jediBladeColor(colors: String...) -> () {
 for color in colors {
  println("\(color)")
   }
}
jediBladeColor("red","green")
```

__Closures__

```swift
{()->() in}
```

_Defining a closure:_

Closures are typically enclosed in curly braces `{ }` and are defined by a function type `() -> ()`, where `->` separates the arguments and the return type, followed by the `in` keyword which separates the closure header from its body.

```swift
{ (params) -> returnType in
  statements
}
```

An example could be the map function applied to an Array:

```swift
let padawans = ["Knox", "Avitla", "Mennaus"]
padawans.map({(padawan: String) -> String in
 "\(padawan) has been trained!"
})
```

_Closures with known types:_
When the type of the closure's arguments are known, you can do as follows:

```swift
func applyMutliplication(value: Int, multFunction: Int -> Int) -> Int {
 return multFunction(value)
}

applyMutliplication(2, {value in
 value * 3
})
```

_Closures shorthand argument names:_

Closure arguments can be references by position `($0, $1, ...)` rather than by name

```swift
applyMutliplication(2, {$0 * 3})
```

Furthermore, when a closure is the last argument of a function, parenthesis can be omitted as such:

```swift
applyMutliplication(2) {$0 * 3}
```

<a name="how-do-i-declare-a-closure-in-swift"></a>

## How Do I Declare a Closure in Swift?

_As a variable:_

```swift
var closureName: (parameterTypes) -> (returnType)
```

_As an optional variable:_

```swift
var closureName: ((parameterTypes) -> (returnType))?
```

_As a type alias:_

```swift
typealias closureType = (parameterTypes) -> (returnType)
```

_As a constant:_

```swift
let closureName: closureType = { ... }
```

_As an argument to a function call:_

```swift
func({(parameterTypes) -> (returnType) in statements})
```

_As a function parameter:_

```swift
array.sort({ (item1: Int, item2: Int) -> Bool in return item1 < item2 })
```

_As a function parameter with implied types:_

```swift
array.sort({ (item1, item2) -> Bool in return item1 < item2 })
```

_As a function parameter with implied return type:_

```swift
array.sort({ (item1, item2) in return item1 < item2 })
```

_As the last function parameter:_

```swift
array.sort { (item1, item2) in return item1 < item2 }
```

_As the last parameter, using shorthand argument names:_

```swift
array.sort { return $0 < $1 }
```

_As the last parameter, with an implied return value:_

```swift
array.sort { $0 < $1 }
```

_As the last parameter, as a reference to an existing function:_

```swift
array.sort(<)
```

_As a function parameter with explicit capture semantics:_

```swift
array.sort({ [unowned self] (item1: Int, item2: Int) -> Bool in
 return item1 < item2
})
```

_As a function parameter with explicit capture semantics and inferred parameters / return type:_

```swift
array.sort({ [unowned self] in return item1 < item2 })
```

<a name="generics"></a>

## Generics

Generic code enables you to write flexible, reusable functions and types that can work with any type, subject to requirements that you define. You can write code that avoids duplication and expresses its intent in a clear, abstracted manner.
Generics are one of the most powerful features of Swift, and much of the Swift standard library is built with generic code. In fact, you’ve been using generics throughout the Language Guide, even if you didn’t realize it. For example, Swift’s Array and Dictionary types are both generic collections. You can create an array that holds Int values, or an array that holds String values, or indeed an array for any other type that can be created in Swift. Similarly, you can create a dictionary to store values of any specified type, and there are no limitations on what that type can be.

```swift
func swapTwoValues<T>(inout a: T, inout _ b: T) {
 let temporaryA = a
 a = b
 b = temporaryA
}
```

<a name="protocols"></a>

## Что такое протокол-ориентированное программирование? Как оно связано со Swift? Чем протоколы Swift отличаются от протоколов Objective-C?

Protocol-Oriented Programming is a new programming paradigm ushered in by Swift 2.0. In the Protocol-Oriented approach, we start designing our system by defining protocols. We rely on new concepts: protocol extensions, protocol inheritance, and protocol compositions. The paradigm also changes how we view semantics. In Swift, value types are preferred over classes. However, object-oriented concepts don’t work well with structs and enums: a struct cannot inherit from another struct, neither can an enum inherit from another enum. So inheritance - one of the fundamental object-oriented concepts - cannot be applied to value types. On the other hand, value types can inherit from protocols, even multiple protocols. Thus, with POP, value types have become first class citizens in Swift.

Protocol-Oriented Programming опирается на Generic Programming и концепцию Traits. Использование POP повышает переиспользование кода, лучше структурирует код, уменьшает дублирование кода, избегает сложности с иерархией наследования классов, делает код более связным.

__Protocol Extensions__

You can extend a protocol and provide default implementation for methods, computed properties, subscripts and convenience initializers.

__Protocol Inheritance__

A protocol can inherit from other protocols and then add further requirements on top of the requirements it inherits.

__Protocol Composition__

Swift types can adopt multiple protocols.

Использование протокола можно разделить на несколько сценариев:

- Протокол как тип
- Протокол как шаблон типа
- Протокол как Trait
- Протокол как маркер
- Retroactive modeling (extensions)
- Протокол как констрейнт

__Отличия POP от OOP__

_Абстракция_

В ООП роль абстрактного типа данных играет класс.

В POP — протокол. Преимущества протокола как абстракции:

- Поддержка value-типов (и классов)
- Поддержка статических отношений типов (и dynamic dispatch)
- Немонолитный
- Поддержка retroactive modeling
- Не навязывает данные объекта (поля базового класса)
- Не обременяет инициализацией (базового класса)
- Даёт понять, что реализовывать

_Инкапсуляция_

Свойство системы, позволяющее объединить данные и методы, работающие с ними, в классе. Протокол не может содержать сами данные, он может содержать только требования на свойства, которые эти данные бы предоставляли. Как и в ООП, необходимые данные должны быть включены в класс/структуру, но функции могут быть определены как в классе, так и в extensions.

_Полиморфизм_

POP поддерживает 2 вида полиморфизма:

- полиморфизм подтипов. Он же используется в ООП:

```swift
func process(service: ServiceType) { ... }
```

- параметрический полиморфизм. Используется в обобщенном программировании.

```swift
func process<Service: ServiceType>(service: Service) { ... }
```

В случае с полиморфизмом подтипов, нам неизвестен конкретный тип, который передаётся в функцию — нахождение реализации методов этого типа будет осуществляться во время выполнения (Dynamic dispatch). При использовании параметрического полиморфизма — тип параметра известен во время компиляции, соответственно и его методы (Static dispatch). За счёт того, что на этапе сборки известны используемые типы, компилятор имеет возможность лучше оптимизировать код — в первую очередь, за счёт использования подстановки (inline) функций.

_Наследование_

Наследование в ООП служит для заимствования функциональности от родительского класса.

В POP получение нужной функциональности происходит за счёт добавления соответствий протоколам, которые предоставляют функции через extensions. При этом мы не ограничены классами, имеем возможность расширять за счёт протоколов структуры и enum-ы. Протоколы могут наследоваться от других протоколов — это означает добавление к собственным требованиям требований от родительских протоколов.

<a name="array-nsarray-anyobject"></a>

## Difference between Array VS NSArray VS [AnyObject]

`Array` is a struct, therefore it is a value type in Swift.

`NSArray` is an immutable Objective C class, therefore it is a reference type in Swift and it is bridged to `Array<AnyObject>`. `NSMutableArray` is the mutable subclass of `NSArray`.

`[AnyObject]` is the same as `Array<AnyObject>`

<a name="id-any"></a>

## Objective-C id is Swift Any or AnyObject

`Any` can represent an instance of any type at all, including function types and optional types.

`AnyObject` can represent an instance of any class type.

> As part of its interoperability with Objective-C, Swift offers convenient and efficient ways of working with Cocoa frameworks. Swift automatically converts some Objective-C types to Swift types, and some Swift types to Objective-C types. Types that can be converted between Objective-C and Swift are referred to as bridged types. Anywhere you can use a bridged Objective-C reference type, you can use the Swift value type instead. This lets you take advantage of the functionality available on the reference type’s implementation in a way that is natural in Swift code. For this reason, you should almost never need to use a bridged reference type directly in your own code. In fact, when Swift code imports Objective-C APIs, the importer replaces Objective-C reference types with their corresponding value types. Likewise, when Objective-C code imports Swift APIs, the importer also replaces Swift value types with their corresponding Objective-C reference types.

<a name="valuetype-vs-referencetype"></a>

## ValueType vs. ReferenceType

> __Reference type__: a type that once initialized, when assigned to a variable or constant, or when passed to a function, returns a reference to the same existing instance.

A typical example of a reference type is an object. Once instantiated, when we either assign it or pass it as a value, we are actually assigning or passing around the reference to the original instance (i.e. its location in memory). Reference types assignment is said to have shallow copy semantics.

When to use:

- Subclasses of NSObject must be class types
- Comparing instance identity with === makes sense
- You want to create shared, mutable state

> __Value type__: a type that creates a new instance (copy) when assigned to a variable or constant, or when passed to a function.

A typical example of a value type is a primitive type. Common primitive types, that are also values types, are: `Int`, `Double`, `String`, `Array`, `Dictionary`, `Set`. Once instantiated, when we either assign it or pass it as a value, we are actually getting a copy of the original instance. The most common value types in Swift are structs, enums and tuples can be value types. Value types assignment is said to have deep copy semantics.

When to use:

- Comparing instance data with == makes sense (Equatable protocol)
- You want copies to have independent state
- The data will be used in code across multiple threads (avoid explicit synchronization)

<a name="copy-on-write"></a>

## What is copy on write mechanism

A fully stack allocated value type will not need reference counting, but a value type with inner references will unfortunately inherit this ability.

```swift
final class ExampleClass {
  let exampleString = "Ex value"
}
struct ExampleStruct {
  let ref1 = ExampleClass()
  let ref2 = ExampleClass()
  let ref3 = ExampleClass()
  let ref4 = ExampleClass()
}
```

This way of having inner reference types is an expensive operation that requires many calls to `malloc/free` and a significant reference counting overhead each time you copy. `COW` enables value types to be referenced when they are copied just like reference types. The real copy only happens when you have an already existing strong reference and you are trying to modify that copy.

```swift
let array = [1,2,3] //address A
var notACopy = array //still address A
notACopy += [4,5,6] //now address B
```

__Manually implementing Copy On Write__

Swift standard library has already implemented `COW` for Dictionary, Array etc. The easiest way to implement copy-on-write is to compose existing copy-on-write data structures, such as Array. Swift arrays are values, but the content of the array is not copied around every time the array is passed as an argument because it features copy-on-write traits.There are two obvious disadvantages of using Array for `COW` semantics. The first problem is that Array exposes methods like `append` and `count` that don’t make any sense in the context of a value wrapper. These methods can make the use of the reference wrapper awkward. It is possible to work around this problem by creating a wrapper struct that will hide the unused APIs and the optimizer will remove this overhead, but this wrapper will not solve the second problem. The Second problem is that Array has code for ensuring program safety and interaction with Objective-C. Swift checks if indexed accesses fall within the array bounds and when storing a value if the array storage needs to be extended. These runtime checks can slow things down. An alternative to using Array is to implement a dedicated copy-on-write data structure to replace Array as the value wrapper.

Let’s consider a struct Car in which we want to use Copy on Write:

```swift
struct Car {
  let model = "M3"
}
```

We can create a `Ref` class which will wrap our `Car` value type.

```swift
final class Ref<T> {
  var val : T
  init(_ v : T) {val = v}
}
struct Box<T> {
    var ref : Ref<T>
    init(_ x : T) { ref = Ref(x) }
    var value: T {
        get { return ref.val }
        set {
          if (!isKnownUniquelyReferenced(&ref)) {
            ref = Ref(newValue)
            return
          }
          ref.val = newValue
        }
    }
}
```

The `Box` struct has a reference to `Ref` class and will return the value of our `Car` struct . When you try to set the value, it checks if there are any existing strong references and creates a new `Ref` if needed thereby limiting the copies to be made only while writing to it. `isKnownUniquelyReferenced` returns a boolean indicating whether the given object is known to have a single strong reference.

<a name="rxswift"></a>

## RxSwift

The first thing you need to understand is that everything in RxSwift is an observable sequence or something that operates on or subscribes to events emitted by an observable sequence. Arrays, Strings or Dictionaries will be converted to observable sequences in RxSwift. You can create an observable sequence of any Object that conforms to the `Sequence` Protocol from the Swift Standard Library. Observable sequences can emit zero or more events over their lifetimes.
In RxSwift an `Event` is just an Enumeration Type with 3 possible states:

1. `.next(value: T)` — When a value or collection of values is added to an observable sequence it will send the next event to its subscribers as seen above. The associated value will contain the actual value from the sequence.
2. `.error(error: Error)` — If an Error is encountered, a sequence will emit an error event. This will also terminate the sequence.
3. `.completed` — If a sequence ends normally it sends a completed event to its subscribers
If you want to cancel a subscription you can do that by calling dispose on it. You can also add the subscription to a `DisposeBag` which will cancel the subscription for you automatically on `deinit` of the `DisposeBag` Instance.

__Subjects__

A `Subject` is a special form of an Observable Sequence, you can subscribe and dynamically add elements to it. There are currently 4 different kinds of Subjects in RxSwift

1. `PublishSubject`: If you subscribe to it you will get all the events that will happen after you subscribed.
2. `BehaviourSubject`: A behavior subject will give any subscriber the most recent element and everything that is emitted by that sequence after the subscription happened.
3. `ReplaySubject`: If you want to replay more than the most recent element to new subscribers on the initial subscription you need to use a `ReplaySubject`. With a `ReplaySubject`, you can define how many recent items you want to emit to new subscribers.
4. `Variable`: A `Variable` is just a `BehaviourSubject` wrapper that feels more natural to a none reactive programmers. It can be used like a normal `Variable`

__Schedulers__

Operators will work on the same thread as where the subscription is created. In RxSwift you use schedulers to force operators do their work on a specific queue. You can also force that the subscription should happen on a specifc Queue. You use `subscribeOn` and `observeOn` for those tasks. If you are familiar with the concept of operation-queues or dispatch-queues this should be nothing special for you. A scheduler can be serial or concurrent similar to `GCD` or `OperationQueue`. There are 5 Types of Schedulers in RxSwift:

1. `MainScheduler` — “Abstracts work that needs to be performed on MainThread. In case schedule methods are called from the main thread, it will perform the action immediately without scheduling.This scheduler is usually used to perform UI work.”
2. `CurrentThreadScheduler` — “Schedules units of work on the current thread. This is the default scheduler for operators that generate elements.”
3. `SerialDispatchQueueScheduler` — “Abstracts the work that needs to be performed on a specific dispatch_queue_t. It will make sure that even if a concurrent dispatch queue is passed, it's transformed into a serial one.Serial schedulers enable certain optimizations for observeOn.The main scheduler is an instance of SerialDispatchQueueScheduler"
4. `ConcurrentDispatchQueueScheduler` — “Abstracts the work that needs to be performed on a specific dispatch_queue_t. You can also pass a serial dispatch queue, it shouldn't cause any problems. This scheduler is suitable when some work needs to be performed in the background.”
5. `OperationQueueScheduler` — “Abstracts the work that needs to be performed on a specific NSOperationQueue. This scheduler is suitable for cases when there is some bigger chunk of work that needs to be performed in the background and you want to fine tune concurrent processing using maxConcurrentOperationCount.”

__Difference between `.drive()` and `.bind(to:)`__

Driver ensures that observe occurs only on main thread. Thumb rule is are you trying to drive a UI component use `drive` else use `bindTo`. Generally if you want your subscribe to occur only on main thread and don't want your subscription to error out (like driving UI components) use `driver` else stick with `bindTo` or `subscribe`

__What's the difference between `bind` and `subscribe`?__

By using `bind(onNext)` you can express that stream should never emit `error` and you interested only in item events. So you should use `subscribe(onNext:...)` when you interested in `error` / `complete` / `disposed` events and `bind(onNext...)` otherwise

<a name="swiftui"></a>

## SwiftUI

SwiftUI предполагает, что описание структуры вашего View целиком находится в коде. Причем, Apple предлагает нам декларативный стиль написания этого кода. То есть, примерно так:

`Это View. Она состоит из двух текстовых полей и одного рисунка. Текстовые поля расположены друг за другом горизонтально. Картинка находится под ними и ее края обрезаны в форме круга.`

```swift
struct ContentView: View {
    var text1 = "some text"
    var text2 = "some more text"
    var body: some View {
        VStack{
            Text(text1)
                .padding()
                .frame(width: 100, height: 50)
            Text(text2)
                .background(Color.gray)
                .border(Color.green)
        }
    }
}
```

Обратите внимание, `View` — это структура с некоторыми параметрами. Что бы структура стала `View` — нам нужно задать вычисляемый параметр `body`, который возвращает `some View`. Содержание замыкания`body: some View { … }` — это и есть описание того, что будет отражено на экране.
Три типа элементов, из которых строится тело View:

- Другие View, т.е. Каждая `View` содержит в себе одну или несколько других `View`. Те, в свою очередь могут так же содержать как предопределенные системные `View` вроде `Text()`, так и кастомные, сложные, написанные самим разработчиком.
- Модификаторы - благодаря им, мы коротко и внятно сообщаем SwiftUI, какой мы хотим видеть данную `View`
- Контейнеры - `HStack`, `VStack`, `ZStack`, `Group`, `Section` и прочие. Фактически, контейнеры — это те же `View`, но у них есть особенность. Вы передаете в них некий контент, который нужно отобразить. Вся фишка контейнера в том, что он должны как-то сгруппировать и отобразить элементы этого контента. В этом смысле, контейнеры похожи на модификаторы, с той лишь разницей, что модификаторы предназначены изменять одну уже готовую `View`, а контейнеры выстраивают эти View (элементы контента, или блоки декларативного синтаксиса) в определенном порядке, например вертикально или горизонтально.

__state параметры__

Прежде всего, это переменные состояния — хранимые параметры нашей структуры, изменение которых должно быть отражено на экране. Их оборачивают в специальные обертки:

`@State` — для примитивных типов

```swift
struct ContentView: View {
    @State var tapCount = 0
    var body: some View {
        VStack {
            Button(action: { tapCount += 1 },
                   label: { Text("Tap count \(tapCount)") })
        }
    }
}
```

`@ObservedObject` — для классов. Класс должен удовлетворять протоколу `ObservableObject` — это значит, что данный класс должен уметь оповещать подписчиков (`View`, которые используют данное значение с оберткой `@ObservedObject`) об изменении своих свойств. Для этого достаточно обернуть требуемые свойства в `@Published`.

`@Published` is one of the most useful property wrappers in SwiftUI, allowing us to create observable objects that automatically announce when changes occur. SwiftUI will automatically monitor for such changes, and re-invoke the body property of any views that rely on the data.

```swift
final class CounterViewModel: ObservableObject {
    @Published var count = 0

    func incrementCounter() {
        count += 1
    }
}

struct CounterView: View {
    @ObservedObject var viewModel = CounterViewModel()

    var body: some View {
        VStack {
            Text("Count is: \(viewModel.count)")
            Button("Increment Counter") {
                viewModel.incrementCounter()
            }
        }
    }
}
```

`@StateObject` — The same as `@ObservedObject` BUT property wrapper don’t get destroyed and re-instantiated at times their containing view struct redraws.

`@Binding` - это еще один Property Wrapper, с помощью которой мы объявляем параметры структуры, которые будут не просто меняться, а и возвращаться в родительскую `View`. When it changes in one place it also changes in the other.

`@EnvironmentObject` — это как `Binding`, только сразу для всех `View` в иерархии, без необходимости их передавать в явном виде.

`ForEach` — это набор subView, сгенерированных для каждого элемента коллекции исходя из переданного контента.

Роль navigation controller берет на себя специальный `NavigationView`. Достаточно обернуть ваш код в `NavigationView{...}`. А само действие перехода можно добавить в специальную кнопку `NavigationLink`, которая пушит условный экран `DetailView`.

```swift
var body: some View {
    NavigationView {
    Text("World Time").font(.system(size: 30))
        NavigationLink(destination: DetailView() {
            Text("Go Detail")
        }
    }
}
```

<a name="combine"></a>

## Combine

На WWDC 2019 был представлен фреймворк Combine от Apple. Он позволяет моделировать все виды асинхронных событий и операций типа “значения, изменяющиеся во времени”. Не смотря на то, что данное понятие, часто используется в мире реактивного программирования как концепция и способ организации логики, поначалу бывает сложно сразу во всем разобраться.

## Publishers

---
Every publisher can emit multiple events of these three types:

1. An output value of the publisher’s generic `Output` type.
2. A successful completion.
3. A completion with an error of the publisher’s `Failure` type.

Publishers do not emit any values if there are no subscribers to potentially receive the output

`Subject` — A publisher that exposes a method for outside callers to publish elements.

```swift
protocol Subject<Output, Failure> : AnyObject, Publisher
```

`PassthroughSubject` — A subject that broadcasts elements to downstream subscribers. They will happily pass along those values and a completion event. As with any publisher, you must declare the type of values and errors it can emit in advance; subscribers must match those types to its input and failure types in order to subscribe to that passthrough subject. *Unlike `CurrentValueSubject`, a `PassthroughSubject` doesn’t have an initial value or a buffer of the most recently-published element. A `PassthroughSubject` drops values if there are no subscribers, or its current demand is zero.*

`CurrentValueSubject` — A subject that wraps a single value and publishes a new element whenever the value changes.. *Unlike `PassthroughSubject`, `CurrentValueSubject` maintains a buffer of the most recently published element. Calling `send(_:)` on a `CurrentValueSubject` also updates the current value, making it equivalent to updating the value directly.*

__Analogy__

> `PassthroughSubject` = A doorbell push button. When someone rings the door, you are notified only if you are at home (you are the subscriber)
`PassthroughSubject` doesn't have a state, it emits whatever it receives to its subscribers.

> `CurrentValueSubject` = A light switch Someone turns on the lights in your home when you are outside. You get back home and you know someone has turned them on. `CurrentValueSubject` has an initial state, it retains the data you put in as its state.

__Difference__

`CurrentValueSubject` is a value, a publisher and a subscriber all in one. Sadly it doesn’t fire `objectWillChange.send()` when used inside an `ObservableObject`. You can specify an error type.

`@Published`is a property wrapper, thus:

- It is not yet supported in top-level code.
- It is not supported in a protocol declaration.
- It can only be used within a class.

`@Published` automatically fires `objectWillChange.send()` when used inside an `ObservableObject`. Xcode will emit a warning if your try to publish to `@Published` wrapped property from a background queue. Probably because `objectWillChange.send()` must be called from the main thread.
The error type of its publisher is `Never`. My biggest beef against `@Published` is that it can’t behave as a subscriber and setting up Combine pipelines requires additional plumbing compared to a `CurrentValueSubject`.

`ConnectablePublisher` — type which doesn’t produce any elements until we call its `connect()` method. We can convert any publisher or subscriber into a ConnectablePublisher by calling the method `makeConnectable()`

__Convenience Publishers__

`Future` — can be used to asynchronously produce a single result and then complete. A Future is a publisher that will eventually produce a single value and finish, or it will fail. It does this by invoking a closure when a value or error is available, and that closure is, in fact, the promise. `Promise` is a type alias to a closure that receives a `Result` containing either a single value published by the `Future`, or an error. A future is greedy, meaning executes as soon as it’s created. It does not require a subscriber like regular publishers that are lazy.

`Just` — creates a publisher that emits a single value to a subscriber and then complete

`Deferred` — A publisher that awaits subscription before running the supplied closure to create a publisher for the new subscriber.

`Empty` — A publisher that never publishes any values, and optionally finishes immediately.

`Fail` — A publisher that immediately terminates with the specified error.

`Record` — A publisher that allows for recording a series of inputs and a completion, for later playback to each subscriber.

## Subscribers

---
A `Subscriber` instance receives a stream of elements from a `Publisher`, along with life cycle events describing changes to their relationship. A given subscriber’s `Input` and `Failure` associated types must match the `Output` and `Failure` of its corresponding publisher.

`Sink` — The sink subscriber allows you to provide closures with your code that will receive output values and completions. From there, you can do anything your heart desires with the received events.

`Assign` — The assign subscriber allows you to, without the need of custom code, bind the resulting output to some property on your data model or on a UI control to display the data directly on-screen via a key path.

## Operators

---
Operators are methods declared on the `Publisher` protocol that return either the same or a new publisher. That’s very useful because you can call a bunch of operators one after the other, effectively chaining them together. As an added bonus, operators always have input and output, commonly referred to as `upstream` and `downstream` — this allows them to avoid shared state.

`Scheduler` — A protocol that defines when and how to execute a closure.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/subscription.png">

__Subscription lifecycle__

By meeting these protocols, now we are secure to understand how the relation between publisher and subscriber is established:

1. A new subscriber requires a subscription from the publisher by calling `receive` method on the publisher by passing the subscriber as a parameter
2. The publisher creates a custom subscription, an object that is responsible for keeping the subscriber up to date with the publisher and sends it to the subscriber through the `receive(Subscription)` method.
3. Within the `receive(Subscription)` method, the subscriber calls the request method on the `Subscription` object that was just received establishing the true demand it requires from the publisher.
4. When receiving the request method, the `Subscription` object has the `Demand` the subscriber requires and knows how many values it must receive from the publisher
5. As the Subscription has some mechanism for keeping track of publisher's emitted values, it just needs to send them to the subscriber via the `receive(Input)` method.
6. When some event requires the subscription to complete, the `Subscription` calls the `receive(Completion)` method on the Subscriber and the process finishes.

__Examples__

`Publishers` могут быть бесконечно активны либо завершены по итогу какого-либо события, а также `Publishers` могут быть опционально не выполнены, если произошла какая-то ошибка. Чтобы внедрить `Combine`, Apple доработали некоторые из своих основных библиотек, чтобы они так же могли поддерживаться `Combine`. Например, вот так может использоваться тип `URLSession` для создания `Publisher`, выполняющего сетевой запрос по заданному URL-адресу:

```swift
let url = URL(string: "https://api.github.com/repos/johnsundell/publish")!
let publisher = URLSession.shared.dataTaskPublisher(for: url)
```

После того, как мы создали `Publisher`, мы можем привязать к нему подписки, например, с помощью `sink` API, который позволяет передавать замыкание, срабатывающее каждый раз, когда было получено новое значение, а так же другое замыкание, которое отрабатывает когда `publisher` завершает свою работу:

```swift
let cancellable = publisher.sink(
    receiveCompletion: { completion in
        switch completion {
        case .failure(let error):
            print(error)
        case .finished:
            print("Success")
        }
    },
    receiveValue: { value in
        print(value)
    }
)
```

Обратите внимание на то, как описанный выше метод `sink` возвращает значение, которое мы храним как `cancellable`. При присоединении нового подписчика, `Publisher` всегда возвращает объект, соответствующий протоколу `Cancellable`, действующему как токен для новой подписки. Затем, нам нужно сохранить этот токен до тех пор, пока мы хотим оставить нашу подписку активной, иначе как только она будет освобождена (deallocated), наша подписка будет автоматически отменена (кстати, подписку можно отменить вручную при помощи вызова метода `cancel()` у токена). Операторы используются для построения реактивных цепочек или пайплайнов (конвейеров), по которым могут проходить наши данные, где каждый оператор применяет некоторую форму преобразования к данным, которые были ему отправлены.
`cancellable` используется для отслеживания подписки (subscription) на `Publisher` и должен сохраняться до тех пор, пока мы хотим, чтобы эта подписка (`subscription`) оставалась активной.

Пример с операторами:

```swift
let sub = NotificationCenter.default
    .publisher(for: NSControl.textDidChangeNotification, object: filterField)
    .map( { ($0.object as! NSTextField).stringValue } )
    .filter( { $0.unicodeScalars.allSatisfy({CharacterSet.alphanumerics.contains($0)}) } )
    .debounce(for: .milliseconds(500), scheduler: RunLoop.main)
    .receive(on: RunLoop.main)
    .assign(to:\MyViewModel.filterString, on: myViewModel)
```

<a name="method-dispatching"></a>

## Metod Dispatching

 Method Dispatch is how a program selects which instructions to execute when invoking a method. It’s something that happens every time a method is called, and not something that you tend to think a lot about.

1. Static or direct dispatch
2. Table or dynamic dispatch
3. Message dispatch

__Static or Direct Dispatch__

`Direct dispatch` is the fastest style of method dispatch. Not only does it result in the fewest number of assembly instructions, but the compiler can perform all sorts of smart tricks, like inlining code, and many more things. However, direct dispatch is also the most restrictive from a programming point of view, and it is not dynamic enough to support subclassing.

- Structs (Value type Data type)
- `static` and `final` (Reference type with this keyword

__Table or Dynamic Dispatch__

`Table dispatch` is the most common implementation of dynamic behaviour in compiled languages. The compiler does not know which executable code should be used for a particular method call. This decision is taken at runtime.

_Virtual table_

Classes have tables, called `Virtual Tables`. Each table has an array of function pointers to methods of the corresponding class. Every subclass has its own copy of `Virtual Table` with different function pointers to those methods, which are overridden. As a subclass adds a new method to its definition, the method is appended to the end of the corresponding table. The compiler builds the tables, and at runtime, the tables are used to determine which method should be called

```swift
class ParentClass {
    func method1() { }
    func method2() { }
}

class ChildClass: ParentClass {
    override func method2() { }
    func method3() { }
}
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/v-table.png">

```swift
let obj = ChildClass()
obj.method2()
```

Each class instance has a property type (or `isa` in Objective-C, each NSObject has this property). The tables are stored in some static memory region and can be taken by this property. When `method2` is called, the process will:

1. take `Virtual Table` for the object of 0xB00 (ChildClass) by its property type
2. take the function pointer of `method2` from the table (the pointer is taken by index 1). Thus, the function pointer is `0x222`
3. jump to the address `0x222`, that contains the executable code

Each method in such tables isn’t aware of self (obj). At runtime self (obj) is passed as a parameter when calling the method

```swift
// ... kind of runtime
method2(obj)
```

`Table Dispatch` is still good but less efficient than the previous one because it takes three additional steps (take the table, take the function address, jump to that address to get executable code). And also, it is less efficient because the compiler applies no optimizations

_Protocol Witness Tables_

`Virtual Tables` are used when using classes and inheritance, and `Protocol Witness Tables` — when conforming to protocols. The problem is that structures don’t support inheritance because they don’t have `Virtual Tables`. But conforming to protocols allows them to use `Table Dispatch` and polymorphism. However, instead of `Virtual Tables`, they get Protocol `Witness Tables`

```swift
// Polymorphism without classes and inheritance
protocol Noisable {
    func makeNoise()
}

struct Cat: Noisable {
    func makeNoise() { print("meow") }


struct Fox: Noisable {
    func makeNoise() { print(".. what does the fox say?") }
}

let noisers: [Noisable] = [Cat(), Cat(), Fox(), Fox(), Cat()]
for noiser in noisers { noiser.makeNoise() } // polymorphism
```

Each type (value and reference) that conforms to a protocol has its own `Protocol Witness Table`. The table has pointers to those methods of the type that are required by the protocol. Structures and classes that conform to a protocol can have different sizes. To store them in the same array (like noisers) or in the same type property, or to pass them as an argument to the same function, and also to find corresponding `Protocol Witness Table` for each of them, Swift uses `existential containers` - is a structure, that always has a fixed size (in x64, it is 5 * 64 = 320 bit or five machine words), and consists of three parts:

1. reference to `Value Witness Table` (VWT),
2. a reference to `Protocol Witness Table` (PWT)
3. a value buffer to store an instance itself

The buffer stores an initial instance. It takes three machine words. If the instance doesn’t fit the buffer size (takes more than three machine words or more than 3 * 64 bit), it gets placed on the heap via VWT (see below), and the buffer contains a reference to that instance. But if it does, the buffer stores the value directly (the value is placed on the stack). However, it is only about value types. For reference types, the buffer stores a reference anyway. `Value Witness Table` is an abstract representation of instance life cycle manipulations. Since different types (value and reference) have different mechanisms of copying, moving, and destroying their values, VWT is used to abstract from the implementation of the current instance and do those manipulations through a single interface. It has the following properties and methods: `size` (initial instance size), `copy`, `move`, `destroy`

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/vwt.png">

__Message Dispatch__

Message Dispatch is the most dynamic style of the method dispatch. It’s a cornerstone of Cocoa development. It’s used by KVO, CoreData, UIAppearance…

The compiler, in this case, also does not know which executable code should be used for a particular method call

A key point of Message Dispatch is modifying the dispatch behavior at runtime, applying method swizzling (exchanging method invocations at runtime) or isa-swizzling (exchanging an object type at runtime)

Method Swizzling allows exchanging the implementation of two class methods at runtime. This will affect every instance of a modified class, which was or will be created. If you have methodA and methodB, method swizzling allows you to call the implementation of methodB when calling methodA, and vice versa. It could be helpful for setting some default behavior to a class, avoiding inheritance. But Swift can use protocols for these purposes (Objective-C cannot)

Isa-Swizzling allows exchanging the type of a given single object with another type at runtime. If you have two classes: ClassA and ClassB, you can create an instance of ClassA, then at runtime change its type to ClassB (change property isa), then call some method of ClassB, and then switch the type back to ClassA

```swift
class ParentClass {
    dynamic func method1() { }
    dynamic func method2() { }
}

class ChildClass: ParentClass {
    override func method2() { }
    dynamic func method3() { }
}
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/method-dispatch.png">

Swift builds this hierarchy as a tree structure and puts it into some static memory region. When a message is dispatched (method2 is called), the process will:

- take the hierarchy tree
- try to find the function pointer of method2 in ChildClass table
- if the function pointer is found, jump to the address to get executable code
- else go to ParentClass (super of ChildClass) and repeat 2–4
- do this until the function pointer is found or the root class of the hierarchy is reached

For the first method call, it’s slower than Table Dispatch because it goes through the tree to find the corresponding function pointer. But after that, Swift caches the found table, and the second method call will take Table Dispatch time

Swift uses the Swift runtime whenever it’s possible. It allows making optimizations when preparing code for runtime. Thus, at runtime, the code is more efficient. Swift only opts for a dynamic dispatch and Objective-C runtime if it has no other choice

Objective-C uses Message Dispatch in most cases, but developers sometimes can use Direct Dispatch there

Where a method is declared determines what the method dispatch is used

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/methods-dispatch.png">

Inheritance from NSObject makes a class “dynamic message dispatchable”, but methods in initial declarations are called via Table Dispatch

Object type determines which type of dispatch will be used on a method call. If the type is a protocol, then look at the protocol row in the table. If it casts the object to its class type or structure type, then look at the class or value type rows in the table

```swift
class A {
    func doAction() { }                      // table dispatch
}
class B: A {
    final override func doAction() { }       // static dispatch
}
let a: A = A()
a.doAction()     // will be called via table dispatch
let b1: A = B()
b1.doAction()    // will be called via table dispatch
let b2: B = B()
b2.doAction()    // will be called via static dispatch
```

__final__

The final keyword enables Static Dispatch on a method defined in a class. This keyword removes the possibility of any dynamic behavior and also hides the method from Objective-C runtime. It doesn’t generate a selector. Applying final to a class denies inheritance from the class and also makes class methods to be called via `Static Dispatch`. Using this keyword allows the compiler to make some optimizations for increasing performance. It can be applied to classes only

```swift
// denies any inheritance from the class
final class Animal {
    // makes the method called via static dispatch
    final func move() { }
}
```

__dynamic__

The dynamic keyword enables Message Dispatch on a method defined in a class. This keyword implicitly marks the method as `@objc`, which means the method is visible for Objective-C runtime. Swift doesn’t say that dynamic is available for classes only, but structures and enumerations don’t support inheritance. The runtime doesn’t have to figure out which implementation it needs to use. Thus, at runtime for structures and enums dynamic doesn’t work. Using this keyword can make your code less performant

```swift
class Animal {
    // message dispatch at Objective-C runtime
    dynamic func move() { }
}
```

__@objc__

The `@objc` keyword does not alter the method dispatch. It just makes the method visible for Objective-C runtime. The most common use of @objc is making selectors. And also, using `@objc` allows overriding methods declared in class extensions (by default, it is impossible because of Static Dispatch)

```swift
class Animal {
    @objc func move() { } // is visible at Objective-C runtime
}
class Animal { }
extension Animal {
    @objc func move() { }
}
class Lion: Animal {
    override func move() { }
}
```

__@nonobjc__

The @nonobjc keyword does alter the method dispatch. It can be used to disable `Message Dispatc`h and to make the method invisible for Objective-C runtime. It seems there is no difference between `@nonobjc` and `final`, so using final makes code more clear

__@objc final__

Keyword `@objc final` enables Direct Dispatch on a method and registers the method selector at Objective-C runtime. The keyword allows the method to respond when performing a selector or other Objective-C features, along with giving the performance of `Direct Dispatch`

```swift
class Animal {
    // direct dispatch, visible for Objective-C runtime
    @objc final func move() { }
}
```

If a property is observed with KVO and that property is upgraded to Direct Dispatch, the code will still compile, but the dynamically generated KVO method won’t be triggered

<a name="#generic-vs-protocol"></a>

## Чем отличается Generic от Protocol?

`Generic` is an `incomplete Type`. Generic code enables you to write flexible, reusable functions and types that can work with any type, subject to requirements that you define. You can write code that avoids duplication and expresses its intent in a clear, abstracted manner.

The problem is that the same can be applied almost exactly to a `Protocol` :-( Where’s the misunderstanding? Let’s expand the official Stack example by adding a simple check to see if the last element added is “cuatro”.

```swift
struct Stack<Element> {
 var items = [Element]()
 mutating func push(_ item: Element) {
  items.append(item)
 }

 mutating func pop() -> Element {
  return items.removeLast()
 }
}

var stackOfStrings = Stack<String> ()
stackOfStrings.push("uno")
stackOfStrings.push("dos")
stackOfStrings.push("tres")
stackOfStrings.push("cuatro")

let lastElement = stackOfStrings.pop()
if lastElement == "cuatro" {
 print("That's a bingo!")
}
```

This code will compile and actually print “That’s a bingo!”.

Let’s try the same thing with our Protocol example.

```swift
struct Stack {
 var items = [StackElement]()
 mutating func push(_ item: StackElement) {
  items.append(item)
 }

 mutating func pop() -> StackElement {
  return items.removeLast()
 }
}

protocol StackElement {}

extension String : StackElement { }

var stackOfStrings = Stack()
stackOfStrings.push("uno")
stackOfStrings.push("dos")
stackOfStrings.push("tres")
stackOfStrings.push("cuatro")

let lastElement = stackOfStrings.pop()
if lastElement == "cuatro" {
 print("That's a bingo!")
}

❌ Value of protocol type 'StackElement' cannot conform to 'StringProtocol'; only struct/enum/class types can conform to protocols
```

This code doesn’t even compile!

In the Protocol stack, what type is our pop function returning?

```swift
mutating func pop() -> StackElement {
 return items.removeLast()
}
```

If you answered StackElement, you’re wrong. The correct answer is, again, “I don’t know“.

Protocols hide away the underlying type. If a `Generic` is an `incomplete Type`, then a `Protocol` is a `masked Type`. When we have a function that returns a `Protocol`, the compiler cannot tell you what concrete type is actually implementing the `Protocol`! Of course you could check what type it is by doing something like if lastElement `is String` but then you’re trying to fit a round peg in a square hole.

Once a Generic becomes complete (e.g. `Array<String>`) it is a fully concrete type. It can be compared to other types. Constants or variables declared as `Protocols` can never be compared to concrete types. That’s the difference between a `Generic` and a `Protocol`. `Protocols` are meant to mask types at the cost of losing concreteness and `Generics` are meant to become complete types by finding their other half.

<a name="#animations"></a>

## Какие бывают анимации?

- UIKit
- Core Animation
- UIViewPropertyAnimator

When to use and what to use?

At the end of the day, all UIKit-style animations are converted to Core Animation-style animations. That is, everything is actually animated using Core Animation. While UIKit and Core Animation both provide animation support, they give access to different parts of the view hierarchy.

- UIKit: animations are performed using UIView objects. View supports a basic set of animations that cover many common tasks such as view transitions. It can accept events from the user like touch, click and tap and it works in the main thread.

- Core Animation: Use Core animations when animating of the underlying layer’s properties. It renders, composes, and animate visual elements which provides high frame rates and smooth animations without burdening the CPU and slowing down the app.

- UIViewPropertyAnimator: allows complex and dynamic animation of UIView properties.

With UIKit, animations are performed using UIView objects. The properties available for animation using UIKit are:

- frame
- bounds
- center
- transform
- alpha
- backgroundColor
- contentStretch

While Core Animation gives access to the view's underlying layer, exposing a different set of properties as outlined below (it's worth noting that because views and layers are intricately linked together, changes to a view's layer affect the view itself):

- The size and position of the layer
- The center point used when performing transformations
- Transformations to the layer or its sublayers in 3D space
- The addition or removal of a layer from the layer hierarchy
- The layer’s Z-order relative to other sibling layers
- The layer’s shadow
- The layer’s border (including whether the layer’s corners are rounded)
- The portion of the layer that stretches during resizing operations
- The layer’s opacity
- The clipping behavior for sublayers that lie outside the layer’s bounds
- The current contents of the layer
- The rasterization behavior of the layer

__UIView's animation methods__

These are still the easiest to use in my opinion. Very straight forward API without making too big of a code footprint. I use this either for simple fire-and-forget animations (such as making a button pop when selected), or when I want to make a complex keyframe animation since its keyframe support is great.

```swift
UIView.animate(withDuration: 0.5, delay: 0.0, options: .curveEaseOut, animations: {
    button.transform = .init(scaleX: 1.1, y: 1.1)
}
```

__Core Animation__

Perhaps a bit less straight-forward to use, but you need it whenever you want to animate layer properties instead of view properties, as mentioned above. Examples of these are corner radius, shadow, and border.

```swift
CATransaction.begin()
CATransaction.setAnimationDuration(0.5)
CATransaction.timingFunction = .init(name: .easeOut)
let cornerAnimation = CABasicAnimation(keyPath: #keyPath(CALayer.cornerRadius))
cornerAnimation.fromValue = 0.0
cornerAnimation.toValue = 10.0
button.layer.add(cornerAnimation, forKey: #keyPath(CALayer.cornerRadius))
CATransaction.commit()
```

__UIViewPropertyAnimator__

Added in iOS 10, as the name suggests this is another view-based animation API. There are a few things that make it different from UIView's animation methods, the main ones being that it supports interactive animations and allows modifying animations dynamically. You can pause, rewind, or scrub an animation, as well as adding more animation blocks on the go or reversing the animation while it's playing, which makes it quite powerful. I use this when I want an animation to be controlled by the user. The scrubbing works by setting a fractionComplete property on the animator object, which can easily be hooked up to a pan gesture recognizer or a force touch recognizer (or even a key using KVO).

As mentioned, you can also store a reference to a UIViewPropertyAnimator and change its animations or completion blocks during the animation.

```swift
// Create an animation object with an initual color change animation
let animator = UIViewPropertyAnimator(duration: duration, curve: .linear) {
    button.backgroundColor = .blue
}

// At any point during the runtime, we can amend the list of animations like so
animator.addAnimations {
    button.transform = .init(scaleX: 1.1, y: 1.1)
}

animator.startAnimation()
```

Worth noting is that you can actually use UIView.animate and UIView.animateKeyframes from within your UIViewPropertyAnimator animations blocks, should you feel the need to use both.

<a name="type-erasure"></a>

## Что такое type erasure?

Type-erasure simply means "erasing" a specific type to a more abstract type in order to do something with the abstract type (like having an array of that abstract type). And this happens in Swift all the time, pretty much whenever you see the word `Any`. The most straightforward way to think of type erasure is to consider it a way to hide an object's "real" type. В стандартной библиотеке Swift много примеров такого подхода: `AnyHashable`, `AnyIterator`, `AnySequence`, `AnyCollection` и т.д.

<a name="map-functions"></a>

## Разница между map, compactMap и flatMap?

The word all three methods share is “map”, which in this context means “transform from one thing to another.”

`compactMap()`: transform then unwrap

`flatMap()`: transform then flatten

<a name="opaque-type"></a>

## Что такое opaque type?

Opaque return types is a new language feature that is introduced in Swift 5.1 by Apple. It can be used to return some value for function/method, and property without revealing the concrete type of the value to client that calls the API. The return type will be some type that implement a protocol. Using this solution, the module API doesn’t have to publicly leak the underlying internal return type of the method, it just need to return the opaque type of the protocol using the some keyword. The Swift compiler also will be able to preserve the underlying identity of the return type unlike using protocol as the return type. SwiftUI uses opaque return types inside its View protocol that returns some View in the body property.

Here are some of the essential things that opaque return types provides to keep in our toolbox and leverage whenever we want to create API using Swift:

- Provide a specific type of a protocol without exposing the concrete type to the API caller for better encapsulation.
- Because the API doesn’t expose the private concrete return type to it’s caller, the client doesn’t have to worry if in the future the underlying types gets changed as long as it implements the base protocol.
- Provides strong guarantees of underlying identity by returning a specific type in runtime. The trade off is losing flexibility of returning multiple type of value offered by using protocol as return type.
- Because of the strong guarantee of returning a specific protocol type. The function can return opaque protocol type that has Self or associated type requirement.
- While the protocol leaves the decision to return the type to its caller of the function. In reverse for opaque return types, the function itself have the decision for the specific type of the return value as long as it implements the protocol.

```swift
protocol MobileOS {
    associatedtype Version
    var version: Version { get }
    init(version: Version)
}

struct iOS: MobileOS {
    var version: Float
}

struct Android: MobileOS {
    var version: String
}

func buildPreferredOS() -> MobileOS {
    return iOS(version: 13.1)
} // Compiler ERROR 😭
Protocol 'MobileOS' can only be used as a generic constraint because it has Self or associated type requirements
```

Solution:

```swift
func buildPreferredOS() -> some MobileOS {
    return iOS(version: 13.1)
}
```

Using the opaque return type, we finally can return MobileOS as the return type of the function. The compiler maintains the identity of the underlying specific return type here and the caller doesn’t have to know the internal type of the return type as long as it implements the MobileOS protocol

<a name="sendable"></a>

## Что такое Sendable?

Протокол `Sendable` и оболочка `@Sendable` добавляет поддержку «отправляемых» данных, то есть данных, которые можно безопасно передавать в другой поток. Это достигается с помощью нового протокола `Sendable` и атрибута `@Sendable` для функций.
К таким данным относятся:

- Все базовые типы данных, такие как `Bool`, `Int`, `String` и т.д.
- Опциональные типы данных, если они являются типами значений.
- Любые типы коллекций, в качестве элементов которых выступают типы значений (`Array<String>`, `Dictionary<Int, String>`).
- Кортежи, в которых все элементы являются типами значений.
- Метатипы, такие как `String.self.`

Все перечисленные выше типы данных теперь подписаны под протокол `Sendable` и их можно безопасно передавать между разными потоками. Что же касается пользовательских типов данных, то тут все ависит от того, чем конкретно они являются:

- Протоколу `Sendable`, автоматически соответствуют все акторы.
- Пользовательские структуры и перечисления, также автоматически соответствуют `Sendable` протоколу, если только они не содержат внутри себя ссылочные типы данных.
- В том случае если пользовательские классы не наследуются от других классов или наследуютсяя только от `NSObject` и при этом помечены ключевым словом `final`, а также имеют в качестве свойств только типы значений, то в этом случае они тоже могут соответствовать `Sendable` протоколу.
  
Атрибут `@Sendable` в функциях или замыканиях, позволяет выполнять код параллельно но с определенными ограничениями, для того, что бы разработчики не стреляли сами себе в ноги:

```swift
func printScore() async { 
    let score = 1
    Task { print(score) }
    Task { print(score) }
}
```

В данном примере действие, которое мы передаем в инициализатор `Task`, по умолчанию помечено как `@Sendable`. Данный атрибут позволяет выполнять задачи параллельно в разных потоках. А это возможно благодаря тому, что, что свойство score, в теле блока замыкания `Task`, является константой. Если бы свойство score было переменной, то доступ к ней могла бы получить одна из задач, в то время как другая может менять значение этой переменной.

Атрибутом `@Sandable` можно помечать и свои собственный функции и замыкания:

```swift
func runLater(_ completionHandler: @escaping @Sendable () -> Void) -> Void {
    DispatchQueue.global().asyncAfter(deadline: .now() + 3, execute: completionHandler)
}
```
