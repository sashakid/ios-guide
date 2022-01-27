- [Тестирование](#тестирование)
  - [Виды тестов](#виды-тестов)
    - [Unit Tests](#unit-tests)
    - [Integration Tests](#integration-tests)
    - [Functional Tests](#functional-tests)
    - [Acceptance Tests](#acceptance-tests)
  - [Как тестировать асинхронные методы?](#async-testing)
  - [Dependency injection](#dependency-injection)

<a name="тестирование"></a>
# Тестирование
<a name="виды-тестов"></a>
## Виды тестов
<a name="unit-tests"></a>
### Unit Tests
Tests the smallest unit of functionality, typically a method/function (e.g. given a class with a particular state, calling x method on the class should cause y to happen). Unit tests should be focussed on one particular feature (e.g., calling the pop method when the stack is empty should throw an InvalidOperationException). Everything it touches should be done in memory; this means that the test code and the code under test shouldn't:

1.	Call out into (non-trivial) collaborators
2.	Access the network
3.	Hit a database
4.	Use the file system
5.	Spin up a thread

Any kind of dependency that is slow / hard to understand / initialise / manipulate should be stubbed / mocked / whatevered using the appropriate techniques so you can focus on what the unit of code is doing, not what its dependencies do.
In short, unit tests are as simple as possible, easy to debug, reliable (due to reduced external factors), fast to execute and help to prove that the smallest building blocks of your program function as intended before they're put together. The caveat is that, although you can prove they work perfectly in isolation, the units of code may blow up when combined which brings us to ...

<a name="integration-tests"></a>
### Integration Tests
Integration tests build on unit tests by combining the units of code and testing that the resulting combination functions correctly. This can be either the innards of one system, or combining multiple systems together to do something useful. Also, another thing that differentiates integration tests from unit tests is the environment. Integration tests can and will use threads, access the database or do whatever is required to ensure that all of the code and the different environment changes will work correctly.
If you've built some serialization code and unit tested its innards without touching the disk, how do you know that it'll work when you are loading and saving to disk? Maybe you forgot to flush and dispose filestreams. Maybe your file permissions are incorrect and you've tested the innards using in memory streams. The only way to find out for sure is to test it 'for real' using an environment that is closest to production.
The main advantage is that they will find bugs that unit tests can't such as wiring bugs (e.g. an instance of class A unexpectedly receives a null instance of B) and environment bugs (it runs fine on my single-CPU machine, but my colleague's 4 core machine can't pass the tests). The main disadvantage is that integration tests touch more code, are less reliable, failures are harder to diagnose and the tests are harder to maintain.
Also, integration tests don't necessarily prove that a complete feature works. The user may not care about the internal details of my programs, but I do!

<a name="functional-tests"></a>
### Functional Tests
Functional tests check a particular feature for correctness by comparing the results for a given input against the specification. Functional tests don't concern themselves with intermediate results or side-effects, just the result (they don't care that after doing x, object y has state z). They are written to test part of the specification such as, "calling function `Square(x)` with the argument of `2` returns `4`".

<a name="acceptance-tests"></a>
### Acceptance Tests
Acceptance testing seems to be split into two types:
Standard acceptance testing involves performing tests on the full system (e.g. using your web page via a web browser) to see whether the application's functionality satisfies the specification. E.g. "clicking a zoom icon should enlarge the document view by 25%." There is no real continuum of results, just a pass or fail outcome.
The advantage is that the tests are described in plain English and ensures the software, as a whole, is feature complete. The disadvantage is that you've moved another level up the testing pyramid. Acceptance tests touch mountains of code, so tracking down a failure can be tricky.
Also, in agile software development, user acceptance testing involves creating tests to mirror the user stories created by/for the software's customer during development. If the tests pass, it means the software should meet the customer's requirements and the stories can be considered complete. An acceptance test suite is basically an executable specification written in a domain specific language that describes the tests in the language used by the users of the system.

<a name="async-testing"></a>
## Как тестировать асинхронные методы?

We create `XCTestExpectation` instance that work like timer. Your test will never finish till one of both cases happend:
* `XCTestExpectation.fulfill()` called
* you got timeout defined with `waitForExpectationsWithTimeout` and therefore test will fail

- Step 1

Create new protocol for class under test:
```swift
protocol MyCallback {
  func onDone(results: String)
}
```
This is our callback.

- Step 2

In Unitest inherit this protocol:
```swift
class Test_MyClass : XCTestCase, MyCallback {
  /* ... */    
}
```

- Step 3

Create `XCTestExpectation` variable:
```swift
var theExpectation: XCTestExpectation?
```
and initiate onDone() method:
```swift
func onDone(results: String) {
  theExpectation?.fulfill() // it will release our "timer"
}
```

- Step 4

Example of our test:
```swift
func test_myFunction() {
  // Declare expectation
  theExpectation = expectationWithDescription("initialized") // dummy text
  var task: MyClass = MyClass()
  task.delegate = self // pass delegate to WmBuildGroupsTask class        
  task.execute();
  // Loop until the expectation is fulfilled in onDone method
  waitForExpectationsWithTimeout(500, { error in
    XCTAssertNil(error, "Oh, we got timeout")
  })
}
```
So now what left us to do is to add some stuff to WmBuildGroupsTask:

- Step 5

Add new variable:
```swift
var delegate: MyCallback?
```

Change onPostExecute method to:
```swift
func onPostExecute(transferItem:WmTransferItem) {
  /* .. */
  delegate?.onDone("finished")// call callback        
}
```

<a name="dependency-injection"></a>
## Dependency injection

Dependency injection (DI) is a popular design pattern in many languages, such as Java and C#, but it hasn’t seen wide adoption in Objective-C. The concept of dependency injection is very simple: __an object should require you to pass in any dependencies rather than creating them itself.__ Dependencies can be passed to an object via the initializer (or “constructor”), or via properties (or “setters”). These are commonly referred to as “constructor injection” and “setter injection.”

Constructor Injection:
```objectivec
- (instancetype)initWithDependency1:(Dependency1 *)d1 dependency2:(Dependency2 *)d2;
```
Setter Injection:
```objectivec
@property (nonatomic, retain) Dependency1 *dependency1;
@property (nonatomic, retain) Dependency2 *dependency2;
```

Constructor injection is preferred, and as a general rule you should only fall back to setter injection if constructor injection is not possible. With constructor injection, you’ll likely still have `@property` definitions for these dependencies, but you can make them read only to simplify your object’s API.

Benefits:

* Clear declaration of dependencies

It becomes obvious what an object needs in order to operate, and dangerous hidden dependencies — like globals — disappear.

* Composition

DI encourages composition over inheritance, which improves the reusability of your code.

* Easy customization

When creating an object, it’s easy to customize parts of the object for specific scenarios.

* Clear ownership

Particularly when using constructor injection, the object ownership rules are strictly enforced — helping to build a directed acyclic object graph.

* Testability

More than anything else, dependency injection improves the testability of your objects. Because they can be created simply by filling in the initializer, no hidden dependencies need to be managed. Furthermore, it becomes simple to mock out the dependencies to focus your tests on the object being tested.
