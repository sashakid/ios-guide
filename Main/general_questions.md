- [Общие вопросы и задачи](#общие-вопросы-и-задачи)
	- [Inout parameters, pass by value, pass by reference](#inout-parameters,-pass-by-value,-pass-by-reference)
	- [Заполнить строку буквами А, чтобы не делать миллионы итераций](#заполнить-строку-буквами-a, чтобы-не-делать-миллионы-итераций)
	- [Написать процедуру, инвертирующую массив символов](#написать-процедуру,-инвертирующую-массив-символов)
	- [Поверхностное и глубокое копирование](#поверхностное-и-глубокое-копирование)
	- [Отличие while от for](#отличие-while-от-for)
	- [Протокол? Что такое абстрактный класс? Чем абстрактный класс отличается от интерфейса?](#протокол?-что-такое-абстрактный-класс?-чем-абстрактный-класс-отличается-от-интерфейса?)
	- [Какие существуют root классы в iOS? Для чего нужны root классы?](#какие-существуют-root-классы-в-ios?-для-чего-нужны-root-классы?)
	- [Чем категория отличается от расширения?](#чем-категория-отличается-от-расширения?)
	- [Можно ли добавить ivar в категорию?](#можно-ли-добавить-ivar-в-категорию?)
	- [Когда лучше использовать категорию, а когда наследование?](#когда-лучше-использовать-категорию,-а-когда-наследование?)
	- [Формальные и неформальные протоколы](#формальные-и-неформальные-протоколы)
	- [Есть ли приватные или защищенные методы в Objective-C? А в Swift?](#есть-ли-приватные-или-защищенные-методы-в-objective-c?-а-в-swift?)
	- [Что не так с этим кодом? Зачем нужны инициализаторы?](#что-не-так-с-этим-кодом?-зачем-нужны-инициализаторы?)
	- [Что такое назначеный инициализатор, напишите любой элементарный инициализатор, почему он так выглядит?](#что-такое-назначеный-инициализатор,-напишите-любой-элементарный-инициализатор,-почему-он-так-выглядит?)
	- [Какой метод вызовется: класса A или класса B?](#какой-метод-вызовется:-класса-a-или-класса-b?)
	- [Что выведется в консоль? Почему?](#что-выведется-в-консоль?-почему?)
	- [Как работают push нотификации?](#как-работают-push-нотификации?)
	- [Memory warning](#memory-warning)
	- [Как лучше всего загрузить UIImage из кеша?](#как-лучше-всего-загрузить-uiimage-из-кеша?)
	- [Какой контент лучше хранить в Documents, а какой в Cache?](#какой-контент-лучше-хранить-в-documents,-а-какой-в-сache?)
	- [Как из строки вытащить подстроку?](#как-из-строки-вытащить-подстроку?)
	- [NSCoding, archiving?](#nscoding,-archiving?)
	- [Как работает UITableView?](#как-работает-uitableview?)
	- [Константы, typedef, enum, #define](#константы,-typedef,-enum,-#define)
	- [Что такое awakeFromNib?](#чтo-такое-awakefromnib?)
	- [Что происходит когда мы пытаемся вызвать метод у nil указателя? Разница между nil и Nil](#что-происходит-когда-мы-пытаемся-вызвать-метод-у-nil-указателя?-Разница-между-nil-и-nil)
	- [Что такое неформальный протокол?](#что-такое-неформальный-протокол?)
	- [В чем разница между NSString и char? Что значит приставка NS в общем?](#в-чем-разница-между-nsstring-и-char?-что-значит-приставка-ns-в-общем?)
	- [Опишите иерархию классов от UIButton до NSObject](#опишите-иерархию-классов-от-uibutton-до-nsobject.)
	- [Что такое контекст?](#что-такое-контекст?)
	- [NSArray arrayWithObjects: a, b, c, nil; зачем nil вконце?](#nsarray-arraywithobjects:-a,-b,-c,-nil;-зачем-nil-вконце?)
	- [Задача про банерокрутилку](#задача-про-банерокрутилку)
	- [Задача на регулярное выражение](#задача-на-регулярное-выражение)
	- [Метод, возвращающий N наиболее часто встречающихся слов во входной строке](#метод,-возвращающий-n-наиболее-часто-встречающихся-слов-во-входной-строке)
	- [Используя NSURLConnection, напишите метод для асинхронной загрузки текстового документа по HTTP. Приведите пример его использования](#используя-nsurlconnection,-напишите-метод-для-асинхронной-загрузки-текстового-документа-по-http.- приведите-пример-его-использования)
	- [Перечислите все проблемы, которые вы видите в приведенном ниже коде. Предложите, как их исправить](#перечислите-все-проблемы,-которые-вы-видите-в-приведенном-ниже-коде.-предложите,-как-их-исправить)

# Общие вопросы и задачи
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

## Заполнить строку буквами А, чтобы не делать миллионы итераций
```objectivec
NSString *str = @"a";
for (int i = 0; i< 5000000; i++) {
  str = [str stringByAppendingString:@"a"];
}
```
_Ответ_
```objectivec
str =[@"" stringByPaddingToLength:5000000 withString:@"a" startingAtIndex:0];
```

## Написать процедуру, инвертирующую массив символов
__Способ 1__
```objectivec
// myString is "hi"
NSMutableString *reversedString = [NSMutableString string];
NSInteger charIndex = [myString length];
while (charIndex > 0) {
  charIndex--;
  NSRange subStrRange = NSMakeRange(charIndex, 1);
  [reversedString appendString:[myString substringWithRange:subStrRange]];
}
NSLog(@"%@", reversedString); // outputs "ih"
```
__Способ 2__
```objectivec
array.reverseObjectEnumerator.allObjects;
```
__Способ 3__
```c++
#include <string.h>
/* reverse: переворачивает строку s (результат в s) */
void reverse(char s[]) {
  int c, i, j;
  for (i = 0, j = strlen(s) - 1; i < j; i++, j--) {
    с = s[i];
    s[i] = s[j];
    s[j] = c;
  } 	
}
```
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

## Отличие while от for
Единственное отличие `while` от `for` в том, что в нем проверяется условие выполнения: ни объявить, ни изменить переменную в конструкции `while` нельзя. Поэтому чтобы выйти из цикла нужно изменять переменные внутри самого цикла так, чтобы условие стало ложным.

## Протокол? Что такое абстрактный класс? Чем абстрактный класс отличается от интерфейса?
Базовый класс, который не предполагает создания экземпляров. Абстрактные классы реализуют на практике один из принципов ООП — полиморфизм. Абстрактный класс может содержать (и не содержать) абстрактные методы и свойства. Абстрактный метод не реализуется для класса, в котором объявлен, однако должен быть реализован для его неабстрактных потомков. Абстрактные классы представляют собой наиболее общие абстракции, то есть имеющие наибольший объём и наименьшее содержание.
В Objective-C есть родительский класс `NSObject`. В языке программирования он как точка в геометрии. Это идеальный класс: в нём нет ничего лишнего, он ничего конкретного делает, но из него можно создать всё что угодно.

Пример: «Примус» — может быть наследником абстрактного класса «Нагревательный прибор»

Главное отличие класса от интерфейса — в том, что класс состоит из интерфейса и реализации.

Язык Objective-C содержит полноценную поддержку протоколов (это аналог интерфейса в Java и абстрактного класса в C++, который также иногда принято называть интерфейсом). Протокол представляет собой просто список описаний методов. Объект реализует протокол, если он содержит реализации всех методов, описанных в протоколе. Абстрактные классы могут содержать в себе реализацию некоторых методов, интерфейсы содержат только прототипы.
Однажды кто-то сказал: «То, что ты есть, и то, что ты делаешь – не одно и то же». Это утверждение справедливо и для объектов: класс объекта не всегда совпадает с его ролью в работающей системе. Например, объект может быть экземпляром `NSМutаblеАrrау`, тогда как в приложении он может обеспечивать управление очередью заданий печати. Действительно хорошо написанный класс имеет более общую природу, которая не ограничивается его ролью в одном конкретном приложении. Это позволяет по разному использовать экземпляры данного класса (полиморфизм). Мы уже говорили о том, как определить класс. Возможно ли определить роль? В определенной степени для определения роли можно использовать конструкцию `@protocol`.

## Какие существуют root классы в iOS? Для чего нужны root классы?
NSObject
NSProxy

A root class inherits from no other class and defines an interface and behavior common to all objects in the hierarchy below it. All objects in that hierarchy ultimately inherit from the root class. A root class is sometimes referred to as a base class. The root class of all Objective-C classes is `NSObject`, which is part of the Foundation framework. All objects in a Cocoa or Cocoa Touch application ultimately inherit from `NSObject`. This class is the primary access point whereby other classes interact with the Objective-C runtime. It also declares the fundamental object interface and implements basic object behavior, including introspection, memory management, and method invocation. Cocoa and Cocoa Touch objects derive the ability to behave as objects in large part from the root class. The Foundation framework defines another root class, `NSProxy`, but this class is rarely used in Cocoa applications and never in Cocoa Touch applications.

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
## Можно ли добавить ivar в категорию?
Директива `@interface` для категорий не может добавлять переменных экземпляра. Однако, она может определять, что категория поддерживает дополнительные протоколы.

## Когда лучше использовать категорию, а когда наследование?
В отличие от наследования, категории не могут добавлять новые переменные в класс. Однако, вы можете переопределять существующие методы в классе, но должны быть очень осторожны. Запомните, что все изменения сделанные в классе через категории повлияют на все экземпляры данного объекта в программе.

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

## Есть ли приватные или защищенные методы в Objective-C? А в Swift?
Нет. Нужно использовать расширение.
Для имитации private методов с помощью расширения, нужно в .m файле, перед `@implementation` добавить безымянную категорию. Для класса `Something` ее определение будет выглядеть как `@interface Something () ... @end`. Стоит обратить особое внимание на пустые скобки — они показывают, что мы определяем именно безымянную категорию. После этого, мы можем добавлять в категорию методы, которые будут для нас считаться private. За счет того, что категория безымянная, имплементация данных методов может находиться рядом с имплементацией основных методов в разделе `@implementation .. @end` и нет необходимости создавать отдельные разделы для имплементации категорий. А за счет того, что она находится в .m файле, которые никто не подключает через `#import`, видимость методов для автодополнения ограничена текущим файлом. Конечно, послать объекту это сообщение извне все равно возможно, но от случайного вызова вы точно застрахованы.

## Что не так с этим кодом? Зачем нужны инициализаторы?
```objectivec
[[[SomeClass alloc] init] init];
```
Пример: есть класс `A`, который имеет поле `NSString *b` и в ините ты делаешь `_b = @"somestring";` Стринг `b` не хранится в памяти выделенной под `A` – в этой памяти хранится лишь ссылка на `b`, а сам объект создается вовне. При повторном ините стринг просто пересоздастся, не стерев старый, и мы получаем утекший стринг. Вообще, такая ситуация есть далеко не везде, и далеко не всегда вызовет проблемы. Но кастомные повторные инициализации реально могут вызывать утечки памяти — зависит от конкретного типа объекта. Двойной инит может вызвать утечку. А может не вызвать. Каждый конкретный класс - отдельный вопрос.

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
## Какой метод вызовется: класса A или класса B?
```objectivec
@interface A : NSObject
- (void)someMethod;
@end

@implementation A
- (void)someMethod {
  NSLog(@"This is class A");
}
@end

@interface B : A
@end

@implementation B
- (void)someMethod {
  NSLog(@"This is class B");
}
@end

@interface C : NSObject
@end

@implementation C
- (void)method {
  A *a = [B new];
  [a someMethod];
}
@end
```
Вызовется метод класса B.

## Что выведется в консоль? Почему?
```objectivec
- (BOOL)objectsCount {
  NSMutableArray *array = [NSMutableArray new];
  for (NSInteger i = 0; i < 1024; i++) {
    [array addObject:[NSNumber numberWithInt:i]];
  }
  return array.count; //return array.count > 0;
}

- (void)someMethod {
  if ([self objectsCount]) {
    NSLog(@"has objects");
  } else {
    NSLog(@"no objects");
  }
}
```
При касте из `NSUInteger` в `BOOL` проверяется на равенство нулю последний несущий байт числа, который равен нулю, если число кратно `256`.

## Как работают push нотификации?
iOS-приложения не могут долгое время находиться в фоновом режиме. В целях сохранения заряда батареи приложениям, работающим в фоне, разрешено выполнять ограниченный набор действий. Вместо того, чтобы беспрерывно проверять события или производить какие-либо действия в фоновом режиме, вы можете создать серверную сторону приложения, которая будет выполнять эти действия. А когда наступит интересующее событие, серверная сторона сможет отправить приложению push-уведомление. Абсолютно любое push-уведомление может выполнять следующие три действия:
* Показать короткое текстовое сообщение.
* Воспроизвести короткий звуковой сигнал.
* Установить число на бейдже иконки приложения.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/apns.png">

APNS cервер – Apple Push Notification Server.

## Memory warning
iOS 2.0 and later.

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

## Как лучше всего загрузить из кеша?
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
## Какой контент лучше хранить в Documents, а какой в Cache?
Кеш - это специальный буфер (контейнер), содержащий информацию. Эта информация может быть запрошена с наибольшей вероятностью. Соответственно, доступ к этому буферу должен быть очень быстрым, он должен быть быстрее чем доступ к сети или к данным на жестком диске. В операционной системе iOS присутствует функция кэширования, но прямого доступа к данным в кэше нету. Для получения доступа следует использовать класс `NSCache`.
* Only documents and other data that is user-generated, or that cannot otherwise be recreated by your application, should be stored in the `<Application_Home>/Documents` directory and will be automatically backed up by iCloud.
* Data that can be downloaded again or regenerated should be stored in the `<Application_Home>/Library/Caches` directory. Examples of files you should put in the Caches directory include database cache files and downloadable content, such as that used by magazine, newspaper, and map applications.
* Data that is used only temporarily should be stored in the `<Application_Home>/tmp` directory. Although these files are not backed up to iCloud, remember to delete those files when you are done with them so that they do not continue to consume space on the user’s device.
* Use the "do not back up" attribute for specifying files that should remain on device, even in low storage situations. Use this attribute with data that can be recreated but needs to persist even in low storage situations for proper functioning of your app or because customers expect it to be available during offline use. This attribute works on marked files regardless of what directory they are in, including the Documents directory. These files will not be purged and will not be included in the user's iCloud or iTunes backup. Because these files do use on-device storage space, your app is responsible for monitoring and purging these files periodically.

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

## NSCoding, archiving?
`NSCoder` — это абстрактный класс который преобразует поток данных. Используется для архивации и разархивации объектов.
Протокол `<NSCoding>` позволяет реализовать архивирование или разархивирование данных. Например, у нас есть обьект мы его можем сохранить, а при следующей загрузке приложения подгрузить обратно. Часто программе требуется хранить состояние объектов в файле для дальнейшего их полного либо частичного восстановления, а также работы с ними. Такой процесс называют сериализацией. Многие современные языки и фреймворки предоставляют для этого вспомогательные средства. Рассмотрим, что нам предоставляет Cocoa Framework для Objective-C.
Сериализованный объект – объект, преобразованный в поток байтов для сохранения в файле или передачи по сети. `NS(M)Array`, `NS(M)Dictionary`, `NS(M)Data`, `NS(M)String`, `NSNumber`, `NSDate`. Сохранить состояние объекта в Cocoa Framework можно двумя способами при помощи:

* архивации (archivation)
* сериализации (serialization)

Каждый из них имеет свои области применения. Так, при помощи сериализации нельзя сохранить объект пользовательского класса. Рассмотрим подробнее оба способа. Протокол `<NSCoding>` объявляет два метода, которые должен реализовать класс, так что экземпляры этого класса могут быть закодированы и декодированы. Эта возможность обеспечивает основу для архивирования (где объекты и другие структуры хранятся на диске) и распространения (где объекты копируются в разные адресные пространства).

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

## Как работает UITableView?
```
UITableView : UIScrollView <NSCoding> : UIView <NSCoding> : UIResponder <NSCoding, UIAppearance, UIAppearanceContainer, UIDynamicItem> : NSObject
UITableViewController : UIViewController <UITableViewDelegate, UITableViewDataSource> : UIResponder <NSCoding, UIAppearanceContainer> : NSObject
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tableview1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tableview2.png">

Ячейки table view, которые больше не отображаются на экране, не выкидываются. Их можно адаптировать под повторное использование, указав идентификатор в процессе инициализации. Когда ячейка table view, отмеченная для повторного использования, пропадает с экрана, table view помещает ее в очередь для повторного использования в дальнейшем. Когда объект table view dataSource запрашивает у table view новую ячейку и указывает идентификатор, table view сначала проверяет очередь ячеек для повторного использования на предмет наличия необходимой ячейки. Если ячейка table view не была обнаружена, то table view создает новую, передавая ее затем объекту dataSource.
```objectivec
UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:CellIdentifier forIndexPath:indexPath];
```

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

## Что такое awakeFromNib?
_NSNibAwaking Protocol Reference (informal protocol)_

Prepares the receiver for service after it has been loaded from an Interface Builder archive, or nib file.

`- (void)awakeFromNib;`

An `awakeFromNib` message is sent to each object loaded from the archive, but only if it can respond to the message, and only after all the objects in the archive have been loaded and initialized. When an object receives an awakeFromNib message, it is guaranteed to have all its outlet instance variables set.

_Note:_ During Interface Builder’s test mode, this method is also sent to objects instantiated from loaded palettes, which include executable code for the objects. It is not sent to objects created using the Classes display of the nib file window in Interface Builder.
An example of how you might use `awakeFromNib` is shown below. Suppose your nib file has two custom views that must be positioned relative to each other at runtime. Trying to position them at initialization time might fail because the other view might not yet be unarchived and initialized yet. However, you can position both of them in the nib file owner’s `awakeFromNib` method. In the code below, `firstView` and `secondView` are outlets of the file’s owner:

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/awakefromnib.png">

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

## Что такое неформальный протокол?
Категория с описанными, но не реализованными методами называется неформальным протоколом. Неформальные протоколы часто определяются для корневого класса `NSObject`, при этом они не имеют реализации в самом классе. Каждый подкласс будет отвечать на сообщения описанные в категории, но при этом будут делать что-то полезное только реализованные методы. Методы, по мере необходимости, могут быть реализованы в подклассах, при этом реализуемые методы должны быть объявлены в секции `@interface`.

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
## Опишите иерархию классов от UIButton до NSObject
`UIButton : UIControl : UIView : UIResponder : NSObject`

## Что такое контекст?
Все рисование происходит в контексте (context), который определяет, где происходит рисование. Чтобы получить context используется Си функция `UIGraphicsGetCurrentContext`. В iOS центр координат при рисовании находится в левом верхнем углу, а не в левом нижнем, как у Mac OS X.
```objectivec
- (void)drawRect:(CGRect)rect {
  // Получим context
  CGContextRef context = UIGraphicsGetCurrentContext();
  CGContextClearRect(context, rect); // Очистим context
  CGContextSetRGBFillColor(context, 255, 0, 0, 1);
  CGContextFillRect(context, CGRectMake(20, 20, 100, 100));
}
```

## NSArray arrayWithObjects: a, b, c, nil; зачем nil вконце?
Чтобы закончить список объектов, которые содержит массив. Этим значением мы даем знать компилятору, что массив окончен.

## Как работает NSNotificationCenter? В каком потоке приходит оповещение?

The notification process is carried out on the thread from which the notification was posted.

***

* что такое `void *`? а что означает просто `void`? в чем разница между void * и id? что такое id? как определен id? можно ли создать структуру и привести к id? id vs instancetype
* что значит root класс? можно ли создать свой root класс? какие есть еще root классы кроме NSObject и NSProxy? можно ли использовать NSObject вместо NSProxy? если ответ «да», то зачем тогда нужен NSProxy?
* как происходит выравнивание указателей на объекты в objc? с чем это связано? какие оптимизации с этим связаны при хранении данных? почему нельзя делать свою реализацию?
* что такое bridge и зачем это нужно?
* все эти методы допустимы? если нет то какие и почему?
```objectivec
- (instancetype)initMyObj {
  self = nil;
  return self;
}

- (instancetype)initmyObj {
  self = nil;
  return self;
}

- (instancetype)myObj {
  self = nil;
  return self;
}
```
* что такое мета-класс?
* `objc_msgSend`, что это за функция? как это связано с [obj foo]? какие еще есть связанные функции? что такое dispatch table? как происходит отправка сообщения? всегда ли сообщения отправляются с одинаковой скоростью? что будет если метод не найден в dispatch table?
* есть ли в objc приватные методы? как протестировать метод, не объявленный в публичном интерфейсе
* exception отправки сообщения, кто выбрасывает? что такое NSInvocation. Привести пример использования. что такое swizzling?
* можно ли сделать private ivar как property, через категорию? какие проблемы могут быть? как в категории сделать свою property?
* target-action, передается селектор, как сделать так, чтобы по селектору был вызван не метод, а блок?
* что такое селектор?
* что такое assert и когда использовать?
* как связаны NSTimer и run loop? как запустить таймер на отдельном потоке? что будет если запустить таймер и держать UIScrollView? как это исправить?
* почему в этом коде утечка памяти и как устранить?
```objectivec
NSString *str;
while (YES) {
  str = [NSString stringWithFormat:@"hello world"];
}
```
* как работает ARC? магически определяет когда удалять объект? напишите реализацию сеттера на MRC. чем отличается weak от strong и почему так много runtime функций для этого? почему weak невозможно использовать на некоторых классах? на каких именно? как быть в этом случае? как работает dealloc? когда расставляются release сообщения для ivar?

* причина выполнения true ветки? причина выполнения false ветки? от чего зависит результат?
```objectivec
BOOL b = 1024;
if (b) {
  NSLog(@"true");
} else {
  NSLog(@"false");
}
```
* одинаковую ли память занимают эти структуры и почему так?
```objectivec
struct StructA {
  int32_t a;
  char b;
  char c;
};

struct StructB {
  char b;
  int32_t a;
  char c;
};
```
* что такое union?
* а сколько памяти занимают эти структура и что это вообще такое?
```objectivec
struct Value1 {
  int32_t foo:12;
  int32_t foo1:4;
  int32_t foo2:6;
  int32_t foo3:10;
};

struct Value2 {
  int32_t foo;
  int32_t foo1;
  int32_t foo2;
  int32_t foo3;
};
```
