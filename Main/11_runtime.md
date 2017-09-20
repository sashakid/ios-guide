- [Runtime](#runtime)
	- [Что такое указатель isa? Для чего он нужен?](#isa)
	- [Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?](#метод-объекта)
	- [Что такое классы в Objective-C, структура классов?](#классы)
	- [Чем объект Objective-c отличается от структуры С, что такое структура в C?](#объект)
	- [Вопрос о методах isKindOfClass, isMemberOfClass](#вisKindOfClass)
	- [Тип id](#тип-id)

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

If you send a message to an object that does not handle that message, before announcing an error the runtime sends the object a forwardInvocation: message with an NSInvocation object as its sole argument—the NSInvocation object encapsulates the original message and the arguments that were passed with it. You can implement a forwardInvocation: method to give a default response to the message, or to avoid the error in some other way. As its name implies, forwardInvocation: is commonly used to forward the message to another object.

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
1. Что случится во время компиляции если мы посылаем сообщение объекту типа id?
2. Что случится во время выполнения если этот метод существует?
3. Что произойдет здесь?
```objectivec
NSString *s = [NSNumber numberWithInt:3];
int i = [s intValue];
```
Переменная типа `id` фактически является указателем на произвольный объект. Для обозначения нулевого указателя на объект используется константа `nil` (= `NULL`). При этом вместо `id` можно использовать и более привычное обозначение с явным указанием класса. В частности последнее позволяет компилятору осуществлять некоторую проверку поддержки сообщения объектами — если компилятор из типа переменной не может сделать вывод о поддержке объектом данного сообщения, то он выдаст предупреждение. Тем самым язык поддерживает проверку типов, но в нестрогой форме (то есть найденные несоответствия возвращаются как предупреждения, а не ошибки).
```objectivec
MyArray *array = [MyArray arrayWithObjects:@(1), @(2), nil];
```
Теперь вы видите, почему возвращаемый тип `arrayWithObjects:` должен быть `id`. Если бы это был `(NSArray *)`, то подклассы потребует, чтобы они были приведены к необходимому классу.
