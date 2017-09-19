- [Структуры данных](#структуры-данных)
	- [Массив](#массив)
		- [Ассоциативный массив](#ассоциативный-массив)
			- [Хеш-таблица](#xеш-таблица)
	- [Множество](#множество)
	- [Список](#список)
		- [Связный список ](#связный-список)
		- [Двусвязный список ](#двусвязный-список)
		- [Кольцевой список ](#кольцевой-список)
	- [Очередь](#очередь)
		- [Стек ](#стек)
		- [Дек](#дек)
	- [Куча](#куча)
	- [Граф](#граф)
	- [Дерево](#дерево)
		- [Бинарное дерево поиска](#бинарное-дерево-поиска)
		- [Красно-черное дерево](#красно-черное-дерево)

<a name="структуры-данных"></a>
# Структуры данных

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/data_structures_kinds1.png">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/data_structures_kinds2.png">

<a name="массив"></a>
## Массив
_array_

Фиксированный набор данных одного типа в виде непрерывного ряда. Простая базовая статическая структура данных с последовательным распределением элементов в памяти с прямым или произвольным доступом (одномерный массив – вектор, двухмерный – матрица).

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/array.png">

Операции:
* Получить элемент за время `log(n)`
* Записать элемент

Плюсы:
* Доступ за постоянное время
* Память тратится только на данные

Минусы:
* Статичная, неизменяемая структура

<a name="ассоциативный-массив"></a>
### Ассоциативный массив
_associative array, map, symbol table, dictionary_

An associative array, map, symbol table, or dictionary is an abstract data type composed of a collection of pairs, such that each possible key appears at most once in the collection.
Operations associated with this data type allow:
* the addition of pairs to the collection
* the removal of pairs from the collection
* the modification of the values of existing pairs
* the lookup of the value associated with a particular key

Ассоциативный массив еще называют нагруженным множеством (data + info), где data – ключ, а нагрузка – значение ключа.

<a name="xеш-таблица"></a>
#### Хеш-таблица
_hash table, hash map_

Ассоциативный массив, хранит пары  в виде связанного списка (open hash, closed address) или массива пар (closed hash, open address). Индекс элемента равен хеш-функции от ключа i = hash(key). Разбиение множества на подмножества происходит с помощью хеш функции (пример: телефонная книга).

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/hash_table.png">

<a name="множество"></a>
## Множество
_set_

A set is an abstract data structure that can store certain values, without any particular order, and no repeated values. It is a computer implementation of the mathematical concept of a finite set. Unlike most other collection types, rather than retrieving a specific element from a set, one typically tests a value for membership in a set. Some set data structures are designed for static or frozen sets that do not change after they are constructed. Static sets allow only query operations on their elements — such as checking whether a given value is in the set, or enumerating the values in some arbitrary order. Other variants, called dynamic or mutable sets, allow also the insertion and deletion of elements from the set.

<a name="список"></a>
## Список
_list_

Простейшая динамическая структура, упорядоченное множество с переменным числом элементов.

<a name="связный-список"></a>
### Связный список
_linked list_

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/singly_linked_list.png">

<a name="двусвязный-список"></a>
### Двусвязный список
_doubly linked list_

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/doubly_linked_list.png">

<a name="кольцевой-список"></a>
### Кольцевой список
_circular Linked list_

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/circular_linked_list.png">

Плюсы
*	Движение в обе стороны
*	Добавление элемента за `O(1)` время
*	Удаление за `O(1)` время

Минусы
*	На указатели тратится дополнительная память
*	Поиск только последовательный путем перебора за `O(n)`

Отличие списка от массива:

Массив имеет фиксированное время перехода по индексу, но нуждается в монолитном секторе памяти, обладает нефиксированным временем вставки и удаления.
Список более требователен к памяти, дольше переход по индексу, но значительно быстрее вставка и удаление за `O(1)`. В Java и в C++ явно различаются `List` и `Array`, в Objective-C `NSMutableArray` скорее список, чем массив.

<a name="очередь"></a>
## Очередь
_queue_

Абстрактный тип данных с дисциплиной доступа к элементам «первый пришёл — первый вышел» (FIFO, first-in-first-out). Добавление элемента (принято обозначать словом enqueue — поставить в очередь) возможно лишь в конец очереди, выборка — только из начала очереди (что принято называть словом dequeue — убрать из очереди), при этом выбранный элемент из очереди удаляется.

<a name="стек"></a>
### Стек
_stack_

Стек – реализация очереди LIFO (last-in-first-out) и является структурированной областью памяти, в отличие от кучи. Последовательный список с переменной длинной, включение и исключение только из вершины стека. Состоит из последовательности фреймов.
Пример: после вызова метода из стека выделяется запрошенная область памяти – фрейм, который хранит значения объявленных переменных.

Операции:
*	Включение
*	Исключение
*	Определение размера
*	Очистка
*	Неразрушающее чтение

Функция стека – сохранить работу, невыполненную до конца, с возможностью переключения на другую работу.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/stack.png">

<a name="дек"></a>
### Дек
_double ended queue, dequeue_

Очередь с двумя концами, включение и исключение из любого конца (левого или правого).

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/dequeue.png">

<a name="куча"></a>
## Куча
_heap_

Куча как структура данных представляет собой дерево, где родитель A >= ребенка B => A – корень кучи. Max куча, Min куча.

Операции:
* Найти max или min
* Удалить max или min
* Увеличить ключи или уменьшить
* Добавить
* Слияние

Куча как область памяти – реализация динамически распределяемой памяти, в которой хранятся все объекты (вызов `alloc` в Objective-C выделяет из кучи требуемую область памяти).

<a name="граф"></a>
## Граф
_graph_

Фигура, состоящая из вершин и ребер, соединяющих вершины. Направленный и ненаправленный.

<a name="дерево"></a>
## Дерево
_tree_

Связаный граф без циклов. Выделена одна вершина – корень. Остальные – сыновья. Если нет ребенка – терминальная вершина

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tree.png">

<a name="бинарное-дерево-поиска"></a>
### Бинарное дерево поиска
_binary search tree_

Состоит из узлов (записей) вида `data`, `left`, `right`, где
```
key[left[x]] < key[x] <= key[right[x]]
```
Ключ данных родительского узла больше левого сына и нестрого меньше правого.

<a name="красно-черное-дерево"></a>
### Красно-черное дерево
_red-black tree, rb-tree_

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/red_black_tree.png">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/red_black_tree_statistics.png">

Одно из самобалансирующихся двоичных деревьев поиска, гарантирующих логарифмический рост высоты дерева от числа узлов и быстро выполняющее основные операции дерева поиска: добавление, удаление и поиск узла. Сбалансированность достигается за счёт введения дополнительного атрибута узла дерева — «цвета». Этот атрибут может принимать одно из двух возможных значений — «чёрный» или «красный».
* Узел либо красный, либо чёрный.
* Корень — чёрный. (В других определениях это правило иногда опускается. Это правило слабо влияет на анализ, так как корень всегда может быть изменен с красного на чёрный, но не обязательно наоборот).
* Все листья (NIL) — черные.
* Оба потомка каждого красного узла — черные.
* Всякий простой путь от данного узла до любого листового узла, являющегося его потомком, содержит одинаковое число черных узлов.
