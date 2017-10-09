- [Паттерны проектирования](#паттерны-проектирования)
	- [Что такое SOLID?](#что-такое-solid)
	- [Архитектурные паттерны](#архитектурные-паттерны)
		- [MVC](#mvc)
		- [MVP](#mvp)
		- [MVVM](#mvvm)
			- [What is the difference between MVC, MVP, MVVM?](#difference)
		- [VIPER](#viper)
	- [Порождающие шаблоны](#порождающие-паттерны)
		- [Abstract factory](#abstract-factory)
		- [Factory method](#factory-method)
		- [Lazy initialization](#lazy-initialization)
		- [Singleton](#singleton)
	- [Структурные шаблоны](#структурные-паттерны)
		- [Adapter](#adapter)
		- [Decorator](#decorator)
		- [Proxy](#proxy)
		- [Facade](#facade)
		- [Кластеры](#кластеры)
		- [Composite](#composite)
	- [Communication Patterns](#communication-patterns)
		- [Observer](#observer)
		- [Делегирование](#делегирование)
		- [KVC](#kvc)
		- [KVO](#kvo)
		- [Notification](#notification)
	- [Поведенческие шаблоны](#поведенческие-шаблоны)
		- [Chain of responsibility](#chain-of-responsibility)			
		- [The Target-Action Mechanism](#the-target-action-mechanism)
		- [Command](#command)
		- [Iterator](#iterator)
		- [Mediator](#mediator)
		- [Memento](#memento)
		- [State](#state)
	- [Анти-паттерны в объектно-ориентированном программировании](#анти-паттерны-в-объектно-ориентированном-программировании)
	- [Какая разница между использованием делагатов и нотификейшенов?](#какая-разница-между-использованием-делагатов-и-нотификейшенов?)

<a name="паттерны-проектирования"></a>
# Паттерны проектирования
Повторимая архитектурная конструкция, представляющая собой решение проблемы проектирования в рамках некоторого часто возникающего контекста.

__How Cocoa Adapts Design Patterns__

You can find adaptations of design patterns throughout Cocoa, in both its OS X and iOS versions. Mechanisms and architectures based on patterns are common in Cocoa frameworks and in the Objective-C runtime and language. Cocoa often puts its own distinctive spin on a pattern because its designs are influenced by factors such as language capabilities or existing architectures.
This section contains summaries of most of the design patterns cataloged in Design Patterns: Elements of Reusable Object-Oriented Software. Each section not only summarizes the pattern but discusses the Cocoa implementations of it. Only patterns that Cocoa implements are listed, and each description of a pattern in the following sections pertains to a particular Cocoa context.
Implementations of design patterns in Cocoa come in various forms. Some of the designs described in the following sections, such as protocols and categories, are features of the Objective-C language. In other cases, the “instance of a pattern” is implemented in one class or a group of related classes (for example, class clusters and singleton classes). And in other cases the pattern adaptation is a major framework architecture, such as the responder chain. Some of the pattern-based mechanisms you get almost “for free” while others require some work on your part. And even if Cocoa does not implement a pattern, you are encouraged to do so yourself when the situation warrants it; for example, object composition (Decorator pattern) is often a better technique than subclassing for extending class behavior.
Two design patterns are reserved for later sections, Model-View-Controller (MVC) and object modeling. MVC is a compound, or aggregate pattern, meaning that it is based on several catalog patterns. Object modeling has no counterpart in the Gang of Four catalog, instead originating from the domain of relational databases. Yet MVC and object modeling are perhaps the most important and pervasive design patterns in Cocoa, and to a large extent they are interrelated patterns. They play a crucial role in the design of several technologies, including bindings, undo management, scripting, and the document architecture. To learn more about these patterns, see The Model-View-Controller Design Pattern and Object Modeling.

<a name="что-такое-solid"></a>
## Что такое SOLID?
SOLID (сокр. от англ. Single responsibility, Open-closed, Liskov substitution, Interface segregation и Dependency inversion) - акроним, введённый Майклом Фэзерсом для первых пяти принципов, названных Робертом Мартином в начале 2000-х, которые означали пять основных принципов ООП и проектирования.

1. "__S__", Single responsibility, Принцип единственной ответственности

Обозначает, что каждый объект должен иметь одну ответственность и эта ответственность должна быть полностью инкапсулирована в класс. Все его поведения должны быть направлены исключительно на обеспечение этой ответственности. Следующие приёмы позволяют соблюдать принцип единственной ответственности: разработка через тестирование, выделение класса, фасад, Proxy, DAO.

2. "__O__", Open-closed, Принцип открытости / закрытости

Программные сущности должны быть:
* открыты для расширения: означает, что поведение сущности может быть расширено, путём создания новых типов сущностей.
* закрыты для изменения: в результате расширения поведения сущности, не должны вносится изменения в код, которые эти сущности использует.

3. "__L__", Liskov substitution, Принцип подстановки Барбары Лисков

Даёт определение понятия замещения — если `S` является подтипом `T`, тогда объекты типа `T` в программе могут быть замещены объектами типа `S` без каких-либо изменений желательных свойств этой программы (например, корректность). Более простыми словами можно сказать, что поведение наследуемых классов не должно противоречить поведению, заданному базовым классом, то есть поведение наследуемых классов должно быть ожидаемым для кода, использующего переменную базового типа.

4. "__I__", Interface segregation, Принцип разделения интерфейса

Роберт Мартин определил его так: «Клиенты не должны зависеть от методов, которые они не используют». Принцип разделения интерфейсов говорит о том, что слишком «толстые» интерфейсы необходимо разделять на более маленькие и специфические, чтобы клиенты маленьких интерфейсов знали только о методах, которые необходимы им в работе. В итоге, при изменении метода интерфейса не должны меняться клиенты, которые этот метод не используют.

5. "__D__", Dependency inversion, Принцип инверсии зависимостей

Принцип, используемый для уменьшения зацепления в компьютерных программах.
* Модули верхних уровней не должны зависеть от модулей нижних уровней. Оба типа модулей должны зависеть от абстракций.
* Абстракции не должны зависеть от деталей. Детали должны зависеть от абстракций.

<a name="архитектурные-паттерны"></a>
## Архитектурные паттерны
<a name="mvc"></a>
### MVC
Модель состоит из классов, в которых хранятся данные приложения.
Представление создает дизайн.
Контроллер связывает модель и представление и организует логику приложения.
Пассивная модель — модель не имеет никаких способов воздействовать на представление или контроллер, и используется ими в качестве источника данных для отображения. Все изменения модели отслеживаются контроллером и он же отвечает за перерисовку представления, если это необходимо. Такая модель чаще используется в структурном программировании, так как в этом случае модель представляет просто структуру данных, без методов их обрабатывающих.
Активная модель — модель оповещает представление о том, что в ней произошли изменения, а представления, которые заинтересованы в оповещении, подписываются на эти сообщения. Это позволяет сохранить независимость модели как от контроллера, так и от представления.

<a name="mvp"></a>
### MVP
Шаблон проектирования, производный от MVC, который используется в основном для построения пользовательского интерфейса. Элемент Presenter в данном шаблоне берёт на себя функциональность посредника (аналогично контроллеру в MVC) и отвечает за управление событиями пользовательского интерфейса (например, использование мыши) так же, как в других шаблонах обычно отвечает представление. Был разработан для облегчения автоматического модульного тестирования и улучшения разделения ответственности в презентационной логике (отделения логики от отображения):
* Модель (англ. Model) — предоставляет данные для пользовательского интерфейса.
* Представление (англ. View) — реализует отображение данных (Модели) и маршрутизацию пользовательских команд или событий Presenterʼу.
* Presenter — управляет Моделью и Представлением. Например, извлекает данные из Модели и форматирует их для отображения в Представлении.
Обычно экземпляр Представления создаёт экземпляр Presenterʼа, передавая ему ссылку на себя. При этом Presenter работает с Представлением в абстрактном виде, через его интерфейс. Когда вызывается событие Представления, оно вызывает конкретный метод Presenterʼа, не имеющего ни параметров, ни возвращаемого значения. Presenter получает необходимые для работы метода данные о состоянии пользовательского интерфейса через интерфейс Представления и через него же передаёт в Представление данные из Модели и другие результаты своей работы.

<a name="mvvm"></a>
### MVVM
* is compatible with your existing MVC architecture
* makes your apps more testable
* works best with a binding mechanism

MVVM удобно использовать вместо классического MVC и ему подобных в тех случаях, когда в платформе, на которой ведётся разработка, присутствует «связывание данных». В шаблонах проектирования MVC/MVP изменения в пользовательском интерфейсе не влияют непосредственно на Mодель, а предварительно идут через Контроллер или Presenter.

<a name="difference"></a>
#### What is the difference between MVC, MVP, MVVM?
In MVP, the Presenter contains the UI business logic for the View. All invocations from the View delegate directly to Presenter. The Presenter is also decoupled directly from the View and talks to it through an interface. This is to allow mocking of the View in a unit test. One common attribute of MVP is that there has to be a lot of two-way dispatching. For example, when someone clicks the "Save" button, the event handler delegates to the Presenter's "OnSave" method. Once the save is completed, the Presenter will then call back the View through its interface so that the View can display that the save has completed.

In the MVC, the Controller is responsible for determining which View is displayed in response to any action including when the application loads. This differs from MVP where actions route through the View to the Presenter. In MVC, every action in the View correlates with a call to a Controller along with an action. In the web each action involves a call to a URL on the other side of which there is a Controller who responds. Once that Controller has completed its processing, it will return the correct View.

In MVVM there is no Presenter. Instead the View binds directly to a Presentation Model. The Presentation Model is a Model crafted specifically for the View. This means this Model can expose properties that one would never put on a domain model as it would be a violation of separation-of-concerns. In this case, the Presentation Model binds to the domain model, and may subscribe to events coming from that Model. The View then subscribes to events coming from the Presentation Model and updates itself accordingly. The Presentation Model can expose commands which the view uses for invoking actions. The advantage of this approach is that you can essentially remove the code-behind altogether as the PM completely encapsulates all of the behaviour for the view.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/mvc-mvp-mvvm.png">

<a name="viper"></a>
### VIPER
* "__V__", View: displays what it is told to by the Presenter and relays user input back to the Presenter.
* "__I__", Interactor: contains the business logic as specified by a use case.
* "__P__", Presenter: contains view logic for preparing content for display (as received from the Interactor) and for reacting to user inputs (by requesting new data from the Interactor).
* "__E__", Entity: contains basic model objects used by the Interactor.
* "__R__", Routing: contains navigation logic for describing which screens are shown in which order.
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/viper.png">

<a name="порождающие-шаблоны"></a>
## Порождающие шаблоны
Шаблоны проектирования, которые абстрагируют процесс инстанцирования. Они позволяют сделать систему независимой от способа создания, композиции и представления объектов. Шаблон, порождающий классы, использует наследование, чтобы изменять инстанцируемый класс, а шаблон, порождающий объекты, делегирует инстанцирование другому объекту.

<a name="abstract-factory"></a>
### Abstract factory
Предоставляет интерфейс для создания семейств взаимосвязанных или взаимозависимых объектов, не специфицируя их конкретных классов. Шаблон реализуется созданием абстрактного класса Factory, который представляет собой интерфейс для создания компонентов системы (например, для оконного интерфейса он может создавать окна и кнопки). Затем пишутся классы, реализующие этот интерфейс.
* Система не должна зависеть от того, как создаются, компонуются и представляются входящие в неё объекты.
* Входящие в семейство взаимосвязанные объекты должны использоваться вместе и вам необходимо обеспечить выполнение этого ограничения.
* Система должна конфигурироваться одним из семейств составляющих её объектов.
* Требуется предоставить библиотеку объектов, раскрывая только их интерфейсы, но не реализацию.

<a name="factory-method"></a>
### Factory Method
Также известен как Виртуальный конструктор — порождающий шаблон проектирования, предоставляющий подклассам интерфейс для создания экземпляров некоторого класса. В момент создания наследники могут определить, какой класс создавать. Иными словами, Фабрика делегирует создание объектов наследникам родительского класса. Это позволяет использовать в коде программы не специфические классы, а манипулировать абстрактными объектами на более высоком уровне.

_Плюсы_

* позволяет сделать код создания объектов более универсальным, не привязываясь к конкретным классам (ConcreteProduct), а оперируя лишь общим интерфейсом (Product)
* позволяет установить связь между параллельными иерархиями классов

_Минусы_

* необходимость создавать наследника Creator для каждого нового типа продукта (ConcreteProduct). Впрочем, современные языки программирования поддерживают конструкции, что позволяет реализовать фабричный метод без иерархии классов Creator

<a name="lazy-initialization"></a>
### Lazy initialization
Приём в программировании, когда некоторая ресурсоёмкая операция (создание объекта, вычисление значения) выполняется непосредственно перед тем, как будет использован её результат. Таким образом, инициализация выполняется «по требованию», а не заблаговременно. Аналогичная идея находит применение в самых разных областях: например, компиляция «на лету» и логистическая концепция «Точно в срок». Частный случай ленивой инициализации — создание объекта в момент обращения к нему — является одним из порождающих шаблонов проектирования.

_Достоинства_

* Инициализация выполняется только в тех случаях, когда она действительно необходима
* Ускоряется начальная инициализация

_Недостатки_

* Невозможно явным образом задать порядок инициализации объектов
* Возникает задержка при первом обращении к объекту
```objectivec
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
	static NSString *CellIdentifier = @"CellIdentifier";
	cell = [tableView dequeueReusableCellWithIdentifier:CellIdentifier];
	if (cell == nil) {
		//ленивая загрузка
		cell = [[UITableViewCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:CellIdentifier];
	}
	cell.textLabel.text = someText;
	return cell;
}
```

<a name="singleton"></a>
### Singleton
Существует в системе в единственном экземпляре => не может быть повторно создан. Объект, к которому обращаются много объектов. Примеры синглтонов в системе:
```objectivec
[NSUserDefaults standardUserDefaults];
[UIApplication sharedApplication];
[UIScreen mainScreen];
[NSFileManager defaultManager];
```
_Non thread safe_
```objectivec
@implementation Singleton
static Singleton *sharedSingleton_ = nil;
+ (Singleton *)sharedInstance {
	if (sharedSingleton_ == nil) {
		sharedSingleton_ = [[Singleton alloc] init];
	}
	return sharedSingleton_;
}
@end
```
However this is wrong on several levels. Firstly, this isn't thread safe, so what happens if multiple threads all try to access this at the same time? There is no reason 1 thread couldn't be in the middle of allocating the object while the other one is trying to access the object. This is actually what Apple shows in its documentation.
If you must use singletons, use `dispatch_once()`
dispatch_once() solves the problem of safely being able to create a singleton in that (1) it guarantees that the code in the block will only be called once for the lifetime of the application (2) its thread safe as I noted in a previous article and (3) its faster than other methods like using `@synchronize()`,etc...
"If called simultaneously from multiple threads, this function waits synchronously until the block has completed." So you should be writing it like this...

_Thread safe_
```objectivec
+ (MyClass *)singleton {
	static dispatch_once_t pred;
	static MyClass *shared = nil;
	dispatch_once(&pred, ^{
		shared = [[MyClass alloc] init];
		});
		return shared;
}
```

__Criticism:__

1. It violates the single responsibility principle because of its quality of controlling its own creation and lifecycle.
2. It introduces global state to your application. I would say global state is very bad because any code can change its value. So at the time of debugging it's really hard to find which portion of the code has made the current stage of global variable.
3. Singleton is generally a bad idea if you are doing unit testing, and it's generally a bad idea not to perform unit testing.

<a name="структурные-шаблоны"></a>
## Структурные шаблоны
Определяют различные сложные структуры, которые изменяют интерфейс уже существующих объектов или его реализацию, позволяя облегчить разработку и оптимизировать программу.
<a name="adapter"></a>
### Adapter
The Adapter design pattern converts the interface of a class into another interface that clients expect. Adapter lets classes work together that couldn’t otherwise because of incompatible interfaces. It decouples the client from the class of the targeted object.

__Protocols__

A protocol is a language-level (Objective-C) feature that makes it possible to define interfaces that are instances of the Adapter pattern. A protocol is essentially a series of method declarations unassociated with a class. (In Java, interface is synonymous with protocol.) If you want a client object to communicate with another object, but the objects’ incompatible interfaces make that difficult, you can define a protocol. The class of the other object then formally adopts the protocol and “conforms” to it by implementing one or more of the methods of the protocol. The protocol may require the conforming class to implement some of its methods and may leave the implementation of others optional. The client object can then send messages to the other object through the protocol interface.
Protocols make a set of method declarations independent of the class hierarchy. They make it possible to group objects on the basis of conformance to a protocol as well as class inheritance. The `NSObject` method `conformsToProtocol:` permits you to verify an object’s protocol affiliation.
Cocoa has informal protocols as well as formal protocols. An informal protocol is a category on the `NSObject` class, thus making any object a potential implementer of any method in the category. The methods in an informal protocol can be selectively implemented. Informal protocols are part of the implementation of the delegation mechanism in OS X.
Note that the design of protocols does not perfectly match the description of the Adapter pattern. But it achieves the goal of the pattern: allowing classes with otherwise incompatible interfaces to work together.

_Uses and Limitations_

You use a protocol primarily to declare an interface that hierarchically unrelated classes are expected to conform to if they want to communicate. But you can also use protocols to declare an interface of an object while concealing its class. The Cocoa frameworks include many formal protocols that enable custom subclasses to communicate with them for specific purposes. For example, the Foundation framework includes the `NSObject`, `NSCopying`, and `NSCoding` protocols, which are all very important ones. AppKit protocols include `NSDraggingInfo`, `NSTextInput`, and `NSChangeSpelling`. `UIKit` protocols include `UITextInputTraits`, `UIWebViewDelegate`, and `UITableViewDataSource`.
Formal protocols implicitly require the conforming class to implement all declared methods. However, they can mark single methods or groups of methods with the `@optional` directive, and the conforming class may choose to implement those. They are also fragile; once you define a protocol and make it available to other classes, future changes to it (except for additional optional methods) can break those classes.

<a name="decorator"></a>
### Decorator
The Decorator design pattern attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality. As does subclassing, adaptation of the Decorator pattern allows you to incorporate new behavior without modifying existing code. Decorators wrap an object of the class whose behavior they extend. They implement the same interface as the object they wrap and add their own behavior either before or after delegating a task to the wrapped object. The Decorator pattern expresses the design principle that classes should be open to extension but closed to modification.

_General Comments_

Decorator is a pattern for object composition, which is something that you are encouraged to do in your own code. Cocoa, however, provides some classes and mechanisms of its own that are based on the pattern. In these implementations, the extending object does not completely duplicate the interface of the object that it wraps, and the implementations use different techniques for interface sharing.
Cocoa uses the Decorator pattern in the implementation of several of its classes, including `NSAttributedString`, `NSScrollView`, `UIDatePicker`. The latter two classes are examples of compound views, which group together simple objects of other view classes and coordinate their interaction.

__Categories__

A category is a feature of the Objective-C language that enables you to add methods (interface and implementation) to a class without having to make a subclass. There is no runtime difference, within the scope of your program, between the original methods of the class and the methods added by the category. The methods in the category become part of the class type and are inherited by all the class’s subclasses.
As with delegation, categories are not a strict adaptation of the Decorator pattern, fulfilling the intent but taking a different path to implementing that intent. The behavior added by categories is a compile-time artifact, and is not something dynamically acquired. Moreover, categories do not encapsulate an instance of the class being extended.

_Uses and Limitations_

The Cocoa frameworks define numerous categories, most of them informal protocols (which are summarized in Protocols). Often they use categories to group related methods. You may implement categories in your code to extend classes without subclassing or to group related methods. However, you should be aware of these caveats: you cannot add instance variables to the class. If you override existing methods of the class, your application may behave unpredictably.

<a name="proxy"></a>
### Proxy
The Proxy design pattern provides a surrogate, or placeholder, for another object in order to control access to that other object. You use this pattern to create a representative, or proxy, object that controls access to another object, which may be remote, expensive to create, or in need of securing. This pattern is structurally similar to the Decorator pattern but it serves a different purpose; Decorator adds behavior to an object whereas Proxy controls access to an object.

__NSProxy__

The `NSProxy` class defines the interface for objects that act as surrogates for other objects, even for objects that don’t yet exist. A proxy object typically forwards a message sent to it to the object that it represents, but it can also respond to the message by loading the represented object or transforming itself into it. Although `NSProxy` is an abstract class, it implements the `NSObject` protocol and other fundamental methods expected of a root object; it is, in fact, the root class of a hierarchy just as the `NSObject` class is.
Concrete subclasses of `NSProxy` can accomplish the stated goals of the Proxy pattern, such as lazy instantiation of expensive objects or acting as sentry objects for security. `NSDistantObject`, a concrete subclass of `NSProxy` in the Foundation framework, implements a remote proxy for transparent distributed messaging. `NSDistantObject` objects are part of the architecture for distributed objects. By acting as proxies for objects in other processes or threads, they help to enable communication between objects in those threads or processes.
`NSInvocation` objects, which are an adaptation of the Command pattern, are also part of the distributed objects architecture.

_Uses and Limitations_

Cocoa employs `NSProxy` objects only in distributed objects. The `NSProxy` objects are specifically instances of the concrete subclasses `NSDistantObject` and `NSProtocolChecker`. You can use distributed objects not only for interprocess messaging (on the same or different computers) but you can also use it to implement distributed computing or parallel processing. If you want to use proxy objects for other purposes, such as the creation of expensive resources or security, you have to implement your own concrete subclass of `NSProxy`.

<a name="facade"></a>
### Facade
The Facade design pattern provides a unified interface to a set of interfaces in a subsystem. The pattern defines a higher-level interface that makes the subsystem easier to use by reducing complexity and hiding the communication and dependencies between subsystems.

__NSImage__

The `NSImage` class of the AppKit framework provides a unified interface for loading and using images that can be bitmap-based (such as those in JPEG, PNG, or TIFF format) or vector-based (such as those in EPS or PDF format). NSImage can keep more than one representation of the same image; each representation is a kind of `NSImageRep` object. NSImage automates the choice of the representation that is appropriate for a particular type of data and for a given display device. It also hides the details of image manipulation and selection so that the client can use many different underlying representations interchangeably.

_Uses and Limitations_

Because `NSImage` supports several different representations of what an image is, some requested attributes might not apply. For example, asking an image for the color of a pixel does not work if the underlying image representation is vector-based and device-independent.

<a name="кластеры"></a>
### Кластеры
Class clusters are a design pattern that the Foundation framework makes extensive use of. Class clusters group a number of private concrete subclasses under a public abstract superclass. The grouping of classes in this way simplifies the publicly visible architecture of an object-oriented framework without reducing its functional richness. Class clusters are based on the Abstract Factory design pattern.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/cluster.png">

`NSMutableArray` is not a concrete class, it is just the abstract superclass of a class cluster. The documentation for `NSMutableArray` does have information about how to subclass, but also strongly advises you not to! Only subclass if you have a special need for actual storage. A class cluster means that the actual class will be chosen at runtime. An array created empty, may not use the same class as an array created with 1000 items. The runtime can do smart choices of what implementation to use for you. In practice `NSMutableArray` will be a bridged `CFArray`. Nothing you need to worry about, but you might see it if you inspect the type of your arrays in the debugger, you will never see `NSArray`, but quite often `NSCFArray`. As mentioned before, subclassing is not the same as extending a class. Objective-C has the concept of categories. A category is similar to what other programming languages call mixins. If you for example want a convenience method on `NSMutableArray` to sort all members on a property, then define the category interface in a .h file.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/cluster_description.png">

<a name="composite"></a>
### Composite
The Composite design pattern composes related objects into tree structures to represent part-whole hierarchies. The pattern lets clients treat individual objects and compositions of objects uniformly.
The Composite pattern is part of the Model-View-Controller aggregate pattern, which is describe in The Model-View-Controller Design Pattern.

__View Hierarchy__

The views in a window are internally structured into a view hierarchy. At the root of the hierarchy is a window and its content view, a transparent view that fills the window’s content rectangle. Views that are added to the content view become subviews of it, and they become the superviews of any views added to them. Except for the content view, a view has one (and only one) superview and zero or any number of subviews. You perceive this structure as containment: a superview contains its subviews.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/view_hierarchy.png">

The view hierarchy is a structural architecture that plays a part in both drawing and event handling. A view has two bounding rectangles, its frame and its bounds, that affect how graphics operations with the view take place. The frame is the exterior boundary; it locates the view in its superview’s coordinate system, defines its size, and clips drawing to the view’s edges. The bounds, the interior bounding rectangle, defines the internal coordinate system of the surface where the view draws itself.
When a window is asked by the windowing system to prepare itself for display, superviews are asked to render themselves before their subviews. When you send some messages to a view, for example, a message that requests a view to redraw itself, the message is propagated to subviews. You can thus treat a branch of the view hierarchy as a unified view.
The view hierarchy is also used by the responder chain for handling events and action messages.

<a name="communication-patterns"></a>
## Communication Patterns
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/communication_patterns.png">

<a name="observer"></a>
### Observer
Определяет одно-ко-многим отношение между объектами, и если изменения происходят в объекте – все подписанные на него объекты тут же узнают про это изменение. Идея проста: объект который мы называем Subject – дает возможность другим объектам, которые реализуют интерфейс Observer, подписываться и отписываться от изменений происходящик в Subject. Когда изменение происходит – всем заинетерсованным объектам высылается сообщение, что изменение произошло. В нашем случае – Subject – это издатель газеты, Observer это мы с вами – те кто подписывается на газету, ну и собственно изменение – это выход новой газеты, а оповещение – отправка газеты всем кто подписался.
Когда используется паттерн:
* Когда Вам необходимо сообщить всем объектам подписанным на изменения, что изменение произошло, при этом вы не знаете типы этих объектов.
Изменения в одном объекте требуют чтоб состояние изменилось в других объектах, при чем количество объектов может быть разное.

<a name="делегирование"></a>
### Делегирование
(англ. Delegation) — основной шаблон проектирования, в котором объект внешне выражает некоторое поведение, но в реальности передаёт ответственность за выполнение этого поведения связанному объекту. Паттерн хорош тем, что нам не нужно хранить всю логику в одном месте и позволяет лучше переиспользовать код. Рассматривайте делегат как обычный обьект, который может выполнять некоторые функции. Например, возьмем `NSTableView` delegate. Вы хотите отрисовать ячейку таблицы как-то по своему. `NSTableView` своему делегату пошлет сообщение о том, что он сейчас будет рисовать данную ячейку и делегат уже сам решает что с ней делать (рисовать по своему, не трогать вообще и т.д.). Это, грубо говоря, способ получения и предоставления информации, о которой `NSTableView` не знает вообще ничего.
Или же пример создания собственных делегатов. Представьте, что у вас есть свой класс, который выполняет некоторую функцию. Для выполнения некоторых задач ему необходима информация из другого класса, о котором сейчас не известно ровным счетом ничего, кроме того, что он существует. Тогда создается конструкция вида:
```objectivec
@interface Class1 {
	id delegate;
}
- (id)delegate;
- (void)setDelegate:(id)newDelegate;

@implementation Class1
- (id)delegate {
	return delegate;
}

- (void)setDelegate:(id)newDelegate {
	delegate = newDelegate;
}
```
Как видно из примера — наш делегат, это просто указатель на какой-либо обьект. Ну и предоставлены геттер и сеттер. Для того, чтобы делегат выполнил некоторое действие для нас, где-то внутри нашего `Class1` мы пошлем сообщение вида
```objectivec
[delegate doSomeWork];
```
Обьект же, который мы назначили делегатом для данного класса в свою очередь получит это сообщение и начнет выполнять какое-то действие.
В принципе и все. Достаточно просто. Делегирование преследует простую цель — сохранять объекты слабо связанными. Таким образом, вы можете отправлять сообщения делегату, не зная какой именно это объект. А сам делегат, при этом, может выполнять разные действия в зависимости от своей реализации. Так что тут мы имеем одно из проявлений полиморфизма. То есть, грубо говоря, делегирующий объект говорит объекту-делегату ЧТО делать, но его не волнует КАК именно это будет сделано.
Плюс, делегирование порой может быть более удобной альтернативой наследованию — вместо того, чтобы плодить иерархию классов, вы определяете необходимый интерфейс для делегатов и используете их.
Delegation is a mechanism by which a host object embeds a weak reference (weak in the sense that it’s a simple pointer reference, unretained) to another object, its delegate, and periodically sends messages to the delegate when it requires its input for a task. The host object is generally an “off-the-shelf” framework object (such as `NSWindow` or `NSXMLParser` object) that is seeking to accomplish something, but can only do so in a generic fashion. The delegate, which is almost always an instance of a custom class, acts in coordination with the host object, supplying program-specific behavior at certain points in the task. Thus delegation makes it possible to modify or extend the behavior of another object without the need for subclassing.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/delegation.png">

Delegation, in the simple sense of one object delegating a task to another object, is a common technique in object-oriented programming. However, Cocoa implements delegation in a unique way. A host class uses a formal protocol or an informal protocol to define an interface that the delegate object may choose to implement. All the methods in the informal protocol are optional, and the formal protocol may declare optional methods, allowing the delegate to implement only some of the methods in the protocol. Before it attempts to send a message to its delegate, the host object determines whether it implements the method (via a `respondsToSelector:` message) to avoid runtime exceptions. For more on formal and informal protocols, see Protocols.
Some classes in the Cocoa frameworks also send messages to their data sources. A data source is identical in all respects to a delegate, except that the intent is to provide the host object with data to populate a browser, a table view, or similar user-interface view. A data source, unlike a delegate, may also be required to implement some methods of the protocol.
Delegation is not a strict implementation of the Decorator pattern. The host (delegating) object does not wrap an instance of the class it wants to extend; indeed, it’s the other way around, in that the delegate is specializing the behavior of the delegating framework class. There is no sharing of interface either, other than the delegation methods declared by the framework class.
Delegation in Cocoa is also part of the Template Method pattern (Template Method).

__Uses and Limitations__

Delegation is a common design in the Cocoa frameworks. Many classes in the AppKit and UIKit frameworks send messages to delegates, including `NSApplication`, `UIApplication`, `UITableView`, and several subclasses of `NSView`. Some classes in the Foundation framework, such as `NSXMLParser` and a `NSStream`, also maintain delegates. You should always use a class’s delegation mechanism instead of subclassing the class, unless the delegation methods do not allow you to accomplish your goal.
Although you can dynamically change the delegate, only one object can be a delegate at a time. Thus if you want multiple objects to be informed of a particular program event at the same time, you cannot use delegation. However, you can use the notification mechanism for this purpose. A delegate automatically receives notifications from its delegating framework object as long as the delegate implements one or more of the notification methods declared by the framework class. See the discussion of notifications in the Observer pattern.
Delegating objects in AppKit do not retain their delegates or data sources.

<a name="kvc"></a>
### KVC
Key-value coding is a mechanism for accessing an object’s properties indirectly, using strings to identify properties, rather than through invocation of an accessor method or accessing them directly through instance variables. In essence, key-value coding defines the patterns and method signatures that your application’s accessor methods implement.
Implementing key-value coding compliant accessors in your application is an important design principle. Accessors help to enforce proper data encapsulation, isolate memory management to centralized locations, and facilitate integration with other technologies such as key-value observing, Core Data, Cocoa bindings, and scriptability.
Соответствующие методы определены в `NSObject`, поэтому каждый объект
поддерживает данную возможность.
```objectivec
[a setProductName:@"Washing Machine"];
```
C использованием KVC:
```objectivec
[a setValue:@"Washing Machine" forKey:@"productName"];
```
Запись «ключ-значение» также позволяет прочитать значение переменной. Каждый раз, когда стандартная библиотека записывает данные в ваши объекты, она использует `setValue:forKey:`. Каждый раз, когда стандартная библиотека читает данные из ваших объектов, она использует `valueForKey:`. Например, библиотека СоrеData упрощает сохранение объектов в базе данных SQLite и их последующую загрузку. Для работы с пользовательским объектами, содержащими данные, используется запись «ключ-значение».
```objectivec
double totalSalary = 0.0;
for (Employee *employee in employees) {
	totalSalary += [employee.salary doubleValue];
}
double averageSalary = totalSalary / [employees count];
```
эквивалентно
```objectivec
[employees valueForKeyPath:@"@avg.salary"];
```
KVC Collection Operators allows actions to be performed on a collection using key path notation in `valueForKeyPath:`. Any time you see `@` in a key path, it denotes a particular aggregate function whose result can be returned or chained, just like any other key path. Collection Operators fall into one of three different categories, according to the kind of value they return:

1. Simple Collection Operators return strings, numbers, or dates, depending on the operator.
2. Object Operators return an array.
3. Array and Set Operators return an array or set, depending on the operator.

Simple Collection Operators

`@count` Returns the number of objects in the collection as an `NSNumber`.

`@sum` Converts each object in the collection to a double, computes the sum, and returns the sum as an `NSNumber`.

`@avg` Takes the double value of each object in the collection, and returns the average value as an `NSNumber`.

`@max` Determines the maximum value using `compare:`. Objects must support comparison with one another for this to work.

`@min` Same as `@max`, but returns the minimum value in the collection.

<a name="kvo"></a>
### KVO
Еще одна реализация патерна наблюдатель. В этом случае наблюдатель следит не за событиями, а за конкретным свойством объекта. Когда значение этого свойства меняется, наблюдателю приходит уведомление и он соответствующим образом реагируют.
По сравнению со многими другими языками реализация KVO в objective c радуют довольно простым синтаксисом. Так в коде наблюдателя достаточно написать:
```objectivec
[company_a addObserver:self forKeyPath:@"people" options:NSKeyValueObservingOptionNew context:nil];
```
И каждый раз когда в `company_a` будет изменяться значение переменной `people` наблюдатель будет уведомляться с помощью вызова метода
`- observeValueForKeyPath:(NSString *)keyPath ofObject:(id)object change:(NSDictionary *)change context:(void *)context` и надо лишь реализовать код, который будет реагировать на уведомление.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/kvo.png">

__Плюсы__

* Минимализм кода (достаточно написать всего лишь несколько строчек, чтобы полностью реализовать паттерн наблюдатель)
* Возможность слежения за любыми свойствами любых классов как написанными нами, так и чужими. Фактически внешние переменные всегда оформляются через свойства, что позволяет с легкостью следить любыми изменениями.

__Недостатки__

* Первая и очень важная проблема — это заметное падение производительности при обильном использовании KVO. Не стоит писать код, где ваши объекты общаются в основном через KVO. Рассматривайте KVO как вспомогательно средство для работы с чужим кодом, а не как основной инструмент.
* Второй проблемой является необходимость очень аккуратно писать код при использовании KVO. Так как строковые идентификаторов не проверяются компилятором на валидность, то это может привести к ошибкам при переименовании переменных. Также, KVO очень чувствительно к порядку добавления / удаления наблюдателей. Так, если наблюдатель пытается отписаться от наблюдаемого, на который наблюдатель в данный момент не подписан, то происходит крэш. Если же, наоброт, наблюдатель не отпишется до того, как наблюдаемый будет уничтожен, то произойдет утечка памяти. Все это приводит к тому, что легко прострелить себе ногу при добавлении / удалении наблюдателей из разных мест кода. Наиболее простой способ обезопасить себя – это хранить в наблюдателе ссылку на объект наблюдения, метод присвоения которой описан следующим образом:
```objectivec
- (void) setObservable:(id)observable {
	[_observable addObserver:self forKeyPath:@"property" options:NSKeyValueObservingOptionNew context:nil];
	_observable = observable;
	[_observable removeObserver:self forKeyPath:@"property"];
}
```
Таким образом соотношение между добавлением и удалением строго равно единице и нет необходимости тщательно следить где именно добавляется / удаляется наблюдение. Вызов деструктора также больше не является проблемой, так как перед уничтожением объекта в свойство запишется `nil`, попутно завершив наблюдение за объектом.

* Always handle nil and other unusual values gracefully
* Don't use accessors (or dot notation) in init or dealloc

<a name="notification"></a>
### Notification
Notificaiton – механизм использования возможностей `NotificationCenter` самой операционной системы. Использование `NSNotificationCenter` позволяет объектам коммуницировать, даже не зная друг про друга. Это очень удобно использовать когда у вас в паралельном потоке пришел push-notification, или же обновилась база, и вы хотите дать об этом знать активному на даный момент View.
Чтобы послать такое сообщение стоит использовать конструкцию типа:
```objectivec
NSNotification *broadCastMessage = [NSNotification notificationWithName:@"broadcastMessage" object:self];
NSNotificationCenter *notificationCenter = [NSNotificationCenter defaultCenter];
```
Как видим, мы создали объект типа `NSNotification`, в котором мы указали имя нашего оповещения: `“broadcastMessage”`, и, собственно, сообщили о нем через `NotificationCenter`.
Чтобы подписаться на событие в объекте который заинтересован в изменении стоит использовать следующую конструкцию:
```objectivec
NSNotificationCenter *notificationCenter = [NSNotificationCenter defaultCenter];
[notificationCenter addObserver:self selector:@selector(update:) name:@"broadcastMessage" object:nil];
```
Собственно, из кода все более-менее понятно: мы подписываемся на событие, и вызывается метод который задан в свойстве `selector`.

<a name="поведенческие-шаблоны"></a>
## Поведенческие шаблоны
Определяют взаимодействие между объектами, увеличивая таким образом его гибкость.

<a name="chain-of-responsibility"></a>
### Chain of responsibility
Responder (ответчик) – объект, который может реагировать на события и обрабатывать их.
`responderObject : UIResponder; // or NSResponder in MacOS`

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/responder_chain.png">

Цепочка ответственности позволяет вам передавать объекте по цепочке объектов-обработчиков, пока не будет найден необходимый объект обработчик.
```
First responder -> next responder -> …
```
Первый ответчик – ответчик, получивший события первым (например view).

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/responder_chain_in_action.png">

Когда использовать этот паттерн:

* У вас более чем один объект-обработчик.
* У вас есть несколько объектов обработчика, при этом вы не хотите специфицировать, который объект должен обрабатывать в даный момент времени.

Примеры:
```objectivec
[foo becomeFirstResponder];
[foo resignFirstResponder];
[foo respondsToSelector:@selector(methodName:)];
```

<a name="the-target-action-mechanism"></a>
### The Target-Action Mechanism

The target-action mechanism enables a control object, that is, an object such as a button, slider, or text field, to send a message to another object that can interpret the message and handle it as an application, specific instruction. The receiving object, or the target, is usually a custom controller object. The message, named an action message, is determined by a selector, a unique runtime identifier of a method.
In the AppKit framework, the cell object that a control owns typically encapsulates the target and action. When the user clicks or otherwise activates the control, the control extracts the information from its cell and sends the message. (A menu item also encapsulates target and action, and sends an action message when the user chooses it.) The target-action mechanism can work on the basis of a selector (and not a method signature) because the signature of an action method in AppKit by convention is always the same.
In UIKit, the target, action mechanism does not rely on cells. Instead, a control maps a target and action to one or more multitouch events that can occur on the control.

_Uses and Limitations_

When creating a Cocoa application, you can set a control’s action and target through the Interface Builder application. You thereby let the control initiate custom behavior without writing any code for the control itself. The action selector and target connection are archived in a nib file and are restored when the nib is unarchived. You can also change the target and action dynamically by sending the control or its cell `setTarget:` and `setAction:` messages.
A Cocoa application for OS X can use the target-action mechanism to instruct a custom controller object to transfer data from the user interface to a model object, or to display data in a model object. The Cocoa bindings technology obviates the need to use target-action for this purpose.

_Uses and Limitations_

You create or modify a view hierarchy whenever you add a view to another view, either programmatically or using Interface Builder. The AppKit framework automatically handles all the relationships associated with the view hierarchy.

<a name="command"></a>
### Command
The Command design pattern encapsulates a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations. The request object binds together one or more actions on a specific receiver. The Command pattern separates an object making a request from the objects that receive and execute that request.

_Invocation Objects_

An instance of the `NSInvocation` class encapsulates an Objective-C message. An invocation object contains a target object, method selector, and method parameters. You can dynamically change the target of the message dispatched by the invocation object as well as its parameters; once the invocation is executed, you can also obtain the return value from the object. With a single invocation object, you can repeatedly invoke a message with multiple variations in target and parameters.
The creation of an `NSInvocation` object requires an `NSMethodSignature` object, which is an object that encapsulates type information related to the parameters and return value of a method. An `NSMethodSignature` object, in turn, is created from a method selector. The implementation of `NSInvocation` also makes use of functions of the Objective-C runtime.

_Uses and Limitations_

`NSInvocation` objects are part of the programmatic interfaces of distributed objects, undo management, message forwarding, and timers. You can also use invocation objects in similar contexts where you need to decouple an object sending a message from the object that receives the message.
The distributed objects technology is for interprocess communication.

<a name="iterator"></a>
### Iterator

The Iterator design pattern provides a way to access the elements of an aggregate object (that is, a collection) sequentially without exposing its underlying representation. The Iterator pattern transfers the responsibility for accessing and traversing the elements of a collection from the collection itself to an iterator object. The Iterator defines an interface for accessing collection elements and keeps track of the current element. Different iterators can carry out different traversal policies.

__Enumerators__

The `NSEnumerator` class in the Foundation framework implements the Iterator pattern. The private, concrete subclass of the abstract `NSEnumerator` class returns enumerator objects that sequentially traverse collections of various types, arrays, sets, dictionaries (values and keys), returning objects in the collection to clients.
`NSDirectoryEnumerator` is a distantly related class. Instances of this class recursively enumerate the contents of a directory in the file system.

_Uses and Limitations_

The collection classes such as `NSArray`, `NSSet`, and `NSDictionary` include methods that return an enumerator appropriate to the type of collection. All enumerators work in the same manner. You send a `nextObject` message to the enumerator object in a loop that exits when `nil` is returned instead of the next object in the collection.
You can also use fast enumeration to access the elements of a collection; this language feature is described in Fast Enumeration.

<a name="mediator"></a>
### Mediator

The Mediator design pattern defines an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently. These objects can thus remain more reusable.
A "mediator object” in this pattern centralizes complex communication and control logic between objects in a system. These objects tell the mediator object when their state changes and, in turn, respond to requests from the mediator object.

<a name="memento"></a>
### Memento

The Memento pattern captures and externalizes an object’s internal state, without violating encapsulation, so that the object can be restored to this state later. The Memento pattern keeps the important state of a key object external from that object to maintain cohesion.

__Archiving__

Archiving converts the objects in a program, along with those objects’ properties (attributes and relationships) into an archive that can be stored in the file system or transmitted between processes or across a network. The archive captures the object graph of a program as an architecture-independent stream of bytes that preserves the identity of the objects and the relationships among them. Because an object’s type is stored along with its data, an object decoded from a stream of bytes is normally instantiated using the same class of the object that was originally encoded.

_Uses and Limitations_

Generally, you want to archive those objects in your program whose state you want to preserve. Model objects almost always fall into this category. You write an object to an archive by encoding it, and you read that object from an archive by decoding it. Encoding and decoding are operations that you perform using an `NSCoder` object, preferably using the keyed archiving technique (requiring you to invoke methods of the `NSKeyedArchiver` and `NSKeyedUnarchiver` classes). The object being encoded and decoded must conform to the `NSCoding` protocol; the methods of this protocol are invoked during archiving.

<a name="state"></a>
### State

With the state pattern, a state machine is implemented by implementing each individual state as a derived class of the state pattern interface, and implementing state transitions by invoking methods defined by the pattern's superclass. The state pattern can be interpreted as a strategy pattern which is able to switch the current strategy through invocations of methods defined in the pattern's interface. This pattern is used in computer programming to encapsulate varying behavior for the same object based on its internal state. This can be a cleaner way for an object to change its behavior at runtime without resorting to large monolithic conditional statements and thus improve maintainability.

<a name="анти-паттерны-в-объектно-ориентированном-программировании"></a>
## Анти-паттерны в объектно-ориентированном программировании
__Базовый класс-утилита (BaseBean):__ Наследование функциональности из класса-утилиты вместо делегирования к нему

__Вызов предка (CallSuper):__ Для реализации прикладной функциональности методу класса-потомка требуется в обязательном порядке вызывать те же методы класса-предка

__Ошибка пустого подкласса (Empty subclass failure):__ Создание класса (в Perl), который не проходит «проверку пустоты подкласса» («Empty Subclass Test») из-за различного поведения по сравнению с классом, который наследуется от него без изменений

__Божественный объект (God object):__ Концентрация слишком большого количества функций в одной части системы (классе)

__Объектная клоака (Object cesspool):__ Переиспользование объектов, находящихся в непригодном для переиспользования состоянии

__Полтергейст (Poltergeist):__ Объекты, чьё единственное предназначение — передавать информацию другим объектам

__Проблема йо-йо (Yo-yo problem):__ Чрезмерная размытость сильно связанного кода (например, выполняемого по порядку) по иерархии классов

__Одиночество (Singletonitis):__ Неуместное использование паттерна одиночка

__Приватизация (Privatisation):__ Сокрытие функциональности в приватной секции (private), что затрудняет его расширение в классах-потомках

__Френд-зона (Friend zone):__ Неуместное использование дружественных классов и дружественных функций в языке C++

<a name="какая-разница-между-использованием-делагатов-и-нотификейшенов"></a>
## Какая разница между использованием делагатов и нотификейшенов?
Уведомление инкапсулирует информацию о событиях, таких как получения фокуса окном или закрытие сетевого соединения. Объекты, которым необходимо знать об этих событиях, регистрируются в центре уведомлений, и при возникновении зарегистрированного события, центр уведомлений информирует все зарегистрированные объекты об событии.

Делегат может модифицировать операцию или отказаться от нее, нотификейшн – прямой приказ.

Основные правила:

* Центры оповещений не владеют своими наблюдателями. Если объект является наблюдателем, он обычно удаляется из центра оповещений в своем методе `dealloc`:
```objectivec
- (void)dealloc {
	[[NSNotificationCenter defaultCenter] removeObserver:self];
}
```
* Объекты не владеют своими делегатами и источниками данных. Если вы создаете объект, который является делегатом или источником данных, он должен «попрощаться» в своем методе `dealloc`:
```objectivec
- (void)dealloc {
	[windowThatBossesMeAround setDelegate:nil];
	[tableViewThatBegsForData setDataSource:nil];
}
```
* Объекты не владеют своими приемниками. Если вы создаете объект, который является приемником, он должен обнулить указатель на приемник в своем методе `dealloc`:
```objectivec
- (void)dealloc {
	[buttonThatKeepsSendingMeMessages setTarget:nil];
}
```

__Делегат__

_Плюсы_

* Very strict syntax. All events to be heard are clearly defined in the delegate protocol.
* Compile time Warnings / Errors if a method is not implemented as it should be by a delegate.
* Protocol defined within the scope of the controller only.
* Very traceable, and easy to identify flow of control within an application.
* Ability to have multiple protocols defined one controller, each with different delegates.
* No third party object required to maintain / monitor the communication process.
* Ability to receive a returned value from a called protocol method. This means that a delegate can help provide information back to a controller.
* Распределение кода,  переиспользование => слабосвязанные объекты. Мой объект ничего не знает о делегате, но отправляет ему сообщение.

_Минусы_

* Many lines of code required to define:

(1) the protocol definition

(2) the delegate property in the controller

(3) the implementation of the delegate method definitions within the delegate itself.

* Need to be careful to correctly set delegates to nil on object deallocation, failure to do so can cause memory crashes by calling methods on deallocated objects.
* Although possible, it can be difficult and the pattern does not really lend itself to have multiple delegates of the same protocol in a controller (telling multiple objects about the same event)

__Нотификейшн__

_Плюсы_

* Easy to implement, with not many lines of code.
* Can easily have multiple objects reacting to the same notification being posted.
* Controller can pass in a context (dictionary) object with custom information (userInfo) related to the notification being posted.

_Минусы_

* No compile time to checks to ensure that notifications are correctly handled by observers.
* Required to unregister with the notification center if your previously registered object is deallocated.
* Not very traceable. Attempting to debug issues related to application flow and control can be very difficult.
* Third party object required to manage the link between controllers and observer objects.
* Notification Names, and UserInfo dictionary keys need to be known by both the observers and the controllers. If these are not defined in a common place, they can very easily become out of sync.
* No ability for the controller to get any information back from an observer after a notification is posted.

__Наблюдение__

_Плюсы_

* Can provide an easy way to sync information between two objects. For example, a model and a view.
* Allows us to respond to state changes inside objects that we did not create, and don’t have access to alter the implementations of (SKD objects).
* Can provide us with the new value and previous value of the property we are observing.
* Can use key paths to observe properties, thus nested objects can be observed.
* Complete abstraction of the object being observed, as it does not need any extra code to allow it to be observed.

_Минусы_

* The properties we wish to observe, must be defined using strings. Thus no compile time warnings or checking occurs.
* Refactoring of properties can leave our observation code no longer working.
* Complex “IF” statements required if an object is observing multiple values. This is because all observation code is directed through a single method.
* Need to remove the observer when it is deallocated.
