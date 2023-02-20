- [Общие вопросы](#общие-вопросы)
  - [Inout parameters, pass by value, pass by reference](#inout-parameters-pass-by-value-pass-by-reference)
  - [Поверхностное и глубокое копирование](#поверхностное-и-глубокое-копирование)
  - [Отличие while от for](#отличие-while-от-for)
  - [Протокол? Что такое абстрактный класс? Чем абстрактный класс отличается от интерфейса?](#протокол-что-такое-абстрактный-класс-чем-абстрактный-класс-отличается-от-интерфейса)
  - [Какие существуют root классы в iOS? Для чего нужны root классы?](#какие-существуют-root-классы-в-ios-для-чего-нужны-root-классы)
  - [Чем категория отличается от расширения?](#чем-категория-отличается-от-расширения)
  - [Можно ли добавить ivar в категорию?](#можно-ли-добавить-ivar-в-категорию)
  - [Когда лучше использовать категорию, а когда наследование?](#когда-лучше-использовать-категорию-а-когда-наследование)
  - [Формальные и неформальные протоколы](#формальные-и-неформальные-протоколы)
  - [Есть ли приватные или защищенные методы в Objective-C? А в Swift?](#есть-ли-приватные-или-защищенные-методы-в-objective-c-а-в-swift)
  - [Что такое назначеный инициализатор, напишите любой элементарный инициализатор, почему он так выглядит?](#что-такое-назначеный-инициализатор-напишите-любой-элементарный-инициализатор-почему-он-так-выглядит)
  - [Как работают push нотификации?](#как-работают-push-нотификации)
  - [Memory warning](#memory-warning)
  - [Как реализовать кеш?](#как-реализовать-кеш)
  - [Какой контент лучше хранить в Documents, а какой в Cache?](#какой-контент-лучше-хранить-в-documents-а-какой-в-cache)
  - [Как из строки вытащить подстроку?](#как-из-строки-вытащить-подстроку)
  - [NSCoding, archiving?](#nscoding-archiving)
  - [Константы, typedef, enum, #define](#константы-typedef-enum-define)
  - [Что такое awakeFromNib?](#что-такое-awakefromnib)
  - [Что происходит когда мы пытаемся вызвать метод у nil указателя? Разница между nil и Nil](#что-происходит-когда-мы-пытаемся-вызвать-метод-у-nil-указателя-разница-между-nil-и-nil)
  - [Что такое неформальный протокол?](#что-такое-неформальный-протокол)
  - [В чем разница между NSString и char? Что значит приставка NS в общем?](#в-чем-разница-между-nsstring-и-char-что-значит-приставка-ns-в-общем)
  - [Опишите иерархию классов от UIButton до NSObject](#опишите-иерархию-классов-от-uibutton-до-nsobject)
  - [NSArray arrayWithObjects: a, b, c, nil; зачем nil в конце?](#nsarray-arraywithobjects-a-b-c-nil-зачем-nil-в-конце)
  - [Как работает NSNotificationCenter? В каком потоке приходит оповещение?](#как-работает-nsnotificationcenter-в-каком-потоке-приходит-оповещение)
  - [Что такое volatile?](#что-такое-volatile)
  - [Что такое inline функция?](#что-такое-inline-функция)
  - [Добавление объектов в коллекции](#добавление-объектов-в-коллекции)
  - [Как использовать свой класс как ключ?](#как-использовать-свой-класс-как-ключ)
  - [Как работает KVC?](#как-работает-kvc)
  - [Как работает KVO и какие могут быть с ним проблемы?](#как-работает-kvo-и-какие-могут-быть-с-ним-проблемы)
  - [Как изменятся свойства, если применить поворот на 45º?](#как-изменятся-свойства-если-применить-поворот-на-45º)
  - [Отличие view от layer?](#отличие-view-от-layer)
  - [Как передвинуть все subviews?](#как-передвинуть-все-subviews)
  - [Swift optionals, Objective-C new modifiers (`nullable`, etc.). что это и как реализовано?](#swift-optionals-objective-c-new-modifiers-nullable-etc-что-это-и-как-реализовано)
  - [Можно ли скачать что-нибудь, пока приложение выполняется в фоне?](#можно-ли-скачать-что-нибудь-пока-приложение-выполняется-в-фоне)
  - [Как реализовать хеш-таблицу? Как избежать коллизий?](#как-реализовать-хеш-таблицу-как-избежать-коллизий)
  - [Что такое реактивное программирование?](#что-такое-реактивное-программирование)
  - [Что такое функциональное программирование? Какие фичи есть для этого в Swift / Objective-C?](#что-такое-функциональное-программирование-какие-фичи-есть-для-этого-в-swift--objective-c)
  - [Можно ли создать свой root класс?](#можно-ли-создать-свой-root-класс)
  - [Как происходит выравнивание указателей на объекты в Objective-C?](#как-происходит-выравнивание-указателей-на-объекты-в-objective-c)
  - [Что такое union?](#что-такое-union)
  - [Что такое метакласс?](#что-такое-метакласс)
  - [Что такое рефлексия и интроспекция?](#что-такое-рефлексия-и-интроспекция)
  - [Когда можно не объявлять self с weak?](#когда-можно-не-объявлять-self-с-weak)
  - [Что происходит, когда юзер нажимает на UIButton на экране?](#что-происходит-когда-юзер-нажимает-на-uibutton-на-экране)
  - [Как работает code signing?](#как-работает-code-signing)
  - [Как проводить код ревью?](#как-проводить-код-ревью)
  - [Что такое fastlane и как он работает?](#что-такое-fastlane-и-как-он-работает)
  - [Что такое CI/CD и зачем он нужен?](#что-такое-cicd-и-зачем-он-нужен)
  - [Как реализовать потоко-безопасный массив?](#как-реализовать-потоко-безопасный-массив)
  - [Какие ты знаешь стайл-гайды? Зачем они нужны?](#какие-ты-знаешь-стайл-гайды-зачем-они-нужны)
  - [Какие ты знаешь менеджеры зависимостей? В чем между ними разница?](#какие-ты-знаешь-менеджеры-зависимостей-в-чем-между-ними-разница)
  - [Чем отличается статическая библиотека от динамической?](#чем-отличается-статическая-библиотека-от-динамической)
  - [Как положить в массив weak объекты?](#как-положить-в-массив-weak-объекты)
  - [Что такое agile, scrum и kanban?](#что-такое-agile-scrum-и-kanban)
  - [Как происходит рендеринг графики?](#как-происходит-рендеринг-графики)

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

- Невозможность добавления переменных
- Возможная коллизия имен с самим классом, поэтому необходимо использовать оригинальные префиксы в наименовании своих методов.
- Невозможно вызвать `[super method];` из категории

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
- Ожидание, что класс поддерживающий протокол выполнит описанные в протоколе функции
- Поддержка протокола на уровне объекта, не раскрывая методы и реализацию самого класса (в противоположность наследованию)
- Ввиду отсутствия множественного наследования - объединить общие черты нескольких классов

__Формальные протоколы__

Объявление формального протокола гарантирует, что все методы объявленные протоколом будут реализованы классом

__Неформальные протоколы__

Добавление категории к классу `NSObject` называется созданием неформального протокола. При работе с неформальными протоколами мы реализуем только те методы, которые хотим. Узнать, поддерживает ли класс какой либо метод можно с помощью селекторов:

```objectivec
First *f = [[First alloc] init];
if ([f respondsToSelector:@selector(setName:)]) {
  NSLog (@"Метод поддерживается");
}
```

__Подводные камни__

- `[NSObject self]` may return a class, or an object
- `[NSObject super]` is undefined

<a name="приватные-методы"></a>

## Есть ли приватные или защищенные методы в Objective-C? А в Swift?

_Objective-C_

Нет. Нужно использовать расширение.
Для имитации private методов с помощью расширения, нужно в .m файле, перед `@implementation` добавить безымянную категорию. Для класса `Something` ее определение будет выглядеть как `@interface Something () ... @end`. Стоит обратить особое внимание на пустые скобки — они показывают, что мы определяем именно безымянную категорию. После этого, мы можем добавлять в категорию методы, которые будут для нас считаться private. За счет того, что категория безымянная, имплементация данных методов может находиться рядом с имплементацией основных методов в разделе `@implementation .. @end` и нет необходимости создавать отдельные разделы для имплементации категорий. А за счет того, что она находится в .m файле, которые никто не подключает через `#import`, видимость методов для автодополнения ограничена текущим файлом. Конечно, послать объекту это сообщение извне все равно возможно, но от случайного вызова вы точно застрахованы.

_Swift_

- __Open__ access and __public__ access enable entities to be used within any source file from their defining module, and also in a source file from another module that imports the defining module.

- __Internal__ access enables entities to be used within any source file from their defining module, but not in any source file outside of that module.

- __File-private__ access restricts the use of an entity to its own defining source file.

- __Private__ access restricts the use of an entity to the enclosing declaration, and to extensions of that declaration that are in the same file.

Open access is the highest (least restrictive) access level and private access is the lowest (most restrictive) access level.

Open access applies only to classes and class members, and it differs from public access as follows:

- Classes with public access, or any more restrictive access level, can be subclassed only within the module where they’re defined.
- Class members with public access, or any more restrictive access level, can be overridden by subclasses only within the module where they’re defined.
- Open classes can be subclassed within the module where they’re defined, and within any module that imports the module where they’re defined.
- Open class members can be overridden by subclasses within the module where they’re defined, and within any module that imports the module where they’re defined.

<a name="назначеный-инициализатор"></a>

## Что такое назначеный инициализатор, напишите любой элементарный инициализатор, почему он так выглядит?

Класс содержит только один основной инициализатор. Если класс содержит другие инициализаторы, то их реализация должна вызывать (прямо или косвенно) основной инициализатор.
- Если класс имеет несколько инициализаторов, только один из них должен выполнять реальную работу. Этот метод называется основным инцициализатором. Все остальные инициализаторы должны вызывать основной инициализатор (прямо или косвенно).
- Основной инициализатор вызывает основной инициализатор суперкласса перед инициализацией своих переменных экземпляров `if (self  = [super...])`
- Если имя основного инициализатора вашего класса отличается от имени основного инициализатора его супер класса, вы должны переопределить основной инициализатор суперкласса, чтобы он вызывал новый основной инициализатор.
- Если класс содержит несколько инициализаторов, четко укажите в заголовочном файле, какой из них является основным.
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
- Designated initializers must always delegate up.
- Convenience initializers must always delegate across.

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
- Показать короткое текстовое сообщение.
- Воспроизвести короткий звуковой сигнал.
- Установить число на бейдже иконки приложения.

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
- Only documents and other data that is user-generated, or that cannot otherwise be recreated by your application, should be stored in the `<Application_Home>/Documents` directory and will be automatically backed up by iCloud.
- Data that can be downloaded again or regenerated should be stored in the `<Application_Home>/Library/Caches` directory. Examples of files you should put in the Caches directory include database cache files and downloadable content, such as that used by magazine, newspaper, and map applications.
- Data that is used only temporarily should be stored in the `<Application_Home>/tmp` directory. Although these files are not backed up to iCloud, remember to delete those files when you are done with them so that they do not continue to consume space on the user’s device.
- Use the "do not back up" attribute for specifying files that should remain on device, even in low storage situations. Use this attribute with data that can be recreated but needs to persist even in low storage situations for proper functioning of your app or because customers expect it to be available during offline use. This attribute works on marked files regardless of what directory they are in, including the Documents directory. These files will not be purged and will not be included in the user's iCloud or iTunes backup. Because these files do use on-device storage space, your app is responsible for monitoring and purging these files periodically.

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

- архивации (archivation)
- сериализации (serialization)

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

<a name="константы-typedef-enum-define"></a>

## Константы, typedef, enum, #define

`typedef` используется для объявления нового типа данных – это команда компилятору и предполагает символьный тип данных.

`#define` – команда препроцессору и может содержать числовые значения.

Переменные, значения которых не изменяются (как, например, математическая постоянная `pi`), Такие данные называются константами. В Objective-C существует два распространенных способа определения констант:
- `#define`
- глобальные переменные

```objectivec
#define M_PI 3.14159265358979323846264338327950288
```

Директива `#define` приказывает препроцессору: «Каждый раз, когда ты встречаешь Х, замени его на У еще до того, как компилятор увидит код».

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

- `0 = 0` Ноль — он везде ноль
- `NULL = (void *)0` Нулевой указатель в языке Си
- `nil = (id)0` Нулевой указатель на объект Objective-C
- `Nil = (Class)0` Нулевой указатель типа `Class` в Objective-C
- `NSNull = [NSNull null]` Синглтон класса `NSNull` — обёртки над `nil` и `Null`

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

Приставка `NS` это аббревиатура от NextStep операционной системы на основе которой и создана часть MAC OS. Apple в свое время купил и использует до сих пор.

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

## NSArray arrayWithObjects: a, b, c, nil; зачем nil в конце?

Чтобы закончить список объектов, которые содержит массив. Этим значением мы даем знать компилятору, что массив окончен.

<a name="nsnotificationcenter"></a>

## Как работает NSNotificationCenter? В каком потоке приходит оповещение?

В общих словах, `NSNotificationCenter` представляет собой словарь, в который мы складываем всех наблюдателей и ассоциированные действия с ними. При наступлении определенного события мы ищем в словаре наблюдателя и вызываем необходимое действие. Оповещение приходит в том же потоке, в котором было отправлено уведомление.

<https://www.mikeash.com/pyblog/friday-qa-2011-07-08-lets-build-nsnotificationcenter.html>

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

Foundation collection classes, which can store weak references and have a broader range of available memory semantics: 

1. `NSPointerArray` (like array)
2. `NSMapTable` (like dictionary)
3. `NSHashTable` (like set)

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

On iOS, every `UIView` is backed by a Core Animation `CALayer`, so you are dealing with `CALayer`s when using a `UIView`, even though you may not realize it. There is a very strong relationship between the view and its layer, and the view derives most of its data from the layer object directly. There are also standalone layers – for example, `AVCaptureVideoPreviewLayer` and `CAShapeLayer` – that present content on the screen without being attached to a view. In either case, there is a layer involved. Still, the layers that are attached to views and the standalone layers behave slightly differently. Working directly with `CALayer`s doesn't give you significant performance advantages over `UIView`s. When you’re working with a programmatically created Layer any changes to the Layer’s properties is automatically animated. All you have to do is set the property and the animation happens. However, the Layers of layer-backed Views will not animate property changes. You must wrap those changes in an animation block. By default, almost every standard property of `CALayer` and its subclasses can be animated, either by adding a `CAAnimation` to the layer (explicit animation), or by specifying an action for the property and then modifying it (implicit animation).

Layers

- Faster to resolve and quicker to draw on the screen
- There is no responder chain overhead unlike with views
- Represent position, shape and anchor point
- Do not receive touch events
- Light-weight
- Implicit animations
- Are drawn directly on the GPU. It happens on a separate thread without burdening the CPU.

Views

- Have more complex hierarchy layouts. To lay them out on the screen we can use Auto Layout
- Can receive touch events
- Are always backed by a Layer on iOS
- No implicit animations
- Working with UIViews happens on the main thread, it means it is using CPU power.

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

<https://github.com/raywenderlich/swift-algorithm-club/tree/master/Hash%20Table>

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

Метод `reduce(_:, _:)` «сворачивает» последовательность `Sequence` до единственного аккумулирующего значения и имеет два параметра. Первый параметр — это стартовое аккумулирующее значение, а второй параметр — это функция, которая комбинирует аккумулирующее значение с элементом последовательности `Sequence` для получения нового аккумулирующего значения. Входная функция-параметр применяется к каждому элементу последовательности `Sequence`, один за другим, до тех пор, пока не достигнет конца и не создаст финальное аккумулируюшее значение.

```swift
let sum = Array(1...100).reduce(0, +)
```

Это классический тривиальный пример использования функции высшего порядка `reduce(_:, _:)` - подсчет суммы элементов массива `Array`.

**Function Concatenation**

```swift
let numbers: [[Int]] = [[1, 3, 6, 2], [2, 5, 7], [1, 3]]
let sum: Int = numbers
    .flatMap({ $0 })
    .reduce(0, { $0 + $1 })
// sum = 30
```

__Pure Functions__

One of the primary concepts in FP that leads to the ability to reason consistently about program structure, as well as confidently test program results, is the idea of a pure function. A function can be considered pure if it meets two criteria:

- The function always produces the same output when given the same input, e.g., the output only depends on its input.
- The function creates zero side effects outside of it.

Pure functions are closely related to the concept of __referential transparency__. An element of a program is referentially transparent if you can replace it with its definition and always produce the same result. It makes for predictable code and allows the compiler to perform optimizations. Pure functions satisfy this condition.

**Functors and Monads**

A functor is just a fancy word for something that can implement `.map()`. So for example, in

```swift
let array = [1, 2, 3].map { $0 * 2 }
```

`array` is a functor.

A monad is simply a functor that can also implement `.flatMap()`. So in

```swift
let newArray = array.flatMap { String($0) }
```

`array` is a monad and `newArray` is a functor.
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

***

**Преимущества и недостатки функционального программирования**

**Плюсы**

1. Высокоуровневые абстракции, которые скрывают большое количество подробностей таких рутинных операций, как, например, итерирование. За счет этого код получается короче, и, как следствие, гарантирует меньшее количество ошибок, которые могут быть допущены.
2. Поскольку чистые функции не изменяют никаких состояний и полностью зависят от ввода, их легко понять. Возвращаемое значение, предоставляемое такими функциями, совпадает с выводом, произведенным ими. Аргументы и тип возвращаемого значения чистых функций выдаются их сигнатурой функции.
3. Из-за природы чистых функций, позволяющих избежать изменения переменных или каких-либо данных за ее пределами, реализация параллелизма становится эффективной.
4. Он поддерживает концепцию ленивого вычисления, что означает, что значение оценивается и сохраняется только тогда, когда оно требуется.
Чистые функции принимают аргументы один раз и выдают неизменяемый результат. Следовательно, они не производят скрытого вывода. Они используют неизменяемые значения, что упрощает отладку и тестирование.
5. Этот стиль рассматривает функции как значения и передает то же самое другим функциям как параметры. Это улучшает понимание и читаемость кода.

**Минусы**

1. На чистых функциональных языках не существует эффективного неупорядоченного словаря и множества
2. Не существует чисто функциональных слабых хэш-таблиц (weak hash table)
3. Не существует чисто функциональных потокобезопасных коллекций
4. Большинство алгоритмов на графах выглядят хуже и работают намного медленнее, если написаны в функциональном стиле
5. Инерция традиционных императивных структур данных и алгоритмов огромна
6. Как оказывается, все существующие реализации функциональных языков, как чистых, так и нечистых (impure), спроектированы так, что аллоцируют слишком много памяти
7. Чистое функциональное программирование хорошо для параллелизма в теории, но не очень хорошо с точки зрения производительности на практике, а высокая производительность на практике—единственная настоящая задача параллелизма
8. Понадобилось 50 лет, чтоб разбавить концентрацию высокомерных снобов в сообществе до той степени, чтоб можно было получить полезный ответ по функциональному программированию
9. О функциональном программировании циркулирует множество ложной информации

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

<https://tproger.ru/translations/art-of-structure-packing/>

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

<a name="metaclass"></a>

## Что такое метакласс?

Метакласс — это класс для объекта Класса.

- Когда Вы отправляете сообщение объекту-экземпляру Класса, сообщение просматривается в **списке методов объекта Класса**.
- Когда Вы отправляете сообщение Классу (а точнее, как мы теперь знаем, объекту Класса), такое сообщение просматривается в **списке методов метакласса**.

Наличие метаклассов обязательно, так как они хранят методы классов. Должен быть уникальный метакласс для каждого Класса, так как каждый Класс имеет потенциально уникальный список методов Класса. Метакласс, как и рассмотренные ранее классы, также является объектом. Это означает, что Вы также можете вызывать методы метакласса. В целом, это означает, что у метакласса также должен быть класс. Все метаклассы используют базовый метакласс (метакласс наивысшего класса в своей иерархии классов) как свой класс. Это означает, что для всех классов, которые наследуются от `NSObject` (а это большинство классов), метаклассы имеют метакласс `NSObject` как свой класс. Следуя правилу, что для всех метаклассов, использующих базовый метакласс Класса как свой класс, любой базовый метакласс будет их собственным классом (их указатель `isa` будет указывать непосредственно на них). Это означает, что указатель `isa` метакласса `NSObject` указывает сам на себя.

<a name="рефлексия-интроспекция"></a>

## Что такое рефлексия и интроспекция?

Интроспекция — это способность программы исследовать тип или свойства объекта во время работы программы. Вы можете поинтересоваться, каков тип объекта, является ли он экземпляром класса.

Рефлексия — это способность компьютерной программы изучать и модифицировать свою структуру и поведение (значения, мета-данные, свойства и функции) во время выполнения. Простым языком: она позволяет вам вызывать методы объектов, создавать новые объекты, модифицировать их, даже не зная имён интерфейсов, полей, методов во время компиляции. Из-за такой природы рефлексии её труднее реализовать в статически типизированных языках, поскольку ошибки типизации возникают во время компиляции, а не исполнения программы

<a name="self-no-weak"></a>

## Когда можно не объявлять self с weak?

There are two kinds of closures, non-escaping and escaping. Non-escaping closures are executed in scope — they execute their code immediately, and cannot be stored or run later. Escaping closures, on the other hand, can be stored, they can be passed around to other closures, and they can be executed at some point in the future. Non-escaping closures (such as higher-order functions like `compactMap`) do not pose a risk of introducing strong reference cycles, and thus do not require the use of `weak` or `unowned`. Escaping closures can introduce reference cycles when you don’t use `weak` or `unowned`, but only if both of these conditions are met:

- The closure is either saved in a property or passed to another closure
- An object inside the closure (such as `self`) maintains a strong reference to the closure (or to another closure that it was passed to)

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/when-to-use-weak-self.png">

<a name="responder-chain"></a>

## Что происходит, когда юзер нажимает на UIButton на экране?

__Understanding cocoa and cocoa touch responder chain__

Applications in cocoa and cocoa touch have an event queue associated to them, this event queue will be filled with events from multiple sources. In order to handle the stream of event, each application maintain an event run loop that accepts and dispatches events in a FIFO order. When an application is launched the call to `UIApplicationMain` will create a `UIApplication` singleton object, this object will be responsible for handling and dispatching the events the system sends to the app events queue.

The application will receive events from sources as:

- UIControl Actions: these are the actions that are registered using the action/target pattern
- User events: Events from user such as touches, shakes, motion, etc…
- System events: Such as low memory, rotation, etc…

Each of these events will be handled and processed by the application singleton before being dispatched to the appropriate receivers.

__UIControl Actions__

`UIControl` actions are the action that are added to a control by calling the `addTarget:action:forControlEvents:` method, the `UIControl` will keep record of all the action/target pairs that have been added to it. When a user perform an event on a control, or when a `UIControl` calls `sendActionsForControlEvents` function, the action related to that control event will be sent to the registered target.

Lets take an example:

```objectivec
UIButton button = [UIButton new];
[button addTarget:self action:@selector(buttonTapped) forControlEvents:UIControlEventTouchUpInside];
```

When the user taps on this button, an event will be dispatched to the `UIApplication` (using a `UIControl` internal copy of `sendActionsForControlEvents`), the application will read this action from its event queue and dispatch it in `UIApplication sendAction:to:from:forEvent:` function, the base implementation of that method will call the action on the registered target, the target will receive `buttonTapped` method in this case.

If we specify nil for the target:

```objectivec
[button addTarget:nil action:@selector(buttonTapped) forControlEvents:UIControlEventTouchUpInside];
```

In this case the base implementation of `sendAction:to:from:forEvent` will send the `buttonTapped` selector to the current first responder. If the first responder does not implement that action (`buttonTapped` in our example), then it will be send to the next responder, the system will keep trying to find a valid responder in the responder chain, until there are no more responders in the chain. in that case this action will be dropped. Using this knowledge we can send an action to the first responder by calling `sendAction:to:from:forEvent` on the `UIApplication` singleton and passing nil as the target. For example we can send `resignFirstResponder` to the first responder and hence resign the keyboard by doing:

```objectivec
[[UIApplication sharedApplication] sendAction:@selector(resignFirstResponder) to:nil from:nil forEvent:nil];
```

__User Events__

User events such as touches and device motion will be sent to the application event queue, if the user event is anything but a touch then the application will dispatch the call to the first responder, if the first responder couldn’t handle it, the system will follow the responder chain to find an appropriate responder.

For touch events the flow is different: when the system detects a touch on the screen it will send this touch to the application, the application will receive the touch event in its `_touchesEvent` internal method. The application will then forward this event using `sendEvent` to the `UIWindow`, the window upon receiving this event start the process of hit-testing the views in order to find the one that received this touch. UIView’s `hitTest:withEvent` will be used to find the view that is under the touch, the implementation of hit-test will check if the touch is within the view bounds, by calling `pointInside:withEvent:` in each view. `hitTest` and `pointInside` will be called recursively until it reaches a top most leaf view. this view will be used as the first responder for the touch event. `UIWindow` will then send the touch events to this view.

```objectivec
- (void)touchesBegan:(NSSet *)touches withEvent:(UIEvent *)event;
- (void)touchesMoved:(NSSet *)touches withEvent:(UIEvent *)event;
- (void)touchesEnded:(NSSet *)touches withEvent:(UIEvent *)event;
- (void)touchesCancelled:(NSSet *)touches withEvent:(UIEvent *)event;
```

When an event is send to a view, this view has three choices:

1. Since the UIResponder base implementation of the four methods above forwards the event to the next responder, then if the view doesn’t implement a method of them, this method will be forwarded to the next responder.
2. A view can implement any method from the above, do some processing, and then call super in order to let the next responder do some additional process.
3. A view can implement any method from the above and choose to not forward the event to the next responder.

If the view chooses to not handle a touch event, then it will be sent up the responder chain, which will follow this path:

- The first responder is the hit-tested view (the view under the touch)
- Next responder is its super view
- The chain continues up the view hierarchy until it reaches a view that is associated with a view controller
- That view controller will be the next responder
- If this view controller is a root controller, then the window will be the next responder
- The application is the window’s next responder
- The last responder in the chain is the App delegate

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/hittest.png">

__System Events__

The system will send events to the application singleton, these system related events will be received by the application singleton and dispatched to the App delegate. The app delegate in turn will receive the events and handle them.

The first responder

Any `UIResponder` can opt to become the first responder by receiving or calling the `becomeFirstResponder` method, the first responder will be given the chance to act upon user events when they are received. The touch events however will not be sent to the first responder, these events are sent to the view found by doing a recursive hit-test.

<https://habr.com/ru/post/584100/>

<a name="code-signing"></a>

## Как работает code signing?

Basic concepts:

- Xcode
- Member Center
- Keychain
- Signing Identity
- Private & Public Key
- Provisioning Profile
- App ID

After you registered for the Apple Developer Program you will be able to login to the Member Center. This is the place where you can create Provisioning Profiles, App IDs, Certificates etc.. Parts of the Member Center are directly connected with Xcode. For instance, you can see and create your Signing Identities or download and refresh Provisioning Profiles in your Xcode Settings.

__Signing Identity, Public & Private Key, Keychain Application__

One thing we need to clear up is the term Signing. Signing your app allows iOS to identify who signed your app and to verify that your app hasn’t been modified since you signed it. The Signing Identity consists of a public-private key pair that Apple creates for you. Think about the public-key as a lock-only mechanism, so you need to know the private key to unwrap, unlock or decode data again.

Where do the public and private key-pair come from and how do you request a certificate containing them? All this magic happens when you create a Certificate Signing Request (CSR) through the Keychain Access Application. If you do so, the Keychain Application will create a private key and a certSigningRequest file which you’ll then upload to Apple. Apple will proof the request and issue a certificate for you. The Certificate will contain the public key that can be downloaded to your system. After you downloaded it you need to put it into your Keychain Access Application by double clicking it. It is used by cryptographic functions to generate a unique signature for your application, which is basically your Code Signing Identity.

The certificate will also be available through the Member Center, but it will only contain the public key, so keep that private key safe.

An intermediate certificate is also required to be in your keychain to ensure that your developer or distribution certificate is issued by another certificate authority. I know that sounds a little bit confusing, but this is how it works. It is installed automatically when setting Xcode up the first time, so basically you don't need to care about it that much because it is configured automatically.

__Provisioning Profile & App ID__

As we know, Apple likes to keep things secure, so it is not possible to install an App on any iOS Device out there using only the certificate. This is where Provisioning Profiles comes in. A Provisioning Profile must be installed on each device your application code should run on. Each Development Provisioning Profile will contain a set of iPhone Development Certificates, Unique Device Identifiers and an App ID. An App ID is a two-part string used to identify one or more apps from a single development team.

Devices specified in the Development Provisioning Profile can be used for testing only by those individuals whose Development Certificates are included in the profile. A single device can contain multiple provisioning profiles. The difference between Development and Distribution Profiles is that Distribution Profiles don’t specify any Device IDs. If you want to release an App which should be limited to a number of registered devices, you need to use an Ad-Hoc profile for that.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/code-signing.png">

1. Xcode will be installed and the Intermediate Certificate will be pushed into the Keychain
2. Certificate Signing Request (CSR) will be created.
3. Private Key will be generated along the CSR creation and stored in the Keychain
4. CSR will be uploaded to the Member Center
5. Apple will proof everything and issue the Certificate
6. Certificate will be downloaded to your Computer
7. The Certificate will be pushed into the Keychain and paired with the private key to form the Code Signing Identity
8. The Provisioning Profile will be created using a Certificate, App ID and Device Identifiers and downloaded by Xcode
9. Xcode will sign the App and push Provisioning Profiles onto the Device
10. iOS will proof if everything is correctly configured.That means that the Provisioning Profile should include the Certificate you used to sign the App, your Device UDID and the correct App ID.
11. Your App should be running now!

<a name="code-review"></a>

## Как проводить код ревью?

CL — changelist
MR — Merge Request
PR — Pull Request
LGTM — Looks Good to Me
Nit — nitpick (придирка)

_Идеальность MR_

На практике можно встретить различные крайности при рассмотрении `MR`. Кто-то всей командой задалбывает замечаниями, пока всё до мелочей не будет исправлено, кто-то смотрит примерно логику и жмёт "апрув". В Гугловском документе написана интересная мысль. MR не должен быть идеальным, но он должен улучшать кодовую базу. Т.е с каждым привносимым изменением код должен становиться лучше и лучше. И если `MR` добавляет много хорошего, то не надо придираться к мелочам; выгоднее, чтобы это улучшение попало в код побыстрее. Никакой `MR` не должен делать код хуже. Единственное исключение — это если MR является срочным фиксом чего-нибудь.

_Если ревьювер и автор MR не согласны друг с другом_

Сначала идет попытка достигнуть консенсуса в комментариях к `MR`. Если это не получается, то личное обсуждение. Если все равно не пришли к единому мнению, то привлекать членов команды. Но главное, `MR` не должен застревать надолго из-за несогласия двух человек.

Обсудили в коментах -> Обсудили лично -> Обсудили в команде -> Двигаемся дальше

__Если ты автор:__

_Описание MR_

В Google описание изменений сохраняется в истории системы контроля версий, и с большой вероятностью его будут читать очень много людей в будущем. Поэтому описание `MR` очень важно. В первой строчке (в заголовке) должно быть одной фразой описано, что было сделано в `MR`. Причем по традиции применяется императивный (повелительный) стиль, т.е. Delete blablabla, а не Deleting blablabla. Само описание должно быть информативным, содержать краткое описание решаемой проблемы, ссылки на необходимые документы (если необходимо), задачи таск трекера и другой контекст. Даже в маленьком `MR` что-то такое должно быть. Описание типа "Fix bug", понятное дело, считается неадекватным.

_MR должен быть как можно меньше_

Слишком большие MR нужно просить разбивать на части. Почти всегда это возможно.

- Маленький MR можно быстро проверить
- Проверка будет более осмысленной
- Меньше вероятность упустить баг
- Не так обидно, если весь `MR` будет отклонен
- Проще вливать изменения, меньше конфликтов
- Легче добиться хорошего качества кода
- Чем больше изменений за раз, тем сложнее откатывать код при такой необходимости

_Факты важнее персональных предпочтений_

Почти всегда стандартные принципы построения ПО (software design), базирующиеся на лучших практиках, лучше, чем хитровымученные велосипеды. Поэтому предпочтение нужно отдавать им. Если можно применить несколько стандартных подходов, то это на усмотрение автора.

_Не принимайте близко к сердцу_

Иногда ревьюверы ведут себя не очень вежливо, могут написать что-нибудь плохое про ваш код. Это не очень профессионально с их стороны, однако зачастую зерно истины в таких комментариях всё же есть, и это надо учитывать. Не отвечайте слишком резко. Это только усугубит ситуацию. В случае, если вам не нравится тон разговора в комментариях, лучше найти этого человека и пообщаться с ним лично, объяснить, что вас не устраивает. Если и это не помогло, обратитесь к менеджеру.

_Объясняйте кодом_

Если вас просят объяснить какой-то момент в коде, подумайте, нельзя ли поправить код так, чтобы он был понятен без объяснений. Потому что если один не понял, то и другие могут не понять.

_Реакция на комментарии ревьювера_

Зачастую, когда работа сделана и отправлена на код ревью, психологически довольно сложно принять тот факт, что придется еще и что-то исправлять. Поэтому постарайтесь не воспринимать комментарии ревьювера в штыки, подумайте, возможно он прав, и код станет в результате лучше. Однако если ревьювер все же не прав, смело пишите об этом, снабдив ответ аргументами и фактами.

__Если ты ревьюер:__

_Свобода делать замечания_

Несмотря на то, что нельзя задалбывать мелочами, тем не менее можно свободно эти мелочи писать хоть к каждой строчке. Противоречие с предыдущим пунктом решается просто: мелочи и придирки ревьювер помечает префиксом `nit:`. Такие замечания фиксить необязательно, однако автор `MR` может захотеть что-то исправить или, даже если нет, учесть на будущее некоторые моменты.

_Скорость проверки MR_

Скорость экстремально важна. Если раз в несколько дней давать по одному комменту, то автор `MR` будет жаловаться, что к нему придираются и не дают работать. Если `MR` проверяется очень быстро, то любые замечания не будут являться большой проблемой — ведь их фиксы тут проверят, и таск пройдет дальше. В Гугле советуют не отвлекаться от фокусировки над своей задачи, но если уж отвлеклись, то просмотреть, нет ли чего-то поревьювить. Например, вернулся с обеда — поревьювил. Пришел на работу — поревьювил.

_Порядок просмотра MR_

Сначала надо просмотреть `MR` в целом. Надо ли это вообще, в правильном ли месте код (или это должно быть в отдельной библиотеке), есть ли какие-то глобальные проблемы. Т.е. нет смысла смотреть какие-то детали реализации, если код вообще не туда и не для того. Вообще, порядок просмотра важен, чтобы как можно быстрее выдавать автору фидбек (смотри предыдущий пункт). Когда посмотрели `MR` вцелом, надо пройтись по основным файлам, т.е. проверить самое главное (если непонятно, что самое главное, можно спросить у разработчика). Опять же, о любых проблемах нужно сообщать сразу, даже если вы еще не досмотрели `MR` и решили вообще досмотреть его позже. Далее надо выбрать логичную последовательность просмотра оставшихся файлов. Ни один файл не должен быть пропущен.

На что обращать внимание при просмотре:

- Код хорошо спроектирован
- Функциональность хорошо сделана с точки зрения пользователей этого кода, кем бы они ни были.
- Внешний вид (если есть) должен быть хорошим
- Учтены все нюансы параллельного программирования (если есть).
- Код не переусложнен
- Разработчик не оверинженирит: не нужно писать код, который может понадобиться, а может не понадобиться
- У кода есть тесты
- Тесты хорошо спроектированы
- Наименования (для всего) выбраны хорошо
- Комментарии к коду понятны и необходимы. Они должны объяснять, почему так сделано, а не как это сделано.
- Добавлена документация.
- Код соответствует стайл гайдам.

_Как писать комментарии на код ревью_

Нужно быть вежливым, не переходить на личности. Обсуждать код, а не кодера. Не просто выдавать директивы к исправлениям, а объяснять, почему нужно исправить.
Соблюдать баланс: обозначить проблему и подтолкнуть разработчика, чтобы он сам понял, как лучше ее решить; или же сразу выдать готовое решение. Первое развивает разработчика (стратегическая выгода), второе улучшает и ускоряет MR (тактическая выгода). Если ревьювер не понял какой-то момент в коде и просит автора объяснить, что к чему, то лучшим ответом будет изменение кода. Так, чтобы было по коду все было понятно без вопросов.

_Если с вашим мнением не согласны_

Нужно разобраться детально. Возможно, вы чего-то не понимаете, запросите больше информации. Возможно наоборот. В любом случае, зачастую понимание приходит только после пары раундов объяснений с обеих сторон.

_Боязнь расстроить автора MR_

Бывает, что разработчик расстраивается, если ревьювер настаивает на каких-то изменениях. Однако, чаще всего разработчики расстраиваются из-за формы замечания, а не из-за содержания. Будьте вежливы, объясняйте аргументами, и скорее всего всё будет ок.

_"Я исправлю это потом"_

Если разработчик согласен с тем, что в коде есть проблема, но просит заапрувить `MR`, обещая, что исправит это в другой раз, то, по мнению ребят из Гугла, это "потом" чаще всего никогда не наступает. Поэтому если `MR` — не какой-то срочный багфикс прода, то нужно настаивать на исправлении.

<https://google.github.io/eng-practices/review/reviewer/>

<a name="fastlane"></a>

## Что такое fastlane и как он работает?

Fastlane  -  это инструмент для автоматизации процессов сборки и выкладки мобильных iOS и Android приложений, которая включает в себя также генерирование скриншотов, запуск Unit/UI тестов, отправка сообщений в Slack, подключение к Crashlytics и многие другие полезные вещи, которые упрощают жизнь.

- cert: автоматически скачивает и устанавливает необходимые сертификаты (Distribution, Development) для подписи собираемых приложений;
- increment_build_number: увеличивает номер билда на 1, либо изменяет на значение, заданное в параметре build_number
- sigh: автоматически скачивает и устанавливает все необходимые provision profiles;
- snapshot: запускает UI-тесты и делает скриншоты, которые можно использовать при отправке на review в App Store;
- gym: собирает архив и, здесь же, конечный ipa вашего приложения;
- scan: все просто  —  запускает таргет тестов;
- deliver: отправляет ipa, скриншоты, метаданные прямиком в App Store;
- pilot: загружает свежий ipa на бета тест в TestFlight. Также с помощью этой команды можно управлять тестировщиками.
- ... <https://docs.fastlane.tools/actions/>

<a name="ci-cd"></a>

## Что такое CI/CD и зачем он нужен?

Непрерывная интеграция (Continuous Integration, CI) и непрерывная поставка (Continuous Delivery, CD) представляют собой культуру, набор принципов и практик, которые позволяют разработчикам чаще и надежнее развертывать изменения программного обеспечения. CI/CD — это одна из DevOps-практик. Она также относится и к agile-практикам: автоматизация развертывания позволяет разработчикам сосредоточиться на реализации бизнес-требований, на качестве кода и безопасности.

__Непрерывная интеграция__ — это методология разработки и набор практик, при которых в код вносятся небольшие изменения с частыми коммитами. И поскольку большинство современных приложений разрабатываются с использованием различных платформ и инструментов, то появляется необходимость в механизме интеграции и тестировании вносимых изменений. С технической точки зрения, цель CI — обеспечить последовательный и автоматизированный способ сборки, упаковки и тестирования приложений. При налаженном процессе непрерывной интеграции разработчики с большей вероятностью будут делать частые коммиты, что, в свою очередь, будет способствовать улучшению коммуникации и повышению качества программного обеспечения.

__Непрерывная поставка__ начинается там, где заканчивается непрерывная интеграция. Она автоматизирует развертывание приложений в различные окружения: большинство разработчиков работают как с продакшн-окружением, так и со средами разработки и тестирования.

Непрерывная интеграция и непрерывная поставка нуждаются в __непрерывном тестировании__, поскольку конечная цель — разработка качественных приложений. Непрерывное тестирование часто реализуется в виде набора различных автоматизированных тестов (регрессионных, производительности и других), которые выполняются в CI/CD-конвейере.

Типичный CD-конвейер состоит из этапов сборки, тестирования и развертывания. Более сложные конвейеры включают в себя следующие этапы:

- Получение кода из системы контроля версий и выполнение сборки.
- Настройка инфраструктуры, автоматизированной через подход “инфраструктура как код”.
- Копирование кода в целевую среду.
- Настройка переменных окружения для целевой среды.
- Развертывание компонентов приложения (веб-серверы, API-сервисы, базы данных).
- Выполнение дополнительных действий, таких как перезапуск сервисов или вызов сервисов, необходимых для работоспособности новых изменений.
- Выполнение тестов и откат изменений окружения в случае провала тестов.
- Логирование и отправка оповещений о состоянии поставки.

Например, в Jenkins конвейер определяется в файле Jenkinsfile, в котором описываются различные этапы, такие как сборка (build), тестирование (test) и развертывание (deploy). Там же описываются переменные окружения, секретные ключи, сертификаты и другие параметры, которые можно использовать в этапах конвейера. В разделе post настраивается обработка ошибок и уведомления.

В более сложном CD-конвейере могут быть дополнительные этапы, такие как синхронизация данных, архивирование информационных ресурсов, установка обновлений и патчей. CI/CD-инструменты обычно поддерживают плагины. Например, у Jenkins есть более 1500 плагинов для интеграции со сторонними платформами, для расширения пользовательского интерфейса, администрирования, управления исходным кодом и сборкой.

<a name="thread-safe-array"></a>

## Как реализовать потоко-безопасный массив?

__Serial Queue Method__

By leveraging serial queues, we can enforce mutual exclusion on a resource. With a serial queue, only one process can run at a time, so if many processes are stuffed in a queue to modify the array, the serial queue will only let one process execute at a time; the array is safe from concurrent processes by design.

```swift
let queue = DispatchQueue(label: "MyArrayQueue")

queue.async() {
  // Manipulate the array here
}

queue.sync() {
  // Read array here
}
```

Dispatch queues are serial by default. We use this queue’s async method to write to the array and not worry about the result; we asynchronously set it and forget it. When reading from the array, we can use the sync method and get the results instantly. We can still do better though. The reads are not optimized because multiple read requests have to wait for each other in a queue. However, reads should be able to happen concurrently, as long as there isn’t a write happening at the same time.

__Concurrent Queue Method__

This technique is more elegant and uses a shared exclusion lock on the array. We will still use Grand Central Dispatch, but this time with a concurrent queue instead of a serial one. That might work for concurrent reads, but we must disallow all concurrency when writing. This can be achieved with the `barrier` flag for the dispatch queue:

```swift
let queue = DispatchQueue(label: "MyArrayQueue", attributes: .concurrent)

queue.async(flags: .barrier) {
  // Mutate array here
}

queue.sync() {
  // Read array here
}
```

Notice the async method has the barrier flag set for writes. This means no other blocks may be scheduled from the queue while the async/barrier process runs. We continue to use the sync method for reads, but all readers will run in parallel this time because of the concurrent queue attribute. Readers will still be blocked when a barrier process is running though. Even if there are several reader blocks already running in parallel, the barrier process will wait for all readers to finish before beginning the write. Once the barrier process is complete, then the readers behind it can run in parallel again. Sweet! 🙂

__What is the sense of using `sync` in concurrent queue? Isn't it the same as `sync` in serial queue?__

The `sync` has nothing to do with whether the destination queue is serial or concurrent. The `sync` only dictates the behavior of the calling thread, namely, should the caller wait for the dispatched task to finish or not. As a general rule, you should avoid calling sync unless
(a) you absolutely have to; and
(b) you are willing to have the calling thread blocked until the sync task runs.

So, with very few exceptions, one should use `async`. And, perhaps needless to say, we never block the main thread for more than a few milliseconds. While using `sync` on a concurrent dispatch queue is generally avoided, one example you might encounter is the “reader-writer” synchronization pattern. In this case, “reads” happen synchronously (because you need to wait the result), but “writes” happen asynchronously with a barrier (because you do not need to wait, but you do not want it to happen concurrently with respect to anything else on that queue).

<a name="code-style"></a>

## Какие ты знаешь стайл-гайды? Зачем они нужны?

1. Обеспечивает линейное развитие проекта и не влияет на объем кодовой базы. Если вы обеспечили историческое написание понятного кода, то, сколько бы не приходило и не уходило разработчиков, вы всегда имеете равное качество кода, что позволяет проекту динамично расти вне зависимости от его объема.

2. Значительно ускоряет процесс адаптации новых программистов. Если ваш код написан понятно, новый специалист очень быстро обучит свою нейросеть на определение блоков и начнет приносить пользу. Есть такое понятие, как точка самоокупаемости сотрудника. Это точка, с которой сотрудник начинает приносить только пользу. А если код написан понятно, новым сотрудникам не нужно разбираться в бизнес-логике, ему достаточно научится читать ваш код. И чем быстрее он это сделает, тем быстрее перестанет задавать тонны вопросов остальным специалистам, отнимая у них время. А время специалистов, которые прошли точку самоокупаемости, значительно дороже для команды и компании с точки зрения потенциальной ценности приносимой продукту.

3. Убирает зависимость от частностей. Не нужно будет постоянно спотыкаться о чью-то оригинальность и специфическое оформление.

4. Минимизирует эффект ментального блокера при изучении нового кода. Ваш мозг меньше сопротивляется, т.к. не нужно вникать в чужую стилистику. Ментальных ресурсов на чтение понятного кода нужно намного меньше.

5. Минимизирует репутационные потери. Очень скоро, после прибытия в новую компанию, программист начнет делиться впечатлениями с бывшими коллегами и друзьями. И он либо скажет, что тут все круто, либо выделит негативные моменты в работе с кодом. В каком-то смысле тут получается HR-бонус: если вы хотите, чтобы с вами работали крутые программисты, делайте хороший проект. Хоть это не всегда важно, и в ряде компаний на качество кода не смотрят в принципе, а смотрят лишь на доставку фич до прода, это приятный бонус. Не секрет, что частой причиной ухода становится усталость от постоянного перепиливания некачественной кодовой базы.

6. Формирует и воспитывает культуру разработки. Задача программиста лежит на более низком уровне, чем будущее всей компании, но важно донести понимание, что понятность и читаемость кода сейчас влияет на динамику дальнейшей разработки. Если код трудночитаем и не стандартизирован, с болью и страданиями поддается рефакторингу и масштабированию, то с ростом кодовой базы проекта, будет падать скорость разработки. Чем больше некачественного кода, тем сложнее писать новый, тем медленнее развивается продукт, тем сложнее компании наращивать обороты и тем сложнее ей платить вам больше денюжек, потому что много денюжек уходит на то, чтобы обеспечивать жизненный цикл проекта все новыми и новыми сотрудниками, который основное время онбоардинга тратят не на то, чтобы приносить пользу компании, а на классификацию наркотиков, под которыми этот код был написан.

Примеры:

<https://www.swift.org/documentation/api-design-guidelines/>

<https://github.com/raywenderlich/swift-style-guide>

<https://google.github.io/swift/>

<https://github.com/tutu-ru/swift-style-guide>

<https://github.com/linkedin/swift-style-guide>

<https://github.com/airbnb/swift>

<https://github.com/spotify/ios-style>

<a name="dependencies-managers"></a>

## Какие ты знаешь менеджеры зависимостей? В чем между ними разница?

A package manager is a tool that automates the process of installing, upgrading, configuring, and removing a software, or in this case, inside our app.

__CocoaPods__

CocoaPods is a centralized dependency manager for Swift and Objective-C Cocoa projects. It is open-source and was built with Ruby by many volunteers and the open-source community. CocoaPods is based on a main repository called Specs that hosts all the framework specifications. In order to make it available to others, package developers have to push new versions to this repository by using the pod command line.

Advantages

- CocoaPods make managing dependencies in your code easier
- Adding and removing dependencies is just a matter of defining them in a file and running a command to install them
- CocoaPods reads the file, determines the dependencies that the listed libraries have, and whether there are any shared dependencies or not
- We can search any kind of dependency in CocoaPods official website
- CocoaPods supports both dynamic and static libraries
- We can easily tell anyone what dependencies we are using in the app
- It's easy to check if a new version of a dependency is available by using the ‘pod outdated’ command
- Lots of contributors with well-grown community

Disadvantages

- Installation process will take more time to install CocoaPods
- With CocoaPods built on RUBY, it is paramount to have its knowledge, if one wants to understand CocoaPods internal implementation.
- Every time you build your project, all your dependencies will also be built, which leads to slower build times
- CocoaPods creates new workspace directory, which has xcworkspace extension. We have to use Xcode workspace in order to make CocoaPods work
- CocoaPods added some scripts in the build phases of our target
- Linked the Pods Frameworks to “Link Binaries with Libraries
- CocoaPods takes controls of entire Xcode project and if something fails, entire project stops building
- Breakpoints doesn’t work properly on the added libraries source code
- As CocoaPods has a centralised repository for all packages and in case of its service being down, a project cannot be built without committing the codes along the pods.
- CI/CD integration with server is hard as we have to install and manage Ruby libraries

__Carthage__

Carthage is a decentralized dependency manager for Swift and Objective-C Cocoa projects. It is open-source and built with Swift by the open-source community. Unlike CocoaPods, you don't have a main Specs repository. This reduces maintenance work and avoids any central points of failure, but project discovery is more difficult. For example, this means that checking for outdated dependencies means checking every dependency repository instead of a single centralized one.

Advantages

- Carthage is purely written in Swift so that iOS developers can understand the technology behind Carthage
- Supports both Dynamic Frameworks and Static Libraries
- Carthage won’t touch your Xcode settings or project files. It downloads and builds dependencies
- Carthage can be easily integrated with Continuous Integration server

Disadvantages

- Not every framework supports Carthage
- Carthage has too many manual steps that need to be performed during setup

__Swift Package Manager__

Advantages

- SPM works on both Mac and Linux platforms
- SPM is built by Apple
- We can easily say what dependencies we are using in the app
- SPM will not compile all the dependencies every time. Hence, compile time will reduce.
- If a package is depending on another package, SPM automatically handles it

Disadvantages

- Currently doesn't support all the platforms like iOS, watchOS, or tvOS.
- You have to follow a specific folder structure.
- Some features on the Foundation corelib are unimplemented. You can find the current status here.
- Creating Unit Tests on Linux is not easy as on macOS. You also have to do additional turnaround.

__Зачем мигрировать с Cocoapods на SPM?__

- Нативность и интеграция в экосистему. Уже сейчас Xcode предлагает создать или добавить SPM Package.
- В отличие от Cocoapods, больше не обязательно иметь workspace для работы над проектом с зависимостями.
- Добавив новую зависимость, не нужно делать pod install и пересобирать весь проект.
- Удобно использовать локальные зависимости: не меняется структура папок, быстрее пересобирается.
- SPM не меняет структуру файла проекта, как это делает Cocoapods, не требует зависимости от Ruby и даже может сгенерировать файл проекта сам (пока недоступно для iOS-проектов).
- Cocoapods не успевает справляться с нововведениями в Xcode и компилятор Swift.
- Не нужно создавать проект Example для каждого репозитория: Xcode умеет открывать Package.swift файл как проект.
- Не нужно оптимизировать дерево зависимостей при помощи abstract_target: SPM из коробки умеет не перекомпилировать код для разных таргетов с общими зависимостями.
- Можно смотреть blame в зависимостях, а не только в основном проекте.
- Не нужно писать скрипты на Ruby, чтобы починить конфигурацию проекта.

<a name="dynamic-vs-static-library"></a>

## Чем отличается статическая библиотека от динамической?

**What is a Library?**

Libraries are files that define pieces of code and data that are not a part of your Xcode target.

The process of merging external libraries with app’s source code files is known as linking. The product of linking is a single executable file that can be run on a device, say iPhone or Mac. Besides linking, every Xcode project undergoes 4 more phases to produce an executable application. Libraries fall into two categories based on how they are linked to the app:

- Static libraries — .a
- Dynamic libraries — .dylib

Additionally, a special kind of libraries exists:

- Text Based .dylib stubs — .tbd

**What is a Framework?**

Framework is a package that can contain resources such as dynamic libraries, strings, headers, images, storyboards etc. With small changes to its structure, it can even contain other frameworks. Such aggregate is known as umbrella framework.

Frameworks are also bundles ending with `.framework` extension. They can be accessed by `NSBundle` / `Bundle` class from code and, unlike most bundle files, can be browsed in the file system that makes it easier for developers to inspect its contents. Frameworks have versioned bundle format which allows to store multiple copies of code and headers to support older program version.

**Static Library**

Static libraries are collections of object files. In its turn, object file is just a name for a file that comes out of a compiler and contains machine code. Static libraries are ending with `.a` suffix and are created with an archiver tool. If it sounds very similar to a ZIP archive, then it’s exactly what it is. You can think of a static library as an archive of multiple object files. `.a` is an old format originally used by UNIX and its ar tool. Object files have `Mach-O` format which is a special file format for iOS and macOS operating systems. It is basically a binary stream with the following chunks:

- Header: Specifies the target architecture of the file. Since one `Mach-O` contains code and data for one architecture, code intended for `x86-64` will not run on `arm64`.
- Load commands: Specify the logical structure of the file, like the location of the symbol table.
- Raw segment data: Contains raw code and data.

An attentive eye might have noticed that `Mach-O` files support single architecture. Then how can a Swift app with lots of static libraries run on all devices and even the simulator? The answer is `lipo` tool. It allows to package multiple single architecture libraries into a universal one, called fat binary, or vice-versa. 

**Dynamic Library**

Dynamic libraries, as opposed to the static ones, rather than being copied into single monolithic executable, are loaded into memory when they are actually needed. This could happen either at load time or at runtime. Dynamic libraries are usually shared between applications, therefore the system needs to store only one copy of the library and let different processes access it. As a result, invoking code and data from dynamic libraries happens slower than from the static ones. All iOS and macOS system libraries are dynamic. Hence our apps will benefit from the future improvements that Apple makes to standard library frameworks without creating and shipping new builds.

**Text Based .dylib Stubs**

When we link system libraries, such as `UIKit` or `Foundation`, we don’t want to copy their entirety into the app, because it would be too large. Linker is also strict about this and does not accept shared `.dylib` libraries to be linked against, but only `.tbd` ones. So what are those? Text-based `.dylib` stub, or `.tbd`, is a text file that contains the names of the methods without their bodies, declared in a dynamic library. It results in a significantly lower size of `.tbd` compared to a matching `.dylib`. Along with method names, it contains location of the corresponding .dylib, architecture, platform and some other metadata. 
Comparing Static vs. Dynamic Libraries

**Static Libraries**

✓ Pros:

- Static libraries are guaranteed to be present in the app and have correct version.
- No need to keep an app up to date with library updates.
- Better performance of library calls.

✕ Cons:

- Inflated app size.
- Launch time degrades because of bloated app executable.
- Must copy whole library even if using single function.
  
**Dynamic Libraries**

✓ Pros:

- Can benefit from library improvements without app re-compile. Especially useful with system libraries.
- Takes less disk space, since it is shared between applications.
- Faster startup time, as it is loaded on-demand during runtime.
- Loaded by pieces: no need to load whole library if using single function.
  
✕ Cons:

- Can potentially break the program if anything changes in the library.
- Slower calls to library functions, as it is located outside application executable.
  
**Summary**

- Libraries and frameworks are basic building blocks for creating iOS and macOS programs.
- Libraries are collections of code and data, while frameworks are hierarchial directories with different kinds of files, including other libraries and frameworks.
- Based on how libraries are linked, they can be static or dynamic. Each kind of linking comes with its pros and cons. Understanding them will help you to make the right choice between static and dynamic libraries for your project.

<a name="array-with-weak"></a>

## Как положить в массив weak объекты?

1. Foundation classes
  
- `NSPointerArray`: A collection similar to an array, but with a broader range of available memory semantics.
- `NSHashTable`: A collection similar to a set, but with broader range of available memory semantics.
- `NSMapTable`: A collection similar to a dictionary, but with a broader range of available memory semantics.

2. Custom container

```swift
class Weak<T: AnyObject> {
  weak var value : T?
  init (value: T) {
    self.value = value
  }
}

class Stuff {}
var weakly : [Weak<Stuff>] = [Weak(value: Stuff()), Weak(value: Stuff())]
```

3. Functional Solution

```swift
let foo = Foo()

var foos = [() -> Foo?]()
foos.append({ [weak foo] in return foo })

foos.forEach { $0()?.doSomething() }
```

<a name="agile-scrum-kanban"></a>

## Что такое agile, scrum и kanban?

Agile (agile software development, от англ. agile – проворный) – это семейство «гибких» подходов к разработке программного обеспечения. Такие подходы также иногда называют фреймворками или agile-методологиями. Agile возник в IT-среде, но затем распространился и в другие сферы – от промышленной инженерии до искусственного интеллекта.

Смысл Agile сформулирован в Agile-манифесте разработки ПО: 
> Люди и взаимодействие важнее процессов и инструментов. Работающий продукт важнее исчерпывающей документации. Сотрудничество с заказчиком важнее согласования условий контракта. Готовность к изменениям важнее следования первоначальному плану.

Agile-манифест – главный документ всех «гибких» подходов к разработке. Он был создан в 2001 году группой энтузиастов-программистов, которые хотели понять, что именно лежит в основе разработки востребованного и полезного IT-продукта. Agile предполагает, что при реализации проекта не нужно опираться только на заранее созданные подробные планы. Важно ориентироваться на постоянно меняющиеся условия внешней и внутренней среды и учитывать обратную связь от заказчиков и пользователей. Это поощряет разработчиков и инженеров экспериментировать и искать новые решения, не ограничивая себя жесткими рамками и стандартами.

К отдельным agile-подходам относятся scrum и kanban.

Scrum – это «подход структуры». Над каждым проектом работает универсальная команда специалистов, к которой присоединяется еще два человека: владелец продукта и scrum-мастер. Первый соединяет команду с заказчиком и следит за развитием проекта; это не формальный руководитель команды, а скорее куратор. Второй помогает первому организовать бизнес-процесс: проводит общие собрания, решает бытовые проблемы, мотивирует команду и следит за соблюдением scrum-подхода. Scrum-подход делит рабочий процесс на равные спринты – обычно это периоды от недели до месяца, в зависимости от проекта и команды. Перед спринтом формулируются задачи на данный спринт, в конце – обсуждаются  результаты, а команда начинает новый спринт. Спринты очень удобно сравнивать между собой, что позволяет управлять эффективностью работы.

Kanban – это «подход баланса». Его задача – сбалансировать разных специалистов внутри команды и избежать ситуации, когда дизайнеры работают сутками, а разработчики жалуются на отсутствие новых задач. Вся команда едина – в kanban нет ролей владельца продукта и scrum-мастера. Бизнес-процесс делится не на универсальные спринты, а на стадии выполнения конкретных задач: «Планируется», «Разрабатывается», «Тестируется», «Завершено» и др. Главный показатель эффективности в kanban – это среднее время прохождения задачи по доске. Задача прошла быстро – команда работала продуктивно и слаженно. Задача затянулась – надо думать, на каком этапе и почему возникли задержки и чью работу надо оптимизировать.

Для визуализации agile-подходов используют доски: физические и электронные. Они позволяют сделать рабочий процесс открытым и понятным для всех специалистов, что важно, когда у команды нет одного формального руководителя.

<a name="rendering"></a>

## Как происходит рендеринг графики?

**FPS**

Количество сменяемых кадров за единицу времени. Дисплеи iPhone и iPad обновляются с 60 Гц. Новый iPhone 13 может и 120 Гц. Дисплеи новейших iPad Pro с частотой 120 Гц. Приложение должно иметь возможность отображать кадры с частотой отображения. Частота 60 Гц означает 60 кадров в секунду для приложения, ~16,67 мс для рендеринга кадра. Обратите внимание, это не обязательно означает, что приложение выполняет рендеринг 60 раз в секунду. Когда содержимое не меняется, нет необходимости его перерисовывать.

**Render Loop**

Цикл отрисовки в системе iOS. 

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/rendering_1.png">

- Получаем событие
- Создаем render tree
- Отправляем на Render Server
- Меняем кадр

**Event**

Сначала происходит какое-то событие (Тач, колбэк с сети, действие с клавиатуры, таймеры). Допустим мы хотим изменить `bounds` нашей вьюхи, то `Core Animation` вызывает метод `setNeedsLayout`. Система понимает, что нужно вызвать апдейт лайут реквеста.

**Commit Transaction**

В основе всех обновлений слоев и анимаций лежит `Core Animation`. Этот фреймворк работает не только внутри самого приложения, но и между другими приложениями. Когда мы переключаемся из приложения в приложение. Сама анимация происходит в другом этапе, за рамками нашего приложения. Этот этап называется render server. На этапе же commit transaction происходит подготовка layer tree и его неявная транзакция для обновления.
> Транзакции — это механизм, который Core Animation использует для обновления свойств. Любые свойства наших слоев не изменяются мгновенно, а вместо этого подготавливаются в транзакцию и ждут своего коммита

Когда мы хотим выполнить анимацию, то сначала проходим 4 этапа:

- Layout — На этом этапе мы подготавливаем вьюхи, их свойства (frame, background color, border и другие). Как только лайаут расчитался, система вызывает метод `setNeedsDisplay`.
- Display — обновляет `CGContext`. Это рисование может включать вызов функций `drawRect`, `drawLayer` каждых `subviews`
- Prepare — На этом этапе `Core Animation` готовится отправить данные анимации на render server. Здесь происходит подготовка и декодинг картинок
- Commit — Это заключительный этап, когда `Core Animation` упаковывает слои и свойства анимации и отправляет их через Interprocess communication (IPC) на render server для отображения.
  
`Core Animation` объединяет изменения в транзакцию, кодирует их и фиксирует на render server.

**Render Server**

Теперь мы на рендер сервере — это отдельный процесс, который вызывает методы отрисовки для GPU с использованием `OpenGL` или `Metal`. Он отвечает за рендер наших слоев в изображение

**Render Prepare**

На этом этапе происходит пробег про layer tree и мы подготавливаем layer pipeline для выполнения его на GPU. Рекурсивно пробегаясь от родительского слоя к дочернему.

**Render Execute**

После layers pipeline передан на отрисовку. Где каждый слой будет собран в финальную текстуру. До этого момента все вычисления происходили в CPU, но дальше работа перешла в руки GPU. Некоторые слои будут отображаться дольше, чем обычные. И это чаще всего то самое бутылочное горлышко для оптимизаций. Как только GPU выполняет отрисовку изображений, то это готово к отображению для следующего VSYNC
**VSYNC** — это дедлайн для каждой фазы нашего рендер лупа. Каждый VSYNC — меняет нам следующий кадр. Для достижения лучшей оптимизации каждый фрейм распараллеривается. Пока CPU читает кадр номер N, в это время GPU рендерит предыдущий кадр N-1

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/rendering_2.png">

**Проблемы с производительностью**

Если мы перегрузим наше приложение или будем плохо следить за ресурсами, то можем столкнуться с такими проблемами:

- Потеря кадров
- Быстрая трата батареи
- Долгая отзывчивость
  
На main thread выполняется код, который отвечает за ивенты типа касания и работу с UI. Он же рендерит экран. В большинстве современных смартфонов рендеринг происходит с частотой 60 кадров в секунду. Это значит, что задачи должны выполняться за 16,67 миллисекунд (1000 миллисекунд / 60 кадров). Поэтому ускорение работы в Main Thread — важно. Если какая-то операция занимает больше 16,67 миллисекунд, автоматически происходит потеря кадров, и пользователи приложения заметят это при воспроизведении анимаций. На некоторых устройствах рендеринг происходит ещё быстрее, например, на iPad Pro 2017 частота обновления экрана составляет 120 Гц, поэтому на выполнение операций за один кадр есть всего 8 миллисекунд.

**Offscreen Rendering**

Внеэкранные расчеты. Под капотом это выглядит следующим образом: во время прорисовки слоя, которому необходима внеэкранные расчеты, GPU останавливает процесс визуализации и передает управление CPU. В свою очередь, CPU выполняет все необходимые операции (например, cоздает тень) и возвращает управление GPU с уже прорисованным слоем. GPU визуализирует его и процесс прорисовки продолжается. Кроме того, offscreen rendering требует выделения дополнительной памяти, для так называемого резервного хранилища. В то же время, она не нужна для прорисовки слоев, где используется аппаратное ускорение. Нашему GPU потребуется дополнительная обратка в случае, если мы изменим свойства ниже:

Тени

Тут все просто. Рендеру не хватает информации для отрисовки тени, поэтому тут расчет тени происходит отдельно. Будет добавлен дополнительный слой. Этот слой был нарисован первым

Маски для `CALayer`

Рендерер должен отобразить поддерево слоев под маской. Но также нужно избежать перезаписи пикселей за пределами маски.
Поэтому мы будем хранить всю информацию об изображение, пока пиксели под маской не будут рассчитаны и не помещены в финальную текстуру.
Эти закадровые вычисления могут хранить множество пикселей, которые юзер никогда не увидит

Радиус закругления углов

Этот тип связан с маской. Закругление углов у слоя также может рассчитываются заэкранно. Если рендерингу не хватает инфы, то он может отрисовать вью полностью и скопировать инфу о пикселях внутри

Визуальные эффекты

Эта работа связана с двумя эффектами:

- Яркостью
- Блюр

Чтобы применить эффект рендер должен скопировать контент под визуальным эффектом в другую текстуру, что хранится в закадровом буфере. Затем применить визуальный эффект к результату и скопировать обратно в рендер буфер

Слишком большое изображение
   
Если вы пытаетесь нарисовать изображение, размер которого превышает максимальный размер текстуры, поддерживаемый GPU (обычно 2048 × 2048 или 4096 × 4096, в зависимости от устройства), для предварительной обработки изображения необходимо использовать CPU. Что может повлиять на перфоманс каждый раз при отрисовке множества таких изображений

Смешивание цветов

Смешивание — это операция кадровой визуализации, которая определяет конечный цвет пикселя. Каждый `UIView` (честно говоря, `CALayer`) влияет на цвет конечного пикселя, на пример, в случае объединения набора таких свойств, как `alpha`, `backgroundColor`, `opaque` всех вышележащих вью

Непрозрачность vs Прозрачность

`UIView.opaque` — это подсказка для визуализатора, что позволяет рассмотреть изображения в качестве полностью непрозрачной поверхности, тем самым улучшая качество отрисовки. Непрозрачность означает: "Ничего не рисуй под поверхностью». `UIView.opaque` позволяет пропускать отрисовку нижних слоев изображения и тем самым смешивание цветов не происходит. Будет использоваться самый верхний цвет для вью.

Alpha

Если значение `alpha` меньше `1`, то значение opaque будет игнорироваться, даже если оно равно `YES`. Несмотря на то, что значение непрозрачности по умолчанию — `YES`, в результате мы получаем смешивание цветов, поскольку мы сделали наше изображение прозрачным, установив значение `alpha` меньше `1`. Делайте слои непрозрачными, когда это возможно — при условии, что у них одинаковые цвета, которые накладываются друг на друга. У слоя есть свойство `opacity`, которому и надо выставить единицу. Всегда проверяйте, что фоновый цвет задан и он непрозрачный.

Переопределение метода `drawRect`

Если мы переопределили метод `drawRect`, то мы вносим значительную нагрузку до того, как мы что-то внутри нарисовали. Чтобы поддерживать произвольное рисование в содержимом слоя, `Core Animation` должен создать фоновое изображение в памяти, равное по размеру размерам вьюхи.
Затем, как только рисунок будет завершен, он должен передать эти данные через IPC на render server. Вдобавок к этим накладным расходам отрисовка `Core Graphics` в любом случае очень медленная, и это точно не тот случай, когда вы захотите делать в критической ситуации с производительностью.

Декодинг изображений и даунсамлинг изображений

В общем случае, декодирование jpeg-изображений стоит делать в фоне. Большинство сторонних библиотек (AsyncDisplayKit, SDWebImage и т.д.) могут делать это по умолчанию. Если вы не хотите использовать фреймворки, то можно сделать декодирование вручную. Для этого вы можете написать расширение над `UIImage`, в котором создадите контекст и вручную отрисуете изображение.

`shouldRasterize`

В настоящее время Apple в значительной степени поддерживает свойство `shouldRasterize`. Включение этого свойства вызывает заэкранный рендеринг, но визуализированный контент будет кэшироваться, его можно повторно использовать при определенных условиях. Если это свойство используется правильно, потребление производительности может быть сведено к минимуму. Если эти условия соблюдены, вы можете использовать `shouldRasterize`: слой и его дочерние слои должны быть статичными, потому что, как только что-то изменится, кеш становится недействительным. Если это случается часто, мы возвращаемся то каждый кадр будет нагружать систему. Это то, чего разработчики должны избегать.
На этом основные моменты работы рендер лупа и его оптимизации я описал. В дальнешем планирую статьи о фреймворках, которые работают с графикой, видео и аудио.