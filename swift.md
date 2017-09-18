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
