- [Коллекции в Objective-C](#коллекции-в-objective-c)
	- [Разница между Set и Array](#разница-между-set-и-array)
	- [Difference between NSArray and CFArray](#difference-between-nsarray-and-cfarray)
	- [Enumeration](#enumeration)
	- [Filtering](#filtering)
	- [Sorting](#sorting)
	- [Зачем нужен NSCache? В чем от реализации кэша на NSDictionary?](#nscache-vs-nsdictionary)

<a name="коллекции-в-objective-c"></a>
# Коллекции в Objective-C
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/objc_collections.png">

__Mutability__

Most collection classes exist in two versions: mutable and immutable (default). What’s the big advantage? Thread safety. Immutable collections are fully thread safe and can be iterated from multiple threads at the same time, without any risk of mutation exceptions. Of course there’s a cost when going from immutable and mutable and back - the object has to be copied twice, and all objects within will be retained/released. Sometimes it’s more efficient to hold an internal mutable collection and return a copied, immutable object on access. Notably, some of the more modern collection classes like `NSHashTable`, `NSMapTable`, and `NSPointerArray` are mutable by default and don’t have immutable counterparts.

__Массив в СИ__

Количество элементов массива определено заранее при объявлении массива. Все элементы упорядочены – каждому присвоен порядковый номер, который называется индексом. Доступ к конкретному элементу массива осуществляется с помощью индекса. В языке Cи все массивы располагаются в отдельной непрерывной области памяти. Первый элемент массива имеет наименьший адрес, а последний – наибольший. Элементы массива могут быть как простыми переменными, так и составными. Элемент массива может иметь несколько индексов. Количество индексов переменной определяет размерность массива. Размерность массивов в языке Cи не ограничена, но чаще используются одномерные и двумерные массивы. Начальное значение индекса элемента массива для каждого измерения в Cи — нуль.
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/c_array.jpg">

## Core Foundation:
* `CFArray / CFMutableArray`

An object of opaque type `CFArray` — is an ordered, compact container of values. The values are in sequential order and the key for accessing these values is their index, an integer specifying a value’s position in the sequence. The range of indexes is from 0 to `n-1` where n is the number of values in the array. An index of `0` identifies the first value in the array. You can think of arrays as numbered slots. An array is said to be compact because, with mutable arrays, deleting a value does not leave a gap in the array.

* `CFDictionary / CFMutableDictionary`

An object of the `CFDictionary` type — is a hashing-based collection whose keys for accessing its values are arbitrary, program-defined pieces of data (or pointers to data). Although the key is usually a string (or, in Core Foundation, a `CFString` object), it can be anything that can fit into the size of a pointer—an integer, a reference to a Core Foundation object, even a pointer to a data structure (unlikely as that might be). The keys of dictionaries are unlike the keys of the other collection objects in that, conceptually, they are also contained by the collection along with the values. Dictionaries are primarily useful for holding and organizing data that can be labeled, such as values extracted from text fields in the user interface.
In Core Foundation, a dictionary differs from an array in that the key used to access a particular value in the dictionary remains the same as values are added to or removed from the dictionary—that is, until a value associated with a particular key is replaced or removed. In an array, the key (that is, the index) that is used to retrieve a particular value can change over time as values are added to or deleted from the array. Also, unlike an array, a dictionary does not put its values in any order. To enable later retrieval of a value, the key of the key-value pair should be constant (or be treated as constant); if the key changes after being used to put a value in the dictionary, the value might not be retrievable. The keys of a dictionary form a set; in other words, keys are guaranteed to be unique in a dictionary.
The access time for a value in the dictionary is guaranteed to be at worst `O(N)` for any implementation, current and future, but will often be `O(1)` (constant time). Insertion or deletion operations will typically be constant time as well, but are `O(N^2)` in the worst case in some implementations. Access of values through a key is faster than accessing values directly (if there are any such operations). Dictionaries will tend to use significantly more memory than a array with the same number of values.

* `CFSet / CFMutableSet`

A set, both in its mathematical sense and in the implementation of `CFSet`, is an unordered collection of distinct elements. `CFSet` creates static sets and `CFMutableSet` creates dynamic sets.

* `CFBag / CFMutableBag`

Sets and bags are related types of collections. What they have in common is that the key for accessing a value in the collection is the value itself. The difference between sets and bags is the membership “rule” for values. With sets, if the value already exists in the collection, an identical value cannot be added to the set; conversely, you can add any value to a bag even if the bag already holds that value.
This “uniquing” functionality (or lack thereof) can have many uses. Say, for example, that your program is searching the Internet and you want to keep all qualifying URLs but don’t want duplicates; a set would work nicely for this purpose. A bag could be useful for statistical sampling; you could put all collected values in it and after you finish collecting data, you could query it for the frequency of each value.

* `CFBinaryHeap`

Implements a container that stores values sorted using a binary search algorithm. All binary heaps are mutable; there is not a separate immutable variety. Binary heaps can be useful as priority queues.

* `CFBitVector / CFMutableBitVector`

For managing bit vectors - ordered collections of bit values, which are either `0` or `1`

* `CFTree / CFMutableTree`

You use `CFTree` to create tree structures that represent hierarchical organizations of information. In such structures, each tree node has exactly one parent tree (except for the root tree, which has no parent) and can have multiple children.

## Foundation:
__Ordered Collections__
* `NSArray / NSMutableArray`

Управляет упорядоченной коллекцией элементов, называемой массивом. Вы можете использовать объекты этого класса для создания неизменяемых массивов. Это значит, что все элементы объектов класса `NSArray` доступны только для чтения. Имеется возможность доступа к элементам массива по индексу. Массивы могут хранить элементы различных типов. Массивы поддерживают сортировку и поиск элементов, а также сравнение самих массивов между собой.
The most interesting part is that Apple doesn’t guarantee `O(1)` access time on individual object access - as you can read in the note about Computational Complexity in the `CFArray.h` `CoreFoundation` header: The access time for a value in the array is guaranteed to be at worst `O(lg N)` for any implementation, current and future, but will often be `O(1)` (constant time). Linear search operations similarly have a worst case complexity of `O(Nlg N)`, though typically the bounds will be tighter, and so on. Insertion or deletion operations will typically be linear in the number of values in the array, but may be `O(Nlg N)` clearly in the worst case in some implementations. There are no favored positions within the array for performance; that is, it is not necessarily faster to access values with low indices, or to insert or delete values with high indices, or whatever.

__Collections of Keys and Values__
* `NSDictionary / NSMutableDictionary`

Следует использовать когда требуется удобный и эффективный способ хранения данных, ассоциированных с ключом. Объекты класса `NSDictionary` позволяют хранить неизменяемые пары объектов “ключ/значение” различных типов. Ключи в словаре `NSDictionary` не могут дублироваться, повторение значений допускается. Типы ключей и значений могут, но не обязаны совпадать. Особенно эффективными по скорости будут операции поиска по ключу, так как словарь специально оптимизирован для них. Because the dictionary copies each key, keys must conform to the NSCopying protocol. Bear this in mind when choosing what objects to use as keys. Although you can use any object that adopts the `NSCopying` protocol and implements the hash and isEqual: methods, it is typically bad design to use large objects, such as instances of `NSImage`, because doing so may incur performance penalties.

__Unordered Collections of Objects__
* `NSSet / NSMutableSet`

Объекты представляют неупорядоченные множества различных объектов. Вы можете использовать множества в качестве альтернативы массивам, когда порядок элементов не важен, но требуется быстрое определение `O(1)` принадлежности объекта множеству. Операция определения принадлежности выполняется значительно быстрее в сравнении с массивами. `NSSet` can only work efficiently if the hashing method used is balanced; if all objects are in the same hash bucket, then `NSSet` is not much faster in object-existence checking than `NSArray`. Variants of `NSSet` are also `NSCountedSet`, and the non-toll-free counter-variant `CFBag / CFMutableBag`.

* `NSOrderedSet / NSMutableOrderedSet`

Объявляет программный интерфейс для упорядоченного множества объектов. Вы задаёте записи неизменяемого множества на этапе его создания, после этого записи не могут быть изменены. Вы можете использовать упорядоченные множества как альтернативу массивам, когда порядок элементов является важным и требуется высокая скорость поиска элементов в коллекции. Класс `NSMutableOrderedSet` объявляет программный интерфейс к изменяемому упорядоченному множеству различных объектов. Объекты класса `NSMutableOrderedSet` объекты не похожи на массивы языка Си. Во время создания такого множества вы можете указать размер, но реальный размер всё равно будет равен `0`.

* `NSCountedSet`

Объявляет программный интерфейс к изменяемой, неупорядоченной коллекции нечетких объектов. Счётное множество также известно как `Bag`. Каждый отдельный объект, вставленный в `NSCountedSet`, имеет счётчик, связанный с ним. Объект `NSCountedSet` отслеживает количество раз, когда объекты были вставлены, и требует, чтобы объекты были удалены такое же количество раз. В то же время, внутри объекта `NSSet` существует только один экземпляр вставляемого объекта, даже если этот объект был добавлен в множество несколько раз.

__Storing Indexes into an Array__
* `NSIndexSet / NSMutableIndexSet`

Represents an immutable collection of unique unsigned integers, known as indexes because of the way they are used. This collection is referred to as an index set. You use index sets in your code to store indexes into some other data structure. For example, given an `NSArray` object, you could use an index set to identify a subset of objects in that array. You should not use index sets to store an arbitrary collection of integer values because index sets store indexes as sorted ranges. This makes them more efficient than storing a collection of individual integers. It also means that each index value can only appear once in the index set. The designated initializers of the `NSIndexSet` class are: `init`, `initWithIndexesInRange:`, and `initWithIndexSet:`. You must not subclass the `NSIndexSet` class. The mutable subclass of `NSIndexSet` is `NSMutableIndexSet`.

* `NSIndexPath`

Представляет путь к конкретному узлу в виде дерева вложенных массивов коллекций. Этот путь известен как индексный путь. Каждый индекс в индексном пути представляет индекс в массиве дочерних элементов от одного узла в дереве к другому.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/complexity.png">

__Pointer collection classes__

The pointer collection classes allow you to further customize the collection to tailor it to your memory and storage needs. The options specified by `NSPointerFunctionsOptions` provide a convenient interface for customizing how the collection manages the pointers it contains.

* `NSPointerArray`

Mutable collection modeled after `NSArray` but it can also hold `NULL` values, which can be inserted or extracted (and which contribute to the object’s count). Moreover, unlike traditional arrays, you can set the count of the array directly. You can use an `NSPointerArray` object when you want an ordered collection that uses weak references. For example, suppose you have a global array that contains some objects. Because global objects are never collected, none of its contents can be deallocated unless they are held weakly. Pointer arrays configured to hold objects weakly do not own their contents. If there are no strong references to objects within such a pointer array, those objects can be deallocated.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/pointerarray.png">

* `NSMapTable`

Is a general-purpose analogue of `NSDictionary`. Contrasted with the behavior of `NSDictionary / NSMutableDictionary`, `NSMapTable` has the following characteristics:
- `NSDictionary` / `NSMutableDictionary` copies keys, and holds strong references to values.
- `NSMapTable` is mutable, without an immutable counterpart.
- `NSMapTable` can hold keys and values with weak references, in such a way that entries are removed when either the key or value is deallocated.
- `NSMapTable` can copy its values on input.
- `NSMapTable` can contain arbitrary pointers, and use pointer identity for equality and hashing checks.

* `NSHashTable`

В отличие от NSSet, поддерживает слабые ссылки. Он может содержать слабые ссылки на объекты. Объекты класса NSHashTable могут содержать произвольные указатели, хранимые объекты не ограничиваются объектами классов. Можно настроить экземпляр `NSHashTable` для работы с произвольными указателями, а не только с объектами классов. Благодаря своим свойствам, класс `NSHashTable` это не множество, потому что он может вести себя по-другому.

_`NSArray` is the best choice to use for a list of items if you're going to iterate over them in sequence, or access directly by index. They are also efficient to use as a queue or stack, as adding or removing items from either the beginning or is `O(1)`. Checking to see if an object exists in the array using `containsObject:` is an `O(N)` operation, as it may take up to `N` comparisons to find the match._
_`NSSet` is a great choice for checking `containsObject:` due to efficient hashing algorithms. Adding/removing items is always `O(1)`. In addition, you have fast set arithmetic operations._
_`NSDictionary` is a great choice if you have a natural key you can use to access objects. This has no inherent order, but if you know the key you can retrieve any object as `O(1)`._

<a name="разница-между-set-и-array"></a>
## Разница между Set и Array
`NSSet` предназначен для создания несортированных массивов данных (например каких-либо объектов). Стоит обратить внимание, что объект, который хранится в `NSSet`, встречается только один раз. Т.е. все элементы `NSSet` — уникальные.
Добавить дубликат элемента в `NSMutableSet` у вас также не получится. Для создания несортированного массива, в котором можно использовать неуникальные элементы, можно использовать `NSCountedSet`. Основным преимуществом `NSCountedSet` перед использованием классического массива `NSArray` является то, что элемент может быть продублирован огромное количество раз и при этом занимать памяти как один элемент. Это объясняется тем, что `NSCountedSet` хранит в памяти только одну копию элемента и запоминает сколько раз этот элемент встречается. Если для вас не важен порядок элементов внутри массива и вы используете действительно большие объемы информации, то использование `NSSet` повысит производительность приложения за счет снижения потребляемой памяти. Несмотря на то, что количество элементов хранящихся в памяти будет одинаковым, `NSSet` не тратит память на то, чтобы помнить в какой последовательности хранятся элементы.

<a name="difference-between-nsarray-and-cfarray"></a>
## Difference between NSArray and CFArray
What's the point of them both existing? There are a few reasons.

* If you want to provide a C API, like the Carbon API, and you need things like arrays and dictionaries of referenced-counted objects, you want a library like Core Foundation (which provides CFArray), and of course it needs to have a C API.
* If you want to write libraries for third-parties to use on Windows (for example), you need to provide a C API.
* If you want to write a low-level library, say for interfacing with your operating system's kernel, and you want avoid the overhead of Objective-C messaging, you need a C API.

So those are good reasons for having Core Foundation, a pure C library.

But if you want to provide a higher-level, more pleasant API in Objective-C, you want Objective-C objects that represent arrays, dictionaries, reference-counted objects, and so on. So you need Foundation, which is an Objective-C library.

When should you use one or the other? Generally, you should use the Objective-C classes (e.g. `NSArray`) whenever you can, because the Objective-C interface is more pleasant to use: `myArray.count` (or `[myArray count]`) is easier to read and write than `CFArrayGetCount(myArray)`. You should use the Core Foundation API only when you really need to: when you're on a platform that doesn't have Objective-C, or when you need features that the Core Foundation API provides but the Objective-C objects lack. For example, you can specify callbacks when creating a `CFArray` or a `CFDictionary` that let you store non-reference-counted objects. The `NSArray` and `NSDictionary` classes don't let you do that - they always assume you are storing reference-counted objects.
Are the CF objects just legacy objects? Not at all. In fact, Nextstep existed for years with just the Objective-C Foundation library and no Core Foundation library. When Apple needed to support both the Carbon API and the Cocoa API on top of the same lower-level operating system facilities, they created Core Foundation support both.

<a name="enumeration"></a>
## Enumeration
Enumeration is where computation gets interesting. It's one thing to encode logic that's executed once, but applying it across a collection – that's what makes programming so powerful.
* Procedural increments a pointer within a loop
* Object Oriented applies a function or block to each object in a collection
* Functional works through a data structure recursively

Cocoa содержит три основных способа перечисления содержимого коллекции. К ним относятся классический луп "for", быстрое перечисление и блочное перечисление. Существует также `NSEnumerator` класс, хотя в целом был замещен быстрым перечислением.

__C Loops (for/while)__

for and while loops are the "classic" method of iterating over a collection. Anyone who's taken Computer Science 101 has written code like this before:
```objectivec
for (NSUInteger i = 0; i < [array count]; i++) {
	id object = array[i];
	NSLog(@"%@", object);
}
```
But as anyone who has used C-style loops knows, this method is prone to off-by-one errors—particularly when used in a non-standard way. Fortunately, Smalltalk significantly improved this state of affairs with an idea called list comprehensions, which are commonly known today as for/in loops.

__List Comprehension (for/in)__

By using a higher level of abstraction, declaring the intention of iterating through all elements of a collection, not only are we less prone to error, but there's a lot less to type:
```objectivec
for (id object in array) {
	NSLog(@"%@", object);
}
```
Поведение для быстрого перечисления немного отличается в зависимости от типа коллекции. Массивы и наборы перечисляют их содержимое, а словари перечисляют свои ключи. `NSIndexSet` и `NSIndexPath` не поддерживают быстрое перечисление.
```objectivec
NSString *key;
for (key in someDictionary) {
	NSLog(@"Key: %@, Value %@", key, [someDictionary objectForKey: key]);
}
```
In Cocoa, comprehensions are available to any class that implements the `NSFastEnumeration` protocol, including `NSArray`, `NSSet`, and `NSDictionary`.
Быстрое перечисление является предпочтительным методом перечисления содержимого коллекции, поскольку оно обеспечивает следующие преимущества:

* Перечисление является более эффективным, чем использование NSEnumerator напрямую.
* Синтаксис краток
* Перечислитель вызывает исключение, если вы измените коллекции при перечислении.
* Вы можете выполнять несколько перечислений одновременно.

__Блочное перечисление__

Для перечисления с блоком, вызовите соответствующий метод и укажите блок для использования.
```objectivec
NSArray *anArray = [NSArray arrayWithObjects:@"A", @"B", @"D", @"M", nil];
NSString *string = @"c";
[anArray enumerateObjectsUsingBlock:^(id obj, NSUInteger index, BOOL *stop) {
	if ([obj localizedCaseInsensitiveCompare:string] == NSOrderedSame) {
		NSLog(@"Object Found: %@ at index: %i", obj, index);
		*stop = YES;
	}
}];
```
Для перечисления `NSArray`, параметр `index` полезен для одновременного перечисления. Без этого параметра, единственный способ получить доступ к индексу был бы использованием метода `indexOfObject:`, который является неэффективным. `stop` параметр важен для производительности, так как он позволяет остановить перечисление раньше, на основе некоторого условия, определяемого в пределах блока. Методы перечисления на основе блока в других коллекциях, немного отличаются по названию.

__Использование перечислителя NSEnumerator__

Абстрактный класс, экземпляры подклассов которого перечисляют коллекции других объектов, таких как массивы и словари. Все методы создания определены в классах коллекций, таких как `NSArray`, `NSSet` и `NSDictionary`, которые обеспечивают специальные объекты `NSEnumerator` для перечисления их содержимого. Например, класс `NSArray` имеет два метода, которые возвращают объект `NSEnumerator`: `objectEnumerator` и `reverseObjectEnumerator`. `NSDictionary` также имеет два метода, которые возвращают объект `NSEnumerator`: `keyEnumerator` и `objectEnumerator`. Эти методы позволяют перечислить содержимое словаря по ключу или по значению, соответственно. Вы отправляете `nextObject`, чтобы вновь созданный объект `NSEnumerator` возвращал следующий объект в оригинальной коллекции. Когда коллекция будет исчерпана, то возвращается `nil`. Вы не можете "сбросить" перечислитель после того, как он исчерпал свои коллекции. Подклассы `NSEnumerator`, используемые `NSArray`, `NSDictionary` и `NSSet` сохраняют коллекцию во время перечисления. Когда перечисление закончено, временные коллекции освобождаются.
_Примечание:_ не безопасно изменение коллекции во время её перечисления. Некоторые коллекции в настоящее время поддерживают такие операции, но такое поведение не гарантировано в будущем.
Для перечисления коллекции, вы должны создать новый перечислитель:
```objective-c
NSMutableDictionary *myMutableDictionary = ... ;
NSMutableArray *keysToDeleteArray = [NSMutableArray arrayWithCapacity:[myMutableDictionary count]];
NSString *aKey;
NSEnumerator *keyEnumerator = [myMutableDictionary keyEnumerator];
while (aKey = [keyEnumerator nextObject]) {
	if (/* Проверка критериев для ключа или значения */) {
		[keysToDeleteArray addObject:aKey];
	}
}
[myMutableDictionary removeObjectsForKeys:keysToDeleteArray];
```

__Array__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/array_performance.png">


__Dictionary__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/dictionary_performance.png">

Why is `NSFastEnumeration` so slow here? Iterating the dictionary usually requires both key and object; fast enumeration can only help for the key, and we have to fetch the object every time ourselves. Using the block-based `enumerateKeysAndObjectsUsingBlock:` is more efficient since both objects can be more efficiently prefetched.

<a name="filtering"></a>
## Filtering
If you look at an arbitrary code base, chances are you’ll sooner or later run into a piece of code similar to this one:
```objectivec
NSMutableArray *oldSkoolFiltered = [[NSMutableArray alloc] init];
for (Book *book in bookshelf) {
	if ([book.publisher isEqualToString:@"Apress"]) {
		[oldSkoolFiltered addObject:book];
	}
}
```
It’s a straight-forward approach to filtering an array of items (in this case, we’re talking about books) using a rather simple if-statement. Nothing wrong with this, but despite the fact we’re using a fairly simple expression here, the code is rather verbose. We can easily imagine what will happen in case we need to use more complicated selection criteria or a combination of filtering criteria.

__Simple filtering with NSPredicate__

Thanks to Cocoa, we can simplify the code by using NSPredicate. NSPredicate is the object representation of an if-statement, or, more formally, a predicate. Predicates are expressions that evaluate to a truth value, i.e. true or false. We can use them to perform validation and filtering. In Cocoa, we can use `NSPredicate` to evaluate single objects, filter arrays and perform queries against Core Data data sets. Let’s have a look at how our example looks like when using `NSPredicate`:
```objectivec
NSPredicate *predicate = [NSPredicate predicateWithFormat:@"publisher == %@", @"Apress"];
NSArray *filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
```

__Filtering with Regular Expressions__

Regular Expressions can be used to solve almost any problem, so it’s good to know you can use them in `NSPredicates` as well. To use regular expressions in your `NSPredicate`, you need to use the `MATCHES` operator. Let’s filter all books that are about iPad or iPhone programming:
```objectivec
predicate = [NSPredicate predicateWithFormat:@"title MATCHES '.*(iPhone|iPad).*'"];
filtered = [bookshelf filteredArrayUsingPredicate:predicate];
NSLog(@"Books that contain 'iPad' or 'iPhone' in their title", filtered);
```
You need to obey some rules when using regular expressions in `NSPredicate`: most importantly, you cannot use regular expression metacharacters inside a pattern set.

__Filtering using set operations__

Let’s for a moment assume you want to filter all books that have been published by your favorite publishers. Using the `IN` operator, this is rather simple: first, we need to set up a set containing the publishers we’re interested in. Then, we can create the predicate and finally perform the filtering operation:
```objectivec
NSArray *favoritePublishers = [NSArray arrayWithObjects:@"Apress", @"O'Reilly", nil];
predicate = [NSPredicate predicateWithFormat:@"publisher IN %@", favoritePublishers];
filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
NSLog(@"Books published by my favorite publishers", filtered);
```

__Advanced filtering thanks to KVC goodness__

NSPredicate relies on key-value coding to achieve its magic. On one hand this means your classes need to be KVC compliant in order to be queried using `NSPredicate` (at least the attributes you want to query). On the other hand, this allows us to perform some very interesting things with very little lines of code. Let’s for example retrieve a list of books written by authors with the name “Mark”:
```objectivec
predicate = [NSPredicate predicateWithFormat:@"authors.lastName CONTAINS %@", @"Mark" ];
filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
```
In case we’d want to return the value of one of the aggregate functions, we don’t need to use NSPredicate itself, but instead use KVC directly. Let’s retrieve the average price of all books on our shelf:
```objectivec
NSNumber *average = [bookshelf valueForKeyPath:@"@avg.price"];
```

<a name="sorting"></a>
## Sorting

Вам может потребоваться разместить несколько созданных пользователем строк в алфавитном порядке, либо вам потребуется разместить номера в убыванию или по возрастанию – используйте дескрипторы блоков и селекторов. Дескрипторы сортировки (экземпляры NSSortDescriptor) обеспечивают удобный и абстрактный способ описания порядка сортировки.
Простая сортировка по алфавиту:
```objectivec
NSArray *myArray = @[@"v", @"a", @"c", @"b", @"z"];
NSLog(@"%@", [myArray sortedArrayUsingSelector:@selector(caseInsensitiveCompare:)]);
```
`sortedArrayUsingDescriptors:` или `sortUsingDescriptors:`
```objectivec
//Сначала создадим массив из словарей
NSString *LAST = @"lastName";
NSString *FIRST = @"firstName";
NSMutableArray *array = [NSMutableArray array];
NSArray *sortedArray;
NSDictionary *dict;
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Jo", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Joe", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Joe", FIRST, @"Smythe", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Joanne", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:@"Robert", FIRST, @"Jones", LAST, nil];
[array addObject:dict];
//Далее сортируем содержимое массива по last name затем first name
//Результаты могут быть показаны пользователю
//Обратите внимание на использование localizedCaseInsensitiveCompare:selector
NSSortDescriptor *lastDescriptor = [[NSSortDescriptor alloc] initWithKey:LAST ascending:YES selector:@selector(localizedCaseInsensitiveCompare:)];
NSSortDescriptor *firstDescriptor = [[NSSortDescriptor alloc] initWithKey:FIRST ascending:YES selector:@selector(localizedCaseInsensitiveCompare:)];
NSArray *descriptors = [NSArray arrayWithObjects:lastDescriptor, firstDescriptor, nil];
sortedArray = [array sortedArrayUsingDescriptors:descriptors];
```

__Сортировка с помощью функции__

Такой подход значительно менее гибкий.
```objectivec
NSInteger lastNameFirstNameSort(id person1, id person2, void *reverse) {
	NSString *name1 = [person1 valueForKey:LAST];
	NSString *name2 = [person2 valueForKey:LAST];
	NSComparisonResult comparison = [name1 localizedCaseInsensitiveCompare:name2];
	if (comparison == NSOrderedSame) {
		name1 = [person1 valueForKey:FIRST];
		name2 = [person2 valueForKey:FIRST];
		comparison = [name1 localizedCaseInsensitiveCompare:name2];
	}
	if (*(BOOL *)reverse == YES) {
		return 0 - comparison;
	}
	return comparison;
}
BOOL reverseSort = YES;
sortedArray = [array sortedArrayUsingFunction:lastNameFirstNameSort context:&reverseSort];
```

__Сортировка с блоками__

```objectivec
NSArray *sortedArray = [array sortedArrayUsingComparator: ^(id obj1, id obj2) {
	if ([obj1 integerValue] > [obj2 integerValue]) {
		return (NSComparisonResult)NSOrderedDescending;
	}
	if ([obj1 integerValue] < [obj2 integerValue]) {
		return (NSComparisonResult)NSOrderedAscending;
	}
	return (NSComparisonResult)NSOrderedSame;
}];
```

__Сортировка с помощью функций и селекторов__

Следующий листинг иллюстрирует использование методов `sortedArrayUsingSelector:`, `sortedArrayUsingFunction:context:`, и `sortedArrayUsingFunction:context:hint:`. Самым сложным из этих методов является `sortedArrayUsingFunction:context:hint:`. Он наиболее эффективен, когда у вас есть большой массив (`N` записей), которые вам надо отсортировать раз и затем лишь слегка изменить (`P` добавлений и удалений, где `P` гораздо меньше, чем `N`). Вы можете использовать работу, которую вы сделали в оригинальнй сортировке, и сделать своего рода слияние между `N` "старых" предметов и `Р` "новых" предметов. Чтобы получить соответствующую подсказку, вы используете sortedArrayHint когда исходный массив был отсортирован, и держите его, пока вам это нужно (если вы хотите, отсортировать массив после того, как он был изменен).
```objectivec
NSInteger alphabeticSort(id string1, id string2, void *reverse) {
	if (*(BOOL *)reverse == YES) {
		return [string2 localizedCaseInsensitiveCompare:string1];
	}
	return [string1 localizedCaseInsensitiveCompare:string2];
}
NSMutableArray *anArray = [NSMutableArray arrayWithObjects:
@"aa", @"ab", @"ac", @"ad", @"ae", @"af", @"ag", @"ah", @"ai", @"aj", @"ak", @"al", @"am", @"an", @"ao", @"ap", @"aq", @"ar", @"as", @"at", @"au", @"av", @"aw", @"ax", @"ay", @"az", @"ba", @"bb", @"bc", @"bd", @"bf", @"bg", @"bh", @"bi", @"bj", @"bk", @"bl", @"bm", @"bn", @"bo", @"bp", @"bq", @"br", @"bs", @"bt", @"bu", @"bv", @"bw", @"bx", @"by", @"bz", @"ca", @"cb", @"cc", @"cd", @"ce", @"cf", @"cg", @"ch", @"ci", @"cj", @"ck", @"cl", @"cm", @"cn", @"co", @"cp", @"cq", @"cr", @"cs", @"ct", @"cu", @"cv", @"cw", @"cx", @"cy", @"cz", nil];
// внимание: anArray отсортирован
NSData *sortedArrayHint = [anArray sortedArrayHint];
[anArray insertObject:@"be" atIndex:5];
NSArray *sortedArray;
// сортировка используя селектор
sortedArray = [anArray sortedArrayUsingSelector:@selector(localizedCaseInsensitiveCompare:)];
// сортировка используя функцию
BOOL reverseSort = NO;
sortedArray = [anArray sortedArrayUsingFunction:alphabeticSort context:&reverseSort];
// сортировка с подсказкой
sortedArray = [anArray sortedArrayUsingFunction:alphabeticSort context:&reverseSort hint:sortedArrayHint];
```
Sorting 1,000,000 elements:
```
selector: 4947.90[ms]
function: 5618.93[ms]
block: 5082.98[ms]
```

<a name="nscache-vs-nsdictionary"></a>
## Зачем нужен NSCache? В чем от реализации кэша на NSDictionary?

`NSCache` objects differ from other mutable collections in a few ways:

* The NSCache class incorporates various auto-removal policies, which ensure that it does not use too much of the system’s memory. The system automatically carries out these policies if memory is needed by other applications. When invoked, these policies remove some items from the cache, minimizing its memory footprint.
* You can add, remove, and query items in the cache from different threads without having to lock the cache yourself.
* Retrieving something from an `NSCache` object returns an autoreleased result.
* Unlike an `NSMutableDictionary` object, a cache does not copy the key objects that are put into it.
* These features are necessary for the `NSCache` class, as the cache may decide to automatically mutate itself asynchronously behind the scenes if it is called to free up memory.
