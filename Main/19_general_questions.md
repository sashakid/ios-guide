- [Общие вопросы](#общие-вопросы)
	- [Inout parameters, pass by value, pass by reference](#inout-parameters)
	- [Поверхностное и глубокое копирование](#поверхностное-и-глубокое-копирование)
	- [Отличие while от for](#while-for)
	- [Протокол? Что такое абстрактный класс? Чем абстрактный класс отличается от интерфейса?](#протокол-абстрактный-класс-интерфейс)
	- [Какие существуют root классы в iOS? Для чего нужны root классы?](#root-классы)
	- [Чем категория отличается от расширения?](#чем-категория-отличается-от-расширения)
	- [Можно ли добавить ivar в категорию?](#можно-ли-добавить-ivar-в-категорию)
	- [Когда лучше использовать категорию, а когда наследование?](#категория-наследование)
	- [Формальные и неформальные протоколы](#формальные-и-неформальные-протоколы)
	- [Есть ли приватные или защищенные методы в Objective-C? А в Swift?](#приватные-методы)
	- [Что такое назначеный инициализатор, напишите любой элементарный инициализатор, почему он так выглядит?](#назначеный-инициализатор)
	- [Как работают push нотификации?](#push-notifications)
	- [Memory warning](#memory-warning)
	- [Как реализовать кеш?](#cash)
	- [Какой контент лучше хранить в Documents, а какой в Cache?](#как-лучше-хранить)
	- [Как из строки вытащить подстроку?](#как-из-строки-вытащить-подстроку)
	- [NSCoding, archiving?](#nscoding,-archiving)
	- [Как работает UITableView?](#как-работает-uitableview)
	- [Константы, typedef, enum, #define](#константы-typedef-enum-define)
	- [Что такое awakeFromNib?](#чтo-такое-awakefromnib)
	- [Что происходит когда мы пытаемся вызвать метод у nil указателя? Разница между nil и Nil](#nil-указателя-разница)
	- [Что такое неформальный протокол?](#неформальный-протокол)
	- [В чем разница между NSString и char? Что значит приставка NS в общем?](#nsstring-char)
	- [Опишите иерархию классов от UIButton до NSObject](#uibutton-to-nsobject)
	- [NSArray arrayWithObjects: a, b, c, nil; зачем nil вконце?](#nsarray-зачем-nil-вконце)
	- [Как работает NSNotificationCenter? В каком потоке приходит оповещение?](#nsnotificationcenter)
	- [Что такое volatile?](#volatile)
	- [Что такое inline функция?](#inline)
	- [Добавление объектов в коллекции](#objects-in-collections)
	- [Как использовать свой класс как ключ?](#class-as-key)
	- [Как работает KVC?](#kvc)
	- [Как работает KVO и какие могут быть с ним проблемы?](#kvo)
	- [Как изменятся свойства, если применить поворот на 45º?](#rotate-view)
	- [Отличие view от layer?](#view-layer-difference)
	- [Как передвинуть все subviews?](#moving-subviews)
	- [Swift optionals, Objective-C new modifiers (`nullable`, etc.). что это и как реализовано?](#optionals-swift-objc)
	- [Можно ли скачать что-нибудь, пока приложение выполняется в фоне?](#download-in-background)
	- [Как реализовать хеш-таблицу? Как избежать коллизий?](#custom-hash-table)
	- [Что такое реактивное программирование?](#reactive-programming)
	- [Что такое функциональное программирование? Какие фичи есть для этого в Swift / Objective-C?](#functional-programming)
	- [Можно ли создать свой root класс?](#custom-root-class)
	- [Как происходит выравнивание указателей на объекты в Objective-C?](#data-structure-alignment)
	- [Что такое union?](#union)

<a name="общие-вопросы"></a>
# Общие вопросы
<a name="inout-parameters"></a>
## Inout parameters, pass by value, pass by reference
__Explanation 1__

When you pass a variable to a function, you are passing a copy of its value to the function instead of your variable itself. If you modified the value of the variable in your function and you printed it when the function is done executing, you'd see the variable still has the original value you originally gave it.

An in-out parameter takes "the variable itself", instead of a copy, and as such you can modify it. In-out parameters are akin to references in C++.

Function parameters are always passed by value. Pass-by-reference is simulated in C by explicitly passing pointer values. C program source text is free-format, using the semicolon as a statement terminator and curly braces for grouping blocks of statements.

Objective-C only support passing parameters by value. Objective-C is a strict superset of C which means that everything C does, ObjC does it too. By having a quick look at Wikipedia, you can see that function parameters are always passed by value. Objective-C is no different. What's happening here is that whenever we are passing an object to a function (for example, `UILabel *label`), we pass the value contained at the pointer's address.

Whatever you do, it will always be the value of what you are passing.

If you want to pass the value of the reference you would have to pass it a `**object` (Like often seen when passing `NSError`).

This is the same thing with scalars, they are passed by value, hence you can modify the value of the variable you received in your method and that won't change the value of the original variable that you passed to the function.
Here's an example to ease the understanding:
```objectivec
- (void)parentFunction {
  int i = 0;
  [self modifyValueOfPassedArgument:i];
  //i == 0 still!
}

- (void)modifyValueOfPassedArgument:(NSInteger)j {
  //j == 0! but j is a copied variable. It is _NOT_ i
  j = 23;
  //j now == 23, but this hasn't changed the value of i.
}
```
If you wanted to be able to modify `i`, you would have to pass the value of the reference by doing the following:
```objectivec
- (void)parentFunction {
  int i = 0; //Stack allocated. Kept it that way for sake of simplicity
  [self modifyValueOfPassedReference:&i];
  //i == 23!
}

- (void)modifyValueOfPassedReference:(NSInteger *)j {
  //j == 0, and this points to i! We can modify i from here.
  *j = 23;
  //j now == 23, and i also == 23!
}
```
__Explanation 2__

Say I want to share a web page with you.
If I tell you the URL, I'm passing by reference. You can use that URL to see the same web page I can see. If that page is changed, we both see the changes. If you delete the URL, all you're doing is destroying your reference to that page - you're not deleting the actual page itself.
If I print out the page and give you the printout, I'm passing by value. Your page is a disconnected copy of the original. You won't see any subsequent changes, and any changes that you make (e.g. scribbling on your printout) will not show up on the original page. If you destroy the printout, you have actually destroyed your copy of the object - but the original web page remains intact.
```c++
// passes a pointer (called reference in java) to an integer
void call_by_value(int *p) { // :1
  p = NULL;
}

// passes an integer
void call_by_value(int p) { // :2
  p = 42;
}

// passes an integer by reference
void call_by_reference(int & p) { // :3
  p = 42;
}

// this is the java style of passing references. NULL is called "null" there.
void call_by_value_special(int *p) { // :4
  *p = 10; // changes what p points to ("what p references" in java)
  // only changes the value of the parameter, but *not* of
  // the argument passed by the caller. thus it's pass-by-value:
  p = NULL;
}

int main() {
  int value = 10;
  int * pointer = &value;

  call_by_value(pointer); // :1
  assert(pointer == &value); // pointer was copied

  call_by_value(value); // :2
  assert(value == 10); // value was copied

  call_by_reference(value); // :3
  assert(value == 42); // value was passed by reference

  call_by_value_special(pointer); // :4
  // pointer was copied but what pointer references was changed.
  assert(value == 10 && pointer == &value);
}
```

__Explanation 3__

```objectivec
- (void)test {
  NSString *stringVar = @"UPPER CASE STRING";
  [self changeString:stringVar];
  NSLog(@"value after changed : %@", stringVar);
}

- (void)changeString:(NSString *)string {
  string = [string lowercaseString];
}
```
I thought the output should be `upper case string`. But it comes out to be `UPPER CASE STRING`.

The `[string lowercaseString]` call creates a new `NSString` object that you assign to the local variable string. This does not change the value of `stringVar` outside the `changeString` function. The pointer itself is passed by value.

One way to do what you want, is to pass a pointer to a pointer:
```objectivec
- (void)test {
  NSString *stringVar = @"UPPER CASE STRING";
  [self changeString:&stringVar];
  NSLog(@"value after changed: %@", stringVar);
}

- (void)changeString:(NSString **)string {
  *string = [*string lowercaseString];
}
```

<a name="поверхностное-и-глубокое-копирование"></a>
## Поверхностное и глубокое копирование
_Поверхностное копирование_ — это просто создание нового указателя на те же самые байты в куче. То есть, в результате мы можем получить два объекта, которые указывают на одно и то же значение.

_Глубокое копирование:_

```objectivec
- (id)copyWithZone:(NSZone *)zone;

@implementation Person
- (id)copyWithZone:(NSZone *)zone {
  Person *copy = [[self class] allocWithZone:zone];
  copy.name = self.name;
  copy.age = self.age;
  copy.surname = self.surname;
  return copy;
}
@end
```
Метод объекта класса `NSArray` с управлением логикой копирования:
```objectivec
- (instancetype)initWithArray:(NSArray<ObjectType> *)array copyItems:(BOOL)flag;
```
If `YES`, each object in array receives a `copyWithZone:` message to create a copy of the object — objects must conform to the `NSCopying` protocol. In a managed memory environment, this is instead of the retain message the object would otherwise receive. The object copy is then added to the returned array.

If `NO`, then in a managed memory environment each object in array simply receives a `retain` message when it is added to the returned array.

<a name="while-for"></a>
## Отличие while от for
Единственное отличие `while` от `for` в том, что в нем проверяется условие выполнения: ни объявить, ни изменить переменную в конструкции `while` нельзя. Поэтому чтобы выйти из цикла нужно изменять переменные внутри самого цикла так, чтобы условие стало ложным.

<a name="протокол-абстрактный-класс-интерфейс"></a>
## Протокол? Что такое абстрактный класс? Чем абстрактный класс отличается от интерфейса?
Базовый класс, который не предполагает создания экземпляров. Абстрактные классы реализуют на практике один из принципов ООП — полиморфизм. Абстрактный класс может содержать (и не содержать) абстрактные методы и свойства. Абстрактный метод не реализуется для класса, в котором объявлен, однако должен быть реализован для его неабстрактных потомков. Абстрактные классы представляют собой наиболее общие абстракции, то есть имеющие наибольший объём и наименьшее содержание.
В Objective-C есть родительский класс `NSObject`. В языке программирования он как точка в геометрии. Это идеальный класс: в нём нет ничего лишнего, он ничего конкретного делает, но из него можно создать всё что угодно.

Пример: «Примус» — может быть наследником абстрактного класса «Нагревательный прибор»

Главное отличие класса от интерфейса — в том, что класс состоит из интерфейса и реализации.

Язык Objective-C содержит полноценную поддержку протоколов (это аналог интерфейса в Java и абстрактного класса в C++, который также иногда принято называть интерфейсом). Протокол представляет собой просто список описаний методов. Объект реализует протокол, если он содержит реализации всех методов, описанных в протоколе. Абстрактные классы могут содержать в себе реализацию некоторых методов, интерфейсы содержат только прототипы.
Однажды кто-то сказал: «То, что ты есть, и то, что ты делаешь – не одно и то же». Это утверждение справедливо и для объектов: класс объекта не всегда совпадает с его ролью в работающей системе. Например, объект может быть экземпляром `NSМutаblеАrrау`, тогда как в приложении он может обеспечивать управление очередью заданий печати. Действительно хорошо написанный класс имеет более общую природу, которая не ограничивается его ролью в одном конкретном приложении. Это позволяет по разному использовать экземпляры данного класса (полиморфизм). Мы уже говорили о том, как определить класс. Возможно ли определить роль? В определенной степени для определения роли можно использовать конструкцию `@protocol`.

<a name="root-классы"></a>
## Какие существуют root классы в iOS? Для чего нужны root классы?
__Objective-C__

`NSObject` and `NSProxy`

A root class inherits from no other class and defines an interface and behavior common to all objects in the hierarchy below it. All objects in that hierarchy ultimately inherit from the root class. A root class is sometimes referred to as a base class. The root class of all Objective-C classes is `NSObject`, which is part of the Foundation framework. All objects in a Cocoa or Cocoa Touch application ultimately inherit from `NSObject`. This class is the primary access point whereby other classes interact with the Objective-C runtime. It also declares the fundamental object interface and implements basic object behavior, including introspection, memory management, and method invocation. Cocoa and Cocoa Touch objects derive the ability to behave as objects in large part from the root class. The Foundation framework defines another root class, `NSProxy`, but this class is rarely used in Cocoa applications and never in Cocoa Touch applications.

__Swift__

В свифте таких классов нет. Swift classes do not inherit from a universal base class. Classes you define without specifying a superclass automatically become base classes for you to build upon.

<a name="чем-категория-отличается-от-расширения"></a>
## Чем категория отличается от расширения?
Категория позволяет расширить функционал класса. При этом не требуется исходников класса и добавленные методы автоматически становятся доступными всем классам, унаследованным от изменяемого. Категория имеет свое имя, список методов и имя класса, который она расширяет.

__Описание категории имеет следующий вид:__

```objectivec
#import "ClassName.h"

@interface ClassName (CategoryName)
объявление методов
@end

//Реализация категории выглядит следующим образом:
#import "CategoryName.h"

@implementation ClassName (CategoryName)
реализация методов
@end
```
__Что делают категории?__

1. Позволяют разбить определение класса по нескольким файлам. В идеале класс должен выполнять одну конкретную роль, но иногда это не так, например в случае реализации фасада и некоторых других шаблонов. В этом случае удобно описать его в нескольких файлах
2. Позволяют действительно элегантно добавить отсутствующую функциональность к существующему классу
3. Создают опережающие ссылки для закрытых методов
4. Позволяют добавление неформального протокола

__Подводные камни__

* Невозможность добавления переменных
* Возможная коллизия имен с самим классом, поэтому необходимо использовать оригинальные префиксы в наименовании своих методов.
* Невозможно вызвать `[super method];` из категории

__Расширение__
Одна из разновидностей категорий. Они по сути являются категориями с тем отличием, что интерфейс расширения описывается в имплементации основного класса до `@implementation`, а реализация прописывается в основном в любом месте имплементации класса и не пишется название категории. В отличии от категорий, расширения используются для собственных классов для сокрытия части реализации.
A class extension bears some similarity to a category, but it can only be added to a class for which you have the source code at compile time (the class is compiled at the same time as the class extension).
```objectivec
@interface SomeClass ()
- (void) anAdditionalMethod;
@end
```

<a name="можно-ли-добавить-ivar-в-категорию"></a>
## Можно ли добавить ivar в категорию?
Директива `@interface` для категорий не может добавлять переменных экземпляра. Однако, она может определять, что категория поддерживает дополнительные протоколы.

<a name="категория-наследование"></a>
## Когда лучше использовать категорию, а когда наследование?
В отличие от наследования, категории не могут добавлять новые переменные в класс. Однако, вы можете переопределять существующие методы в классе, но должны быть очень осторожны. Запомните, что все изменения сделанные в классе через категории повлияют на все экземпляры данного объекта в программе.

<a name="формальные-и-неформальные-протоколы"></a>
## Формальные и неформальные протоколы
Цели для которых используются протоколы:
* Ожидание, что класс поддерживающий протокол выполнит описанные в протоколе функции
* Поддержка протокола на уровне объекта, не раскрывая методы и реализацию самого класса (в противоположность наследованию)
* Ввиду отсутствия множественного наследования - объединить общие черты нескольких классов

__Формальные протоколы__

Объявление формального протокола гарантирует, что все методы объявленные протоколом будут реализованы классом

__Неформальные протоколы__

Добавление категории к классу `NSObject` называется созданием неформального протокола. При работе с неформальными протоколами мы реализуем только те методы, которые хотим. Узнать поддержевает ли класс какой либо метод можно с помощью селекторов:
```objectivec
First *f = [[First alloc] init];
if ([f respondsToSelector:@selector(setName:)]) {
  NSLog (@"Метод поддерживается");
}
```

__Подводные камни__

* `[NSObject self]` may return a class, or an object
* `[NSObject super]` is undefined

<a name="приватные-методы"></a>
## Есть ли приватные или защищенные методы в Objective-C? А в Swift?

_Objective-C_

Нет. Нужно использовать расширение.
Для имитации private методов с помощью расширения, нужно в .m файле, перед `@implementation` добавить безымянную категорию. Для класса `Something` ее определение будет выглядеть как `@interface Something () ... @end`. Стоит обратить особое внимание на пустые скобки — они показывают, что мы определяем именно безымянную категорию. После этого, мы можем добавлять в категорию методы, которые будут для нас считаться private. За счет того, что категория безымянная, имплементация данных методов может находиться рядом с имплементацией основных методов в разделе `@implementation .. @end` и нет необходимости создавать отдельные разделы для имплементации категорий. А за счет того, что она находится в .m файле, которые никто не подключает через `#import`, видимость методов для автодополнения ограничена текущим файлом. Конечно, послать объекту это сообщение извне все равно возможно, но от случайного вызова вы точно застрахованы.

_Swift_

* __Open__ access and __public__ access enable entities to be used within any source file from their defining module, and also in a source file from another module that imports the defining module.

* __Internal__ access enables entities to be used within any source file from their defining module, but not in any source file outside of that module.

* __File-private__ access restricts the use of an entity to its own defining source file.

* __Private__ access restricts the use of an entity to the enclosing declaration, and to extensions of that declaration that are in the same file.

Open access is the highest (least restrictive) access level and private access is the lowest (most restrictive) access level.

Open access applies only to classes and class members, and it differs from public access as follows:

* Classes with public access, or any more restrictive access level, can be subclassed only within the module where they’re defined.
* Class members with public access, or any more restrictive access level, can be overridden by subclasses only within the module where they’re defined.
* Open classes can be subclassed within the module where they’re defined, and within any module that imports the module where they’re defined.
* Open class members can be overridden by subclasses within the module where they’re defined, and within any module that imports the module where they’re defined.

<a name="назначеный-инициализатор"></a>
## Что такое назначеный инициализатор, напишите любой элементарный инициализатор, почему он так выглядит?
Класс содержит только один основной инициализатор. Если класс содержит другие инициализаторы, то их реализация должна вызывать (прямо или косвенно) основной инициализатор.
* Если класс имеет несколько инициализаторов, только один из них должен выполнять реальную работу. Этот метод называется основным инцициалuзатором. Все остальные инициализаторы должны вызывать основной инициализатор (прямо или косвенно).
* Основной инициализатор вызывает основной инициализатор суперкласса перед инициализацией своих переменных экземпляров `if (self  = [super...])`
* Если имя основного инициализатора вашего класса отличается от имени основного инициализатора его супер класса, вы должны переопределить основной инициализатор суперкласса, чтобы он вызывал новый основной инициализатор.
* Если класс содержит несколько инициализаторов, четко укажите в заголовочном файле, какой из них является основным.
Установившейся практикой в таком случае является выделение среди всех init-методов одного, называемого designated initializer. Все остальные init-методы должны вызывать его и только он вызывает унаследованный init-метод.
```objectivec
// designated initializer
- initWithName:(const char *)theName {  
  // call inherited method
  [super init];                       
  name = strdup(theName);
}

- init {
  return [self initWithName:@"name"];
}
```
Swift provides a __default initializer__ for any structure or class that provides default values for all of its properties and does not provide at least one initializer itself. The default initializer simply creates a new instance with all of its properties set to their default values.

__Designated initializers__ are the primary initializers for a class. A designated initializer fully initializes all properties introduced by that class and calls an appropriate superclass initializer to continue the initialization process up the superclass chain. Classes tend to have very few designated initializers, and it is quite common for a class to have only one. Designated initializers are “funnel” points through which initialization takes place, and through which the initialization process continues up the superclass chain.

__Convenience initializers__ are secondary, supporting initializers for a class. You can define a convenience initializer to call a designated initializer from the same class as the convenience initializer with some of the designated initializer’s parameters set to default values. You can also define a convenience initializer to create an instance of that class for a specific use case or input value type. You do not have to provide convenience initializers if your class does not require them.

Designated initializers for classes are written in the same way as simple initializers for value types:
```swift
init(<parameters>) {
    <statements>
}
```

Convenience initializers are written in the same style, but with the convenience modifier placed before the init keyword, separated by a space:
```swift
convenience init(parameters) {
    statements
}
```
__Rule 1__

A designated initializer must call a designated initializer from its immediate superclass.

__Rule 2__

A convenience initializer must call another initializer from the same class.

__Rule 3__

A convenience initializer must ultimately call a designated initializer.

A simple way to remember this is:
* Designated initializers must always delegate up.
* Convenience initializers must always delegate across.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/initializers.png">

Unlike subclasses in Objective-C, Swift subclasses do not inherit their superclass initializers by default. Swift’s approach prevents a situation in which a simple initializer from a superclass is inherited by a more specialized subclass and is used to create a new instance of the subclass that is not fully or correctly initialized.

__Rule 1__

If your subclass doesn’t define any designated initializers, it automatically inherits all of its superclass designated initializers.

__Rule 2__

If your subclass provides an implementation of all of its superclass designated initializers—either by inheriting them as per rule 1, or by providing a custom implementation as part of its definition—then it automatically inherits all of the superclass convenience initializers.

__Failable Initializers__

It is sometimes useful to define a class, structure, or enumeration for which initialization can fail. This failure might be triggered by invalid initialization parameter values, the absence of a required external resource, or some other condition that prevents initialization from succeeding.
```swift
class Product {
	let name: String
	init?(name: String) {
		if name.isEmpty {
			return nil
		}
		self.name = name
	}
}
```

<a name="push-notifications"></a>
## Как работают push нотификации?
iOS-приложения не могут долгое время находиться в фоновом режиме. В целях сохранения заряда батареи приложениям, работающим в фоне, разрешено выполнять ограниченный набор действий. Вместо того, чтобы беспрерывно проверять события или производить какие-либо действия в фоновом режиме, вы можете создать серверную сторону приложения, которая будет выполнять эти действия. А когда наступит интересующее событие, серверная сторона сможет отправить приложению push-уведомление. Абсолютно любое push-уведомление может выполнять следующие три действия:
* Показать короткое текстовое сообщение.
* Воспроизвести короткий звуковой сигнал.
* Установить число на бейдже иконки приложения.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/apns.png">

APNS cервер – Apple Push Notification Server.

<a name="memory-warning"></a>
## Memory warning
Your app never calls this method directly. Instead, __this method is called when the system determines that the amount of available memory is low__. You can override this method to release any additional memory used by your view controller. If you do, your implementation of this method must call the super implementation at some point.
```objectivec
- (void)applicationDidReceiveMemoryWarning:(UIApplication *)application {
  /*
  Free up as much memory as possible by purging cached data objects that can be recreated (or reloaded from disk) later.
  */
}

- (void)didReceiveMemoryWarning {
  // Releases the view if it doesn't have a superview.
  [super didReceiveMemoryWarning];
  // Release any cached data, images, etc that aren't in use.
}
```
Если на устройстве заканчивается память в центр уведомлений приходит сообщение `UIApplicationDidReceiveMemoryWarningNotification`, наш обьект может об этом узнать через уведомления и что-либо сделать, например почистить кеш или сохранить данные.

<a name="cash"></a>
## Как реализовать кеш?
Кеширование уменьшает количество необходимых обращений к сети, улучшает впечатление от работы с программой во время полного отсутствия интернета или проблем с сетевым соединением. После загрузки ответа сервера, его копия сохраняется в локальном кеше. В следующий раз при посылке такого же запроса, ответ будет возвращен мгновенно, без обращения к сети. `NSURLCache` прозрачным для пользователя образом вернет закешированные данные. Для использования `NSURLCache` нужно установить значение синглтона `sharedURLCache`. Это можно сделать в методе `application:didFinishLaunchingWithOptions`:
```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  NSURLCache *URLCache = [[NSURLCache alloc] initWithMemoryCapacity:4 * 1024 * 1024 diskCapacity:20 * 1024 * 1024 diskPath:nil];
  [NSURLCache setSharedURLCache:URLCache];
}

NSArray *paths = NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES);
NSString *cachePath = [paths objectAtIndex:0];
NSURL *fileURL = [NSURL fileURLWithPath:[cachePath stringByAppendingPathComponent:@"Matsedl.pdf"]];
```
<a name="как-лучше-хранить"></a>
## Какой контент лучше хранить в Documents, а какой в Cache?
Кеш - это специальный буфер (контейнер), содержащий информацию. Эта информация может быть запрошена с наибольшей вероятностью. Соответственно, доступ к этому буферу должен быть очень быстрым, он должен быть быстрее чем доступ к сети или к данным на жестком диске. В операционной системе iOS присутствует функция кэширования, но прямого доступа к данным в кэше нету. Для получения доступа следует использовать класс `NSCache`.
* Only documents and other data that is user-generated, or that cannot otherwise be recreated by your application, should be stored in the `<Application_Home>/Documents` directory and will be automatically backed up by iCloud.
* Data that can be downloaded again or regenerated should be stored in the `<Application_Home>/Library/Caches` directory. Examples of files you should put in the Caches directory include database cache files and downloadable content, such as that used by magazine, newspaper, and map applications.
* Data that is used only temporarily should be stored in the `<Application_Home>/tmp` directory. Although these files are not backed up to iCloud, remember to delete those files when you are done with them so that they do not continue to consume space on the user’s device.
* Use the "do not back up" attribute for specifying files that should remain on device, even in low storage situations. Use this attribute with data that can be recreated but needs to persist even in low storage situations for proper functioning of your app or because customers expect it to be available during offline use. This attribute works on marked files regardless of what directory they are in, including the Documents directory. These files will not be purged and will not be included in the user's iCloud or iTunes backup. Because these files do use on-device storage space, your app is responsible for monitoring and purging these files periodically.

<a name="как-из-строки-вытащить-подстроку"></a>
## Как из строки вытащить подстроку?
С помощью методов: `substringToIndex:`, `substringFromIndex:` и `substringWithRange:`. Можно также разделить строку на подстроки (основано на разделителе строки) методом `componentsSeparatedByString:`
```objectivec
NSString *source = @"0123456789";
NSString *firstFour = [source substringToIndex:4];
// firstFour содержит: @"0123"
NSString *allButFirstThree = [source substringFromIndex:3];
// allButFirstThree содержит: @"3456789"
NSRange twoToSixRange = NSMakeRange(2, 4);
NSString *twoToSix = [source substringWithRange:twoToSixRange];
// twoToSix содержит: @"2345"
NSArray *split = [source componentsSeparatedByString:@"45"];
// массив split содержит: { @"0123", @"6789" }
```

<a name="nscoding,-archiving"></a>
## NSCoding, archiving?
`NSCoder` — это абстрактный класс который преобразует поток данных. Используется для архивации и разархивации объектов.
Протокол `<NSCoding>` позволяет реализовать архивирование или разархивирование данных. Например, у нас есть обьект мы его можем сохранить, а при следующей загрузке приложения подгрузить обратно. Часто программе требуется хранить состояние объектов в файле для дальнейшего их полного либо частичного восстановления, а также работы с ними. Такой процесс называют сериализацией. Многие современные языки и фреймворки предоставляют для этого вспомогательные средства. Рассмотрим, что нам предоставляет Cocoa Framework для Objective-C.
Сериализованный объект – объект, преобразованный в поток байтов для сохранения в файле или передачи по сети. `NS(M)Array`, `NS(M)Dictionary`, `NS(M)Data`, `NS(M)String`, `NSNumber`, `NSDate`. Сохранить состояние объекта в Cocoa Framework можно двумя способами при помощи:

* архивации (archivation)
* сериализации (serialization)

Каждый из них имеет свои области применения. Так, при помощи сериализации нельзя сохранить объект пользовательского класса. Протокол `<NSCoding>` объявляет два метода, которые должен реализовать класс, так что экземпляры этого класса могут быть закодированы и декодированы. Эта возможность обеспечивает основу для архивирования (где объекты и другие структуры хранятся на диске) и распространения (где объекты копируются в разные адресные пространства).

`encodeWithCoder:` кодирует приемник с помощью данного архиватора. (обязательный)
```objectivec
- (void)encodeWithCoder:(NSCoder *)encoder
```
`initWithCoder:` возвращает объект инициализированный из данных в данном разархиваторе. (обязательный)
```objectivec
- (id)initWithCoder:(NSCoder *)decoder
```
_Создание архивов_

Самый простой способ создать архив - использовать метод `archiveRootObject:toFile:` архиватора. Этот метод класса создает временный экземпляр архиватора и записывает объект в файл.
```objectivec
MapView *myMapView;
result = [NSKeyedArchiver archiveRootObject:myMapView toFile:@"/tmp/MapArchive"];
```
_Чтение архивов_

Для чтения архивов, также как и для записи (см. выше), можно использовать 2 метода.
Первый - простой и пригодный для большинства случаев - с использованием метода класса:
```objectivec
MapView *myMapView;
myMapView = [NSKeyedUnarchiver unarchiveObjectWithFile:@"/tmp/MapArchive"];
```
Второй метод предполагает создание экземпляра объекта `NSKeyedUnarchiver`.

<a name="как-работает-uitableview"></a>
## Как работает UITableView?
```
UITableView : UIScrollView <NSCoding> : UIView <NSCoding>

UITableViewController : UIViewController <UITableViewDelegate, UITableViewDataSource> : UIResponder <NSCoding, UIAppearanceContainer> : NSObject
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tableview1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tableview2.png">

Ячейки table view, которые больше не отображаются на экране, не выкидываются. Их можно адаптировать под повторное использование, указав идентификатор в процессе инициализации. Когда ячейка table view, отмеченная для повторного использования, пропадает с экрана, table view помещает ее в очередь для повторного использования в дальнейшем. Когда объект table view dataSource запрашивает у table view новую ячейку и указывает идентификатор, table view сначала проверяет очередь ячеек для повторного использования на предмет наличия необходимой ячейки. Если ячейка table view не была обнаружена, то table view создает новую, передавая ее затем объекту dataSource.
```objectivec
UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:CellIdentifier forIndexPath:indexPath];
```
<a name="константы-typedef-enum-define"></a>
## Константы, typedef, enum, #define
`typedef` используется для объявления нового типа данных – это команда компилятору и предполагает символьный тип данных.

`#define` – команда препроцессору и может содержать числовые значения.

Переменные, значения которых не изменяются (как, например, математическая постоянная `pi`), Такие данные называются константами. В Objective-C существует два распространенных способа определения констант:
* `#define`
* глобальные переменные

```objectivec
#define M_PI 3.14159265358979323846264338327950288
```
Директива `#define` приказывает препропессору: «Каждый раз, когда ты встречаешь Х, замени его на У еще до того, как компилятор увидит код».

Вместо `#define` программисты Objective-C обычно используют для хранения постоянных значений глобальные переменные. Например:
```objectivec
extern NSString const *NSLocaleCurrencyCode;
```
Ключевое слово `соnst` говорит о том, что указатель не будет изменяться в течение всего жизненного цикла программы. Ключевое слово extern означает: «Я гарантирую, что это существует, но оно определяется в другом файле». И действительно, файл NSLocale.m содержит строку следующего вида:
```objectivec
NSString const *NSLocaleCurrencyCode = @"currency";
```
__`#define` и глобальные переменные__

Если для определения констант можно использовать как `#define`, так и глобальные переменные (включая `enum`), почему программисты Objective-C обычно используют глобальные переменные? Иногда глобальные переменные повышают быстродействие программы. Например, при работе с глобальной переменной для сравнения строк можно использовать `==` вместо `isEqual:` (а математическая операция выполняется быстрее отправки сообщения). Кроме того, с глобальными переменными удобнее работать в отладчике. Используйте для констант глобальные переменные и `enum`, а не `#define`.

__`enum`__

Часто в программе требуется определить набор констант. Допустим, вы программируете блендер с пятью рабочими режимами. Ваш класс `Blender` содержит метод `setSpeed:`. Было бы хорошо, если бы тип аргумента указывал, что допустимыми являются только пять конкретных значений. Для этого в программе определяется перечисляемый тип, или перечисление:
```objectivec
enum BlenderSpeed {
  BlenderSpeedStir = 1,
  BlenderSpeedChop = 2,
  BlenderSpeedLiquify = 5,
  BlenderSpeedPulse = 9,
  BlenderSpeedIceCrush = 15
};

@interface Blender : NSObject {
  //пять допустимых значений скорости
  enum BlenderSpeed speed;
}

//setSpeed: получает одно из пяти допустимых значений
- (void)setSpeed:(enum BlenderSpeed)x;

@end
```
Чтобы разработчикам не приходилось постоянно вводить `enum BlenderSpeed`, они часто определяют сокращенную запись с использованием
```objectivec
typedef enum {
  BlenderSpeedStir = 1,
  BlenderSpeedChop = 2,
  BlenderSpeedLiquify = 5,
  BlenderSpeedPulse = 9,
  BlenderSpeedIceCrush = 15
} BlenderSpeed;

@interface Blender : NSObject {
  //пять допустимых значений скорости
  BlenderSpeed speed;
  }

//setSpeed: получает одно из пяти допустимых значений
- (void)setSpeed:(BlenderSpeed)x;

@end
```
Часто для программиста совершенно неважно, какими числами представлены пять скоростей - лишь бы они отличались друг от друга. Значения элементов перечисления можно не указывать, в этом случае компилятор сгенерирует их автоматически:
```objectivec
typedef enum {
  BlenderSpeedStir,
  BlenderSpeedChop,
  BlenderSpeedLiquify,
  BlenderSpeedPulse,
  BlenderSpeedIceCrush
} BlenderSpeed;
```
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/flags1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/flags2.png">

__Объявление структуры__

Как правило, объявление структуры используется в программе многократно, поэтому для типа структур обычно создается `typedef` - псевдоним для объявления типа, позволяющий использовать его как обычный тип данных.
```objectivec
typedef struct {
  float heightInMeters;
  int weightInKilos;
} Person;
```

<a name="чтo-такое-awakefromnib"></a>
## Что такое awakeFromNib?
_NSNibAwaking Protocol Reference (informal protocol)_

Prepares the receiver for service after it has been loaded from an Interface Builder archive, or nib file.

`- (void)awakeFromNib;`

An `awakeFromNib` message is sent to each object loaded from the archive, but only if it can respond to the message, and only after all the objects in the archive have been loaded and initialized. When an object receives an awakeFromNib message, it is guaranteed to have all its outlet instance variables set.

_Note:_ During Interface Builder’s test mode, this method is also sent to objects instantiated from loaded palettes, which include executable code for the objects. It is not sent to objects created using the Classes display of the nib file window in Interface Builder.
An example of how you might use `awakeFromNib` is shown below. Suppose your nib file has two custom views that must be positioned relative to each other at runtime. Trying to position them at initialization time might fail because the other view might not yet be unarchived and initialized yet. However, you can position both of them in the nib file owner’s `awakeFromNib` method. In the code below, `firstView` and `secondView` are outlets of the file’s owner:

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/awakefromnib.png">

<a name="nil-указателя-разница"></a>
## Что происходит когда мы пытаемся вызвать метод у nil указателя? Разница между nil и Nil
На самом деле, в контексте указателей применим как `NULL`, так и `0`, ввиду того что первый — не более чем макрос-обёртка для второго:
```objectivec
#define NULL ((void *)0)
```
`nil` это указатель на нулевой объект:
```objectivec
#if !defined(nil)
#define nil (id)0
#endif
```
Но и это ещё не всё: в дополнение к четырём вышеперечисленным мнемоникам, Foundation определяет макрос `Nil` (не путать с `nil`) — нулевой указатель типа `Class`:
```objectivec
#if !defined(Nil)
#define Nil (Class)0
#endif
```
`NSNull` используется внутри фреймворка Foundation и некоторых других для того, чтобы обойти ограничение стандартных коллекций, вроде `NSArray` или `NSDictionary`, заключающееся в том, что они не могут содержать в себе значения `nil`.

* `0 = 0` Ноль — он везде ноль
* `NULL = (void *)0` Нулевой указатель в языке Си
* `nil = (id)0` Нулевой указатель на объект Objective-C
* `Nil = (Class)0` Нулевой указатель типа `Class` в Objective-C
* `NSNull = [NSNull null]` Синглтон класса `NSNull` — обёртки над `nil` и `Null`

Иногда разработчики той или иной функции (метода) допускают возможность, что не все входные параметры могут быть заданы пользователем. Например, метод `-capitalizedStringWithLocale:` класса `NSString` принимает в качестве аргумента локаль (объект класса `NSLocale`), либо `nil` — в последнем случае при изменении регистра строки будет использоваться каноническая декомпозиция (NFD) Unicode-символов независимо от настроек локали на компьютере пользователя (то есть, данный метод будет эквивалентен методу `-capitalizedString`).

Инициализация и «опустошение» объектов (например, для того, чтобы сообщить об ошибке):
```objectivec
- (NSDictionary *)dictionaryForLicenseFile:(NSString *)path {
  NSData *licenseFile = [NSData dataWithContentsOfFile:path];
  /*
  «Достаточно, вы мне плюнули в душу!»
  */
  if (!licenseFile) {
    return nil;
  }            
  return [self dictionaryForLicenseData:licenseFile];
}  	
```
В ответ на посылаемое ему сообщение `nil` не бросает исключение, а попросту игнорирует это сообщение. То есть, `nil` из Objective-C ведёт себя как "черная дыра". Это пустота. Это ничто. При посылке к `nil` любого сообщения, всё что вы получите назад - это `nil`. Не будет никаких исключений, никаких возвращенных значений. Ничего.

<a name="неформальный-протокол"></a>
## Что такое неформальный протокол?
Категория с описанными, но не реализованными методами называется неформальным протоколом. Неформальные протоколы часто определяются для корневого класса `NSObject`, при этом они не имеют реализации в самом классе. Каждый подкласс будет отвечать на сообщения описанные в категории, но при этом будут делать что-то полезное только реализованные методы. Методы, по мере необходимости, могут быть реализованы в подклассах, при этом реализуемые методы должны быть объявлены в секции `@interface`.

<a name="nsstring-char"></a>
## В чем разница между NSString и char? Что значит приставка NS в общем?
Приставка `NS` это абревиатура от NextStep операционной системы на основе которой и создана часть MAC OS. Apple в свое время купил и использует до сих пор.
```objectivec
сhar *myCharPtr = "This is a string.";
//In memory: myCharPtr contains an address, e.g. |0x27648164|
//at address 0x27648164: |T|h|i|s| |i|s| |a| |s|t|r|i|n|g|.|\0|

NSString *myStringPtr = @"This is an NSString.";
//In memory: myStringPtr contains e.g. |0x27648164|
//at address 0x27648164: |Object data|length|You don't know what else|UTF-16 data|etc.|
```

<a name="uibutton-to-nsobject"></a>
## Опишите иерархию классов от UIButton до NSObject
`UIButton : UIControl : UIView : UIResponder : NSObject`

<a name="nsarray-зачем-nil-вконце"></a>
## NSArray arrayWithObjects: a, b, c, nil; зачем nil вконце?
Чтобы закончить список объектов, которые содержит массив. Этим значением мы даем знать компилятору, что массив окончен.

<a name="nsnotificationcenter"></a>
## Как работает NSNotificationCenter? В каком потоке приходит оповещение?
В общих словах, `NSNotificationCenter` представляет собой словарь, в который мы складываем всех наблюдателей и ассоциированные действия с ними. При наступлении определенного события мы ищем в словаре наблюдателя и вызываем необходимое действие. Оповещение приходит в том же потоке, в котором было отправлено уведомление.

https://www.mikeash.com/pyblog/friday-qa-2011-07-08-lets-build-nsnotificationcenter.html

<a name="volatile"></a>
## Что такое volatile?
Это спецификатор, применяемый при объявлении переменной. Он сообщает компилятору, что значение переменной может изменяться в любой момент – без какого-либо действия со стороны кода, который компилятор обнаруживает поблизости. Ключевое слово volatile пишется до или после типа данных объявляемой переменной:
```c
volatile int foo;
int volatile foo;
```
Указатели на volatile переменные объявляются так:
```c
volatile int * pReg;
int volatile * pReg;
```
Если вы используете volatile для структуры (struct) или объединения (union), действие спецификатора будет распространяться на все содержимое структуры/объединения. Если вы не хотите этого, то можете применить спецификатор volatile к отдельным элементам структуры/объединения. Переменная должна быть объявлена с ключевым словом volatile  всякий раз, когда ее значение может измениться неожиданно. На практике так ведут себя только три типа переменных:

1. Отображаемые в памяти периферийные регистры
2. Глобальные переменные, изменяемые в обработчике прерывания
3. Глобальные переменные, используемые в многопотоковом приложении

<a name="inline"></a>
## Что такое inline функция?
Inline функция избавляет процессор прыгать в ячейку, по адресу которой начинается эта функция. Сам смысл inline состоит в том, чтобы вместо вызова функции подставить ее тело (код функции) в место, где она вызывается. Различие между inline функцией и обычной функцией — дублирование кода тела функции везде, где она оказывается задействована. В обычной функции, её тело находится в единственном экземпляре в одном и том же месте внутри программы. Но в бытовых условиях да еще и на современных компьютерах, программы, использующие inline подстановку тела функции вместо вызова, не дают особых преимуществ.

<a name="objects-in-collections"></a>
## Добавление объектов в коллекции

- Что происходит со счетчиком ссылок когда объект добавляется в array, dictionary, set?

Объекту посылается сообщение `retain`

- Если нужно другое поведение, что использовать?

1. `NSPointerArray`
2. Self made container:
```swift
struct WeakContainer<T where T: AnyObject> {
  weak var _value : T?
  init (value: T) {
    _value = value
  }
  func get() -> T? {
    return _value
  }
}

let myArray: Array<WeakContainer<MyClass>> = [myObject1, myObject2]
```
- Mожно ли узнать, какой объект сколько раз был добавлен в set?

`NSCountedSet`

<a name="class-as-key"></a>
## Как использовать свой класс как ключ?

You're using `setValue:forKey:` which only takes `NSString` as keys. You should be using `setObject:forKey:` instead. A class object (pointers to class objects can be passed as type Class) is a full-fledged Objective-C object (a class object is an instance of its meta-class, and you can use all the `NSObject` methods on a class object; so they can be used anywhere objects are used.

<a name="kvc"></a>
## Как работает KVC?

Essentially, each class maintains a mapping of method names to their actual implementations (which are just C functions). This is akin to the dictionary you talk about, although it is managed by the Objective-C runtime itself. This mapping is used every time a method is called. For example, let's say you have this bit of code:
```objectivec
[obj doSomething];
```
What really happens is that, at runtime, the Objective-C runtime searches obj's method mapping for an entry called `doSomething`. This returns a function that the runtime then calls, passing in `obj` as the first parameter to that function. Because methods are dispatched at runtime, Objective-C provides a number of ways to call functions using strings. The Objective-C runtime itself also tracks the names of instance variables and where they are actually located in memory, relative to an object. This is how KVC is able to do its thing. When you call:
```objectivec
[obj setValue:@"value" forKey:@"property"];
```
The KVC runtime uses the Objective-C runtime to first look for a method called `setProperty`. The runtime fetches the function corresponding to that method, and the KVC machinery can then call that method, passing `obj` and `@"value"` as the parameters to that function. What if a method can't be found? Well, then the KVC machinery looks for an instance variable with the same name, using a function from the Objective-C runtime like `ivar_getOffset` or the like. Probably at some point it uses a function like `object_setIvar` to set the instance variable. If KVC fails to find both a method and an instance variable, it calls `setValue:forUndefinedKey:` or `valueForUndefinedKey:`, which can optionally be defined on a class to dynamically handle properties.

<a name="kvo"></a>
## Как работает KVO и какие могут быть с ним проблемы?

> The key-value observing `addObserver:forKeyPath:options:context:` method does not maintain strong references to the observing object, the observed objects, or the context. You should ensure that you maintain strong references to the observing, and observed, objects, and the context as necessary.

Наблюдение не создает сильных ссылок ни на наблюдателя, ни на наблюдаемый объект, ни на контекст. Однако документация умалчивает о том, что же произойдет, когда один из этих объектов будет удален.

So how does that work, not needing any code in the observed object? Well it all happens through the power of the Objective-C runtime. When you observe an object of a particular class for the first time, the KVO infrastructure creates a brand new class at runtime that subclasses your class. In that new class, it overrides the set methods for any observed keys. It then switches out the `isa` pointer of your object (the pointer that tells the Objective-C runtime what kind of object a particular blob of memory actually is) so that your object magically becomes an instance of this new class. The overridden methods are how it does the real work of notifying observers. The logic goes that changes to a key have to go through that key's set method. It overrides that set method so that it can intercept it and post notifications to observers whenever it gets called. (Of course it's possible to make a modification without going through the set method if you modify the instance variable directly. KVO requires that compliant classes must either not do this, or must wrap direct ivar access in manual notification calls.) It gets trickier though: Apple really doesn't want this machinery to be exposed. In addition to setters, the dynamic subclass also overrides the -class method to lie to you and return the original class! If you don't look too closely, the KVO-mutated objects look just like their non-observed counterparts.

<a name="rotate-view"></a>
## Как изменятся свойства, если применить поворот на 45º?

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/rotate-view.jpg">

It is important to note that if you transform a view, then the frame becomes undefined. So actually, the yellow frame that I drew around the rotated green bounds in the image above never actually exists. That means if you rotate, scale or do some other transformation then you shouldn't use the frame values any more. You can still use the bounds values, though. The Apple docs warn:

> Important: If a view’s transform property does not contain the identity transform, the frame of that view is undefined and so are the results of its autoresizing behaviors.

> When modifying the transform property of your view, all transformations are performed relative to the center point of the view.

So if you do need to move a view around in the parent after a transformation has been done, you can do it by changing the view.center coordinates. Like frame, center uses the coordinate system of the parent view.

__When to use frame and when to use bounds?__

Since __frame__ relates a view's location in its parent view, you use it when you are making __outward changes__, like changing its width or finding the distance between the view and the top of its parent view.

Use the __bounds__ when you are making __inward changes__, like drawing things or arranging subviews within the view. Also use the bounds to get the size of the view if you have done some transfomation on it.

<a name="view-layer-difference"></a>
## Отличие view от layer?

On iOS, every `UIView` is backed by a Core Animation `CALayer`, so you are dealing with `CALayer`s when using a UIView, even though you may not realize it. There is a very strong relationship between the view and its layer, and the view derives most of its data from the layer object directly. There are also standalone layers – for example, `AVCaptureVideoPreviewLayer` and `CAShapeLayer` – that present content on the screen without being attached to a view. In either case, there is a layer involved. Still, the layers that are attached to views and the standalone layers behave slightly differently. Working directly with `CALayer`s doesn't give you significant performance advantages over `UIView`s. When you’re working with a programmatically created Layer any changes to the Layer’s properties is automatically animated. All you have to do is set the property and the animation happens. However, the Layers of layer-backed Views will not animate property changes. You must wrap those changes in an animation block. By default, almost every standard property of `CALayer` and its subclasses can be animated, either by adding a `CAAnimation` to the layer (explicit animation), or by specifying an action for the property and then modifying it (implicit animation).

Layers

- Represent position, shape and anchor point
- Do not receive touch events
- Light-weight
- Implicit animations

Views

- Can receive touch events
- Are always backed by a Layer on iOS
- No implicit animations

<a name="moving-subviews"></a>
## Как передвинуть все subviews?

You're talking about two different coordinate systems. `mainView.center` is expressed in the coordinate system of the view that contains `mainView`, whereas `firstView.center` and `secondView.center` are in terms of the coordinate system of `mainView`. You can certainly move `firstView` and `secondView` together by moving the view that contains them, but you need to translate between those two coordinate systems if you want to get the same result that you get by moving the two views themselves.

<a name="optionals-swift-objc"></a>
## Swift optionals, Objective-C new modifiers (`nullable`, etc.). что это и как реализовано?

__Optional in Swift__

> A type that represents either a wrapped value or `nil`, the absence of a value. You use the `Optional` type whenever you use optional values, even if you never type the word `Optional`. Swift's type system usually shows the wrapped type's name with a trailing question mark (`?`) instead of showing the full type name. For example, if a variable has the type `Int?`, that's just another way of writing `Optional<Int>`. The shortened form is preferred for ease of reading and writing code. The types of `shortForm` and `longForm` in the following code sample are the same:
```swift
let shortForm: Int? = Int("42")
let longForm: Optional<Int> = Int("42")
```
The `Optional` type is an enumeration with two cases. `Optional.none` is equivalent to the `nil` literal. `Optional.some(Wrapped)` stores a wrapped value. For example:
```swift
let number: Int? = Optional.some(42)
let noNumber: Int? = Optional.none
print(noNumber == nil)
// Prints "true"
```

```swift
public enum Optional<Wrapped> : ExpressibleByNilLiteral {
	/// The absence of a value.
  /// In code, the absence of a value is typically written using the `nil`
  /// literal rather than the explicit `.none` enumeration case.
  case none

  /// The presence of a value, stored as `Wrapped`.
  case some(Wrapped)
	..................
}
```

__Nullability (type) qualifiers in Objective-C__

> The nullability (type) qualifiers express whether a value of a given pointer type can be null (the `_Nullable` qualifier), doesn’t have a defined meaning for null (the `_Nonnull` qualifier), or for which the purpose of null is unclear (the `_Null_unspecified` qualifier). Because nullability qualifiers are expressed within the type system, they are more general than the `nonnull` and `returns_nonnull` attributes, allowing one to express (for example) a `nullable` pointer to an array of `nonnull` pointers. Nullability qualifiers are written to the right of the pointer to which they apply.

> In Objective-C, there is an alternate spelling for the nullability qualifiers that can be used in Objective-C methods and properties using context-sensitive, non-underscored keywords

- `null_unspecified`: bridges to a Swift implicitly-unwrapped optional. This is the default.
- `nonnull`: the value won’t be nil; bridges to a regular reference.
- `nullable`: the value can be nil; bridges to an optional.
- `null_resettable`: the value can never be nil when read, but you can set it to nil to reset it. Applies to properties only.

So for method returns and parameters you can use the double-underscored versions `__nonnull`/`__nullable`/`__null_unspecified` instead of either the single-underscored ones, or instead of the non-underscored ones. The difference is that the single and double underscored ones need to be placed after the type definition, while the non-underscored ones need to be placed before the type definition. Thus, the following declarations are equivalent and are correct:
```objectivec
- (nullable NSNumber *)result
- (NSNumber * __nullable)result
- (NSNumber * _Nullable)result
```
For parameters:
```objectivec
- (void)doSomethingWithString:(nullable NSString *)str
- (void)doSomethingWithString:(NSString * _Nullable)str
- (void)doSomethingWithString:(NSString * __nullable)str
```
For properties:
```objectivec
@property(nullable) NSNumber *status
@property NSNumber *__nullable status
@property NSNumber * _Nullable status
```
Things however complicate when double pointers or blocks returning something different than `void` are involved, as the non-underscore ones are not allowed here:
```objectivec
- (void)compute:(NSError *  _Nullable * _Nullable)error
- (void)compute:(NSError *  __nullable * _Null_unspecified)error;
// and all other combinations
```
Similar with methods that accept blocks as parameters, please note that the `nonnull`/`nullable` qualifier applies to the block, and not its return type, thus the following are equivalent:
```objectivec
- (void)executeWithCompletion:(nullable void (^)())handler
- (void)executeWithCompletion:(void (^ _Nullable)())handler
- (void)executeWithCompletion:(void (^ __nullable)())handler
```
If the block has a return value, then you're forced into one of the underscore versions:
```objectivec
- (void)convertObject:(nullable id __nonnull (^)(nullable id obj))handler
- (void)convertObject:(id __nonnull (^ _Nullable)())handler
- (void)convertObject:(id _Nonnull (^ __nullable)())handler
// the method accepts a nullable block that returns a nonnull value
// there are some more combinations here, you get the idea
```

<a name="download-in-background"></a>
## Можно ли скачать что-нибудь, пока приложение выполняется в фоне?

When downloading files, apps should use an `NSURLSession` object to start the downloads so that the system can take control of the download process in case the app is suspended or terminated. When you configure an `NSURLSession` object for background transfers, the system manages those transfers in a separate process and reports status back to your app in the usual way. If your app is terminated while transfers are ongoing, the system continues the transfers in the background and launches your app (as appropriate) when the transfers finish or when one or more tasks need your app’s attention. To support background transfers, you must configure your `NSURLSession` object appropriately. To configure the session, you must first create a `NSURLSessionConfiguration` object and set several properties to appropriate values. You then pass that configuration object to the appropriate initialization method of `NSURLSession` when creating your session. The process for creating a configuration object that supports background downloads is as follows:

1. Create the configuration object using the `backgroundSessionConfigurationWithIdentifier:` method of `NSURLSessionConfiguration`.
2. Set the value of the configuration object’s `sessionSendsLaunchEvents` property to `YES`.
3. If your app starts transfers while it is in the foreground, it is recommend that you also set the discretionary property of the configuration object to `YES`.
4. Configure any other properties of the configuration object as appropriate.
5. Use the configuration object to create your `NSURLSession` object.

Once configured, your `NSURLSession` object seamlessly hands off upload and download tasks to the system at appropriate times. If tasks finish while your app is still running (either in the foreground or the background), the session object notifies its delegate in the usual way. If tasks have not yet finished and the system terminates your app, the system automatically continues managing the tasks in the background. If the user terminates your app, the system cancels any pending tasks.

When all of the tasks associated with a background session are complete, the system relaunches a terminated app (assuming that the `sessionSendsLaunchEvents` property was set to `YES` and that the user did not force quit the app) and calls the app delegate’s `application:handleEventsForBackgroundURLSession:completionHandler:` method. (The system may also relaunch the app to handle authentication challenges or other task-related events that require your app’s attention.) In your implementation of that delegate method, use the provided identifier to create a new `NSURLSessionConfiguration` and `NSURLSession` object with the same configuration as before. The system reconnects your new session object to the previous tasks and reports their status to the session object’s delegate.

<a name="custom-hash-table"></a>
## Как реализовать хеш-таблицу? Как избежать коллизий?

https://github.com/raywenderlich/swift-algorithm-club/tree/master/Hash%20Table

<a name="reactive-programming"></a>
## Что такое реактивное программирование?

Парадигма программирования, ориентированная на потоки данных и распространение изменений. Это означает, что должна существовать возможность легко выражать статические и динамические потоки данных, а также то, что нижележащая модель исполнения должна автоматически распространять изменения благодаря потоку данных. К примеру, в императивном программировании присваивание `a := b + c` будет означать, что переменной a будет присвоен результат выполнения операции `b + c`, используя текущие (на момент вычисления) значения переменных. Позже значения переменных `b` и `c` могут быть изменены без какого-либо влияния на значение переменной `a`. В реактивном же программировании значение `a` будет автоматически пересчитано, основываясь на новых значениях.

<a name="functional-programming"></a>
## Что такое функциональное программирование? Какие фичи есть для этого в Swift / Objective-C?

Парадигма программирования, в которой процесс вычисления трактуется как вычисление значений функций в математическом понимании последних (в отличие от функций как подпрограмм в процедурном программировании). Противопоставляется парадигме императивного программирования, которая описывает процесс вычислений как последовательное изменение состояний. При необходимости, в функциональном программировании вся совокупность последовательных состояний вычислительного процесса представляется явным образом, например, как список. Функциональное программирование предполагает обходиться вычислением результатов функций от исходных данных и результатов других функций, и не предполагает явного хранения состояния программы. Соответственно, не предполагает оно и изменяемость этого состояния (в отличие от императивного, где одной из базовых концепций является переменная, хранящая своё значение и позволяющая менять его по мере выполнения алгоритма). На практике отличие математической функции от понятия «функции» в императивном программировании заключается в том, что императивные функции могут опираться не только на аргументы, но и на состояние внешних по отношению к функции переменных, а также иметь побочные эффекты и менять состояние внешних переменных. Таким образом, в императивном программировании при вызове одной и той же функции с одинаковыми параметрами, но на разных этапах выполнения алгоритма, можно получить разные данные на выходе из-за влияния на функцию состояния переменных. А в функциональном языке при вызове функции с одними и теми же аргументами мы всегда получим одинаковый результат: выходные данные зависят только от входных. Это позволяет средам выполнения программ на функциональных языках кешировать результаты функций и вызывать их в порядке, не определяемом алгоритмом и распараллеливать их без каких-либо дополнительных действий со стороны программиста (что обеспечивают функции без побочных эффектов — чистые функции).
***
__Swift__

_First-Class and Higher-Order Functions_

In FP languages functions are first-class citizens, meaning that functions are treated just like other objects, and can be assigned to variables. Because of this, functions can also accept other functions as parameters, or return other functions. Functions that accept or return other functions are called higher order functions.

__Filter__

`filter(_:)` is a method on Collection types, such as Swift arrays. It accepts another function a parameter. This other function accepts as input a single value from the array, and returns a `Bool`. `filter(_:)` applies the input function to each element of the calling array and returns another array that has only the array elements for which the parameter function returns true.

__Map__

The Collection method `map(_:)` also accepts a single function as a parameter, and in turn, it produces an array of the same length after being applied to each element of the collection. The return type of the mapped function does not have to be the same type as the collection elements.

__Reduce__

The Collection method `reduce(_:_:)` takes two parameters. The first is a starting value of a generic type `Element`, and the second is a function that combines a value of type `Element` with an element in the collection to produce another value of type `Element`.
The input function applies to each element of the calling collection, one-by-one, until it reaches the end of the collection and produces a final accumulated value of type `Element`.

__Pure Functions__

One of the primary concepts in FP that leads to the ability to reason consistently about program structure, as well as confidently test program results, is the idea of a pure function. A function can be considered pure if it meets two criteria:
* The function always produces the same output when given the same input, e.g., the output only depends on its input.
* The function creates zero side effects outside of it.

Pure functions are closely related to the concept of __referential transparency__. An element of a program is referentially transparent if you can replace it with its definition and always produce the same result. It makes for predictable code and allows the compiler to perform optimizations. Pure functions satisfy this condition.

***
__Objective-C__

The concept of a lambda in Objective-C is now encapsulated with the idea of Blocks which are the equivalent of pass-by-reference functions. Of course, arguably one had that already in C with the idea of function pointers; blocks are just a way of also capturing local state (i.e. can be closures). Here's an example of defining a lambda to multiply two numbers together:
```objectivec
int (^mult)(int, int) = ^(int a, int b) { return a * b; };
```
The first part declares a variable, of type `^int(int, int)` and then assigns it to the lambda expression (aka block) which returns the multiple of its two arguments. You can then pass that function around, define it in other places etc; you can even use it in other functions.

Here's an example of defining a function, which when invoked, returns another function:
```objectivec
multiplyBy = ^(int a) { return ^(int b) { return b * a; }; };
triple = multiplyBy(3);
```
Note that you can intermix blocks with object types (usually using `id` as the object type) and many of the new Objective-C object data structures have some kind of block-level operation. GCD also uses blocks in order to pass in arbitrary events; however, note that GCD can also be used with function pointers as well.

<a name="custom-root-class"></a>
## Можно ли создать свой root класс?

It is true that on the Apple Objective-C 2.0 runtime, you must implement certain methods in order for your code to work. There is actually only one method that you need to implement: the class method `initialize`.
```objectivec
@interface MyBase
+ (void)test;
@end

@implementation MyBase
+ (void)initialize {

}

+ (void)test {
	// whatever
}
@end
```
The runtime will automatically call initialize when you first use your class (as explained in Apple's documentation). Not implementing this method is the reason for the message forwarding error. Making object allocation work is a different story. At the very least, you'll need an `isa` pointer on your base class if you're using instance variables. The runtime expects this to be there.

<a name="data-structure-alignment"></a>
## Как происходит выравнивание указателей на объекты в Objective-C?

На современных процессорах ваш компилятор располагает базовые типы в памяти так, чтобы обеспечить наиболее быстрый доступ к ним. На процессорах x86 и ARM примитивные типы не могут находиться в произвольной ячейке памяти. Каждый тип, кроме `char`, требует выравнивания. `char` может начинаться с любого адреса, однако двухбайтовый `short` должен начинаться только с четного адреса, четырехбайтный `int` или `float` — с адреса, кратного 4, восьмибайтные `long` или `double` — с адреса, кратного 8. Наличие или отсутствие знака значения не имеет. Указатели — 32-битные (4 байта) или 64-битные (8 байт) — также выравниваются. Выравнивание ускоряет доступ к памяти за счет генерации кода, в котором на чтение и запись ячейки памяти требуется по одной инструкции. Без выравнивания мы можем столкнуться с ситуацией, когда процессору придется использовать две и более инструкции для доступа к данным, расположенным между адресами, кратными размеру машинного слова. `char` — особый случай, они занимают ровно одно машинное слово и всегда требуют одинакового количества инструкций для доступа. Поэтому для них нет предпочтительного выравнивания.

https://tproger.ru/translations/art-of-structure-packing/

<a name="union"></a>
## Что такое union?

With a __union__, you're only supposed to use one of the elements, because they're all stored at the same spot. This makes it useful when you want to store something that could be one of several types.

A __struct___, on the other hand, has a separate memory location for each of its elements and they all can be used at once.
```c
union foo {
  int a; // can't use both a and b at once
  char b;
} foo;

struct bar {
  int a; // can use both a and b simultaneously
  char b;
} bar;

union foo x;
x.a = 3; // OK
x.b = 'c'; // NO! this affects the value of x.a!

struct bar y;
y.a = 3; // OK
y.b = 'c'; // OK
```
