- [MEMORY MANAGEMENT](#memory-management)
	- [Память в стеке и в куче](#память-в-стеке-и-в-куче)
	- [Manual retain-release](#manual-retain-release)
	- [Automatic Reference Counting](#automatic-reference-counting)
	- [Модификаторы](#модификаторы)
	- [Что такое property](#что-такое-property)
	- [Написать сеттер и геттер для свойства, с ARC и без](#написать-сеттер-и-геттер)
	- [В каких случаях лучше использовать strong, а в каких copy для NSString? Почему?](#copy-strong-nsstring)
	- [autorelease vs release](#autorelease-vs-release)
	- [Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC](#arc-nonarc)
	- [Владение объектами в массиве](#владение-объектами-в-массиве)
	- [Вопрос о циклах в графах владения, и почему свойства delegate обычно задаются как assign?](#retain-cycle)
	- [Нужно ли ретейнить делегат для CAAnimation?](#caanimation-retain)
	- [Если я вызову performSelector:withObject:afterDelay: объекту пошлется сообщение retain?](#performselectorwithobject)
	- [Что происходит когда вы посылаете объекту сообщение autorelease?](#сообщение-autorelease)
	- [Что такое retain count?](#retain-count)

<a name="memory-management"></a>
# MEMORY MANAGEMENT
Memory management – процесс выделения памяти под объекты, и освобождение ее после использования.
* __Manual Retain-Release__ (ручное сохранение-освобождение) или MRR – вы явно управляете памятью, отслеживая объекты, которые у вас есть. Это реализуется с помощью модели, известной как подсчет ссылок, что Foundation класса NSObject обеспечивает совместно со средой выполнения.
* В __Automatic Reference Counting__ (автоматическом подсчете ссылок), или ARC, система использует тот же подсчет ссылок, что и система MRR, но он вставляет соответствующий вызов метода управления памятью за вас во время компиляции.
* В __Garbage Collection__ (сборе мусора), система автоматически отслеживает, какие объекты владеют другими объектами. Затем она автоматически освобождает (или собирает мусор) объекты, на которые больше не ссылаются. Метод использует другой механизм, нежели, чем у используемых в MRR и ARC, и поддерживается только в среде выполнения на Mac OS X, а не IOS.

_Отличие ARC от GC:_

GC работает во время выполнения программы с помощью кода, который переодически запускается и проверяет объекты. ARC работает во время компиляции и вставляет retain и release автоматически в код.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/memory_management.png">

<a name="память-в-стеке-и-в-куче"></a>
## Память в стеке и в куче

__Stack__

The stack is a region of memory which contains storage for local variables, as well as internal temporary values and housekeeping. On a modern system, there is one stack per thread of execution. When a function is called, a stack frame is pushed onto the stack, and function-local data is stored there. When the function returns, its stack frame is destroyed. All of this happens automatically, without the programmer taking any explicit action other than calling a function.

__Heap__

The heap is, essentially, everything else in memory. (Yes, there are things other than the stack and heap, but let's ignore that for this discussion.) Memory can be allocated on the heap at any time, and destroyed at any time. You have to explicitly request for memory to be allocated from the heap, and if you aren't using garbage collection, explicitly free it as well. This is where you store things that need to outlive the current function call. The heap is what you access when you call `malloc` and `free`.

__Stack vs Heap Objects__

Given that, what's a stack object, and what's a heap object?
First, we must understand what an object is in general. In Objective-C (and many other languages), an object is simply a contiguous blob of memory with a particular layout.
The precise location of that memory is less important. As long as you have some memory somewhere with the right contents, it's a working Objective-C object. In Objective-C, objects are usually created on the heap:
```objectivec
NSObject *obj = [[NSObject alloc] init];
```
The storage for the obj variable itself is on the stack, but the object it points to is in the heap. The `[NSObject alloc]` call allocates a chunk of heap memory, and fills it out to match the layout needed for an NSObject.

A stack object is just an object where the memory for that object is allocated on the stack. Objective-C doesn't have any support for this directly, but you can construct one manually without too much trouble:
```objectivec
struct {
  Class isa;
} fakeNSObject;

fakeNSObject.isa = [NSObject class];

NSObject *obj = (NSObject *)&fakeNSObject;
NSLog(@"%@", [obj description]);
```
This works fine, although you shouldn't depend on it, as it depends on replicating the internal layout of the class.

__Advantages of Stack Objects__

It's obviously possible to have stack objects in general. Aside from the above hack, real languages like C++ have language support for stack objects. In C++, you can create objects on the stack or the heap:
```c++
std::string stackString;
std::string *heapString = new std::string;
```
Stack objects have two compelling advantages:

* Speed: Allocating memory on the stack is really fast. All of the bookkeeping is done by the compiler when you build your program. At runtime, the function prolog just carves out the amount of space it needs for all local variables, and the code knows what goes where because it was all computed in advance. Stack allocations are essentially free, whereas heap allocations can be quite expensive.
* Simplicity: Stack objects have a defined lifetime. You can never leak one, because it always gets destroyed at the end of the scope where it was declared.

__Disadvantages of Stack Objects__

The strictly defined lifetime of a stack object is a disadvantage as well, and a major one. In Objective-C (and C++, and many other languages), it is impossible to move an object after it's created. The reason for this is because there may be many pointers to that object, and those pointers are not tracked. They would all need to be updated to track the move, but there's no way to accomplish this.
(Note: it's not an impossibility in general, and many languages move objects around as a matter of course, often as part of garbage collection schemes. However, this requires more runtime smarts and a stricter type system than you get in Objective-C.)
As used in Cocoa, Objective-C uses a reference counting system for memory management. The advantage of this system is that any single object can have multiple "owners", and the system won't allow the object to be destroyed until all owners have relinquished ownership.
Stack allocated objects inherently have a single owner, the function which created them. If Objective-C had stack objects, what would happen if you passed it to some other code which then tried to keep it around by retaining it? There's no way to prevent the object from being destroyed when the function which created it returns, so the retain can't work. The code which tries to keep the object around will fail, end up with a dangling reference, and will crash.
Another problem is that stack objects are not very flexible. It's not uncommon in Objective-C to implement an initializer which destroys the original object and returns a new one instead. How could you do that with a stack object? You really couldn't. Much of the runtime flexibility of Objective-C depends on having heap objects.

__Actual Stack Objects in Objective-C__

It turns out that Objective-C does have stack objects, truly and officially, as of 10.6!
Don't get too excited, though. It's only supported for a single kind of object: blocks. When you write a block inside a function using the `^{}` syntax, the result of that expression is a stack object!

## Manual retain-release
Используйте методы доступа, чтобы сделать управление памятью проще. Рассмотрим счетчик объекта, количество которого вы хотите установить.
```objectivec
@interface Counter : NSObject {
	NSNumber *_count;
}
@property (nonatomic, retain) NSNumber *count;
@end;
```
В свойстве объявляется два метода доступа. Как правило, вы должны попросить компилятор для синтезации методов, однако, поучительно посмотреть, как они могли бы быть реализованы. В `get` методе, вы просто возвращаете переменную экземпляра, так что нет необходимости в `retain` или `release`:
```objectivec
- (NSNumber *)count {
	return _count;
}
```
В `set` методе, если все остальные играют по тем же правилам, вы должны принять новое значение счетчика, которое может быть удалено в любое время, поэтому вам придется взять на себя ответственность объектно, отправив ему `retain` сообщение, чтобы убедиться что его не будет. Вы должны также отказаться от права владения на старый объект, отправив ему `release` сообщение. (Отправка сообщения к `nil` допускается в Objective-C, так что реализация все равно будет работать, если `_count` до сих пор не установлена.) Вы должны послать это после `[newCount retain]` на случай, если два и более объекта захотят, ненароком ее освободить.
```objectivec
- (void)setCount:(NSNumber *)newCount {
	[newCount retain];
	[_count release];
	// Make the new assignment.
	_count = newCount;
}
```

__Использование методов доступа для установки значений свойств__

Предположим, вы хотите реализовать метод для сброса счетчика. У вас есть несколько вариантов. Первая реализация создает экземпляр `NSNumber` с `alloc`, который вы балансируете `release`ом.
```objectivec
- (void)reset {
	NSNumber *zero = [[NSNumber alloc] initWithInteger:0];
	[self setCount:zero];
	[zero release];
}
```
Второй использует удобство конструктора для создания нового объекта `NSNumber`. Он уже существует поэтому нет необходимости в `retain` или `release`
```objectivec
- (void)reset {
	NSNumber *zero = [NSNumber numberWithInteger:0];
	[self setCount:zero];
}
```
Обратите внимание, что оба используют `set` метод доступа.
Следующий код почти наверняка работает правильно для простых случаев, но как заманчиво бы это не выглядело, чтобы отказаться от методов доступа, сделав это почти наверняка в будущем приведет к ошибке на определенном этапе (например, если вы забыли сохранить или освободить, или если изменится семантика управления памятью для переменной экземпляра).
```objectivec
- (void)reset {
	NSNumber *zero = [[NSNumber alloc] initWithInteger:0];
	[_count release];
	_count = zero;
}
```
Отметим также, что если вы используете методику ключ-значение (`KVO`), то изменение переменной, таким путем, не совместимо с `KVO`.
* Не используйте методы доступа в методах инициализаторов и `dealloc`
Единственные места, где вы не должны использовать методы доступа для установки переменной экземпляра находятся в методах - инициализаторе и dealloc. Для инициализации счетчика объекта со значением нуль, вы можете реализовать метод инициализации следующим образом:
```objectivec
- init {
	self = [super init];
	if (self) {
		_count = [[NSNumber alloc] initWithInteger:0];
	}
	return self;
}
```
Чтобы позволить счетчику при инициализации принимать значение отличное от нуля, вы можете реализовать метод `initWithCount:` следующим образом:
```objectivec
- initWithCount:(NSNumber *)startingCount {
	self = [super init];
	if (self) {
		_count = [startingCount copy];
	}
	return self;
}
```
Так как переменная счетчика класса - экземпляр объекта, необходимо также реализовать `dealloc` метод. Следует отказаться от владения любыми переменными экземпляра, отправив им сообщение `release`, и в конечном счете он должн вызывать реализацию супер класса:
```objectivec
- (void)dealloc {
	[_count release];
	[super dealloc];
}
```
* Используйте `weak` (слабые) ссылки чтобы избежать сохранения циклов. Сохранение объекта создает сильную ссылку на этот объект. Объект не может быть освобожден, пока все его сильные ссылки не будут освобождены. Проблема, известная как сохранность цикла, может возникнуть, если два объекта имеют циклические ссылки, то есть, у них есть сильные ссылки друг на друга (либо непосредственно, либо через цепочку других объектов, каждый из которых имеет сильную ссылку на следующую ведущую к первой).
* Не освобождайте объекты, которые используете
* Не используйте dealloc для управления ограниченными ресурсами
Вы должны управлять как правило, не ограниченными ресурсами, такими как дескрипторы файлов, сетевые подключения, и буферы или кэш в `dealloc` методе. В частности, вы не должны проектировать классы так, чтобы `dealloc` был вызван, когда вы думаете, он будет вызван. Вызов `dealloc`, может быть отложен или обойден, либо из-за ошибки или из-за падения приложения.

__Коллекции собственных объектов__

При добавлении объекта в коллекцию (например, массив, словарь, или набор), коллекция становится его владельцем. Коллекция откажется от владения объектом, когда объект удаляется из коллекции или коллекця будет освобождена. Так, например, если вы хотите создать массив чисел вы можете выполнить одно из следующих действий:
```objectivec
NSMutableArray *array = <#Получаем изменяемый массив#>;
NSUInteger i;
// ...
for (i = 0; i < 10; i++) {
	NSNumber *convenienceNumber = [NSNumber numberWithInteger:i];
	[array addObject:convenienceNumber];
}
```
В этом случае вы не вызываете `alloc`, так что нет необходимости вызывать `release`. Значит нет необходимости вызова retain для новых номеров (`convenienceNumber`), так как массив это сделает.
Базовая модель используемая для управления памятью со счетчиком ссылок обеспечивается сочетанием методов, определенных в протоколе `NSObject` и стандартными методами именования. Класс `NSObject` также определяет метод `dealloc`, который вызывается автоматически, когда объект будет освобожден.
Вы владеете каким-либо объектом вами созданным:

* Вы можете создать объект, используя метод, имя которого начинается с `alloc`, `new`, `copy`, или `mutableCopy`.
* Вы можете стать владельцем объекта, используя `retain`: Полученный объект, как правило, гарантированно остается в силе в течение выполнения метода, в котором он был получен, и этот метод также может безопасно вернуть объект к вызвовшему его методу. Вы используете `retain` в двух случаях:
1. В реализации метода доступа или инициализации метода, чтобы стать владельцем объекта, который нужно сохранить как значение свойства
2. Для предотвращения освобождения объекта как побочного эффекта от некоторых других операций

_Если объект вам больше не нужен, вы должны отказаться от права собственности на него:_
Вы отказываетесь от права собственности на объект, послав ему сообщение `release` или `autorelease` сообщение. В Cocoa терминологии, из отказа от права владения объектом, как правило следует, "освобождение" объекта.
_Вы не должны отказаться от права владения объектом, которого у вас нет:_ Это всего лишь следствие предыдущих правил политики, заявиленных в явном виде.
Используйте `autorelease` для отправки отложенного `release`.
_Вы не являетесь владельцем объектов, возвращаемых по ссылке:_
Некоторые методы в Cocoa указавают, что объект возвращается по ссылке (то есть, они не имеют аргумента типа `ClassName **` или `id *`). Данная закономерность заключается в использовании `NSError` объекта, который содержит информацию об ошибках, если они происходит, о чем свидетельствуют `initWithContentsOfURL:options:error:` (`NSData`) и `initWithContentsOfFile:encoding:error:` (`NSString`). В этих случаях применяются те же правила, как уже было описано. При вызове любого из этих методов, вы не создаете `NSError` объект, так что вы не являетесь его владельцем.
_Реализация `dealloc` для отказа от права владения объектами:_
Класс `NSObject` определяет метод `dealloc`, который вызывается автоматически, когда объект не имеет владельцев и его память будет утилизирована, в терминологии Cocoa это называется "освободил" или "освобождена". Роль `dealloc` метода заключается в освобождении собственной памяти объекта, и распоряжением любыми ресурсами которыми он располагает, в том числе любыми переменными экземпляра объекта, которыми он владеет.
Важно:

* Вы никогда не должны ссылаться на dealloc метод другого объекта непосредственно.
* Вы должны вызвать реализацию суперкласса в конце вашей реализации.
* Вы не должны привязывать управление системными ресурсами, как к объектам кон-тролируемым временем жизни.

<a name="automatic-reference-counting"></a>
## Automatic Reference Counting
Автоматический подсчет ссылок является компиляторной функцией, которая обеспечивает автоматическое управление памятью в Objective-C объектах. Вместо того, чтобы думать о со-хранении и освобождении объектов, ARC позволяет сосредоточиться на непосредственном ко-де Вашего приложения. ARC работает путем добавления кода во время компиляции, чтобы время жизни объекта было ровно столько, сколько необходимо, но не более того. Концептуально, это то же управление памятью, что и ручной подсчет ссылок (описанное в практическом управлении памятью) путем добавления соответствующего кода управления памятью, за вас. ARC поддерживается начиная с Xcode 4.2 для Mac OS X v10.6 и v10.7 (64-bit applications), а также iOS 4 и iOS 5. Слабые (`weak`) ссылки не поддерживаются в Mac OS X v10.6 и iOS 4 и более ранних.
Существует несколько ограничений на использование механизма ARC.
* Нельзя использовать свойство, имя которого начинается со слова `new`. Например, не допускается объявление
```objectivec
@property NSString *newString;
```
* Нельзя использовать свойство только для чтения без атрибутов управления памятью. Если вы не используете механизм ARC, то можете использовать объявление
```objectivec
@property (readonly) NSString *title;
```
Но если вы используете механизм ARC, то должны указать, кто управляет памятью, так что достаточно просто вставить ключевое слово unsafe_unretained, потому что по умолчанию используется атрибут `assign`.
ARC only works with retainable object pointers (ROPs). There are three kinds of retainable object pointers:

1. Block pointers
2. Objective-C object pointers
3. Typedefs marked with `__attribute__((NSObject))`

All other pointer types, such as `char *` and CF objects such as `CFStringRef`, are not ARC compatible. If you use pointers that aren’t handled by ARC, you’ll have to manage them yourself. That’s OK, because ARC interoperates with manually managed memory.

<a name="модификаторы"></a>
## Модификаторы
__Для свойств__

`readwrite` (по-умолчанию) и `readonly`
* генерируются одновременно сеттеры и геттеры (setters/getters) или только геттеры

`assign` (по-умолчанию)
просто присваивает переданное значение.
* assign is the default and simply performs a variable assignment
* assign is a property attribute that tells the compiler how to synthesize the property's setter implementation
* I would use assign for C primitive properties and weak for weak references to Objective-C ob-jects.

`retain`
посылает release текущему значению переменной экземпляра, потом посылает retain новому объекту, и присваивает новое значение переменной экземпляра.
* it is retained, old value is released and it is assigned retain specifies the new value should be sent
* retain on assignment and the old value sent -release
* retain is the same as strong.
* apple says if you write retain it will auto converted/work like strong only.
* methods like alloc include an implicit retain

`copy`
посылает `release` текущему значению переменной экземпляра, затем copy новому объекту и присваивает новый объект переменной экземпляра. В последних двух случаях, вы должны послать `release` (или присвоить `nil`) свойству при `dealloc`. Атрибут сору создает копию объекта и переводит на нее указатель. Атрибут сору чаще всего используется с объектными типами, имеющими изменяемые субклассы. Например, `NSString` имеет субкласс с именем `NSMutаblеString`.

`assign` (по-умолчанию), `retain`, `copy` — применяются только для свойств, которые могут быть безопасно приведены к `id`.

`atomic` (по-умолчанию) и `nonatomic`
свойства с ключевым словом atmoic — потокобезопасны, с nonatomic — могут быть проблемы при многопоточном доступе. Доступ к nonatomic свойствам обычно быстрее чем к atomic, по-этому они часто используются в однопоточных приложениях.

`strong` (ARC)
это синоним для `retain`
* it says "keep this in the heap until I don't point to it anymore"
* in other words "I'am the owner, you cannot dealloc this before aim fine with that same as re-tain"
* you use strong only if you need to retain the object.
* by default all instance variables and local variables are strong pointers.
* we generally use strong for `UIViewController` (UI item's parents)
* strong is used with ARC and it basically helps you, by not having to worry about the retain count of an object. ARC automatically releases it for you when you are done with it. Using the keyword strong means that you own the object.

`weak` (ARC)
синоним `assign`, с одним лишь исключением, что свойство с `weak` автоматически устанавливается в `nil` когда объект уничтожается. Также следует учитывать, что ключ `weak` доступен только начиная с iOS 5 и Mac OS X 10.7 (Lion). Если переменная указатель сохраняет адрес объекта, этот объект является активным и имеет владельца – сильная ссылка (`strong`). Если переменная не принимает владения объектом – слабая ссылка (`weak`, `__weak`). Родитель может владеть своим потомком, но потомок – родителем не должен.
* it says "keep this as long as someone else points to it strongly"
* the same thing as assign, no retain or release
* a weak reference is a reference that you do not retain.
* we generally use weak for `IBOutlets` (`UIViewController`'s Childs). This works because the child object only needs to exist as long as the parent object does.
* a weak reference is a reference that does not protect the referenced object from collection by a garbage collector.
* `weak` is essentially `assign`, a unretained property. Except the when the object is deallocated the weak pointer is automatically set to `nil`

`unsafe_unretained` (по умолчанию)
всегда используется для свойств, содержащих необъектные значения. Что делать, если вы хотите использовать механизм ARC в более старых операционных системах, в которых обнуляе-мые слабые ссылки недоступны? Компания Apple предлагает использовать ключевое слово `__unsafe_unretained` и атрибут `unsafe_unretained`, которые сообщают механизму ARC, что указанная ссылка является слабой.

_Strong & Weak Explanation_
_Imagine our object is a dog, and that the dog wants to run away (be deallocated). Strong pointers are like a leash on the dog. As long as you have the leash attached to the dog, the dog will not run away. If five people attach their leash to one dog, (five strong pointers to one object), then the dog will not run away until all five leashes are detached. Weak pointers, on the other hand, are like little kids pointing at the dog and saying "Look! A dog!" As long as the dog is still on the leash, the little kids can still see the dog, and they'll still point to it. As soon as all the leashes are detached, though, the dog runs away no matter how many little kids are pointing to it. As soon as the last strong pointer (leash) no longer points to an object, the object will be deallocated, and all weak pointers will be zeroed out. When we use weak? The only time you would want to use weak, is if you wanted to avoid retain cycles (e.g. the parent retains the child and the child retains the parent so neither is ever released)._

_Если делать все стронг - то если нам понадобится сослать друг на друга два класса - то есть в класса А завести проперти класса В, а в нем - ссылку но этот объект - то они не освободятся. Я обычно предпочитаю, чтобы стронг ссылки были только в одном экземпляре - особенно в коде, где об одном объекте знает несколько сущностей_

__Для переменных__

Generally speaking, these extra qualifiers don’t need to be used very often. You might first encounter these qualifiers and others when using the migration tool. For new projects however, you generally you won’t need them and will mostly use strong/weak with your declared properties.

`__strong`
по умолчанию. Объект остается "живым", если на него есть сильный указатель. This means any object created using alloc/init is retained for the lifetime of its current scope. The “current scope” usually means the braces in which the variable is declared (i.e. a method, for loop, if block, etc…)

`__weak`
указывается (слабая) ссылка, которая не сохраняет указанный объект живым. Слабая ссылка устанавливается в `nil`, когда на объект нет сильных ссылок. This is only useful if the object is somehow strongly referenced somewhere else. When destroyed, a variable with `__weak` is set to `nil`. Будьте осторожны с применением `__weak` слабых ссылок, так, если Вы создадите объект только со слабой ссылкой, то нет никакой гарантии, что он доживет до своего применения и не освободится.

`__unsafe_unretained`
указывается ссылка, которая не сохраняет указанный объект живым и не устанавливается в `nil`, когда нет сильных ссылок на объект. Если объект, на который она ссылается, будет освобожден, то указатель остается болтаться со значением, которого уже нет. Можете использовать `__unsafe_unretained` вместо `__weak`. Это создаст слабую ссылку, которая НЕ будет обнулена. Но вы должны быть уверены, что не используете этот указатель (предпочтительно, чтобы вы обнулили его вручную) ПОСЛЕ того, как объект, на который он указывает, был уничтожен. Используется только тогда, когда недоступен `weak`.

`__autoreleasing`
используется для обозначения аргументов, которые передаются по ссылке `(id *)` и autoreleased по возвращении. not to be confused with calling autorelease on an object before returning it from a method, this is used for passing objects by reference, for example when passing `NSError` objects by reference such as
```objectivec
[myObject performOperationWithError:&tmp];
```
Absolutely not. The key difference in the two definitions that you've pointed out is the "as long as someone else". It's the "someone else" that is important.

_Consider the following:_
```objectivec
__strong id strongObject = <some_object>;
__weak id weakObject = strongObject;
```
_Now we've got a two pointers to `<some_object>`, one `strong` and one `weak`. If we set_ `strongObject` to `nil` like so:
```objectivec
strongObject = nil;
```
_Then if you go through the rules you outlined then you'll ask yourself these questions:_

__Strong: "keep this in the heap until I don't point to it anymore"__

_`strongObject` doesn't point to `<some_object>` any more. So we don't need to keep it._

__Weak: "keep this as long as someone else points to it strongly"__

_`weakObject` still points to `<some_object>`. But since nobody else points to it, this rule also means that we don't need to keep it.
The result is that `<some_object>` is deallocated and if your runtime supports it (Lion and iOS 5 upwards) then weakObject will automatically be set to nil._

_Now consider what happens if we set `weakObject` to `nil` like so:_
```objectivec
weakObject = nil;
```
_Then if you go through the rules you outlined then you'll ask yourself these questions:_

__Strong: "keep this in the heap until I don't point to it anymore"__

_strongObject does point to <some_object>. So we do need to keep it._

__Weak: "keep this as long as someone else points to it strongly"__

_`weakObject` doesn't point to `<some_object>`.
The result is that `<some_object>` is not deallocated, but `weakObject` will be the `nil` pointer._

_[Note that all that is assuming `<some_object>` is not pointed to by another strong reference somewhere else / some other means of being "held"]_

<a name="что-такое-property"></a>
## Что такое property?
Упрощенный способ для определения и создания методов доступа, обращающихся к существующим переменным экземплярам. Классы, которые подставляют переменные экземпляра, могут использовать обозначение свойства вместо того, чтобы использовать синтаксис getter и setter.

<a name="написать-сеттер-и-геттер"></a>
## Написать сеттер и геттер для свойства, с ARC и без
__ARC__
```objectivec
- (void)setNumerator:(int)n {
	numerator = n;
}

- (int)numerator {
	return numerator;
}
```
__MRR__
```objectivec
- (NSArray *)sushiTypes {
	return _sushiTypes;
}

- (void)setSushiTypes:(NSArray *)sushiTypes {
	[sushiTypes retain];
	[_sushiTypes release];
	_sushiTypes = sushiTypes;
}

- (void)dealloc {
	[super dealloc];
	[sushiTypes release];
}
```
<a name="copy-strong-nsstring"></a>
## В каких случаях лучше использовать strong, а в каких copy для NSString? Почему?
```objectivec
@property (nonatomic, strong) NSString *someString;
@property (nonatomic, copy) NSString *anotherString;
```
`сopy` используется только для объектов, реализующих протокол `<NSCopying>`. Обычно его используют с mutable объектами или со свойствами, представляющими какое-то значение (value).

<a name="autorelease-vs-release"></a>
## `autorelease` vs `release`?
Autorelease pool это — механизм отложеного отказа от ответсвенности. Это означет что вы больше не хотите владеть объектом и он вам в общем-то не нужен, но не хотите чтобы он удалился прямо сейчас. Зачастую вам не нужно создавать свой пул, просто используется NSAutoreleasePool и то даже не напрямую. Чтобы поместить объект в autorelease pool нужно отправить ему сообщение autorelease (один объект может быть добавлен в пул несколько раз) и на следующем цикле сообщений autorelease pool отправит всем этим объектам сообщение release, так как сам получит dealloc после чего будет создан новый autorelease pool. Таким образом Cocoa ожидает, что как минимум один autorelease pool будет всегда, и автоматически создает его в main.
Autorelease pool добавляются по принципу стека, самый последний добавленый пул будет в самом верху стека авторелиз пулов в текущем потоке. Создание пула осуществляется стандартным alloc и init, удаление drain. Если послать сообщение drain не самому верхнему пулу, то все пулы над ним тоже получат это сообщение и соответсвенно удалят все из себя. Оффициальная документация показывает нам вот такой пример использования своего пула:
```objectivec
NSArray *urls = <# An array of file URLs #>;
for (NSURL *url in urls) {
	NSAutoreleasePool *loopPool = [[NSAutoreleasePool alloc] init];
	NSError *error = nil;
	NSString *fileContents = [[[NSString alloc] initWithContentsOfURL:url encoding:NSUTF8StringEncoding error:&error] autorelease];
	/* Process the string, creating and autoreleasing more objects. */
	[loopPool drain];
}
```
Мы тут видим, что был создан свой пул (он разместился вверху стека пулов и будет освобож-ден первым), в него добавляются `NSString *fileContents` и потом пул освобождается (а так как он самый верхний — освобождается только он).

<a name="arc-nonarc"></a>
## Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC?
1 способ: Edit – Refactor – Convert to ObjC ARC

2 способ: App – Targets – Build Phases – Compile Sources – поставить флаг `-fno-objc-arc`

<a name="владение-объектами-в-массиве"></a>
## Владение объектами
* Что случится если вы добавите только что созданный объект в `NSMutableArray`, и пошлете ему сообщение `release`?

//объект останется в массиве

* Что случится если послать сообщение `release` массиву?

//массив удалится

* Что случится если вы удалите объект из массива и попытаетесь его использовать?

//объект удалится из массива, использовать объект дальше можно

<a name="retain-cycle"></a>
## Вопрос о циклах удержания, и почему свойства delegate обычно задаются как assign?
```
A creates B;
A sets itself as B’s delegate;
[A release];
if B retained A => leak;
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/retain_cycle.png">

<a name="caanimation-retain"></a>
## Нужно ли ретейнить делегат для CAAnimation?
Да. Это одно из редких исключений в политике управления памятью. Specific task that has some sort of “finished” state. Также нужно ритейнить `NSURLConnection`.

<a name="performselectorwithobject"></a>
## Если я вызову performSelector:withObject:afterDelay: объекту пошлется сообщение retain?
Да. Это создает таймер который вызывает селектор в RunLoop'е текущего потока (thread).

<a name="сообщение-autorelease"></a>
## Вы можете объяснить, что происходит когда вы посылаете объекту сообщение autorelease?
Когда вы посылаете объекту сообщение `autorelease`, его счетчик ссылок уменьшится на 1 в определенный момент в будущем. Объект будет добавлен в autorelease pool (пул автоосвобождения) в текущем потоке (thread). Цикл главного потока (main thread loop `NSRunLoop`) создает autorelease pool в начале функции и освобождает его в конце. Это устанавливает pool на время выполнения задачи. Это также означает что авторелизные (объекты помещенные в пул) объекты созданные в течение выполнеения задачи не будут уничтожены пока задача не завершится. Это может привести к излишнему потреблению памяти для задачи (объекты будут уже не нужны но освободятся только в конце задачи). Вы также можете попробовать создать вложенный пул и освободить его раньше, или использовать NSOperationQueue с его собственным пулом.

<a name="retain-count"></a>
## Объясните что такое retain count?
Подсчет ссылок (retain count) — это механизм с помощью которого в Objective-C реализовано управление памятью. Когда вы создаете объект, его счетчик ссылок (retain count) установлен на `1`. Когда вы посылаете объекту сообщение `retain` , его счетчик ссылок увеличивается на `1`. Когда вы посылаете объекту сообщение `release` , его счетчик ссылок уменьшается на `1`. Когда вы посылаете объекту сообщение autorelease , его счетчик ссылок уменьшится на `1` в определенный момент в будующем. Когда счетчик ссылок объекта становится равным `0` то объект уничтожается (`dealloc`).
