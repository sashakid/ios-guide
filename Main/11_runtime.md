- [Runtime](#runtime)
	- [Что такое указатель isa? Для чего он нужен?](#isa)
	- [Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?](#метод-объекта)
	- [Что такое классы в Objective-C, структура классов?](#классы)
	- [Чем объект Objective-c отличается от структуры С, что такое структура в C?](#объект)
	- [Вопрос о методах isKindOfClass, isMemberOfClass](#вisKindOfClass)
	- [Тип id](#тип-id)
	- [Dynamic method resolution](#dynamic-method-resolution)

<a name="runtime"></a>
# Runtime
The heart of this power is the Objective-C runtime, provided by libobjc. The Objective-C runtime is a collection of functions that provides the dynamic features of Objective-C. It includes such core functions
As `objc_msgSend`, which is called every time you use the `[object message];` syntax. It also includes functions to allow you to inspect and modify the class hierarchy at runtime, including creating new classes and methods. Библиотека времени выполнения. Objective-C is a runtime-oriented language. Now the question that arises is, what is a runtime language? A runtime language is a language that decides what to implement in a function and other decisions during the runtime of the applications. Is Objective-C a runtime language? NO. It is a runtime-oriented language, which means that whenever it is possible, it defers decisions from compile and link time to the time when the code in the application is actually being executed. Функции и структуры Runtime-библиотеки определены в нескольких заголовочных файлах: `NSObjCRuntime.h`, `objc.h`, `runtime.h` и `message.h`.
Система вызова методов в Objective-C реализована через посылку сообщений объекту. Каждый вызов метода транслируется в соответствующий вызов функции `objc_msgSend`:
```objectivec
// Вызов метода
[array insertObject:foo atIndex:1];
// Соответствующий ему вызов Runtime-функции
objc_msgSend(array, @selector(insertObject:atIndex:), foo, 1);
```
Вызов `objc_msgSend` инициирует процесс поиска реализации метода, соответствующего селектору, переданному в функцию. Реализация метода ищется в так называемой таблице диспетчеризации класса. Поскольку этот процесс может быть достаточно продолжительным, с каждым классом ассоциирован кеш методов. После первого вызова любого метода, результат поиска его реализации будет закеширован в классе. Если реализация метода не найдена в самом классе, дальше поиск продолжается вверх по иерархии наследования — в суперклассах данного класса. Если же и при поиске по иерархии результат не достигнут, в дело вступает механизм динамического поиска — вызывается один из специальных методов: `resolveInstanceMethod` или `resolveClassMethod` (динамическое переопределение методов).

<a name="isa"></a>
## Что такое указатель isa? Для чего он нужен?
Каждый объект Objective-C содержит в себе атрибут `isa` - указатель на class object для данного объекта. class object автоматически создается компилятором и существует как один экземпляр, на который через `isa` ссылаются все экземпляры данного класса.
First there is a pointer to your class definition. Then each of your superclasses’ ivars (instance variables) are laid out as struct properties, and then your class’s ivars are laid out as struct properties. This structure is called `objc_object`, and a pointer to it is called `id`:
```objectivec
typedef struct objc_object {
  Class isa;
} *id;
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/isa.png">

<a name="метод-объекта"></a>
## Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?

_Форвардинг_

So if you pass a `doSomething` message to an object `[object doSomething]`
1. It will first check whether it has a `doSomething` method
2. Then it will check its superclasses
3. It'll try dynamic method resolution (`resolveInstanceMethod` for instance)
see [Dynamic method resolution](#dynamic-method-resolution)
4. It'll look for a forwarding target (`forwardingTargetForSelector:`)

> This method gives an object a chance to redirect an unknown message sent to it before the much more expensive forwardInvocation: machinery takes over. This is useful when you simply want to redirect messages to another object and can be an order of magnitude faster than regular forwarding. It is not useful where the goal of the forwarding is to capture the NSInvocation, or manipulate the arguments or return value during the forwarding.

5. Finally, if everything else fails, it'll create an invocation (using `methodSignatureForSelector:` and put to `forwardInvocation:`. By default, `forwardInvocation:` just calls doesNotRecognizeSelector: which crashes you on iOS (or terminates the current thread on OS X). But you can override it to do something else (like they have here).

The `NSInvocation` object encapsulates the original message and the arguments that were passed with it. You can implement a `forwardInvocation:` method to give a default response to the message, or to avoid the error in some other way. As its name implies, `forwardInvocation:` is commonly used to forward the message to another object.

<a name="классы"></a>
## Что такое классы в Objective-C, структура классов?
```objectivec
#import <objc/objc.h>
/*
*	Class Template
*/
struct objc_class {			
  struct objc_class *isa;
  struct objc_class *super_class;
  const char *name;		
  long version;
  long info;
  long instance_size;
  struct objc_ivar_list *ivars;

  #if defined(Release3CompatibilityBuild)
  struct objc_method_list *methods;
  #else
  struct objc_method_list **methodLists;
  #endif

  struct objc_cache *cache;
  struct objc_protocol_list *protocols;
};
```

<a name="объект"></a>
## Чем объект Objective-c отличается от структуры С, что такое структура в C?
Структура – специальный тип данных языка C, который содержит в себе другие типы данных в одном блоке и группрует их под одним именем.
```c
struct point {
  int x;
  int у;
};
```
Объекты в ObjС представляют собой структуры cо своими данными и в которых имеется ссылка isa на объект класса.

<a name="isKindOfClass"></a>
## Вопрос о методах isKindOfClass, isMemberOfClass
Протокол `<NSObject>`, методы тестирования наследования:

1. `isKindOfClass:`
2. `isMemberOfClass:`
3. `respondsToSelector:`
4. `conformsToProtocol:`

`isKindOfClass:`

Возвращает логическое значение, указывающее, является ли приемник экземпляром заданного класса или экземпляром любого класса, который наследует от этого класса (обязательный):
```objectivec
`- (BOOL)isKindOfClass:(Class)aClass`
```
Аргументы:

`aClass` Объект класс, представляющий Objective-C класс для тестирования.

Возвращаемое значение:

`YES`, если получатель является экземпляром `aClass` или экземпляром любого класса, который наследует от `aClass`, в противном случае `NO`.

`isMemberOfClass:`

Возвращает логическое значение, указывающее, является ли приемник экземпляром заданного класса (обязательный).
```objectivec
- (BOOL)isMemberOfClass:(Class)aClass
```
Аргументы:

`aClass` Объект класс, представляющий Objective-C класс для тестирования.

Возвращаемое значение:

`YES`, если получатель является экземпляром `aClass`, в противном случае `NO`.

`respondsToSelector:`

Возвращает логическое значение, указывающее, что приемник реализует или наследует метод, который может реагировать на указанное сообщение. (обязательный).
```objectivec
- (BOOL)respondsToSelector:(SEL)aSelector
```
Аргументы:

`aSelector` Селектор, который идентифицирует сообщение.

Возвращаемое значение:

`YES`, если приемник реализует или наследует метод, который может реагировать на `aSelector`, в противном случае `NO`.

`conformsToProtocol:`

Возвращает логическое значение, указывающее, что приемник соответствует заданному протоколу. (обязательный).
```objectivec
- (BOOL)conformsToProtocol:(Protocol *)aProtocol
```
Аргументы:

`aProtocol` Объект протокола, который представляет определенный протокол.

Возвращаемое значение:

`YES`, если приемник поддерживает `aProtocol`, в противном случае `NO`.

Рассмотрение:

Этот метод работает идентично методу класса `conformsToProtocol`: объявленному в `NSObject`. Это сделано для удобства, так чтобы вам не нужно было получать объект класса, чтобы узнать, может ли экземпляр ответить на заданный набор сообщений.

<a name="тип-id"></a>
## Тип id

__id__

```c
typedef struct objc_class *Class;
typedef struct objc_object {
    Class isa;
} *id;
```
`id` is a pointer to any Objective-C object (`objc_object`). It is not just a `void` pointer and you should not treat it as so. It references an object that should have a valid `isa` pointer. The values that can be stored in `id` are also not just limited to `NSObject` and its descendants, which starts to make sense of the existence of the `NSObject` protocol as well as the `NSProxy` class which does not even inherit from `NSObject`. The compiler will allow you to assign an object referenced by type `id` to any object type, assign any object type to `id`, as well as send it any message (that the compiler has seen) without warning.

Thus “id” type is polymorphic. This is very powerful as it doesn’t require a cast to use such a value:
```objectivec
id data = ...;
NSString *host = [data host]; // assume NSURL
```
Sure enough `id` usage can lead to bugs, because the availability of the method is determined at runtime. This is called “dynamic (or late) binding”. Nevertheless if used carefully it is very useful and lets you write parts of the code faster as if using a scripting language.

Unfortunately this doesn’t work with property syntax:
```objectivec
id data = ...;
NSString *host = data.host; // error: "Property 'host' not found"
data.host = @"dobegin.com"; // same error
```

__instancetype__

> Use the `instancetype` keyword as the return type of methods that return an instance of the class they are called on (or a subclass of that class). These methods include `alloc`, `init`, and class factory methods. Using `instancetype` instead of `id` in appropriate places improves type safety in your Objective-C code.

* Что случится во время компиляции если мы посылаем сообщение объекту типа id?

With a variable typed `id`, you can send it any known message and the compiler will not complain. With a variable typed `NSObject *`, you can only send it messages declared by `NSObject` (not methods of any subclass) or else it will generate a warning.

* Что произойдет здесь?
```objectivec
NSString *s = [NSNumber numberWithInt:3];
int i = [s intValue];
```
Переменная типа `id` фактически является указателем на произвольный объект. Для обозначения нулевого указателя на объект используется константа `nil` (= `NULL`). При этом вместо `id` можно использовать и более привычное обозначение с явным указанием класса. В частности последнее позволяет компилятору осуществлять некоторую проверку поддержки сообщения объектами — если компилятор из типа переменной не может сделать вывод о поддержке объектом данного сообщения, то он выдаст предупреждение. Тем самым язык поддерживает проверку типов, но в нестрогой форме (то есть найденные несоответствия возвращаются как предупреждения, а не ошибки).
```objectivec
MyArray *array = [MyArray arrayWithObjects:@(1), @(2), nil];
```
Теперь вы видите, почему возвращаемый тип `arrayWithObjects:` должен быть `id`. Если бы это был `(NSArray *)`, то подклассы потребует, чтобы они были приведены к необходимому классу.

* В чем разница между `void` и `void *`?

The `void` type, in several programming languages derived from C and Algol68, is the type for the result of a function that returns normally, but does not provide a result value to its caller. Usually such functions are called for their side effects, such as performing some task or writing to their output parameters.
C and C++ also support the pointer to `void` type (specified as `void *`), but this is an unrelated notion. Variables of this type are pointers to data of an unspecified type, so in this context (but not the others) `void *` acts roughly like a universal or top type. A program can probably convert a pointer to any type of data (except a function pointer) to a pointer to `void` and back to the original type without losing information, which makes these pointers useful for polymorphic functions. The C language standard does not guarantee that the different pointer types have the same size.

In C and C++

A function with `void` result type ends either by reaching the end of the function or by executing a return statement with no returned value. The `void` type may also appear as the sole argument of a function prototype to indicate that the function takes no arguments. Note that despite the name, in all of these situations, the `void` type serves as a unit type, not as a zero or bottom type (which is sometimes confusingly is also called the "void type"), even though unlike a real unit type which is a singleton, the `void` type lacks a way to represent it's a value and the language does not provide any way to declare an object or represent a value with type `void`.

* Можно ли создать структуру и привести к id?

`NSValue`

> A simple container for a single C or Objective-C data item. An `NSValue` object can hold any of the scalar types such as `int`, `float`, and `char`, as well as pointers, structures, and object `id` references. Use this class to work with such data types in collections (such as `NSArray` and `NSSet`), Key-value coding, and other APIs that require Objective-C objects. `NSValue` objects are always immutable.

```objectivec
[NSValue valueWithBytes:&struct objCType:@encode(MyStruct)];
```
And to get the value back out:
```objectivec
MyStruct struct;
[value getValue:&struct];
```

<a name="dynamic-method-resolution"></a>
## Dynamic method resolution

There are situations where you might want to provide an implementation of a method dynamically. For example, the Objective-C declared properties feature includes the `@dynamic` directive, which tells the compiler that the methods associated with the property will be provided dynamically. You can implement the methods `resolveInstanceMethod:` and `resolveClassMethod:` to dynamically provide an implementation for a given selector for an instance and class method respectively.

An Objective-C method is simply a C function that take at least two arguments — `self` and `_cmd`. You can add a function to a class as a method using the function `class_addMethod`. Therefore, given the following function:
```c
void dynamicMethodIMP(id self, SEL _cmd) {
  // implementation ....
}
```
you can dynamically add it to a class as a method (called `resolveThisMethodDynamically`) using `resolveInstanceMethod:` like this:
```objectivec
@implementation MyClass
+ (BOOL)resolveInstanceMethod:(SEL)aSEL {
  if (aSEL == @selector(resolveThisMethodDynamically)) {
    class_addMethod([self class], aSEL, (IMP) dynamicMethodIMP, "v@:");
      return YES;
    }
  return [super resolveInstanceMethod:aSEL];
}
@end
```
A class has the opportunity to dynamically resolve a method before the forwarding mechanism kicks in. If `respondsToSelector:` or `instancesRespondToSelector:` is invoked, the dynamic method resolver is given the opportunity to provide an `IMP` for the selector first. If you implement `resolveInstanceMethod:` but want particular selectors to actually be forwarded via the forwarding mechanism, you return `NO` for those selectors.

__Dynamic Loading__

An Objective-C program can load and link new classes and categories while it’s running. The new code is incorporated into the program and treated identically to classes and categories loaded at the start. Dynamic loading can be used to do a lot of different things. For example, the various modules in the System Preferences application are dynamically loaded. In the Cocoa environment, dynamic loading is commonly used to allow applications to be customized. Others can write modules that your program loads at runtime—much as Interface Builder loads custom palettes and the OS X System Preferences application loads custom preference modules. The loadable modules extend what your application can do. They contribute to it in ways that you permit but could not have anticipated or defined yourself. You provide the framework, but others provide the code.
