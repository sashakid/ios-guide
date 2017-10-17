
- [Swift](#swift)
	- [Сlosures and functions](#closures-and-functions)
	- [How Do I Declare a Closure in Swift?](#how-do-i-declare-a-closure-in-swift)
	- [Что такое протокол-ориентированное программирование? Как оно связано со Swift? Чем протоколы Swift отличаются от протоколов Objective-C?](#protocols)
	- [Difference between Array VS NSArray VS |AnyObject|](#array-nsarray-anyobject)
	- [Objective-C id is Swift Any or AnyObject](#id-any-anyobject)
	- [ValueType vs. ReferenceType](#valuetype-vs-referencetype)

<a name="swift"></a>
# Swift
* Multi-paradigm: protocol-oriented, object-oriented, functional, imperative, block structured
* Designed by	Chris Lattner and Apple Inc.
* First appeared:	June 2, 2014
* Stable release:	3.1.1 / April 21, 2017
* Typing discipline:	Static, strong, inferred
* OS: Darwin, Linux, FreeBSD
* Influenced by C#, CLU, D, Haskell, Objective-C, Python, Ruby, Rust

Swift is a multi-paradigm, compiled programming language created by Apple Inc. for iOS, OS X, watchOS and tvOS development. Swift is designed to work with Apple's Cocoa and Cocoa Touch frameworks and the large body of existing Objective-C code written for Apple products. Swift is in-tended to be more resilient to erroneous code ("safer") than Objective-C and also more concise. It is built with the LLVM compiler framework included in Xcode 6 and later and uses the Objective-C runtime, allowing C, Objective-C, C++ and Swift code to run within a single program.
Swift supports the core concepts that made Objective-C flexible, notably dynamic dispatch, wide-spread late binding, extensible programming, and similar features. These features also have well known performance and safety trade-offs, which Swift was designed to address. For safety, Swift introduced a system that helps address common programming errors like null pointers, as well as introducing syntactic sugar to avoid the pyramid of doom that can result. For performance issues, Apple has invested considerable effort in aggressive optimization that can flatten out method calls and accessors to eliminate this overhead. More fundamentally, Swift has added the concept of protocol extensibility, an extensibility system that can be applied to types, structs and classes, Apple promotes this as a real change in programming paradigms they refer to as "protocol-oriented programming".
Swift was introduced at Apple's 2014 Worldwide Developers Conference (WWDC). It underwent an upgrade to version 1.2 during 2014, and a more major upgrade to Swift 2 at WWDC 2015. Initially a proprietary language, it was announced that Swift 2 would become open source later that year, sup-porting iOS, OS X and Linux.

__History__

Development on Swift began in 2010 by Chris Lattner, with the eventual collaboration of many other programmers at Apple. Swift took language ideas "from Objective-C, Rust, Haskell, Ruby, Python, C#, CLU, and far too many others to list". On June 2, 2014, the Worldwide Developers Conference (WWDC) application became the first publicly released app written in Swift. A beta version of the programming language was released to registered Apple developers at the conference, but the company did not promise that the final version of Swift would be source-compatible with the test version. Apple planned to make source code converters available if needed for the full release.
The Swift Programming Language, a free 500-page manual, was also released at WWDC, and is available on the iBooks Store.

__Features__

Swift is an alternative for the Objective-C language that employs contemporary programming language theory concepts and strives to present a simpler syntax. During its introduction, it was described simply as "Objective-C without the C".
By default, Swift does not expose pointers and other unsafe accessors, contrary to Objective-C, which uses pointers pervasively to refer to object instances. Additionally, Objective-C's use of a Smalltalk-like syntax for making method calls has been replaced with a dot-notation style and namespace system more familiar to programmers from other common object-oriented (OO) languages like Java or C#. Swift introduces true named parameters and retains key Objective-C concepts, including protocols, closures and categories, often replacing former syntax with cleaner versions and allowing these concepts to be applied to other language structures, like enums.

_Generics_

Generic code enables you to write flexible, reusable functions and types that can work with any type, subject to requirements that you define. You can write code that avoids duplication and expresses its intent in a clear, abstracted manner.
Generics are one of the most powerful features of Swift, and much of the Swift standard library is built with generic code. In fact, you’ve been using generics throughout the Language Guide, even if you didn’t realize it. For example, Swift’s Array and Dictionary types are both generic collections. You can create an array that holds Int values, or an array that holds String values, or indeed an array for any other type that can be created in Swift. Similarly, you can create a dictionary to store values of any specified type, and there are no limitations on what that type can be.
```swift
func swapTwoValues<T>(inout a: T, inout _ b: T) {
	let temporaryA = a
	a = b
	b = temporaryA
}
```

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

<a name="protocols"></a>
## Что такое протокол-ориентированное программирование? Как оно связано со Swift? Чем протоколы Swift отличаются от протоколов Objective-C?

Protocol-Oriented Programming is a new programming paradigm ushered in by Swift 2.0. In the Protocol-Oriented approach, we start designing our system by defining protocols. We rely on new concepts: protocol extensions, protocol inheritance, and protocol compositions. The paradigm also changes how we view semantics. In Swift, value types are preferred over classes. However, object-oriented concepts don’t work well with structs and enums: a struct cannot inherit from another struct, neither can an enum inherit from another enum. So inheritancefa - one of the fundamental object-oriented concepts - cannot be applied to value types. On the other hand, value types can inherit from protocols, even multiple protocols. Thus, with POP, value types have become first class citizens in Swift.

__Protocol Extensions__

You can extend a protocol and provide default implementation for methods, computed properties, subscripts and convenience initializers.

__Protocol Inheritance__

A protocol can inherit from other protocols and then add further requirements on top of the requirements it inherits.

__Protocol Composition__

Swift types can adopt multiple protocols.

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

Mutable: The reference can be changed (mutable): you can mutate the instance itself and also change the instance reference.

Immutable: The reference remains constant (immutable): you can’t change the instance reference, but you can mutate the instance itself.

When to use:

* Subclasses of NSObject must be class types
* Comparing instance identity with === makes sense
* You want to create shared, mutable state

> __Value type__: a type that creates a new instance (copy) when assigned to a variable or constant, or when passed to a function.

A typical example of a value type is a primitive type. Common primitive types, that are also values types, are: `Int`, `Double`, `String`, `Array`, `Dictionary`, `Set`. Once instantiated, when we either assign it or pass it as a value, we are actually getting a copy of the original instance. The most common value types in Swift are structs, enums and tuples can be value types. Value types assignment is said to have deep copy semantics.

Mutable: The instance can be changed (mutable): you can change the properties of the instance.

Immutable: The instance remains constant (immutable): you can’t change the properties of the instance, regardless whether a property is declared with let or var.

When to use:

* Comparing instance data with == makes sense (Equatable protocol)
* You want copies to have independent state
* The data will be used in code across multiple threads (avoid explicit synchronization)
