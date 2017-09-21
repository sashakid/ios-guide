- [Блоки](#блоки)
	- [Типы блоков](#типы-блоков)
	- [When and why block captures self and when they don't?](#block-captures-self)
	- [Примеры объявления и использования блоков](#примеры)
	- [В чем отличие блока от лямбды и замыкания](#блок-лямбда-замыкание)
	- [Обратный вызов](#обратный-вызов)
	- [Когда использовать блоки, делегаты, KVO и уведомления?](#блоки-делегаты-kvo-уведомления)

<a name="блоки"></a>
# Блоки

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/blocks.png">

Objective-C blocks introduce a new class of language-level types to represent block types. They match the standard (but tricky) syntax for C function pointer types, but with a `^` in place of the `*`:
```c
void (*)(int) // function pointer taking int and returning void
void (^)(int) // block taking int and returning void
```
As with function and method definitions, the braces indicate the start and end of the block. In this example, the block doesn’t return any value, and doesn’t take any arguments. In the same way that you can use a function pointer to refer to a C function, you can declare a variable to keep track of a block, like this:
```objectivec
void (^simpleBlock)(void);

simpleBlock = ^{
    NSLog(@"This is a block");
};
```
Once you’ve declared and assigned a block variable, you can use it to invoke the block:
```objectivec
simpleBlock();
```
Blocks are Objective-C objects. When you write a block in code, that is an expression of object type, much like the `@"..."` constant string syntax gives you an expression of object type. You can then use this object like you would any other Objective-C object, by sending it messages that it responds to, putting it into containers, passing it as a parameter, returning it, etc.

There is a major difference from the constant string syntax. Unlike constant strings, blocks are not exactly the same each time through a piece of code. This is because blocks capture their enclosing scope, and that scope is different every time they're called. In short, each time code execution hits a `^{...}` construct, a new object is created.

Allocating a new object every time would be kind of slow, so blocks take an unusual approach: the object you get from a `^{...}` construct is a stack object. The cost of calling a block is therefore about the same as the cost of calling a C function. This means that it has the same lifetime as local variables, and will be destroyed automatically upon leaving the current scope.

It's frequently useful for a block to outlive the scope where it was created. For example, you may want to return a block, or save it for later. For this to work, you must copy the block. You can do this like any other Objective-C object by sending it the `copy` message. And like any other Objective-C object, if you aren't running under Garbage Collection then you own the resulting object and must eventually dispose of it using `release` or `autorelease`.

Any reference to `self` is a reference to a local object variable, causing `self` to be retained. Any reference to an instance variable is an implicit reference to `self` and causes the same thing.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/block_capturing.png">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/blocks_structure.png">

```c
struct Block_literal_1 {
    void *isa; // initialized to &_NSConcreteStackBlock or &_NSConcreteGlobalBlock
    int flags;
    int reserved;
    void (*invoke)(void *, ...);
    struct Block_descriptor_1 {
    unsigned long int reserved;         // NULL
        unsigned long int size;         // sizeof(struct Block_literal_1)
        // optional helper functions
        void (*copy_helper)(void *dst, void *src);     // IFF (1<<25)
        void (*dispose_helper)(void *src);             // IFF (1<<25)
        // required ABI.2010.3.16
        const char *signature;                         // IFF (1<<30)
    } *descriptor;
    // imported variables
};

enum {
    BLOCK_HAS_COPY_DISPOSE =  (1 << 25),
    BLOCK_HAS_CTOR =          (1 << 26), // helpers have C++ code
    BLOCK_IS_GLOBAL =         (1 << 28),
    BLOCK_HAS_STRET =         (1 << 29), // IFF BLOCK_HAS_SIGNATURE
    BLOCK_HAS_SIGNATURE =     (1 << 30),
};
```

Objective-C blocks are objects which contain an embedded function pointer. A block call translates to a call to that function pointer, passing the block as an implicit parameter:
```objectivec
block();
// equivalent to:
block->impl(block);
```
It's slightly higher due to the need to look up the implementation pointer first, but just slightly.

It's actually fairly straightforward and described in Clang's Block Implementation Spec, in the "Imported Variables" section.

When the compiler encounters a Block like:
```objectivec
^{ if( numBalloons > numClowns) abort(); }
```
it creates a literal structure that includes -- among other things -- two elements that are important here. There's a function pointer to the executable code in the Block, and a const field for each variable that's referred to inside the Block. Something like this:
```c
struct __block_literal_1 {
    /* other fields */
    void (*invoke)(struct __block_literal_1 *);
    /* ... */
    const int numBalloons;
    const int numClowns;
};
```
Notice that the invoke function will take a pointer to a struct of the kind that's being defined right here; that is, the Block passes itself in when executing its code. Thus, the code gets access to the members of the structure.

Right after the declaration, the compiler creates a definition of the Block, which simply uses the referenced variables to initialize the correct fields in the struct:
```c
struct __block_literal_1 __block_literal_1 = {
    /* Other fields */
    __block_invoke_2, /* This function was also created by the compiler. */
    /* ... */
    numBalloons, /* These two are the exact same variables as */
    numClowns /* those referred to in the Block literal that you wrote. */
};
```
Then, inside the invoke function, references to the captured variables are made like any other member of a struct, `the_block->numBalloons`.

<a name="типы-блоков"></a>
## Типы блоков

* Global block (_NSConcreteGlobalBlock, NSGlobalBlock)

Normally, the `Block_literal` data appears on the stack (like a regular struct would in its surrounding function). With no references to the surrounding scope, clang configures the `Block_literal` as a global block instead. This causes the block to appear in a fixed global location instead of on the stack (the flags value has the `BLOCK_IS_GLOBAL` flag set to indicate this at runtime but it's not immediately clear to me if this is ever used).
The implication of this is that global blocks are never actually copied or disposed, even if you invoke the functions to do so. This optimisation is possible because without any references to the surrounding scope, no part of the block (neither its code nor its `Block_literal`) will ever change — it becomes a shared constant value.
```objectivec
Class class = [^{
} class];
NSLog(@"%@", NSStringFromClass(class));
//__NSGlobalBlock__
```

* Stack block (_NSConcreteStackBlock, NSStackBlock)

It is a stack allocated Objective-C object. If you have ever tried to allocate an Objective-C object on the stack (not as a pointer but statically allocated) you'll know that the compiler normally forbids this.
```objectivec
int foo = 3;
Class class = [^{
		int foo1 = foo + 1;
} class];
NSLog(@"%@", NSStringFromClass(class));
//__NSStackBlock__
```

* Malloc block (NSMallocBlock)

Copying a block doesn't really give you a copy of the block — if the block is already an `NSMallocBlock`, a copy simply increases the retain count of the block (this retain count is an internal reserved field — the retainCount returned from the object will remain at 1). This is perfectly appropriate since the scope of the block cannot change after it is created (therefore the block is constant) but it does mean that invoking copy on a block is not the same thing as recreating it.
```objectivec
int foo = 3;
Class class = [[^{
		int foo1 = foo + 1;
} copy] class];
NSLog(@"%@", NSStringFromClass(class));
//__NSMallocBlock__
```

Как видно, если блок не захватывает внешние переменные, то мы получаем `__NSGlobalBlock__`. Если же блок захватывает внешние переменные, то блок `__NSStackBlock__` (на стеке). Однако если же послать блоку `copy`, то блок будет скопирован в кучу (`__NSMallocBlock__`).

<a name="block-captures-self"></a>
## When and why block captures `self` and when they don't?

_Example:_
```objectivec
- (void)makeAsyncNetworkCall {
    [self.networkService performAsyncNetworkCallWithCompletion:^{
        dispatch_async(dispatch_get_main_queue(), ^{
                [self.activityIndicatorView stopAnimating];
            }
        });
    }];
}
```
I think the issue is that the `networkService` may keep a strong reference to the block. And the view controller may have a strong reference to the `networkService`. So the possible cycle of `VC->NetworkService->block->VC` could exist. However, in this case, it's usually safe to assume that the block will be released after it has run, in which case the cycle is broken. So, in this case, it isn't necessary.

Where it is necessary is if the block is not released. Say, instead of having a block that runs once after a network call, you have a block that is used as a callback. i.e. the `networkService` object maintains a strong reference to the block and uses it for all callbacks. In this case, the block will have a strong reference to the VC, and this will create a strong cycle, so a weak reference is preferred.

__Case 1: using the keyword self inside a block:__

If the block is retained by a property, a retain cycle is created between `self` and the block and both objects can’t be destroyed anymore. If the block is passed around and copied by others, `self` is retained for each copy.

The situation for object-type variables is a little more complicated, but the same principle applies.

__Case 2: declaring a `__weak` reference to `self` outside the block and use it inside the block:__

There is no retain cycle and no matter if the block is retained or not by a property. If the block is passed around and copied by others, when executed, `weakSelf` can have been turned `nil`. The execution of the block can be preempted and different subsequent evaluations of the `weakSelf` pointer can lead to different values (i.e. `weakSelf` can become `nil` at a certain evaluation).
```objectivec
__weak typeof(self) weakSelf = self;
dispatch_block_t block =  ^{
	[weakSelf doSomething]; // weakSelf != nil
	// preemption, weakSelf turned nil
	[weakSelf doSomethingElse]; // weakSelf == nil
};
```

__Case 3: declaring a `__weak` reference to `self` outside the block and use a `__strong` reference inside the block:__

There is no retain cycle and, again, no matter if the block is retained or not by a property. If the block is passed around and copied by others, when executed, `weakSelf` can have been turned `nil`. When the strong reference is assigned and it is not `nil`, we are sure that the object is retained for the entire execution of the block if preemption occurs and therefore subsequent evaluations of `strongSelf` will be consistent and will lead to the same value since the object is now retained. If `strongSelf` evaluates to `nil` usually the execution is returned since the block cannot execute properly.
```objectivec
__weak typeof(self) weakSelf = self;
myObj.myBlock = ^{
	__strong typeof(self) strongSelf = weakSelf;
	if (strongSelf) {
		[strongSelf doSomething]; // strongSelf != nil
		// preemption occurs, strongSelf still not nil
		[strongSelf doSomethingElse]; // strongSelf != nil
	} else {
		// Probably nothing...
		return;
	}
};
```
Dereferencing a `__weak` pointer is not allowed due to possible `null` value caused by race condition, assign it to a strong variable first. It can be shown with the following code:
```objectivec
__weak typeof(self) weakSelf = self;
myObj.myBlock =  ^{
    id localVal = weakSelf->someIVar;
};
```
_Case 1 should be used only when the block is not assigned to a property, otherwise it will lead to a retain cycle._

_Case 2 should be used when the block is assigned to a property and self is referenced only once and the block has a single statement._

_Case 3 should be used when the block is assigned to a property and self is referenced more the once and the block has more than a statement._

<a name="примеры"></a>
## Примеры объявления и использования блоков
```objectivec
#import "NSArray+Map.h"

@implementation NSArray (Map)

- (NSArray *)map:(id (^)(id))block {
	// takes an id, returns an id
	NSMutableArray *ret = [NSMutableArray array];
	for (id obj in self) {
		[ret addObject:block(obj)];
	}
	return ret;
}

- (NSArray *)select:(BOOL (^)(id obj))block {
	NSMutableArray *new = [NSMutableArray array];
	for (id obj in self) {
		if (block(obj)) {
			[new addObject: obj];
		}
	}
	return new;
}

@end

NSArray *array = @[@1, @2, @3, @4, @5];
NSArray *mappedArray = [array map:^id(id element) {
	NSNumber *current = (NSNumber *)element;
	return [NSNumber numberWithInt:[current intValue] * [current intValue]];
}];

NSArray *longStrings = [strings select:^BOOL (id obj) { return [obj length] > 5; }];
```

As a local variable:
```objectivec
returnType (^blockName)(parameterTypes) = ^returnType(parameters) {...};
```
As a property:
```objectivec
@property (nonatomic, copy) returnType (^blockName)(parameterTypes);
```
As a method parameter:
```objectivec
- (void)someMethodThatTakesABlock:(returnType (^)(parameterTypes))blockName;
````
As an argument to a method call:
```objectivec
[someObject someMethodThatTakesABlock:^returnType (parameters) {...}];
```
As a typedef:
```objectivec
typedef returnType (^TypeName)(parameterTypes);
TypeName blockName = ^returnType(parameters) {...};
```

## В чем отличие блока от лямбды и замыкания
Замыкание (англ. closure) в программировании — функция, в теле которой присутствуют ссылки на переменные, объявленные вне тела этой функции и не в качестве её параметров (а в окружающем коде). Говоря другим языком, замыкание — функция, которая ссылается на свободные переменные в своём контексте. Замыкание, так же как и экземпляр объекта, есть способ представления функциональности и данных, связанных и упакованных вместе.

Examples:
```python
def func(): return h
def anotherfunc(h):
	return func()
```   
This will cause an error, because `func` does not close over the environment in `anotherfunc` - `h` is undefined. `func` only closes over the global environment. This will work:
```python
def anotherfunc(h):
	def func(): return h
    return func()
```
Because here, `func` is defined in `anotherfunc`, and in python 2.3 and greater (or some number like this) when they almost got closures correct (mutation still doesn't work), this means that it closes over `anotherfunc`'s environment and can access variables inside of it. In Python 3.1+, mutation works too when using the `nonlocal` keyword.

Another important point - `func` will continue to close over `anotherfunc`'s environment even when it's no longer being evaluated in `anotherfunc`. This code will also work:
```python
def anotherfunc(h):
    def func(): return h
    return func

print anotherfunc(10)()
```
This will print `10`.

This, as you notice, has nothing to do with lambda's - they are two different (although related) concepts.

Лямбда-выражение — это специальный синтаксис для объявления анонимных функторов по месту их использования. Используя лямбда-выражения, можно объявлять функции в любом месте кода. Обычно лямбда-выражение допускает замыкание на лексический контекст, в котором это выражение использовано. Лямбда-выражения поддерживаются во многих языках программирования (C, Common Lisp, Python, PHP, C#, F#, Visual Basic .NET, C++, Java и других).
Нестандартное расширение синтаксиса языков программирования C/C++/Objective-C, позволяющее инкапсулировать код и данные в один объект. Блоковые объекты это C-уровневые синтаксические функции. Они похожи на стандартные функции C, но в дополнение к исполняемому коду они также могут содержать переменные привязанные к автоматической (стеку) или управляемой (куче) памяти. Поэтому блок может поддерживать набор состояний (данные), которые он может использовать, чтобы повлиять на поведение при выполнении. Блоки особенно полезны в качестве обратного вызова, потому что блок несет как код, который будет выполняться на обратном вызове, так и данные, необходимые во время этого выполнения.
A lambda is just an anonymous function - a function defined with no name. In some languages, such as Scheme, they are equivalent to named functions. In fact, function definition is rewritten as binding a lambda to a variable internally. In other languages, like Python, there are some (rather needless) distinctions between them, but they behave the same way otherwise.

As lower level languages, C and C++ had no concept of anonymous functions. To add them, new syntax had to be created. Because of this, Objective-C blocks and C++0x lambdas ended up with somewhat different syntax. An empty Objective-C block looks like this:
```
^{}
```
Whereas an empty C++0x lambda looks like this:
```
[]{}
```
So far not much different. They both use the standard C `{}` symbols to separate a block of code, with a special symbol to indicate that this is a block or lambda, not a normal C block. In both cases, the `{}` section takes normal code.
The anonymous function can take arguments by writing them in parentheses, in the style of function arguments, after the leading bit:
```objectivec
^(int x, NSString *y){} // ObjC, take int and NSString*
```
```c++
[](int x, std::string y){} // C++, take int and std::string
```
In both languages, a value can be returned, and the return type can be inferred from the return statement:
```objectivec
^{ return 42; } // ObjC, returns int
```
```c++
[]{ return 42; } // C++, returns int
```
Here, the two features begin to diverge. With C++0x lambdas, the return type can only be inferred if the lambda contains a single statement, and that statement is a return statement. So while the above is valid, this is not:
```c++
[]{ if(something) return 42; else return 43; }
```
In a more complicated lambda with an inferred return type, the return type is always inferred to be `void`. The code above will therefore produce an error, because it's invalid to return `42` from something with a return type of `void`.

Замыкание — процедура, которая ссылается на свободные переменные в своём лексическом контексте. На примере лямбда это анонимный метод который допускает замыкание.
```c#
//oldArray 1, 2, 5, 10, 20
var newArray = oldArray.Select(x=>x > 5); // замыкание не используется

int y = 1;
var newArray = oldArray.Select(x=>x * y); // замыкание используется
```
Таким образом, лямбда-функция это жаргонное название анонимной функции, то есть функции у которой нет имени.
Замыкание, строго говоря, никак не связано с анонимностью. Замыкание - это по сути вложенная функция, которая может обращаться к переменным в функции, в которую она вложена. Поэтому можно говорить, что замыкание - это функция, у которой есть состояние. При этом замыкающаяся функция может быть анонимной (то есть лямбдой), а может и не быть. Лямбда-функция, аналогично, может быть замыканием, а может и не быть (если она не обращается к переменным, объявленным вне её).

<a name="обратный-вызов"></a>
## Обратный вызов
Ситуация, в которой код ожидает внешних событий, называется обратным вызовом. Для программистов Objective-C существуют три основных формы обратного вызова.

1. Приемник/действие: перед началом ожидания вы говорите: «Когда произойдет Х, отправь это конкретное сообщение этому конкретному объекту». Объект, получающий сообщение, называется приемником. Селектор сообщения и есть действие.
2. Вспомогательные объекты: перед началом ожидания вы говорите: «Здесь имеется вспомогательный объект, поддерживающий твой протокол. Когда что-нибудь произойдет, отправляй ему сообщения. Вспомогательные объекты часто называются делегатами или источниками данных.
3. Оповещения: имеется объект, называемый центром оповещений. Перед началом ожидания вы говорите ему: «Этот объект ожидает таких-то оповещений. При поступлении одного из них отправь объекту это сообщение». Когда происходит Х, объект отправляет оповещение центру оповещений, а последний пересылает его вашему объекту.
4. Блоки

__Example 1__

There is no "callback" in C - not more than any other generic programming concept. They're implemented using function pointers. Here's an example:
```c
void populate_array(int *array, size_t arraySize, int (*getNextValue)(void)) {
    for (size_t i=0; i<arraySize; i++)
        array[i] = getNextValue();
}

int getNextRandomValue(void) {
    return rand();
}

int main(void) {
    int myarray[10];
    populate_array(myarray, 10, getNextRandomValue);
    ...
}
```
Here, the `populate_array` function takes a function pointer as its third parameter, and calls it to get the values to populate the array with. We've written the callback `getNextRandomValue`, which returns a randomish value, and passed a pointer to it to `populate_array`. `populate_array` will call our callback function 10 times and assign the returned values to the elements in the given array.

__Example 2__

Let's say you want to write some code that allows registering callbacks to be called when some event occurs. First define the type of function used for the callback:
```c
typedef void (*event_cb_t)(const struct event *evt, void *userdata);
```
Now, define a function that is used to register a callback:
```c
int event_cb_register(event_cb_t cb, void *userdata);
```
This is what code would look like that registers a callback:
```c
static void my_event_cb(const struct event *evt, void *data) {
    /* do stuff and things with the event */
}

...
event_cb_register(my_event_cb, &my_custom_data);
...
```
In the internals of the event dispatcher, the callback may be stored in a struct that looks something like this:
```c
struct event_cb {
    event_cb_t cb;
    void *data;
};
```
This is what the code looks like that executes a callback.
```c
struct event_cb *callback;
...

/* Get the event_cb that you want to execute */

callback->cb(event, callback->data);
```

<a name="блоки-делегаты-kvo-уведомления"></a>
## Когда использовать блоки, делегаты, KVO и уведомления?
__Block__

* 1–3 callbacks
* Single observer

__Delegate__

* Many callbacks
* Single observer
* Formal interface

__KVO__

* Any number of observers
* Just want to be notified of changes to state of an object
* Simplistic updates, unrelated to behavior

__Notifications__

* Multiple observers
* Observer 'far away' from observee

http://albertodebortoli.com/blog/2013/04/21/objective-c-blocks-under-the-hood/

http://albertodebortoli.com/blog/2013/08/03/objective-c-blocks-caveat/

https://www.mikeash.com/pyblog/friday-qa-2009-08-14-practical-blocks.html

http://rypress.com/tutorials/objective-c/blocks

https://clang.llvm.org/docs/Block-ABI-Apple.html
