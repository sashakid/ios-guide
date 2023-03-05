- [Тестирование](#тестирование)
  - [Основные понятия](#основные-понятия)
  - [Виды тестов](#виды-тестов)
    - [Unit Tests](#unit-tests)
    - [Integration Tests](#integration-tests)
    - [Functional Tests](#functional-tests)
    - [Acceptance Tests](#acceptance-tests)
  - [Что такое BDD и TDD?](#что-такое-bdd-и-tdd)
  - [F.I.R.S.T Principles of Unit Testing](#first-principles-of-unit-testing)
  - [Как тестировать асинхронные методы?](#как-тестировать-асинхронные-методы)
  - [Как протестировать метод, не объявленный в публичном интерфейсе?](#как-протестировать-метод-не-объявленный-в-публичном-интерфейсе)
  - [Что такое assert и когда использовать?](#что-такое-assert-и-когда-использовать)
  - [Как протестировать синглтон?](#как-протестировать-синглтон)

# Тестирование

## Основные понятия

**SUT (System under test)**

Тестируемая система относится к системе, правильность работы которой тестируется.

**5 видов тестовых двойников:**

- Пустышка (dummy)
- Стаб (stub)
- Шпион (spy)
- Мок (mock)
- Фейк (fake)

Прежде чем перейти к теме того, когда использовать моки, давайте обсудим, что такое мок. Люди часто используют термины тестовый двойник (test double) и мок (mock) как синонимы, но технически это не так:
- Тестовый двойник - это всеобъемлющий термин, который описывает все виды фальшивых (fake) зависимостей, непригодных к использованию в конечном продукте (non-production-ready), в тестах. Такая зависимость выглядит и ведет себя как ее аналог, предназначенный для production, но на самом деле является упрощенной версией, которая снижает сложность и облегчает тестирование. Само название происходит от понятия дублера в кино.
- Мок – это лишь один из видов таких зависимостей.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/mock-stub.png">

- Моки помогают имитировать и изучать исходящие (outcoming) взаимодействия. То есть вызовы, совершаемые тестируемой системой (SUT) к ее зависимостям для изменения их состояния.
- Стабы помогают имитировать входящие (incoming) взаимодействия. То есть вызовы, совершаемые SUT к ее зависимостям для получения входных данных.

Например, отправка электронной почты является исходящим (outcoming) взаимодействием: это взаимодействие приводит к побочному эффекту на SMTP-сервере. Тестовый двойник, имитирующий такое взаимодействие, - это мок.

Извлечение данных из БД является входящим (incoming) взаимодействием — оно не приводит к побочному эффекту. Соответствующий тестовый двойник является стабом.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/mock-stub-diff.png">

**Spies (шпионы)**

Выполняют ту же роль, что и моки. Отличие в том, что spies пишутся вручную, а моки создаются с помощью готовых инструментов. Иногда spies называют рукописными моками.

С другой стороны, разница между стабами, dummy (пустышками) и фейками заключается в том, насколько они умны:

**Dummy**

Аростое, жестко закодированное значение, такое как null значение или выдуманная строка. Он используется для удовлетворения сигнатуры метода SUT и не участвует в получении конечного результата.

**Stub**

Стаб посложнее. Это полноценная зависимость, которую вы настраиваете для возврата разных значений для разных сценариев.

**Fake**

Это то же самое, что и стаб для большинства целей. Разница заключается в причинах его создания: фейк обычно используется для замены еще не существующей зависимости.

## Виды тестов

### Unit Tests

Tests the smallest unit of functionality, typically a method/function (e.g. given a class with a particular state, calling x method on the class should cause y to happen). Unit tests should be focussed on one particular feature (e.g., calling the pop method when the stack is empty should throw an InvalidOperationException). Everything it touches should be done in memory; this means that the test code and the code under test shouldn't:

1. Call out into (non-trivial) collaborators
2. Access the network
3. Hit a database
4. Use the file system
5. Spin up a thread

Any kind of dependency that is slow / hard to understand / initialise / manipulate should be stubbed / mocked / whatevered using the appropriate techniques so you can focus on what the unit of code is doing, not what its dependencies do.
In short, unit tests are as simple as possible, easy to debug, reliable (due to reduced external factors), fast to execute and help to prove that the smallest building blocks of your program function as intended before they're put together. The caveat is that, although you can prove they work perfectly in isolation, the units of code may blow up when combined which brings us to ...

### Integration Tests

Integration tests build on unit tests by combining the units of code and testing that the resulting combination functions correctly. This can be either the innards of one system, or combining multiple systems together to do something useful. Also, another thing that differentiates integration tests from unit tests is the environment. Integration tests can and will use threads, access the database or do whatever is required to ensure that all of the code and the different environment changes will work correctly.
If you've built some serialization code and unit tested its innards without touching the disk, how do you know that it'll work when you are loading and saving to disk? Maybe you forgot to flush and dispose filestreams. Maybe your file permissions are incorrect and you've tested the innards using in memory streams. The only way to find out for sure is to test it 'for real' using an environment that is closest to production.
The main advantage is that they will find bugs that unit tests can't such as wiring bugs (e.g. an instance of class A unexpectedly receives a null instance of B) and environment bugs (it runs fine on my single-CPU machine, but my colleague's 4 core machine can't pass the tests). The main disadvantage is that integration tests touch more code, are less reliable, failures are harder to diagnose and the tests are harder to maintain.
Also, integration tests don't necessarily prove that a complete feature works. The user may not care about the internal details of my programs, but I do!

### Functional Tests

Functional tests check a particular feature for correctness by comparing the results for a given input against the specification. Functional tests don't concern themselves with intermediate results or side-effects, just the result (they don't care that after doing x, object y has state z). They are written to test part of the specification such as, "calling function `Square(x)` with the argument of `2` returns `4`".

### Acceptance Tests

Acceptance testing seems to be split into two types:
Standard acceptance testing involves performing tests on the full system (e.g. using your web page via a web browser) to see whether the application's functionality satisfies the specification. E.g. "clicking a zoom icon should enlarge the document view by 25%." There is no real continuum of results, just a pass or fail outcome.
The advantage is that the tests are described in plain English and ensures the software, as a whole, is feature complete. The disadvantage is that you've moved another level up the testing pyramid. Acceptance tests touch mountains of code, so tracking down a failure can be tricky.
Also, in agile software development, user acceptance testing involves creating tests to mirror the user stories created by/for the software's customer during development. If the tests pass, it means the software should meet the customer's requirements and the stories can be considered complete. An acceptance test suite is basically an executable specification written in a domain specific language that describes the tests in the language used by the users of the system.

## Что такое BDD и TDD?

TDD, Test Driven Development - это методология разработки ПО, которая основывается на повторении коротких циклов разработки: изначально пишется тест, покрывающий желаемое изменение, затем пишется программный код, который реализует желаемое поведение системы и позволит пройти написанный тест. Затем проводится рефакторинг написанного кода с постоянной проверкой прохождения тестов.

BDD, Behaviour Driven Development - Из-за некоторого методологического сходства TDD (Test Driven Development) и BDD (Behaviour Driven Development) часто путают даже профессионалы. В чем же отличие? Концепции обоих подходов похожи, сначала идут тесты и только потом начинается разработка, но предназначение у них совершенно разное. TDD — это больше о программировании и тестировании на уровне технической реализации продукта, когда тесты создают сами разработчики. BDD предполагает описание тестировщиком или аналитиком пользовательских сценариев на естественном языке — если можно так выразиться, на языке бизнеса.

## F.I.R.S.T Principles of Unit Testing

**Fast**

- A developer should not hesitate to run the tests as they are slow.
- All of these including setup, the actual test and tear down should execute really fast (milliseconds) as you may have thousands of tests in your entire project.

**Isolated/Independent**

- A test method should do the 3 As => Arrange, Act, Assert
- Arrange: The data used in a test should not depend on the environment in which the test is running. All the data needed for a test should be arranged as part of the test.
- Act: Invoke the actual method under test.
- Assert: A test method should test for a single logical outcome, implying that typically there should be only a single logical assert. A logical assert could have multiple physical asserts as long as all the asserts test the state of a single object. In a few cases, an action can update multiple objects.
- Avoid doing asserts in the Arrange part, let it throw exceptions and your test will still fail.
- No order-of-run dependency. They should pass or fail the same way in suite or when run individually.
- Do not do any more actions after the assert statement(s), preferably single logical assert.

**Repeatable**

- A test method should NOT depend on any data in the environment/instance in which it is running.
- Deterministic results - should yield the same results every time and at every location where they run.
- No dependency on date/time or random functions output.
- Each test should setup or arrange it's own data.
- What if a set of tests need some common data? Use Data Helper classes that can setup this data for re-usability.

**Self-Validating**

- No manual inspection required to check whether the test has passed or failed.

**Thorough**

- Should cover every use case scenario and NOT just aim for 100% coverage.
- Tests for corner/edge/boundary values.
- Tests for large data sets - this will test runtime and space complexity.
- Tests for security with users having different roles - behavior may be different based on user's role.
- Tests for large values - overflow and underflow errors for data types like integer.
- Tests for exceptions and errors.
- Tests for illegal arguments or bad inputs.

## Как тестировать асинхронные методы?

We create `XCTestExpectation` instance that work like timer. Your test will never finish till one of both cases happend:
- `XCTestExpectation.fulfill()` called
- you got timeout defined with `waitForExpectationsWithTimeout` and therefore test will fail

*Step 1*

Create new protocol for class under test:

```swift
protocol MyCallback {
  func onDone(results: String)
}
```

This is our callback.

*Step 2*

In Unitest inherit this protocol:

```swift
class Test_MyClass : XCTestCase, MyCallback {
  /* ... */    
}
```

*Step 3*

Create `XCTestExpectation` variable:

```swift
var theExpectation: XCTestExpectation?
```

and initiate `onDone()` method:

```swift
func onDone(results: String) {
  theExpectation?.fulfill() // it will release our "timer"
}
```

*Step 4*

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

So now what left us to do is to add some stuff to `WmBuildGroupsTask`:

*Step 5*

Add new variable:

```swift
var delegate: MyCallback?
```

Change `onPostExecute` method to:

```swift
func onPostExecute(transferItem:WmTransferItem) {
  /* .. */
  delegate?.onDone("finished")// call callback        
}
```

## Как протестировать метод, не объявленный в публичном интерфейсе?

Варианты ответов:

1. To test private methods, you just need to test the public methods that call them. Call your public method and make assertions about the result or the state of the object. If the tests pass, you know your private methods are working correctly.
2. You don't need it. From Martin Fowler's article:
> If you ever find yourself in a situation where you really really need to test a private method you should take a step back and ask yourself why. I'm pretty sure this is more of a design problem than a scoping problem. Most likely you feel the need to test a private method because it's complex and testing this method through the public interface of the class requires a lot of awkward setup.
Whenever I find myself in this situation I usually come to the conclusion that the class I'm testing is already too complex. It's doing too much and violates the single responsibility principle - the S of the five SOLID 4 principles.
The solution that often works for me is to split the original class into two classes. It often only takes one or two minutes of thinking to find a good way to cut the one big class into two smaller classes with individual responsibility. I move the private method (that I urgently want to test) to the new class and let the old class call the new method. Voilà, my awkward-to-test private method is now public and can be tested easily. On top of that I have improved the structure of my code by adhering to the single responsibility principle.

## Что такое assert и когда использовать?

Assert provides a way for your code to reflect your assumptions explicitly, and check them when your code is running. Ideally, they are never triggered. In an unlikely situation when an assertion is triggered, the message lets you know that your code has been modified in a way that breaks your assumption. This is very valuable, because it shrinks the area in which you search for newly introduced errors.

## Как протестировать синглтон?

```swift
class DataLoader {
    enum Result {
        case data(Data)
        case error(Error)
    }

    func load(from url: URL, completionHandler: @escaping (Result) -> Void) {
        let task = URLSession.shared.dataTask(with: url) { (data, response, error) in
            if let error = error {
                return completionHandler(.error(error))
            }

            completionHandler(.data(data ?? Data()))
        }

        task.resume()
    }
}
```

The above `DataLoader` is currently very hard to test, as it will automatically call the shared URL session and perform a network call. This would require us to add waiting and timeouts to our testing code, and it quickly becomes very tricky and unstable.
Instead, let’s go through 3 easy steps to make this code still as simple to use as currently, but making it a lot easier to test.

**1. Abstract into a protocol**

```swift
protocol NetworkEngine {
    typealias Handler = (Data?, URLResponse?, Error?) -> Void

    func performRequest(for url: URL, completionHandler: @escaping Handler)
}

extension URLSession: NetworkEngine {
    typealias Handler = NetworkEngine.Handler

    func performRequest(for url: URL, completionHandler: @escaping Handler) {
        let task = dataTask(with: url, completionHandler: completionHandler)
        task.resume()
    }
}
```

**2. Use the protocol with the singleton as the default**

```swift
class DataLoader {
    enum Result {
        case data(Data)
        case error(Error)
    }

    private let engine: NetworkEngine

    init(engine: NetworkEngine = URLSession.shared) {
        self.engine = engine
    }

    func load(from url: URL, completionHandler: @escaping (Result) -> Void) {
        engine.performRequest(for: url) { (data, response, error) in
            if let error = error {
                return completionHandler(.error(error))
            }

            completionHandler(.data(data ?? Data()))
        }
    }
}
```

**3. Mock the protocol in your tests**

```swift
func testLoadingData() {
    class NetworkEngineMock: NetworkEngine {
        typealias Handler = NetworkEngine.Handler 

        var requestedURL: URL?

        func performRequest(for url: URL, completionHandler: @escaping Handler) {
            requestedURL = url

            let data = "Hello world".data(using: .utf8)
            completionHandler(data, nil, nil)
        }
    }

    let engine = NetworkEngineMock()
    let loader = DataLoader(engine: engine)

    var result: DataLoader.Result?
    let url = URL(string: "my/API")!
    loader.load(from: url) { result = $0 }

    XCTAssertEqual(engine.requestedURL, url)
    XCTAssertEqual(result, .data("Hello world".data(using: .utf8)!))
}
```