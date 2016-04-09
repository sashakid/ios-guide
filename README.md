# ios-guide

Оглавление

Структуры данных	7
Массив	8
Ассоциативный массив	9
Множество	9
Список	9
Стек и фрейм	10
Очередь FIFO	11
Дек	11
Куча	12
Граф	12
Дерево	12
Коллекции в Objective-C	13
Разница между set и array?	17
Difference between NSArray and CFArray	17
Enumeration	18
Using NSPredicate to Filter Data	20
Сортировка массивов	21
Алгоритмы	23
Нотация «большое О»	23
Последовательный поиск	25
Бинарный поиск 	25
Сортировка вставками 	26
How to merge two sorted arrays into a sorted array?	29
Рекурсивная функция 	29
Факториал	30
Последовательность Фибоначчи	30
 Программирование	30
Язык СИ.	32
Битовые операции	33
Примеры битовых операций	36
Что такое указатель и ссылка и в чем разница?	36
Почему (NSError **) использует указатель на указатель?	37
How to return 2+ values from a function?	38
What is the difference between char * const and const char *?	40
Что значит n & (n – 1)?	40
ООП	41
История ООП	41
Основные понятия ООП: абстракция, инкапсуляция, наследование, полиморфизм.	41
Другие понятия ООП	44
В чем плюсы и минусы ООП? 	45
Objective-C	48
Swift	50
Вопросы	51
Xcode, фреймворки	51
Core Foundation 	53
UIKit	55
AddressBook	56
CFNetwork	57
QuartzCore	58
CoreText	59
Templates в Xcode, структура проекта, код?	60
iOS	60
IPhone, resolution, pixels vs points?	61
Файловая система iOS	62
App lifecycle	62
Возможные состояния программы	63
Жизненный цикл UIViewController	64
Представления	65
MEMORY MANAGEMENT	66
Память в стеке и в куче	66
Manual retain-release	68
Automatic Reference Counting.	70
Модификаторы	71
Для свойств	71
Для переменных	73
Что такое property?	74
Написать сеттер и геттер для свойства, с ARC и без.	74
В каких случаях лучше использовать strong, а в каких copy для NSString? Почему?	74
autorelease vs release?	74
Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC?	75
Основные темы управления памятью, такие как владение retain/release/autorelease	75
Вопрос о циклах в графах владения, и почему свойства delegate (предоставляющие доступ к делегату) обычно задаются как assign?	75
Что произойдет если сначала нажать на кнопку 1 а потом на кнопку 2?	75
Нужно ли ретейнить (посылать сообщение retain) делегат для CAAnimation? 	75
Что произойдет при исполнении следующего кода? 	75
Реализуйте следующие методы: retain, release, autorelease	75
Если я вызову performSelector:withObject:afterDelay: – объекту пошлется сообщение retain? 	76
Вы можете объяснить, что происходит когда вы посылаете объекту сообщение autorelease? 	76
Объясните что такое подсчет ссылок (retain count)? 	76
Паттерны проектирования	76
Communication Patterns	77
Концепция Model–View–Controller	78
Делегирование 	79
Кластеры	79
Синглтон	80
Adapter	81
Command	82
Composite	82
Decorator	83
Facade	85
Iterator	85
Mediator	86
Memento	86
Proxy	87
Ленивая загрузка 	87
Observer 	88
Notification	88
KVC	88
KVO	89
Цепочка ответственности	91
Анти-паттерны в объектно-ориентированном программировании	91
Какая разница между использованием делагатов и нотификейшенов?	91
Runtime	93
Что такое указатель isa? Для чего он нужен?	94
Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?	95
Как в C можно описать вызов метода [someObject someMethod:someArgument]? 	95
Что такое Run Loop?	95
Что такое классы в Objective-C (структура классов)? 	95
Чем объект Objective-c отличается от структуры С, что такое структура в C? 	96
Вопрос о методах isKindOfClass, isMemberOfClass, etc…	96
Тип id	97
Директивы компилятора	97
Concurrency	99
POSIX Threads	100
NSThread 	100
GCD (Grand Central Dispatch) 	100
NSOperationQueue	101
NSObject instance methods	101
Run Loops	102
Что такое мьютекс?	103
Что такое deadlock?	103
Что такое livelock?	103
Что такое семафор?	103
Чем отличается dispatch_async от dispatch_sync?	103
Для чего при разработке под iOS использовать POSIX-потоки? 	104
Как многопоточность работает с UIKit?	104
Выведется ли в дебагер «Hello world»? Почему? 	104
Что выведется в консоль?	104
Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?	105
Network	105
Преимущества и недостатки синхронного и асинхронного соединения?	105
Что означает http, tcp?	105
Какие различия между HEAD, GET, POST, PUT? 	105
Что такое REST  архитектура?	107
Как загрузить что-то из интернета? (NSURL, NSURLSession, NSURLConnection, NSURLRequest)	108
Парсинг (JSON, HTML, XML).	108
Data	110
Что такое Core Data?	110
В каких случаях лучше использовать SQLite, а в каких Core Data?	110
Что такое Managed object context?	111
Что такое Persistent store coordinator?	111
Какие есть нюансы при использовании Core Data в разных потоках? Как синхронизировать данные между потоками?	112
Какие типы хранилищ поддерживает CoreData?	112
Что такое ленивая загрузка (lazy loading)? Что ее связывает с CoreData? Опишите ситуация когда она может быть полезной?	112
Что такое fetch result controller?	112
Тестирование	112
Общие вопросы	113
Блоки 	113
Обратный вызов	114
Когда использовать блоки, делегаты, KVO и уведомления?	115
Swift closures and functions	115
Closures	116
How Do I Declare a Closure in Swift?	117
Заполнить строку буквами А, чтобы не делать миллионы итераций: 	117
Написать процедуру, инвертирующую массив символов (первый элемент должен стать последним, второй пердпоследним и т.д.)?  	117
Поверхностное и глубокое копирование?	118
Отличие while от for? 	118
Протокол? Что такое абстрактный класс? Чем абстрактный класс отличается от интерфейса?	118
Какие существуют root классы в iOS? Для чего нужны root классы?	119
Чем категория отличается от расширения (extention, неименованная категория)?	119
Можно ли добавить ivar в категорию?	120
Когда лучше использовать категорию, а когда наследование?	120
Формальные и неформальные протоколы	120
Есть ли приватные или защищенные методы в Objective-C?	120
Что не так с этим кодом? Зачем нужны инициализаторы? [[[SomeClass alloc] init] init];	121
Что такое назначеный инициализатор (designated initializer), напишите любой элементарный инициализатор, почему он так выглядит? if (self  = [super...]) 	121
Какой метод вызовется: класса A или класса B? Как надо изменить код, чтобы вызвался метод класса A?	121
Что выведется в консоль? Почему?	122
Как работают push нотификации?	122
Memory warning	123
Как лучше всего загрузить UIImage c диска (с кеша)?	123
Какой контент лучше хранить в Documents, а какой в Cache?	124
Как из строки вытащить подстроку?	124
NSCoding, archiving? 	124
Как работает UITableView?	125
Константы, typedef, enum, #define	126
Что такое awakeFromNib?	129
Что происходит когода мы пытаемся вызвать метод у nil указателя? Разница между nil и Nil. 	129
Что такое неформальный протокол?	130
В чем разница между NSString и char? (Что значит приставка NS в общем?)	130
Опишите иерархию классов от UIButton до NSObject. 	130
Что такое контекст (context)? 	130
[NSArray arrayWithObjects: a, b, c, nil]; зачем nil вконце?	131
Сработает ли таймер? Что нужно чтобы сработал?	131
Что такое xib и storyboard, в чем отличие, что лучше использовать?	131
Задачи	137
Задача про банерокрутилку	137
Задача на регулярное выражение	137
Метод, возвращающий N наиболее часто встречающихся слов во входной строке.	137
Используя NSURLConnection, напишите метод для асинхронной загрузки текстового документа по HTTP. Приведите пример его использования.	139
Перечислите все проблемы, которые вы видите в приведенном ниже коде. Предложите, как их исправить.	139
Напишите запрос, возвращающий названия треков, скачанных более 1000 раз.	140






























Бит и байт	И. – мера разрешения неопределенности. Бит (Binary digIT, bit – кусо-чек) выбран как мера неопределенности с двумя возможными состоя-ниями: истина-ложь, да-нет, 1-0. Любые данные в компьютере пред-ставлены в виде последовательности битов. Цифровая И. хранится благодаря различию между разными величинами какой-либо физиче-ской характеристики (ток, напряжение) => чем больше велечин, кото-рые нужно различать, тем меньше различий между смежными вели-чинами => тем менее надежна память. В двоичной системе следует различать всего два состояния => это самый надеждный метод коди-рования И. 8 бит памяти позволяет хранить 28 = 256 комбинаций нулей и единиц.
Память	Сверхоперативная, оперативная и внешняя. Некоторые регистры сверхоперативной П. (в которые могут помещаться аргументы ариф-митических операций) находятся в ЦП. Также они используются для хранения текущих или следующих команд. Оперативная П. – для запо-минания более постоянной И. Каждая ячейка ОП имеет свой иденти-фикатор (адрес) в массиве ячеек П. Самая маленькая ячейка имеет размер 8 бит (байт). Внешняя П. служит для долговременного хране-ния И., используется для хранения самих программ. 
Тип данных, аб-страктный тип данных	Например, числа: натуральные, целые, вещественные; литеры, строки и т. д. В языке СИ: int, float, char. Тип данных указывает, как будут использоваться определенные наборы битов. Функция задает операции, выполняемые над данными. Структура служит для группировки порций И. Указатели – для непрямой ссылки на И. АТД – тип данных с доступом через интерфейс, реализация – скрыта. Доступ к переменным – через операции, определенные в интерфейсе. 
Структура данных	Пространственное понятие: схема организации И. в компьютере. Мно-жество элементов данных и множество связей между ними. От выбора СД зависит производительность программы. Тип СД определяет:
•	Как хранятся данные в структуре (выделение памяти, представ-ление данных)
•	Множество допустимых значений, который принимает объект в СД
•	Множество операций, которые могут применяться к объекту
Операции над СД – CRUD
 
СД в ООП реализуется в виде классов, данные хранятся в переменных класса, системе предписаний соответстует набор методов класса. 
ПРОСТЫЕ БАЗОВЫЕ (числовые, символьные, логические, перечисление, интервал, указатели)
СТАТИЧЕСКИЕ (вектор, массив, множество, запись, таблица)
ПОЛУСТАТИЧЕСКИЕ (стек, очередь, дек, строка)
ДИНАМИЧЕСКИЕ (связный список, граф, дерево)
Алгоритмы	«Рецепт расчета» – метод, разработанный для решения задачи, при-годный для реализации в компьютерной программе. Сам алгоритм яв-ляется абстракцией, но его представление – конкретно и может ме-няться в зависимости от архитектуры компьютера, ЯП и т. д. Пред-ставление алгоритма конструируется из блоков – примитивов. Набор примитивов и правил, как комбинировать эти примитивы для вопло-щения более сложных идей организуют ЯП. Примитив состоит из син-таксической и семантической части. Описание алгоритма на низком уровне – неудобно, поэтому используются абстракции для примитивов более высокого уровня, которые состоят из примитивов низкого. Ите-рационная структура – выполнение набора инструкций в циклическом режиме. Рекурсивная – каждая стадия повторения цикла реализуется как подзадача предыдущей стадии. Чтобы оценить производитель-ность нужно подсчитать кол-во операций. Различают временную сложность и пространственную (используемая память).
О – (сложность в наихудшем случае), асимптотическая верхняя оценка кол-ва операций => времени работы (худший вариант). При оценке берется кол-во операций, возрастающих быстрее всего. 
Ω – сложность в лучшем случае
Θ – сложность в среднем, когда оценка Ω = О
Наилучшая оценка алгоритма – О(1), константная, когда алгоритм без циклов и рекурсии.
ЯП	Служит для точного описания АТД и алгоритмов. Компилятор транс-лирует текст программы на ЯП в машинный код, связывая каждый идентификатор (имя) с адресом памяти. 
Программа	СД и алгоритмы – это материалы, из которых строятся программы и сам компьютер. В основе работы компьютера – умение работать с дво-ичными данными, битами, под командами ЦП в виде специальных ин-струкций – алгоритмов. Задачи редко выражаются в виде битов: они выражаются в виде чисел, символов, строк и более сложных структур – последовательностей, списков, деревьев и т. д. Задача, которую решает программа – преобразование входных данных в выходные. 
Объект	Сущность в  виртуальном пространстве, которой можно посылать со-общения и которая может на них реагировать, используя свои данные, появляющаяся при создании экземпляра класса или копирования прототипа, обладающая определённым состоянием и поведением, имеющая заданные значения свойств (атрибутов) и операций над ними (методов). Как правило, при рассмотрении объектов выделяется то, что объекты принадлежат одному или нескольким классам, которые определяют поведение или роль (являются моделями) объекта. Термины «экземпляр класса» и «объект» взаимозаменяемы. Объект, наряду с понятием класс, является важным понятием объектно-ориентированного подхода. Объекты обладают свойствами наследования, инкапсуляции и полиморфизма.
Прототип	Объект-образец, по образу и подобию которого создаются другие объекты. Объекты-копии могут сохранять связь с родительским объектом, автоматически наследуя изменения в прототипе.
Класс	Модель еще не существующей сущности (объекта). Описывает устройство объекта, является как бы чертежом объекта.
Метод	Действие, которое выполняется над экземпляром класса (простой метод) (-) или самим классом (статический метод) (+). Простые методы имеют доступ к данным объекта (конкретного экземпляра данного класса), статические методы  не имеют доступа к данным объекта и для их использования не нужно создавать экземпляры (данного класса). Метод класса используется для создания новых объектов и называется фабричным методом. Также может использоваться для доступа к глобальным данным.
NSString: + stringWithContentsOfFile:encoding:error:, + stringWithString:, + stringWithFormat:, – init, – initWithString:, – lowercaseString.
Глобальная пере-менная	Объявляется в начале программы вне любого метода, значение которой можно использовать из любого места модуля или другого файла. 
Локальная пере-менная 	Существует только во время выполнения метода и доступ к ним может выполняться только внутри метода, в котором она определена.
Статическая пере-менная	Сохраняет свое значение при нескольких вызовах метода, в отличие от локальной переменной. Инициализируется только один раз в начале выполнения программы.
Переменная экзем-пляра, instance var-iable, ivar	Данные, которые может содержать объект класса. Каждый раз создавая новый объект, создается и новый, причем уникальный, набор переменных экземпляра объекта. Поэтому, если у вас имеется два экземпляра объекта класса Fraction, к примеру, fracA и fracB, то каждый из них будет иметь свой собственный набор переменных. То есть, fracA и fracB будут иметь свои собственные numerator и denomi-nator.
Абстракция	Смысловая конструкция, кратко описывающая СД и операции над ни-ми для упрощения понимания. Отделение объекта от его реализации (данные обрабатываются функцией высокого уровня с помощью функции низкого уровня). Существует из-за неудобства описания опе-раций на низком уровне.
Инкапсуляция	Сокрытие методов и переменных от других объектов и частей про-граммы.
Наследование	Процесс при котором один объект приобретает свойства и методы другого объекта.
Полиморфизм	Возможность объектов с одинаковой спецификацией иметь различную реализацию (например, объект UIViewController может быть и кон-троллером в MVC, и делегатом и источником данных для UITableView, если поддерживает соответствующие протоколы).



Структуры данных


 
 
Массив
Фиксированный набор данных одного типа в виде непрерывного ряда. Простая базовая стати-ческая СД с последовательным распределением элементов в памяти с прямым или произволь-ным доступом (одномерный массив – вектор, двухмерный – матрица).
 
Операции
•	Получить элемент за время log(n)
•	Записать элемент
Плюсы
•	Доступ за постоянное время
•	Память тратится только на данные
Минусы
•	Статичная, неизменяемая структура
Массив в СИ
Количество элементов массива определено заранее при объявлении массива. Все элементы упорядочены – каждому присвоен порядковый номер, который называется индексом. Доступ к конкретному элементу массива осуществляется с помощью индекса. В языке C все массивы располагаются в отдельной непрерывной области памяти. Первый элемент массива имеет наименьший адрес, а последний – наибольший. Элементы массива могут быть как простыми переменными, так и составными. Элемент массива может иметь несколько индексов. Количе-ство индексов переменной определяет размерность массива. Размерность массивов в языке C не ограничена, но чаще используются одномерные и двумерные массивы. Начальное значение индекса элемента массива для каждого измерения в C – нуль.

Ассоциативный массив
An associative array, map, symbol table, or dictionary is an abstract data type composed of a collec-tion of   pairs, such that each possible key appears at most once in the collection.
Operations associated with this data type allow:
•	the addition of pairs to the collection
•	the removal of pairs from the collection
•	the modification of the values of existing pairs
•	the lookup of the value associated with a particular key
Dictionary (Map) еще называют нагруженным множеством (data + info), где data – ключ, а нагрузка – значение ключа.
Хеш-таблица – ассоциативный массив, хранит пары   в виде связанного списка (open hash, closed address) или массива пар (closed hash, open address). Индекс элемента равен хеш-функции от ключа i = hash(key). Разбиение множества на подмножества происходит с по-мощью хеш функции (пример: телефонная книга).

Множество
A set is an abstract data structure that can store certain values, without any particular order, and no repeated values. It is a computer implementation of the mathematical concept of a finite set. Unlike most other collection types, rather than retrieving a specific element from a set, one typically tests a value for membership in a set. Some set data structures are designed for static or frozen sets that do not change after they are constructed. Static sets allow only query operations on their elements — such as checking whether a given value is in the set, or enumerating the values in some arbitrary or-der. Other variants, called dynamic or mutable sets, allow also the insertion and deletion of elements from the set.
Конечное множество (finit set) — множество, количество элементов которого конечно, то есть, существует неотрицательное целое число k, равное количеству элементов этого множества. В противном случае множество называется бесконечным. Например,
  – конечное множество из пяти элементов. Число элементов конечного множества это натуральное число и называется мощно-стью множества. Множество всех положительных целых чисел бесконечно:  

Список
Простейшая динамическая структура, упорядоченное множество с переменным числом эле-ментов. 
Односвязный список
 

Двусвязный список
 

Кольцевой список
 
Плюсы
•	Движение в обе стороны
•	Добавление элемента за O(1) время
•	Удаление за O(1) время
Минусы
•	На указатели тратится дополнительная память
•	Поиск только последовательный путем перебора за O(n)
Отличие списка от массива:
Массив имеет фиксированное время перехода по индексу, но нуждается в монолитном секторе памяти, обладает нефиксированным временем вставки и удаления.
Список более требователен к памяти, дольше переход по индексу, но значительно быстрее вставка и удаление за O(1). В Java и в C++ явно различаются List и Array, в ObjC NSMutableArray скорее список, чем массив.

Стек и фрейм
Стек – очередь LIFO (last-in-first-out) структурированная область памяти, в отличие от кучи. Последовательный список с переменной длинной, включение и исключение только из верши-ны стека. Состоит из последовательности фреймов. После вызова метода из стека выделяется запрошенная область памяти – фрейм, который хранит значения объявленных переменных.
•	Включение
•	Исключение
•	Определение размера
•	Очистка
•	Неразрушающее чтение
Функция стека – сохранить работу, невыполненную до конца, с возможностью переключения на другую работу. 

 
 
Очередь FIFO
Акроним First In, First Out — «первым пришёл — первым ушёл» — способ организации и манипулирования данными относительно времени и приоритетов. Это выражение описывает принцип технической обработки очереди или обслуживания конфликтных требований путём упорядочения процесса по принципу: «первым пришёл — первым обслужен» (ПППО). Тот, кто приходит первым, тот и обслуживается первым, пришедший следующим ждёт, пока обслужи-вание первого не будет закончено, и так далее. В информатике этот термин относится к спосо-бу запоминания данных, обрабатываемых в очереди. Каждый элемент очереди хранится в структуре данных очереди (без исключений). Первые данные, добавленные в очередь, будут первыми из неё удалены, то есть обработка производится последовательно в том же порядке, что и поступление. Это типичное поведение для очереди, хотя и не единственно возможное

Дек
Double ended queue – очередь с двумя концами, включение и исключение из любого конца (ле-вого или правого).
 

Куча
Куча как СД – дерево, родитель A >= ребенка B => A – корень кучи. Max куча, Min куча.
•	Найти max или min
•	Удалить max или min
•	Увеличить ключи или уменьшить
•	Добавить
•	Слияние
Куча как область памяти – реализация динамически распределяемой памяти, в которой хра-нятся все объекты. alloc – из кучи выделяется требуемая область памяти.
Двоичная куча

Граф
Фигура, состоящая из вершин и ребер, соединяющих вершины. Направленный и ненаправлен-ный. 

Дерево
Связаный граф без циклов. Выделена одна вершина – корень. Остальные – сыновья. Если нет ребенка – терминальная вершина
Бинарное дерево поиска
 
Состоит из узлов (записей) вида data, left, right, где 
key[left[x]] < key[x] <= key[right[x]]
Ключ данных родительского узла больше левого сына и нестрого меньше правого.
Красно-черное дерево

 
 
Одно из самобалансирующихся двоичных деревьев поиска, гарантирующих логарифмический рост высоты дерева от числа узлов и быстро выполняющее основные операции дерева поиска: добавление, удаление и поиск узла. Сбалансированность достигается за счёт введения допол-нительного атрибута узла дерева — «цвета». Этот атрибут может принимать одно из двух возможных значений — «чёрный» или «красный».
•	Узел либо красный, либо чёрный.
•	Корень — чёрный. (В других определениях это правило иногда опускается. Это
правило слабо влияет на анализ, так как корень всегда может быть изменен с красного на чёрный, но не обязательно наоборот).
•	Все листья (NIL) — черные.
•	Оба потомка каждого красного узла — черные.
•	Всякий простой путь от данного узла до любого листового узла, являющегося его потомком, содержит одинаковое число черных узлов.
Коллекции в Objective-C
 
Mutability
Most collection classes exist in two versions: mutable and immutable (default). What’s the big ad-vantage? Thread safety. Immutable collections are fully thread safe and can be iterated from multiple threads at the same time, without any risk of mutation exceptions. Your API should never expose mutable collections. Of course there’s a cost when going from immutable and mutable and back - the object has to be copied twice, and all objects within will be retained/released. Sometimes it’s more efficient to hold an internal mutable collection and return a copied, immutable object on access. Notably, some of the more modern collection classes like NSHashTable, NSMapTable, and NSPointerArray are mutable by default and don’t have immutable counterparts. They are meant for internal class use, and a use case where you would want those immutable would be quite unusual.

Core Foundation:
•	CFMutableDictionary
The access time for a value in the dictionary is guaranteed to be at worst O(N) for any implemen-tation, current and future, but will often be O(1) (constant time). Insertion or deletion operations will typically be constant time as well, but are O(N*N) in the worst case in some implementations. Access of values through a key is faster than accessing values directly (if there are any such opera-tions). Dictionaries will tend to use significantly more memory than a array with the same number of values.
•	CFMutableArray
•	CFMutableBag
•	CFBinaryHeap
•	CFMutableBitVector
•	CFMutableTree
•	CFMutableSet

Foundation:
1.	NSArray (NSMutableArray) – управляет упорядоченной коллекцией элементов, называемой массивом. Вы можете использовать объекты этого класса для создания неизменяемых массивов. Это значит, что все элементы объектов класса NSArray доступны только для чтения. Имеется возможность доступа к элементам массива по индексу. Массивы могут хранить элементы различных типов. Массивы поддерживают сортировку и поиск элементов, а также сравнение самих массивов между собой. Для создания изменяемых массивов следует использовать NSMutableArray.
 
The most interesting part is that Apple doesn’t guarantee O(1) access time on individual object access - as you can read in the note about Computational Complexity in the CFArray.h CoreFoundation header:
The access time for a value in the array is guaranteed to be at worst O(lg N) for any implementa-tion, current and future, but will often be O(1) (constant time). Linear search operations similarly have a worst case complexity of O(Nlg N), though typically the bounds will be tighter, and so on. Insertion or deletion operations will typically be linear in the number of values in the array, but may be O(Nlg N) clearly in the worst case in some implementations. There are no favored positions within the array for performance; that is, it is not necessarily faster to access values with low indices, or to insert or delete values with high indices, or whatever.
2.	NSPointerArray – mutable collection modeled after NSArray but it can also hold NULL values, which can be inserted or extracted (and which contribute to the object’s count). Moreover, unlike traditional arrays, you can set the count of the array directly. In a garbage collected environment, if you specify a zeroing weak memory configuration, if an element is collected it is replaced by a NULL value.
3.	NSDictionary (NSMutableDictionary) – следует использовать когда требуется удобный и эффективный способ хранения данных, ассоциированных с ключом. Объекты класса NSDictionary позволяют хранить неизменяемые пары объектов “ключ/значение” различных типов. Ключи в словаре NSDictionary не могут дублироваться, повторение значений допускается. Типы ключей и значений могут, но не обязаны совпадать. Особенно эффективными по скорости будут операции поиска по ключу, так как словарь специально оптимизирован для них. Если для решения задачи требуется изменение словаря объектов, следует использвать класс NSMutableDictionary.
4.	NSSet (NSMutableSet) – объекты представляют неупорядоченные множества различных объектов. Объект NSSet при создании заполняется множеством объектов, которое не может быть изменено до конца своего существования. Если требуется использовать изменяемые множества, следует воспользоваться классом NSMutableSet. Вы можете использовать множества в качестве альтернативы массивам, когда порядок элементов не важен, но требуется быстрое определение O(1) принадлежности объекта множеству. Операция определения принадлежности выполняется значительно быстрее в сравнении с массивами
NSSet can only work efficiently if the hashing method used is balanced; if all objects are in the same hash bucket, then NSSet is not much faster in object-existence checking than NSArray. Variants of NSSet are also NSCountedSet, and the non-toll-free counter-variant CFBag/CFMutableBag.
5.	NSOrderedSet (NSMutableOrderedSet) – объявляет программный интерфейс для упорядоченного множества объектов. Класс NSOrderedSet объявляет программный интерфейс для неизменяемых множеств различных объектов. Вы задаёте записи неизменяемого множества на этапе его создания, после этого записи не могут быть изменены.С другой стороны, класс NSMutableOrderedSet, объявляет программный интерфейс для динамически изменяемых множеств различных объектов. Динамического или изменяемые множества позволяет добавлять и удалять записи в любое время, автоматически выделяя память по мере необходимости. Вы можете использовать упорядоченные множества как альтернативу массивам, когда порядок элементов является важным и требуется высокая скорость поиска элементов в коллекции. Класс NSMutableOrderedSet объявляет программный интерфейс к изменяемому упорядоченному множеству различных объектов. Объекты класса NSMut-ableOrderedSet объекты не похожи на массивы языка С. Во время создания такого множества вы можете указать размер, но реальный размер всё равно будет равен 0. 
6.	NSCountedSet – объявляет программный интерфейс к изменяемой, неупорядоченной коллекции нечетких объектов. Счётное множество также известно как bag. Каждый отдельный объект, вставленный в NSCountedSet, имеет счётчик, связанный с ним. Объект NSCountedSet отслеживает количество раз, когда объекты были вставлены, и требует, чтобы объекты были удалены такое же количество раз. В то же время, внутри объекта NSSet существует только один экземпляр вставляемого объекта, даже если этот объект был добавлен в множество несколько раз.
7.	NSIndexSet (NSMutableIndexSet) – represents an immutable collection of unique unsigned integers, known as indexes because of the way they are used. This collection is referred to as an index set. You use index sets in your code to store indexes into some other data structure. For example, given an NSArray object, you could use an index set to identify a subset of objects in that array. You should not use index sets to store an arbitrary collection of integer values because index sets store indexes as sorted ranges. This makes them more efficient than storing a collection of individual integers. It also means that each index value can only appear once in the index set. The designated initializers of the NSIndexSet class are: init, initWithIndexesInRange:, and initWithIndexSet:. You must not subclass the NSIndexSet class. The mutable subclass of NSIndexSet is NSMutableIndexSet.
8.	NSHashTable – в отличие от NSSet, поддерживает слабые ссылки. Он может содержать слабые ссылки на объекты. Объекты класса NSHashTable могут содержать произвольные указатели, хранимые объекты не ограничиваются объектами классов. Можно настроить экземпляр NSHashTable для работы с произвольными указателями, а не только с объектами классов. Благодаря своим свойствам, класс NSHashTable это не множество, потому что он может вести себя по-другому.
9.	NSMapTable – is a general-purpose analogue of NSDictionary. Contrasted with the behavior of NSDictionary / NSMutableDictionary, NSMapTable has the following characteristics:
•	NSDictionary / NSMutableDictionary copies keys, and holds strong references to values.
•	NSMapTable is mutable, without an immutable counterpart.
•	NSMapTable can hold keys and values with weak references, in such a way that entries are removed when either the key or value is deallocated.
•	NSMapTable can copy its values on input.
•	NSMapTable can contain arbitrary pointers, and use pointer identity for equality and hashing checks.
Usage: Instances where one might use NSMapTable include non-copyable keys and storing weak references to keyed delegates or another kind of weak object.
10.	NSIndexPath – представляет путь к конкретному узлу в виде дерева вложенных массивов коллекций. Этот путь известен как индексный путь. Каждый индекс в индексном пути представляет индекс в массиве дочерних элементов от одного узла в дереве к другому.
 
 

 
•	NSArray is the best choice to use for a list of items if you're going to iterate over them in se-quence, or access directly by index. They are also efficient to use as a queue or stack, as adding or removing items from either the beginning or is O(1). Checking to see if an object exists in the array using containsObject: is an O(N) operation, as it may take up to N comparisons to find the match.
•	NSSet is a great choice for checking containsObject: due to efficient hashing algorithms. Add-ing/removing items is always O(1). In addition, you have fast set arithmetic operations.
•	NSDictionary is a great choice if you have a natural key you can use to access objects. This has no inherent order, but if you know the key you can retrieve any object as O(1).

Разница между set и array?
NSSet предназначен для создания несортированных массивов данных (например каких-либо объектов). Существует модифицируемая версия класса NSSet — это NSMutableSet, используя которую можно добавлять и удалять элементы. Стоит обратить внимание, что объект, кото-рый хранится в NSSet, встречается только один раз. Т.е. все элементы NSSet — уникальные.
Добавить дубликат элемента в NSMutableSet у вас также не получится. Для создания несорти-рованного массива, в котором можно использовать неуникальные элементы, можно использо-вать NSCountedSet. Основным преимуществом NSCountedSet перед использованием классиче-ского массива NSArray является то, что элемент может быть продублирован огромное количе-ство раз и при этом занимать памяти как один элемент. Это объясняется тем, что NSCountedSet хранит в памяти только одну копию элемента и запоминает сколько раз этот элемент встреча-ется. Если для вас не важен порядок элементов внутри массива и вы используете действи-тельно большие объемы информации, то использование NSSet повысит производительность приложения за счет снижения потребляемой памяти. Несмотря на то, что количество элемен-тов хранящихся в памяти будет одинаковым, NSSet не тратит память на то, чтобы помнить в какой последовательности хранятся элементы.
NSSet *set = [NSSet setWithObjects:@"1", @"2", @"3", @"4", @"5", @"6", @"7", @"8", @"9", @"0", nil];
NSLog(@"%@", set);

Difference between NSArray and CFArray
What's the point of them both existing? There are a few reasons.
If you want to provide a C API, like the Carbon API, and you need things like arrays and dictionaries of referenced-counted objects, you want a library like Core Foundation (which provides CFArray), and of course it needs to have a C API.
If you want to write libraries for third-parties to use on Windows (for example), you need to provide a C API.
If you want to write a low-level library, say for interfacing with your operating system's kernel, and you want avoid the overhead of Objective-C messaging, you need a C API.
So those are good reasons for having Core Foundation, a pure C library.
But if you want to provide a higher-level, more pleasant API in Objective-C, you want Objective-C objects that represent arrays, dictionaries, reference-counted objects, and so on. So you need Foundation, which is an Objective-C library.
When should you use one or the other? Generally, you should use the Objective-C classes (e.g. NSArray) whenever you can, because the Objective-C inter-face is more pleasant to use: myArray.count (or [myArray count]) is easier to read and write than CFArrayGetCount(myArray). You should use the Core Foundation API only when you really need to: when you're on a platform that doesn't have Objective-C, or when you need features that the Core Foundation API provides but the Objective-C objects lack. For example, you can specify callbacks when creating a CFArray or a CFDictionary that let you store non-reference-counted objects. The NSArray and NSDictionary classes don't let you do that - they always assume you are storing reference-counted objects.
Are the CF objects just legacy objects? Not at all. In fact, Nextstep existed for years with just the Objective-C Foundation library and no Core Foundation library. When Apple needed to support both the Carbon API and the Cocoa API on top of the same lower-level operating system facilities, they created Core Foundation support both.
Enumeration
Enumeration is where computation gets interesting. It's one thing to encode logic that's executed once, but applying it across a collection—that's what makes programming so powerful.
•	Procedural increments a pointer within a loop
•	Object Oriented applies a function or block to each object in a collection
•	Functional works through a data structure recursively
Cocoa содержит три основных способа перечисления содержимого коллекции. К ним относятся быстрое перечисление и блочное перечисление. Существует также NSEnumerator класс, хотя в целом был замещен быстрым перечислением.
Быстрое перечисление является предпочтительным методом перечисления содержимого кол-лекции, поскольку оно обеспечивает следующие преимущества:
•	Перечисление является более эффективным, чем использование NSEnumerator напрямую.
•	Синтаксис краток
•	Перечислитель вызывает исключение, если вы измените коллекции при перечислении.
•	Вы можете выполнять несколько перечислений одновременно.
C Loops (for/while)
for and while loops are the "classic" method of iterating over a collection. Anyone who's taken Comput-er Science 101 has written code like this before:
for (NSUInteger i = 0; i < [array count]; i++) {
id object = array[i];
NSLog(@"%@", object);
}
But as anyone who has used C-style loops knows, this method is prone to off-by-one errors—particularly when used in a non-standard way. Fortunately, Smalltalk significantly improved this state of affairs with an idea called list comprehensions, which are commonly known today as for/in loops.
List Comprehension (for/in)
By using a higher level of abstraction, declaring the intention of iterating through all elements of a collection, not only are we less prone to error, but there's a lot less to type:
for (id object in array) {
    NSLog(@"%@", object);
}
Поведение для быстрого перечисления немного отличается в зависимости от типа коллекции. Массивы и наборы перечисляют их содержимое, а словари перечисляют свои ключи. NSIndexSet и NSIndexPath не поддерживают быстрое перечисление.
NSString *key;
for (key in someDictionary) {
   	NSLog(@"Key: %@, Value %@", key, [someDictionary objectForKey: key]);
}
In Cocoa, comprehensions are available to any class that implements the NSFastEnumeration proto-col, including NSArray, NSSet, and NSDictionary.
Использование перечислений на основе блоков
NSArray, NSDictionary и NSSet разрешают перечисление их содержимого с помощью блоков. Для перечисления с блоком, вызовите соответствующий метод и укажите блок для использо-вания.
NSArray *anArray = [NSArray arrayWithObjects:@"A", @"B", @"D", @"M", nil];
NSString *string = @"c";
[anArray enumerateObjectsUsingBlock:^(id obj, NSUInteger index, BOOL *stop) {
if ([obj localizedCaseInsensitiveCompare:string] == NSOrderedSame) {
NSLog(@"Object Found: %@ at index: %i", obj, index);
*stop = YES;
}
}];
Для перечисления NSArray, параметр index полезен для одновременного перечисления. Без этого параметра, единственный способ получить доступ к индексу был бы использованием метода indexOfObject:, который является неэффективным. stop параметр важен для произво-дительности, так как он позволяет остановить перечисление раньше, на основе некоторого условия, определяемого в пределах блока. Методы перечисления на основе блока в других коллекциях, немного отличаются по названию.
Использование перечислителя NSEnumerator
Абстрактный класс, экземпляры подклассов которого перечисляют коллекции других объек-тов, таких как массивы и словари. Все методы создания определены в классах коллекций, та-ких как NSArray, NSSet и NSDictionary, которые обеспечивают специальные объекты NSEnume-rator для перечисления их содержимого. Например, класс NSArray имеет два метода, которые возвращают объект NSEnumerator: objectEnumerator и reverseObjectEnumerator. NSDictionary также имеет два метода, которые возвращают объект NSEnumerator: keyEnumerator и objectE-numerator. Эти методы позволяют перечислить содержимое словаря по ключу или по значе-нию, соответственно. Вы отправляете nextObject, чтобы вновь созданный объект NSEnumerator возвращал следующий объект в оригинальной коллекции. Когда коллекция будет исчерпана, то возвращается nil. Вы не можете "сбросить" перечислитель после того, как он исчерпал свои коллекции. Подклассы NSEnumerator, используемые NSArray, NSDictionary и NSSet сохраняют коллекцию во время перечисления. Когда перечисление закончено, временные коллекции освобождаются. 
Примечание: не безопасно изменение коллекции во время её перечисления. Некоторые кол-лекции в настоящее время поддерживают такие операции, но такое поведение не гарантиро-вано в будущем.
Для перечисления коллекции, вы должны создать новый перечислитель.
NSMutableDictionary *myMutableDictionary = ... ;
NSMutableArray *keysToDeleteArray =
[NSMutableArray arrayWithCapacity:[myMutableDictionary count]];
NSString *aKey;
NSEnumerator *keyEnumerator = [myMutableDictionary keyEnumerator];
while (aKey = [keyEnumerator nextObject]) {
if (/* Проверка критериев для ключа или значения */) {
[keysToDeleteArray addObject:aKey];
}
}
[myMutableDictionary removeObjectsForKeys:keysToDeleteArray];

Array
 
Dictionary
 
Why is NSFastEnumeration so slow here? Iterating the dictionary usually requires both key and ob-ject; fast enumeration can only help for the key, and we have to fetch the object every time ourselves. Using the block-based enumerateKeysAndObjectsUsingBlock: is more efficient since both objects can be more efficiently prefetched.
Using NSPredicate to Filter Data
If you look at an arbitrary code base, chances are you’ll sooner or later run into a piece of code similar to this one:
NSMutableArray *oldSkoolFiltered = [[NSMutableArray alloc] init];
for (Book *book in bookshelf) {
if ([book.publisher isEqualToString:@"Apress"]) {
[oldSkoolFiltered addObject:book];
}
}
It’s a straight-forward approach to filtering an array of items (in this case, we’re talking about books) using a rather simple if-statement. Nothing wrong with this, but despite the fact we’re using a fairly simple expression here, the code is rather verbose. We can easily imagine what will happen in case we need to use more complicated selection criteria or a combination of filtering criteria.
Simple filtering with NSPredicate
Thanks to Cocoa, we can simplify the code by using NSPredicate. NSPredicate is the object representation of an if-statement, or, more formally, a predicate. Predicates are expressions that evaluate to a truth value, i.e. true or false. We can use them to perform validation and filtering. In Cocoa, we can use NSPredicate to evaluate single objects, filter arrays and perform queries against Core Data data sets. Let’s have a look at how our example looks like when using NSPredicate:
NSPredicate *predicate = [NSPredicate predicateWithFormat:
@"publisher == %@", @"Apress" ];
NSArray *filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
Filtering with Regular Expressions
Regular Expressions can be used to solve almost any problem ;-) so it’s good to know you can use them in NSPredicates as well. To use regular expressions in your NSPredicate, you need to use the MATCHES operator. Let’s filter all books that are about iPad or iPhone programming:
predicate = [NSPredicate predicateWithFormat:@"title MATCHES '.*(iPhone|iPad).*'"];
filtered = [bookshelf filteredArrayUsingPredicate:predicate];
dumpBookshelf(@"Books that contain 'iPad' or 'iPhone' in their title", filtered);
You need to obey some rules when using regular expressions in NSPredicate: most importantly, you cannot use regular expression metacharacters inside a pattern set.
Filtering using set operations
Let’s for a moment assume you want to filter all books that have been published by your favorite publishers. Using the IN operator, this is rather simple: first, we need to set up a set containing the publishers we’re interested in. Then, we can create the predicate and finally perform the filtering operation:
NSArray *favoritePublishers = [NSArray arrayWithObjects:@"Apress", @"O'Reilly", nil];
predicate = [NSPredicate predicateWithFormat:@"publisher IN %@", favoritePublishers];
filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
dumpBookshelf(@"Books published by my favorite publishers", filtered);
Advanced filtering thanks to KVC goodness
NSPredicate relies on key-value coding to achieve its magic. On one hand this means your classes need to be KVC compliant in order to be queried using NSPredicate (at least the attributes you want to query). On the other hand, this allows us to perform some very interesting things with very little lines of code. Let’s for example retrieve a list of books written by authors with the name “Mark”:
predicate = [NSPredicate predicateWithFormat:
@"authors.lastName CONTAINS %@", @"Mark" ];
filtered  = [bookshelf filteredArrayUsingPredicate:predicate];
In case we’d want to return the value of one of the aggregate functions, we don’t need to use NSPredicate itself, but instead use KVC directly. Let’s retrieve the average price of all books on our shelf:
NSNumber *average = [bookshelf valueForKeyPath:@"@avg.price"];
Сортировка массивов
Вам может потребоваться разместить несколько созданных пользователем строк в алфавит-ном порядке, либо вам потребуется разместить номера в убыванию или по возрастанию – ис-пользуйте дескрипторы блоков и селекторов. Дескрипторы сортировки (экземпляры NSSortDescriptor) обеспечивают удобный и абстрактный способ описания порядка сортировки. 
Простая сортировка по алфавиту:
NSArray *myArray = @[@"v", @"a", @"c", @"b", @"z"];
NSLog(@"%@",
[myArray sortedArrayUsingSelector:@selector(caseInsensitiveCompare:)]);
sortedArrayUsingDescriptors: или sortUsingDescriptors:
//Сначала создадим массив из словарей
NSString *LAST = @"lastName";
NSString *FIRST = @"firstName";
NSMutableArray *array = [NSMutableArray array];
NSArray *sortedArray;
NSDictionary *dict;
dict = [NSDictionary dictionaryWithObjectsAndKeys:
@"Jo", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:
@"Joe", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:
@"Joe", FIRST, @"Smythe", LAST, nil];
[array addObject:dict];	
dict = [NSDictionary dictionaryWithObjectsAndKeys:
@"Joanne", FIRST, @"Smith", LAST, nil];
[array addObject:dict];
dict = [NSDictionary dictionaryWithObjectsAndKeys:
@"Robert", FIRST, @"Jones", LAST, nil];
[array addObject:dict];
//Далее сортируем содержимое массива по last name затем first name
//Результаты могут быть показаны пользователю
//Обратите внимание на использование localizedCaseInsensitiveCompare: selector
NSSortDescriptor *lastDescriptor = [[NSSortDescriptor alloc] initWithKey:LAST
ascending:YES 
selector:@selector(localizedCaseInsensitiveCompare:)];
NSSortDescriptor *firstDescriptor = [[NSSortDescriptor alloc] initWithKey:FIRST
ascending:YES
selector:@selector(localizedCaseInsensitiveCompare:)]; 
NSArray *descriptors = [NSArray arrayWithObjects:lastDescriptor, firstDescriptor, nil];
sortedArray = [array sortedArrayUsingDescriptors:descriptors];
Сортировка с помощью функции. Такой подход значительно менее гибкий.
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
Сортировка с блоками
NSArray *sortedArray = [array sortedArrayUsingComparator: ^(id obj1, id obj2) {
     	if ([obj1 integerValue] > [obj2 integerValue]) {
          	return (NSComparisonResult)NSOrderedDescending;
     	}
if ([obj1 integerValue] < [obj2 integerValue]) {
       	   return (NSComparisonResult)NSOrderedAscending;
     	}
    	return (NSComparisonResult)NSOrderedSame;
}];
Сортировка с помощью функций и селекторов
Следующий листинг иллюстрирует использование методов sortedArrayUsingSelector:, sortedArrayUsingFunction:context:, и sortedArrayUsingFunction:context:hint:. Самым сложным из этих методов является sortedArrayUsingFunction:context:hint:. Он наиболее эффективен, когда у вас есть большой массив (N записей), которые вам надо отсортировать раз и затем лишь слег-ка изменить (P добавлений и удалений, где P гораздо меньше, чем N). Вы можете использовать работу, которую вы сделали в оригинальнй сортировке, и сделать своего рода слияние между N "старых" предметов и Р "новых" предметов. Чтобы получить соответствующую подсказку, вы используете sortedArrayHint когда исходный массив был отсортирован, и держите его, пока вам это нужно (если вы хотите, отсортировать массив после того, как он был изменен).
NSInteger alphabeticSort(id string1, id string2, void *reverse) {
if (*(BOOL *)reverse == YES) {
return [string2 localizedCaseInsensitiveCompare:string1];
}
return [string1 localizedCaseInsensitiveCompare:string2];
}
NSMutableArray *anArray =
[NSMutableArray arrayWithObjects:
@"aa", @"ab", @"ac", @"ad", @"ae", @"af", @"ag", @"ah", @"ai", @"aj", @"ak", @"al", @"am", @"an", @"ao", @"ap", @"aq", @"ar", @"as", @"at", @"au", @"av", @"aw", @"ax", @"ay", @"az", @"ba", @"bb", @"bc", @"bd", @"bf", @"bg", @"bh", @"bi", @"bj", @"bk", @"bl", @"bm", @"bn", @"bo", @"bp", @"bq", @"br", @"bs", @"bt", @"bu", @"bv", @"bw", @"bx", @"by", @"bz", @"ca", @"cb", @"cc", @"cd", @"ce", @"cf", @"cg", @"ch", @"ci", @"cj", @"ck", @"cl", @"cm", @"cn", @"co", @"cp", @"cq", @"cr", @"cs", @"ct", @"cu",
@"cv", @"cw", @"cx", @"cy", @"cz", 
nil];
// внимание: anArray отсортирован
NSData *sortedArrayHint = [anArray sortedArrayHint];
[anArray insertObject:@"be" atIndex:5];
NSArray *sortedArray;
// сортировка используя селектор
sortedArray = 
[anArray sortedArrayUsingSelector:@selector(localizedCaseInsensitiveCompare:)];
// сортировка используя функцию
BOOL reverseSort = NO;
sortedArray = [anArray sortedArrayUsingFunction:alphabeticSort context:&reverseSort];
// сортировка с подсказкой
sortedArray = [anArray sortedArrayUsingFunction:alphabeticSort context:&reverseSort hint:sortedArrayHint];

Sorting 1,000,000 elements: 
selector: 4947.90[ms] 
function: 5618.93[ms] 
block: 5082.98[ms]

Алгоритмы
Нотация «большое О»
Performance is usually described with the Big O Notation. It defines the limiting behavior of a function and is often used to characterize algorithms on their performance. O defines the upper bound of the growth rate of the function. To see just how big the difference is, see commonly used O notations and the number of operations needed.
 
For example, if you sort an array with 50 elements, and your sorting algorithm has a complexity of O(n^2), there will be 2,500 operations necessary to complete the task. Furthermore, there’s also overhead in internal management and calling that method - so it’s 2,500 operations times constant. O(1) is the ideal complexity, meaning constant time. Good sorting algorithms usually need O(n log n) time.

 
 

 

Последовательный поиск
Для неупорядоченного массива – перебор всех элементов, пока либо не найдется элемент, ли-бо не закончится массив.
//O(n)
int linearSearch(int array[], int size, int x) {
    for (int i = 0; i < size; i++) {
        if (x == array[i]) {
            return x;
        }
    }
    return -1;
}

//O(n)
int linearSearchMax(int array[], int size) {
    int max = array[0];
    for (int i = 0; i < size; i++) {
        if (array[i] >= max) {
            max = array[i];
        }
    }
    return max;
}

Бинарный поиск 
log(n), отсортированный массив
Алгоритм двоичного поиска похож на то, как мы ищем слово в словаре. Открываем словарь по-середине, смотрим в какой из половин будет нужное нам слово. Допустим, в первой. Открыва-ем первую часть посередине, продолжаем половинить, пока не найдем  нужное слово. С масси-вами так: есть упорядоченный массив, берем число из середины массива, сравниваем с иско-мым. Если оно оказалось больше, значит искомое число в первой половине массива, если меньше — во второй. Продолжаем делить оставшуюся половину, когда находим нужное число возвращаем его индекс, если не находим возвращаем null.
int binarySearch(int array[], int size, int x) {
    int first = 0; // Первый элемент в массиве
    int last = size - 1; // Последний элемент в массиве
    if (x < array[first] || array[last] < x) {
        // x лежит вне заданного массива
        return -1;
        printf("-1");
    } else {
        while (first < last) {
            int mid = (first + last) / 2;
            if (x < array[mid]) {
                last = mid - 1;
            } else {
                first = mid;
            }
        }
        if (array[last] == x) {
            // Искомый элемент найден. last - искомый индекс
            return x;
            printf("%i", x);
        } else {
            // Искомый элемент не найден.
            return -1;
            printf("-1");
        }
    }
}
NSArray has come with built-in binary search since iOS 4 / Snow Leopard:
typedef NS_OPTIONS(NSUInteger, NSBinarySearchingOptions) {
        NSBinarySearchingFirstEqual     = (1UL << 8),
        NSBinarySearchingLastEqual      = (1UL << 9),
        NSBinarySearchingInsertionIndex = (1UL << 10),
};

- (NSUInteger)indexOfObject:(id)obj 
              inSortedRange:(NSRange)range 
                    options:(NSBinarySearchingOptions)options 
            usingComparator:(NSComparator)cmp;
Why would you want to use this? Methods like containsObject: and indexOfObject: start at index 0 and search every object until the match is found - they don’t require the array to be sorted but have a perfor-mance characteristic of O(n). Binary search, on the other hand, requires the array to be sorted, but only needs O(log n) time. Thus, for one million entries, binary search requires, at most, 21 comparisons, while the naive linear search would require an average of 500,000 comparisons.
Time to search for 1000 entries within 1000000 objects. 
Linear: 54130.38[ms]. 
Binary: 7.62[ms]
For comparison, the search for a specific index with NSOrderedSet took 0.23 ms - that’s more than 30 times faster, even compared to binary search. Keep in mind that sorting is expensive as well. Apple uses merge sort, which takes O(n*log n), so if you just have to call indexOfObject: once, there’s no need for bi-nary search.

Сортировка вставками 
O(n^2), частично отсортированный массив
Суть его заключается в том что, на каждом шаге алгоритма мы берем один из элементов мас-сива, находим позицию для вставки и вставляем. Стоит отметить что массив из 1-го элемента считается отсортированным.
•	Устойчив
•	Может сортировать массив по мере его поступления
void insertionSort(int array[], int size) {
    int i, j, tmp;
    for (i = 1; i < size; i++) {
        tmp = array[i];
        for (j = i - 1; j >= 0 && array[j] > tmp; j--) {
            array[j + 1] = array[j];
        }
        array[j + 1] = tmp;
    }
}

Сортировка пузырьком 
O(n^2)
Алгоритм состоит из повторяющихся проходов по сортируемому массиву. За каждый проход элементы последовательно сравниваются попарно и, если порядок в паре неверный, выполня-ется обмен элементов. Проходы по массиву повторяются N-1 раз или до тех пор, пока на оче-редном проходе не окажется, что обмены больше не нужны, что означает — массив отсорти-рован. При каждом проходе алгоритма по внутреннему циклу, очередной наибольший элемент массива ставится на своё место в конце массива рядом с предыдущим «наибольшим элементом», а наименьший элемент перемещается на одну позицию к началу массива («всплывает» до нужной позиции как пузырёк в воде, отсюда и название алгоритма).
•	Эффективен для небольших массивов из-за сложности
void bubbleSort(int array[], int size) {
    bool swapped = true;
    int i;
    for (i = 1; i < size; i++) {
        swapped = false; //this flag is to check if the array is already sorted
        int j;
        for (j = 0; j < size - i; j++) {
            if (array[j] > array[j + 1]) {
                int tmp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = tmp;
                swapped = true;
            }
        }
        if (swapped == false) {
            break; //if it is sorted then stop
        }
    }
}

Сортировка выбором 
O(n^2)
На каждом шаге алгоритма мы выбираем один из элементов входных данных и вставляем его на нужную позицию в уже отсортированном списке, до тех пор, пока набор входных данных не будет исчерпан. Метод выбора очередного элемента из исходного массива произволен; может использоваться практически любой алгоритм выбора. Обычно (и с целью получения устойчи-вого алгоритма сортировки), элементы вставляются по порядку их появления во входном мас-сиве. Приведенный ниже алгоритм использует именно эту стратегию выбора.
Плюсы:
•	эффективен на небольших наборах данных, на наборах данных до десятков элементов может оказаться лучшим;
•	эффективен на наборах данных, которые уже частично отсортированы;
•	это устойчивый алгоритм сортировки (не меняет порядок элементов, которые уже отсортированы);
•	может сортировать список по мере его получения;
•	использует O(1) временной памяти, включая стек.
Минусы:
•	может быть и устойчивым, и неустойчивым
int selectionSort(int array[], int size) {
    int i, j;
    int tmp;
    int min;
    for (i = 0; i < size - 1; i++) {
        min = i; //current minimum
        //find the global minimum
        for (j = i + 1; j < size; j++) {
            if (array[min] > array[j]) {
                min = j; // new minimum
            }
        }
        //swap array[i] and array[min]
        tmp = array[i];
        array[i] = array[min];
        array[min] = tmp;
    }
    return 0;
}

Быстрая сортировка 
O(n*log(n)), разделяй и властвуй
QuickSort является существенно улучшенным вариантом алгоритма сортировки с помощью прямого обмена (его варианты известны как «Пузырьковая сортировка» и «Шейкерная сорти-ровка»), известного, в том числе, своей низкой эффективностью. Принципиальное отличие со-стоит в том, что в первую очередь производятся перестановки на наибольшем возможном рас-стоянии и после каждого прохода элементы делятся на две независимые группы. Любопыт-ный факт: улучшение самого неэффективного прямого метода сортировки дало в результате один из наиболее эффективных улучшенных методов.
Общая идея алгоритма состоит в следующем:
1.	Выбрать из массива элемент, называемый опорным. Это может быть любой из элементов массива.
2.	Сравнить все остальные элементы с опорным и переставить их в массиве так, чтобы разбить массив на три непрерывных отрезка, следующие друг за другом — «меньшие опорного», «равные» и «большие».
3.	Для отрезков «меньших» и «больших» значений выполнить рекурсивно ту же последовательность операций, если длина отрезка больше единицы.
На практике массив обычно делят не на три, а на две части, например, «меньшие опорного» и «равные и большие». Такой подход в общем случае эффективнее, так как упрощает алгоритм разделения.
Достоинства:
•	Один из самых быстродействующих (на практике) из алгоритмов внутренней сортировки общего назначения.
•	Прост в реализации.
•	Требует лишь O(lg n) дополнительной памяти для своей работы. (Не улучшенный рекурсивный алгоритм в худшем случае O(n) памяти)
•	Хорошо сочетается с механизмами кэширования и виртуальной памяти.
•	Допускает естественное распараллеливание (сортировка выделенных подмассивов в параллельно выполняющихся подпроцессах).
•	Допускает эффективную модификацию для сортировки по нескольким ключам (в частности — алгоритм Седжвика для сортировки строк): благодаря тому, что в процессе разделения автоматически выделяется отрезок элементов, равных опорному, этот отрезок можно сразу же сортировать по следующему ключу.
•	Работает на связных списках и других структурах с последовательным доступом, допускающих эффективный проход как от начала к концу, так и от конца к началу.
Недостатки:
•	Сильно деградирует по скорости (до Theta(n^2)) в худшем или близком к нему случае, что может случиться при неудачных входных данных.
•	Прямая реализация в виде функции с двумя рекурсивными вызовами может привести к ошибке переполнения стека, так как в худшем случае ей может потребоваться сделать O(n) вложенных рекурсивных вызовов.
•	Неустойчив
int partition(int a[], int l, int r) {
    int pivot, i, j, t;
    pivot = a[l];
    i = l; j = r + 1;
    while (1) {
        do ++i; while (a[i] <= pivot && i <= r );
        do --j; while (a[j] > pivot );
        if (i >= j ) break;
        t = a[i]; a[i] = a[j]; a[j] = t;
    }
    t = a[l]; a[l] = a[j]; a[j] = t;
    return j;
}

void quickSort(int a[], int l, int r) {
    int j;
    if (l < r ) {
        // divide and conquer
        j = partition(a, l, r);
        quickSort(a, l, j - 1);
        quickSort(a, j + 1, r);
    }
}

How to merge two sorted arrays into a sorted array?
public static int[] merge(int[] a, int[] b) {
    int[] answer = new int[a.length + b.length];
    int i = 0, j = 0, k = 0;

    while (i < a.length && j < b.length)
    {
        if (a[i] < b[j])       
            answer[k++] = a[i++];

        else        
            answer[k++] = b[j++];               
    }

    while (i < a.length)  
        answer[k++] = a[i++];


    while (j < b.length)    
        answer[k++] = b[j++];

    return answer;
}
Рекурсивная функция 
Функция, вызывающая саму себя. Вопрос о желательности использования рекурсивных функ-ций в программировании неоднозначен: с одной стороны, рекурсивная форма может быть структурно проще и нагляднее, в особенности, когда сам реализуемый алгоритм по сути ре-курсивен. Кроме того, в некоторых декларативных или чисто функциональных языках (таких как Пролог или Haskell) просто нет синтаксических средств для организации циклов, и рекур-сия в них — единственный доступный механизм организации повторяющихся вычислений. С другой стороны, обычно рекомендуется избегать рекурсивных программ, которые приводят (или в некоторых условиях могут приводить) к слишком большой глубине рекурсии. Так, ши-роко распространённый в учебной литературе пример рекурсивного вычисления факториала является, скорее, примером того, как не надо применять рекурсию, так как приводит к доста-точно большой глубине рекурсии и имеет очевидную реализацию в виде обычного цикличе-ского алгоритма.
Плюсы
•	Наглядность
•	Простота
Минусы
•	Возможна большая глубина рекурсии, из-за которой может произойти быстрое переполнение стека и нехватка памяти. 
Факториал
//O(n)
int factorialRecursive(int value) {
    if (value == 1) {
        return value;
    } else {
        return value * factorialRecursive(value - 1);
    }
}

//O(n)
int factorialIterative(int value) {
    int result = 1;
    for (int number = 1; number <= value; number++) {
       result *= number;
    }
    return result;
}
Последовательность Фибоначчи
//O(2^n)
int fibonacciRecursive(int position) {
    int result = 0;
    if (position < 2) {
        result = position;
    } else {
        result = fibonacciRecursive(position - 1) + fibonacciRecursive(position - 2);
    }
    return result;
}

//O(n)
int fibonacciIterative(int position) {
    int a = 1;
    int b = 1;
    int c;
    printf("%i\n%i\n", a, b);
    for (int i = 3; i <= position; i++) {
        c = a;
        a = b;
        b = c + b;
        printf("%i\n", b);
    }
    return b;
}

 Программирование
Программирование — процесс создания компьютерных программ.
В узком смысле (так называемое кодирование) под программированием понимается написа-ние инструкций (программ) на конкретном языке программирования (часто по уже имеюще-муся алгоритму — плану, методу решения поставленной задачи). В настоящее время активно используются интегрированные среды разработки (IDE), включающие в свой состав также ре-дактор для ввода и редактирования текстов программ, отладчики для поиска и устранения ошибок, трансляторы с различных языков программирования, компоновщики для сборки про-граммы из нескольких модулей и другие служебные модули. С помощью текстового редактора программист производит набор и редактирования текста создаваемой программы, который называют исходным кодом. Язык программирования определяет синтаксис и изначальную семантику исходного кода. Компилятор преобразует текст программы в машинный код, непо-средственно исполняемый электронными компонентами компьютера. Интерпретатор создаёт виртуальную машину для выполнения программы, которая полностью или частично берёт на себя функции исполнения программ. 
Код –> препроцессор (#define, etc. – развертывание, замена) –> компилятор –> машинный код
Язык программирования — формальная знаковая система, предназначенная для записи компьютерных программ. Классы языков программирования: 
•	Функциональные: на основе достаточно строгих абстрактных понятий и методов символь-ной обработки данных. Тексты программ на функциональных языках программирования описывают «как решить задачу», но не предписывают последовательность действий для решения. Lisp, Erlang, Haskell, Scala.
•	Процедурные (императивные): последовательно выполняемые операторы можно собрать в подпрограммы, то есть более крупные целостные единицы кода, с помощью механизмов самого языка. Процедурное программирование является отражением архитектуры тради-ционных ЭВМ. Процедурный язык программирования предоставляет возможность про-граммисту определять каждый шаг в процессе решения задачи. Особенность таких языков программирования состоит в том, что задачи разбиваются на шаги и решаются шаг за ша-гом. Используя процедурный язык, программист определяет языковые конструкции для выполнения последовательности алгоритмических шагов. C, Basic, Pascal.
•	Динамические: позволяют определять типы данных и осуществлять синтаксический ана-лиз и компиляцию «на лету», на этапе выполнения программы. Динамические языки удоб-ны для быстрой разработки приложений. Динамическая типизация (при котором перемен-ная связывается с типом в момент присваивания значения, а не в момент объявления пе-ременной. Таким образом, в различных участках программы одна и та же переменная мо-жет принимать значения разных типов) является основным, но не единственным критери-ем динамического языка программирования. Perl, Tcl, Python, PHP, Ruby, Smalltalk, JavaScript.
•	Объектно-ориентированные: язык, построенный на принципах объектно-ориентированного программирования. В основе концепции объектно-ориентированного программирования лежит понятие объекта — некой сущности, которая объединяет в себе поля (данные) и методы (выполняемые объектом действия). C#, C++, Java. Objective-C, Perl, Python, Scala, Ruby, Smaltalk, PHP.
API – интерфейс программирования приложений (иногда интерфейс прикладного програм-мирования) (англ. application programming interface) — набор готовых классов, процедур, функций, структур и констант, предоставляемых приложением (библиотекой, сервисом) для использования во внешних программных продуктах. Используется программистами для напи-сания всевозможных приложений. API операционных систем: Cocoa, Windows API. 
API не решение для моей системы (как фреймворк), а доступ к функциям другой системы. 
IDE, Интегрированная среда разработки (Integrated development environment) — система про-граммных средств, используемая программистами для разработки программного обеспечения.
Обычно, среда разработки включает в себя:
•	текстовый редактор,
•	компилятор и/или интерпретатор,
•	средства автоматизации сборки,
•	отладчик.
Иногда содержит также средства для интеграции с системами управления версиями и разно-образные инструменты для упрощения конструирования графического интерфейса пользова-теля. Многие современные среды разработки также включают браузер классов, инспектор объ-ектов и диаграмму иерархии классов — для использования при объектно-ориентированной разработке ПО. Частный случай IDE — среды визуальной разработки, которые включают в се-бя возможность визуального редактирования интерфейса программы. 
Высокоуровневый язык программирования — язык программирования, разработанный для быстроты и удобства использования программистом. Основная черта высокоуровневых язы-ков — это абстракция, то есть введение смысловых конструкций, кратко описывающих такие структуры данных и операции над ними, описания которых на машинном коде (или другом низкоуровневом языке программирования) очень длинны и сложны для понимания. 
Компиляция — трансляция программы, составленной на исходном языке высокого уровня, в эквивалентную программу на низкоуровневом языке, близком машинному коду (абсолютный код, объектный модуль, иногда на язык ассемблера). Входной информацией для компилятора (исходный код) является описание алгоритма или программа на проблемно-ориентированном языке, а на выходе компилятора — эквивалентное описание алгоритма на машинно-ориентированном языке (объектный код). 
Компилировать — проводить трансляцию машинной программы с проблемно-ориентированного языка на машинно-ориентированный язык. 

Язык СИ.
•	Лаконичность и быстрота (почти как Ассемблер)
•	Переносимость на различные архитектуры
•	Набор низкоуровневых средств
•	Прямой доступ к памяти
•	Операции над битами
•	Адресная арифметика
Си – универсальный язык программирования,  считается удобным для системного программирования, хотя он удобен и для написания при-кладных программ. Среди преимуществ языка Си следует отметить переносимость программ на компьютеры различной архитектуры и из одной операционной системы в другую, лаконичность записи алгоритмов, логическую стройность программ, а также возможность получить программный код, сравнимый по скорости выполнения с программами, написанными на языке ассемблера. Последнее связано с тем, что хотя Си является языком высокого уровня, имеющим полный набор конструкций структурного программирования, он также обладает набором низкоуровневых средств, обеспечивающих доступ к аппаратным средствам компьютера. 
Программа на C состоит из программных единиц одного типа – функций. Аргументы могут передаваться функциям посредством копирования значений этих аргументов; при этом вызванная функция не может изменить фактический аргумент в вызывающей подпрограмме.
Возможен иной вариант – передача параметра по ссылке, когда явно передается указатель, т. е. адрес, при этом функция сможет изменить объект, на который ссылается указатель.
В C предусмотрен ряд операций низкого уровня: прямой доступ к памяти, операции над битами данных и адресной арифметики.
Программы на языке C компактны и гибки. Язык C доверяет программисту и разрешает ему практически все; из-за этого C нельзя считать языком надежного программирования, и вся ответственность за качество программы лежит на программисте, который должен знать особен-ности языка и его реализации. Программа, написанная на языке Си, состоит из операторов. Каждый оператор вызывает выполнение некоторых действий на соответствующем шаге выполнения программы.
При написании операторов применяются латинские прописные и строчные буквы, цифры и специальные знаки. К таким знакам, например, относятся: точка (.), запятая (,), двоеточие (:), точка с запятой (;) и др. Совокупность символов, используемых в языке, называется алфавитом языка. Программы оперируют с различными данными, которые могут быть простыми и структурированными. Простые данные - это целые и вещественные числа, символы и указатели (адреса объектов в памяти). Целые числа не имеют, а вещественные имеют дробную часть. Струк-турированные данные - это массивы и структуры.
 

Битовые операции
В своих программах вы не адресуете отдельные биты, а имеете дело с группами битов - байтами. Если представить байт как 8-разрядное целое число без знака, его биты соответ-ствуют последовательным степеням 2.
 
Однако компьютерам удобнее иметь дело со степенями 2. Программисты часто используют шестнадцатеричную систему
(16 = 24) - особенно при работе с отдельными разрядами целых чисел. В качестве дополни-тельных цифр в шестнадцатеричной системе используются буквы а, b, с, d, е и f. Таким обра-зом, счет в шестнадцатеричной системе выглядит так: 0,1,2,3,4,5,6,7,8,9, а, b, с, d, е, f, 10, 11, ... Числа, записанные в шестнадцатеричной системе, обозначаются префиксом 0х.
 
Один байт всегда может быть представлен шестнадцатеричным числом из двух цифр (напри-мер, 3с). По этой причине шестнадцатеричные числа удобны для работы с двоичными данны-ми.
 

Побитовое И AND &
2 байта можно объединить поразрядной операцией И для создания третьего байта. В этом случае бит третьего байта равен 1 только в том случае, если оба соответствующих бита первых двух байтов равны 1.

0011
0101
0001



Часто используется для обнуления некоторой группы разрядов. Например
n = n & 0177;
обнуляет в n все разряды, кроме младших семи.

Побитовое ИЛИ OR |
 
Программа выдает результат объединения двух байтов поразрядной операцией ИЛИ:
Hex: 03c0 | 0a90 = 0bd
Decimal: 0600 | 01690 = 0189

0011
0101
0111



Применяют для установки разрядов; так,
х = х | SET_ON;
устанавливает единицы в тех разрядах х, которым соответствуют единицы в SET_ON.

Побитовое исключающее ИЛИ (сложение по модулю два) XOR ^ 
Исключающая операция ИЛИ объединяет два байта и создает третий байт. Бит результата ра-вен 1 в том случае, если ровно один из двух соответствующих битов входных байтов равен 1.

0011
0101
0110



Побитовое отрицание (дополнение, унарный оператор) НЕ  NOT ~
Дополнением к существующему байту называется байт, биты которого находятся в противопо-ложном состоянии: все нули заменяются единицами, а все единицы заменяются нулями.

0011
1100



Унарный оператор ~ поразрядно "обращает" целое т. е. превращает каждый единичный бит в нулевой и наоборот. Например
х = х & ~077	
обнуляет в х последние 6 разрядов. Заметим, что запись х & ~077 не зависит от длины слова, и, следовательно, она лучше, чем х & 0177700, поскольку последняя подразумевает, что х занимает 16 битов. Не зависимая от машины форма записи ~077 не потребует дополнительных затрат при счете, так как ~077 — константное выражение, которое будет вычислено во время компи-ляции.

Сдвиг влево <<
При выполнении операции сдвига влево каждый бит смещается в направлении старшего бита. Биты, выходящие за пределы числа, теряются, а возникающие справа «пустоты» заполняются нулями.
 

Сдвиг вправо >>

Примеры битовых операций
 
 

 

67 & 114 = 66
67 | 114 = 115
67 ^ 114 = 49
~67 	   = 188
Что такое указатель и ссылка и в чем разница?
Есть два способа обращения к функции – вызов по значению и вызов по ссылке. При вызове по значению создается копия аргумента и передается вызываемой функции. Изменение копии не влияют на значение оригинала в операторе вызова. Один из минусов этого способа – если пе-редается большой элемент данных, то на его копирование может уйти дополнительное время. 
Ссылочный параметр – это псевдоним аргумента.
int &count; //count является ссылкой на int.
В вызове функции достаточно указать имя переменной и она будет передана по ссылке, тогда упоминание в теле вызываемой функции переменной по имени ее параметра в действительности является обращением к исходной переменной в вызывающей функции и эта исходная переменная может быть изменена непосредственно вызываемой функцией. Для передачи больших объектов используется константный ссылочный параметр, чтобы обеспечить защиту параметра, как при вызове по значению, и в то же время избежать накладных расходов при передаче копии большого объекта:
const int &count;
Ссылка – это псевдоним для другой переменной и все операции, выполняемые с псевдонимом (ссылкой) выполняются на самом деле с истинной переменной. Псевдоним – другое имя переменной и для него не резервируется место в памяти. 
Если возвращение ссылки переменной объявлено в функции, то эта переменная должна быть объявлена внутри функции как статическая, иначе ссылка адресуется автоматической переменной, которая после выполнения функции уничтожается.

Указатель – переменная, которая содержит в качестве значения адрес памяти переменной, ко-торая уже в свою очередь содержит значение. Т. о. имя переменной отсылает к значению пря-мо, а указатель – косвенно. 
int y = 5;
int *yPtr;
yPtr = &y;
Теперь yPtr указывает на y.
Операция * – операция косвенной адресации или операция разыменования. 

Аргументы можно передавать в функцию тремя способами
1.	Вызов по значению
2.	Вызов по ссылке с аргументами ссылками
3.	Вызов по ссылке с аргументами указателями
Указатели как и ссылки тоже можно использовать для модификации оного или более значе-ний переменных в вызывающем операторе, или передавать указатели на большие объекты данных, чтобы избежать расходов, сопутствующих передаче объектов по значению. 

const с указателем значит, что значение переменной не изменяется.


Почему (NSError **) использует указатель на указатель?
Explanation 1:
if you pass a pointer to an object to your function, the function can only modify what the pointer is pointing to.
if you pass a pointer to a pointer to an object then the function can modify the pointer to point to an-other object.
In the case of NSError, the function might want to create a new NSError object and pass you back a pointer to that NSError object. Thus, you need double indirection so that the pointer can be modified.

Explanation 2:
A pointer to a pointer is a form of multiple indirection, or a chain of pointers. Normally, a pointer con-tains the address of a variable. When we define a pointer to a pointer, the first pointer contains the address of the second pointer, which points to the location that contains the actual value as shown below.
 
A variable that is a pointer to a pointer must be declared as such. This is done by placing an additional asterisk in front of its name. For example, the following declaration declares a pointer to a pointer of type int −
int **var;
When a target value is indirectly pointed to by a pointer to a pointer, accessing that value requires that the asterisk operator be applied twice, as is shown below in the example −
int main () {

   int  var;
   int  *ptr;
   int  **pptr;

   var = 3000;

   /* take the address of var */
   ptr = &var;

   /* take the address of ptr using address of operator & */
   pptr = &ptr;

   /* take the value using pptr */
   printf("Value of var = %d\n", var );
   printf("Value available at *ptr = %d\n", *ptr );
   printf("Value available at **pptr = %d\n", **pptr);

   return 0;
}
Value of var = 3000
Value available at *ptr = 3000
Value available at **pptr = 3000

with a regular parameter, say int you get a local copy 
with a pointer parameter, say int* you can modify what it points to 
with a double pointer parameter, say int** you can modify the pointer itself, ie 'repoint' it.

How to return 2+ values from a function?

In C:
1. Returning the address of the first element of a local array has undefined behavior(at least dereferencing it later is). You may use output parameters, that is, pass two pointers, and set the values inside:
void Calculate(int x, int y, int* prod, int* quot)
{
    *prod = x*y;
    *quot = x/y;
}

usage:

int x = 10,y = 2, prod, quot;
Calculate(x, y, &prod, &quot)

2. Another thing you could do is pack your data into a struct
typedef struct 
{
    int prod;
    int quot;
} product_and_quot;

product_and_quot Calculate(int x, int y)
{
    product_and_quot p = {x*y, x/y};
    return p;
}

in Objective-C:
1. Pointers
- (void)convertA:(float)a B:(float)b C:(float) intoX:(float *)xOut Y:(float *)yOut Z:(float)zOut {
    *xOut = 3*a + b;
    *yOut = 2*b;
    *zOut = a*b + 4*c;
}

and call it like this:

float x, y, z;
[self convertA:a B:b C:c intoX:&x Y:&y Z:&z];

2. Another way is to create a struct and return it:
struct XYZ {
    float x, y, z;
};

- (struct XYZ)xyzWithA:(float)a B:(float)b C:(float)c {
    struct XYZ xyz;
    xyz.x = 3*a + b;
    xyz.y = 2*b;
    xyz.z = a*b + 4*c;
    return xyz;
}

Call it like this:

struct XYZ output = [self xyzWithA:a B:b C:c];

3. Double pointers with objects
If you want to return more than one new object, your function should take pointers to the object pointer, thus:
-(void)mungeFirst:(NSString**)stringOne andSecond:(NSString**)stringTwo
{
    *stringOne = [NSString stringWithString:@"foo"];
    *stringTwo = [NSString stringWithString:@"baz"];
}

4. Blocks
You can return two values with help of block:
- (void)getUIControlles:(void (^)(UITextField * objTextFiled, UIView * objView))completionBlock {
    UITextField * textFiled = nil;
    /*
     do code here for textfiled
     */
    UIView * viewDemo = nil;

    /*
     do code here for Uiview.
     */

    completionBlock (textFiled, viewDemo);
}

- (void) testMethod {

    // Call function with following way.

    [self getUIControlles:^(UITextField *objTextFiled, UIView *objView) {

// objTextFiled = This is your textfiled object
// objView = This is your view object

    }];
}

What is the difference between char * const and const char *?

Существует четыре способа передачи в функцию указателя
1.	Неконстантный указатель на неконстантные данные
2.	Неконстнатный указатель на константные данные
3.	Константный указатель на неконстантные данные
4.	Константный указатель на константные данные

 

Что значит n & (n – 1)?
It's figuring out if n is either 0 or an exact power of two.
It works because a binary power of two is of the form 1000...000 and subtracting one will give you 111...111. Then, when you AND those together, you get zero, such as with:
   1000 0000 0000 0000
&&  111 1111 1111 1111
   ==== ==== ==== ====
 = 0000 0000 0000 0000
Any non-power-of-two input value will not give you zero when you perform that operation.
For example, let's try all the 3-bit combinations:
      <----- binary ---->
 n     n    n-1   n&(n-1)
---   ---   ---   -------
 0    000   111     000 *
 1    001   000     000 *
 2    010   001     000 *
 3    011   010     010
 4    100   011     000 *
 5    101   100     100
 6    110   101     100
 7    111   110     110
You can see that only 0 and the powers of two (1, 2 and 4) result in a 000/false bit pattern, all others are non-zero or true.
See the full Bit Twiddling Hacks document for all sorts of other wonderful (or dastardly, depending on your viewpoint) hackery.

ООП
История ООП
ООП – парадигма программирования, в которой основными концепциями являются понятия объектов и классов. В центре ООП находится понятие объекта. Объект — это сущность, которой можно посылать сообщения, и которая может на них реагировать, используя свои данные. Объект — это экземпляр класса. Данные объекта скрыты от остальной программы. Сокрытие данных называется инкапсуляцией. Наличие инкапсуляции достаточно для объектности языка программирования, но ещё не означает его объектной ориентированности — для этого требуется наличие наследования. Но даже наличие инкапсуляции и наследования не делает язык программирования в полной мере объектным с точки зрения ООП. Основные преимуще-ства ООП проявляются только в том случае, когда в языке программирования реализован по-лиморфизм; то есть возможность объектов с одинаковой спецификацией иметь различную ре-ализацию. Первым языком программирования, в котором были предложены принципы объ-ектной ориентированности, была Симула. В момент своего появления (в 1967 году), этот язык программирования предложил поистине революционные идеи: объекты, классы, виртуальные методы и др., однако это всё не было воспринято современниками как нечто грандиозное. Тем не менее, большинство концепций были развиты Аланом Кэйем и Дэном Ингаллсом в языке Smalltalk. Именно он стал первым широко распространённым объектно-ориентированным языком программирования. (C#, C++, Java, Ruby, PHP, Perl, Python). ООП дает возможность со-здавать расширяемые системы (extensible systems). Это одно из самых значительных досто-инств ООП и именно оно отличает данный подход от традиционных методов программирова-ния. Расширяемость (extensibility) означает, что существующую систему можно заставить ра-ботать с новыми компонентами, причем без внесения в нее каких-либо изменений. Компонен-ты могут быть добавлены на этапе выполнения. Smalltalk — объектно-ориентированный язык программирования с динамической типизацией, разработанный в Xerox PARC Аланом Кэйем, Дэном Ингаллсом, Тедом Кэглером, Адель Голдберг, и другими в 1970-х годах. Язык был представлен как Smalltalk-80. Smalltalk оказал большое влияние на развитие многих дру-гих языков, таких как: Objective-C, Actor, Java, Groovy и Ruby. Многие идеи 1980-х и 1990-х по написанию программ появились в сообществе Smalltalk. К ним можно отнести рефакторинг, шаблоны проектирования (применительно к ПО), карты «класс — обязанности — взаимодей-ствие» и экстремальное программирование в целом. Си (англ. C) — язык программирования, разработанный в 1969—1973 годах сотрудниками Bell Labs Кеном Томпсоном и Деннисом Ритчи как развитие языка Би. Благодаря близости по скорости выполнения программ, напи-санных на Си, к языку ассемблера, этот язык получил широкое применение при создании си-стемного программного обеспечения и прикладное программное обеспечение для решения широко круга задач. Язык программирования Си оказал существенное влияние на развитие индустрии программного обеспечения, а его синтаксис стал основой для таких языков про-граммирования как C++, C# и Java. 

Основные понятия ООП: абстракция, инкапсуляция, наследование, полиморфизм.
Абстракция – это придание объекту характеристик, которые чётко определяют его концепту-альные границы, отличая от всех других объектов. Основная идея состоит в том, чтобы отде-лить способ использования составных объектов данных от деталей их реализации в виде бо-лее простых объектов, подобно тому, как функциональная абстракция разделяет способ ис-пользования функции и деталей её реализации в терминах более примитивных функций, та-ким образом, данные обрабатываются функцией высокого уровня с помощью вызова функций низкого уровня. (Пример: говорить о предметах, не упоминая материалы, из которых они сде-ланы). Абстракция позволяет задействовать концепцию, игнорируя ее некоторые детали и ра-ботая с разными деталями на разных уровнях. Имея дело с составным объектом, вы имеете дело с абстракцией. Если вы рассматриваете объект как «дом», а не как комбинацию стекла, древесины и гвоздей, вы прибегаете к абстракции. Если вы рас- сматриваете множество домов как «город», вы прибегаете к другой абстракции. Базовые классы представляют собой аб-стракции, позволяющие концентрироваться на общих атрибутах производных классов и игно-рировать детали конкретных классов при работе с базовым классом. Удачный интерфейс класса — это абстракция, позволяющая сосредоточиться на интерфейсе, не беспокоясь о внут-ренних механизмах работы класса. Мы используем абстракции на каждом шагу. Если б, открывая или закрывая дверь, вы должны были иметь дело с отдельными волокнами древесины, молекулами лака и стали, вы вряд ли смогли бы войти в дом или выйти из него. Абстракция — один из главных способов борьбы со сложностью реального мира.
Слой абстрагирования (или уровень абстракции) — это способ уйти от деталей реализации конкретного множества функций. 
 
Инкапсуляция – скрытие методов и переменных от других методов или переменных или дру-гих частей программы. Сокрытие реализации целесообразно применять в следующих целях:
•	При необходимости максимальной локализации предстоящих изменений, когда изменяется только работа объекта, а не программы;
•	При необходимости предсказания предстоящих изменений и их последствий;
•	При необходимости очистки глобальной области видимости.
Когда абстракция нас покидает, на помощь приходит инкапсуляция. Абстракция говорит: «Вы можете рассмотреть объект с общей точки зрения». Инкапсуляция добавляет: «Более того, вы не можете рассмотреть объект с иной точки зрения». 
Продолжим нашу аналогию: инкапсуляция позволяет вам смотреть на дом, но не дает подойти достаточно близко, чтобы узнать, из чего сделана дверь. Инкапсуляция позволяет вам знать о существовании двери, о том, открыта она или заперта, но при этом вы не можете узнать, из чего она сделана (из дерева, стекловолокна, стали или другого материала), и уж никак не сможете рассмотреть отдельные волокна древесины. 
Наследование – процесс, посредством которого один объект может приобретать свойства дру-гого. Точнее, объект может наследовать основные свойства другого объекта и добавлять к ним черты, характерные только для него. Польза наследования в том, что оно дополняет идею аб-стракции. Абстракция позволяет представить объекты с разным уровнем детальности. Если помните, на одном уровне мы рассматривали дверь как набор определенных типов молекул, на втором — как набор волокон древесины, а на третьем — как что􏰀то, что защищает нас от воров. Древесина имеет определенные свойства — скажем, вы можете распилить ее пилой или склеить столярным клеем, — при этом и плинтусы, и подоконники имеют общие свойства древесины, но вместе с тем и некоторые специфические свойства. Наследование упрощает программирование, позволяя создать универсальные методы для выполнения всего, что осно-вано на общих свойствах дверей, и затем написать специфические методы для выполнения специфических операций над конкретными типами дверей. Некоторые операции, такие как Open() или Close(), будут универсальными для всех дверей: внутренних, входных, стеклянных, стальных — каких угодно. Поддержка языком операций вроде Open() или Close() при отсут-ствии информации о конкретном типе двери вплоть до периода выполнения называется по-лиморфизмом. Объектно-ориентированные языки, такие как C++, Java и более поздние версии Microsoft Visual Basic, поддерживают и наследование, и полиморфизм. 
В объектно-ориентированном программировании под агрегированием (также называемом композицией или включением) подразумевают методику создания нового класса из уже существующих классов путём включения, называемого также делегированием. Об агрегировании также часто говорят как об «отношении принадлежности» по принципу «у машины есть корпус, колёса и двигатель». Вложенные объекты нового класса обычно объявляются закрытыми, что делает их недоступными для прикладных программистов, работающих с классом. С дру-гой стороны, создатель класса может изменять эти объекты, не нарушая при этом работы существующего клиентского кода. Кроме того, за-мена вложенных объектов на стадии выполнения программы позволяет динамически изменять её поведение. Механизм наследования такой гибкостью не обладает, поскольку для производных классов устанавливаются ограничения, проверяемые на стадии компиляции. На базе агрегирования реализуется методика делегирования, когда поставленная перед внешним объектом задача перепоручается внутреннему объ-екту, специализирующемуся на решении задач такого рода.
Агрегация (агрегирование по ссылке) — отношение «часть-целое» между двумя равноправными объектами, когда один объект (контейнер) имеет ссылку на другой объект. Оба объекта могут существовать независимо: если контейнер будет уничтожен, то его содержимое — нет.
Композиция (агрегирование по значению) — более строгий вариант агрегирования, когда включаемый объект может существовать только как часть контейнера. Если контейнер будет уничтожен, то и включённый объект тоже будет уничтожен.
@interface Unicycle : NSObject {
	Pedal *pedal;
	Tire *tire;
}
@end

 
(Абстрактный класс белым цветом)

Как имитировать множественное наследование?
Композиция:
@interface ClassA : NSObject {
}
-(void)methodA;
@end

@interface ClassB : NSObject {
}

-(void)methodB;
@end

@interface MyClass : NSObject {
ClassA *a;
ClassB *b;
}
-(id)initWithA:(ClassA *)anA b:(ClassB *)aB;
-(void)methodA;
-(void)methodB;
@end
Полиморфизм – возможность объектов с одинаковой спецификацией иметь различную реали-зацию (использование одного имени для решения двух или более схожих, но технически раз-ных задач). Если функция описывает разные реализации (возможно, с различным поведением) для ограниченного набора явно заданных типов и их комбинаций, это называется ситуативным полиморфизмом (ad hoc polimorphism). Ситуативный полиморфизм поддерживается во многих языках посредством перегрузки функций и методов.
Если же код написан отвлеченно от конкретного типа данных и потому может свободно ис-пользоваться с любыми новыми типами, имеет место параметрический полиморфизм. Неко-торые языки совмещают различные формы полиморфизма, порой сложным образом, что фор-мирует самобытную идеологию в них и влияет на применяемые методологии декомпозиции задач. Например, в Smalltalk любой класс способен принять сообщения любого типа, и либо об-работать его самостоятельно (в том числе посредством интроспекции), либо ретранслировать другому классу — таким образом, несмотря на широкое использование перегрузки функций, формально любая операция является неограниченно полиморфной и может применяться к данным любого типа.
 

Другие понятия ООП
Конструктор
В объектно-ориентированном программировании конструктор класса (от англ. constructor, иногда сокращают ctor) — специальный блок ин-струкций, вызываемый при создании объекта.
Конструктор схож с методом, но отличается от метода тем, что не имеет явным образом определённого типа возвращаемых данных, не насле-дуется, и обычно имеет различные правила для рассматриваемых модификаторов. Конструкторы часто выделяются наличием одинакового имени с именем класса, в котором объявляется. Их задача — инициализировать члены объекта и определить инвариант класса, сообщив в случае некорректности инварианта. Корректно написанный конструктор оставит объект в «правильном» состоянии. Неизменяемые объекты тоже должны быть проинициализированы конструктором.
В большинстве языков конструктор может быть перегружен, что позволяет использовать несколько конструкторов в одном классе, причём каждый конструктор может иметь различные параметры.
Деструктор
Вызывается при уничтожении объекта. Он обычно используется для освобождения памяти. 
Виртуальный метод
В объектно-ориентированном программировании метод (функция) класса, который может быть переопределён в классах-наследниках так, что конкретная реализация метода для вызова будет определяться во время исполнения. Таким образом, программисту необязательно знать точный тип объекта для работы с ним через виртуальные методы: достаточно лишь знать, что объект принадлежит классу или наследнику класса, в котором метод объявлен. Виртуальные методы — один из важнейших приёмов реализации полиморфизма. Они позволяют создавать общий код, который может работать как с объектами базового класса, так и с объектами любого его класса-наследника. При этом базовый класс определяет способ работы с объектами и любые его наследники могут предоставлять конкретную реализацию этого способа. В некоторых языках программирования, например в Java, нет понятия виртуального метода, данное понятие следует применять лишь для язы-ков, в которых методы родительского класса не могут быть переопределены по умолчанию, а только с помощью некоторых вспомогательных ключевых слов. В некоторых же (как, например, в Python), все методы — виртуальные.
Базовый класс может и не предоставлять реализации виртуального метода, а только декларировать его существование. Такие методы без реализации называются «чистыми виртуальными» (перевод англ.  pure virtual) или абстрактными. Класс, содержащий хотя бы один такой метод, тоже будет абстрактным. Объект такого класса создать нельзя (в некоторых языках допускается, но вызов абстрактного метода при-ведёт к ошибке). Наследники абстрактного класса должны предоставить реализацию для всех его абстрактных методов, иначе они, в свою очередь, будут абстрактными классами.
Для каждого класса, имеющего хотя бы один виртуальный метод, создаётся таблица виртуальных методов. Каждый объект хранит указатель на таблицу своего класса. Для вызова виртуального метода используется такой механизм: из объекта берётся указатель на соответствующую таблицу виртуальных методов, а из неё, по фиксированному смещению, — указатель на реализацию метода, используемого для данного класса. При использовании множественного наследования ситуация несколько усложняется за счёт того, что таблица виртуальных методов становится нелинейной.
Принцип единственной обязанности (англ. Single responsibility principle) обозначает, что каждый объект должен иметь одну обязанность и эта обязанность должна быть полностью инкапсулирована в класс. Все его сервисы должны быть направлены исключительно на обеспечение этой обязанности.

В чем плюсы и минусы ООП? 
Общие положения
			Преимущества		          			Недостатки                                                     
Классы позволяют проводить конструирование из полезных компонент, обладающих простыми инструментами, что дает возможность абстрагироваться от деталей реализации.	ООП порождает огромные иерархии клас-сов, что приводит к тому, что функцио-нальность расползается или, как говорят, размывается по базовым и производным членам класса, и отследить логику работы того или иного метода становится сложно.
Полиморфизм
Можно создавать новые классы с помощью протокола, «ведущие себя» аналогично род-ственным, что, в свою очередь, позволяет достигнуть расширяемости и модифициру-емости, что помогает снижать сложность программ, разрешая использование того же интерфейса для задания единого класса действий. "Один интерфейс, множество ме-тодов"	На скорости выполнения программ может неблагоприятно сказаться реализация по-лиморфизма, которая основана на меха-низмах позднего связывания вызова мето-да с конкретной его реализацией в одном из производных классов.
Возможность создавать переменные и ме-тоды с одинаковым именем, но ведущие се-бя по-разному в зависимости от контекста (локальные переменные и перекрытие методов)	Многоразовое использование требует от программиста познакомиться с большими библиотеками классов. А это может ока-заться сложнее, чем даже изучение нового языка программирования. Библиотека классов фактически представляет собой виртуальный язык, который может вклю-чать в себя сотни типов и тысячи опера-ций.
Обработка разнородных структур данных. Программы могут работать, не утруждая себя изучением вида объектов. Новые виды могут быть добавлены в любой момент.
for (id object in array) {
    NSLog(@"%@", object);
}	В некоторых языках все данные являются объектами, в том числе и элементарные типы, а это не может не приводить к до-полнительным расходам памяти и процес-сорного времени.
Реализация родовых компонент. Алгоритмы можно обобщать до такой степени, что они уже смогут работать более, чем с одним ви-дом объектов.
Доведение полуфабрикатов. Компоненты нет надобности подстраивать под опреде-ленное приложение. Их можно сохранять в библиотеке в виде полуфабрикатов (semifinished products) и расширять по мере необходимости до различных законченных продуктов.
Расширение фреймворка. Независимые от приложения части предметной области мо-гут быть реализованы в виде фреймворка и в дальнейшем расширены за счет добавле-ния частей, специфичных для конкретного приложения.	Изменение поведения во время выполне-ния. На этапе выполнения один объект может быть заменен другим. Это может привести к изменению алгоритма, в кото-ром используется данный объект.
Инкапсуляция
Сокрытие данных от несанкционированного доступа	Функции представляют собой черные ящики, которые трансформируют ввод в вывод. Если я понимаю ввод и вывод, то я понимаю функцию. Это не означает, что я могу написать эту функцию.
Инкапсуляция повышает надежность рабо-ты программного кода, поскольку гаранти-рует, что определенные данные не могут быть изменены за пределами содержащего их класса.	В то время как состояние в языках про-граммирования является нежелательным, реальный мир богат на состояния. Я очень интересуюсь состоянием моего банковского счета. И когда я вкладываю или снимаю с него деньги, я ожидаю, что его состояние будет корректно обновлено. Выбранный ООЯП подход “спрятать состояние от про-граммиста” является наихудшим возмож-ным выбором. Вместо показа состояния и поиска путей для минимизации неудобств от него, они прячут его поглубже.
	Очень трудно изучать классы, не имея возможности их «пощупать». Только с приобретением мало-мальского опыта можно уверенно себя почувствовать при работе с использованием ООП. Поэтому проектирование классов — задача куда более сложная, чем их использование. Проектирование класса, как и проектиро-вание языка, требует большого опыта. Это итеративный процесс, где приходится учиться на своих же ошибках.
Наследование
Когда вас почти устраивает какой-то класс, вы можете создать потомка и переопреде-лить какую-то часть его функциональности.	Унаследовавшись от одного предка, класс уже не может наследоваться от других. Изменение предка так же становится опасным.
Лаконичность абстракции данных, создан-ной с помощью наследования, является преимуществом. Используя наследование, не обязательно писать весь код для доступа к функциям базового класса. По этой при-чине реализации с использованием насле-дования (как это было в нашем случае) зна-чительно меньше по объему, если сравнить их с композицией. 	О степени понятности кода судить трудно. Чтобы точно знать, какие операции раз-решены для новой структуры, програм-мист должен рассмотреть объявление ис-ходной структуры. Трудность состоит в следующем: чтобы понять класс, скон-струированный с помощью наследования, программист должен постоянно переклю-чаться «взад-вперед» между двумя (или более) описаниями классов. Она известна как проблема «вверх-вниз». В сложных иерархиях классов поля и методы обычно наследуются с разных уровней. И не всегда легко определить, какие поля и методы фактически относятся к данному классу.
	Наследование – уничтожение инкапсуля-ции. Любой класс всегда неявно объявляет свой интерфейс — то, что доступно при использовании класса извне. Если у нас есть класс Ключ и у него публичный метод Открыть, который вызывает приватные методы Вставить, Повернуть и Вынуть, то интерфейс класса Ключ состоит из метода Открыть. Когда мы унаследуем какой-то класс от класса Ключ, он унаследует этот интерфейс. Кроме этого интерфейса, у класса есть также реализация — методы Вставить, Повернуть, Вынуть и их вызов в методе Открыть. Наследники Ключа наследуют вместе с интерфейсом и реализацию. И вот здесь таятся проблемы.


Objective-C
Компилируемый язык программирования, используемый корпорацией Apple, построенный на ос-нове языка Си и парадигм Smalltalk. В частности, объектная модель построена в стиле Small-talk — то есть объектам посылаются сообщения. Язык Objective-C является надмножеством языка Си, поэтому Си-код полностью понятен компилятору Objective-C. Компилятор Objective-C доступен на большинстве основных платформ. Язык используется в первую очередь для Mac OS X (Cocoa) и GNUstep — реализаций объектно-ориентированного интерфейса OpenStep. Также язык используется для iOS (Cocoa Touch). ObjC был создан Брэдом Коксом в начале 1980-х в его компании Stepstone. Он искал возможность собирать программы из готовых компонентов (объ-ектов), подобно тому как сложные электронные устройства могут быть легко собраны из набора готовых интегральных микросхем. При этом такой язык должен быть достаточно про-стым и основанным на языке С, чтобы облегчить переход разработчиков на него. Таким обра-зом, Objective-C является именно расширением языка С — в язык С просто добавлены новые воз-можности для объектно-ориентированного программирования. При этом любая программа на С является программой и на Objective-C. 

•	Мультипарадигма́льный язы́к программи́рования — как правило, язык программирования, который был разработан специально как инструмент мультипарадигмального программирования, то есть изобразительные возможности которого изначально предполагалось унаследовать от нескольких, чаще всего неродственных языков. Иногда термин мультипарадигмальный язык программирования определяют как «язык, который поддерживает больше чем одну парадигму программирования». Цель разработки мультипарадигмальных языков программирования состоит, как правило, в том, чтобы позволить программистам использовать лучший инструмент для работы, признавая, что никакая парадигма не решает все проблемы самым лёгким или самым эффективным способом.
•	Рефлексивно-ориентированный – в информатике отражение или рефлексия (синоним интроспекция, англ. reflection) означает процесс, во время которого программа может отслеживать и модифицировать собственную структуру и поведение во время выполнения. Парадигма программирования, положенная в основу отражения, называется рефлексивным программированием. An object refers to its class to get various information about itself, particularly what code to run to handle each action.
•	Message-oriented – вызовы метода интерпретируются не как вызов функции (хотя к этому обычно все сводится), а именно как посылка сообщения (с именем и аргументами) объекту, подобно тому, как это происходит в Smalltalk-е. Такой подход дает целый ряд плюсов — так, любому объекту можно послать любое сообщение. Объект может вместо обработки сообщения просто переслать его другому объекту для обработки (так называемое делегирование), в частности именно так можно легко реализовать распределенные объекты (то есть объекты, находящиеся в различных адресных пространствах и даже на разных компьютерах). The receiver is an object, and the message tells it what to do. In source code, the message is simply the name of a method and any arguments that are passed to it. When a message is sent, the runtime system selects the appropriate method from the receiver’s repertoire and invokes it. Object can contain state, which in practical terms means that they can contain data and references to other objects. In implementation and use, state usually consists of member variables, instance data, or whatever terminology you use. Can receive messages sent from other objects. Can send messages to other objects.
•	Runtime-oriented – динамичность, целый ряд решений, обычно принимаемых на этапе компиляции, здесь откладывается непосредственно до этапа выполнения. Примеры использования библиотеки рантайма - не рефлексии напрямую - получения списка всех наследников класса, маппинг объекта в словарь, динамическое добавление свойства в объект для динамических баз данных (это уже совсем рефлексия), свиззлинг для добавления дополнительной логики для методов системных фреймворков.
•	Dynamic Typing – The id type is completely nonrestrictive. By itself, it yields no information about an object, except that it is an object. At some point, a program needs to find more specific information about the objects it contains—what the object’s instance variables are, what methods it can perform, and so on. Since the id type designator can’t supply this information to the compiler, each object has to be able to supply it at runtime. This is possible because every object carries with it an isa instance variable that identifies the object’s class—what kind of object it is. Objects are thus dynamically typed at runtime. Whenever it needs to, the runtime system can find the exact class that an object belongs to, just by asking the object. Dynamic typing in Objective-C serves as the foundation for dynamic binding. A crucial difference between function calls and messages is that a function and its arguments are joined together in the compiled code, but a message and a receiving object aren’t united until the program is running and the message is sent. Therefore, the exact method that’s invoked to respond to a message can only be determined at runtime, not when the code is compiled. This dynamic binding of methods to messages works hand-in-hand with polymorphism to give object-oriented programming much of its flexibility and power. Since each object can have its own version of a method, a program can achieve a variety of results, not by varying the message itself, but by varying just the object that receives the message. This can be done as the program runs; receivers can be decided “on the fly” and can be made dependent on external factors such as user actions. The compiler creates just one accessible object for each class, a class object that knows how to build new objects belonging to the class. (For this reason it’s traditionally called a “factory object.”) The class object is the compiled version of the class; the objects it builds are instances of the class. The objects that do the main work of your program are instances created by the class object at runtime. Утиная типизация – границы использования объекта определяются его текущим набором методов и свойств, в противоположность наследованию от определённого класса. То есть считается, что объект реализует интерфейс, если он содержит все методы этого интерфейса, независимо от связей в иерархии наследования и принадлежности к какому-либо конкретному классу. «Если нечто выглядит как утка, плавает как утка и крякает как утка, то это, наверное, и есть утка»

Swift
Paradigm
Multi-paradigm (Protocol-oriented programming, object-oriented, functional, imperative, block structured)
Designed by
Chris Lattner and Apple Inc.
Developer
Apple Inc.
First appeared	June 2, 2014
Stable release
2.1 / October 21, 2015
Typing disci-pline
Static, strong, inferred
OS
iOS, OS X, watchOS, tvOS, Linux later in 2015
License
Proprietary, transitioning to open source in 2015
Filename exten-sions
.swift
Website	developer.apple.com/swift/
Influenced by
Objective-C, Rust, Haskell, Ruby, Python, C#, CLU, D
Influenced
Rust



Swift is a multi-paradigm, compiled programming language created by Apple Inc. for iOS, OS X, watchOS and tvOS development. Swift is designed to work with Apple's Cocoa and Cocoa Touch frameworks and the large body of existing Objective-C code written for Apple products. Swift is in-tended to be more resilient to erroneous code ("safer") than Objective-C and also more concise. It is built with the LLVM compiler framework included in Xcode 6 and later and uses the Objective-C runtime, allowing C, Objective-C, C++ and Swift code to run within a single program.
Swift supports the core concepts that made Objective-C flexible, notably dynamic dispatch, wide-spread late binding, extensible programming, and similar features. These features also have well known performance and safety trade-offs, which Swift was designed to address. For safety, Swift in-troduced a system that helps address common programming errors like null pointers, as well as in-troducing syntactic sugar to avoid the pyramid of doom that can result. For performance issues, Apple has invested considerable effort in aggressive optimization that can flatten out method calls and accessors to eliminate this overhead. More fundamentally, Swift has added the concept of protocol extensibility, an extensibility system that can be applied to types, structs and classes, Apple promotes this as a real change in programming paradigms they refer to as "protocol-oriented programming".
Swift was introduced at Apple's 2014 Worldwide Developers Conference (WWDC). It underwent an upgrade to version 1.2 during 2014, and a more major upgrade to Swift 2 at WWDC 2015. Initially a proprietary language, it was announced that Swift 2 would become open source later that year, sup-porting iOS, OS X and Linux.
History
Development on Swift began in 2010 by Chris Lattner, with the eventual collaboration of many other programmers at Apple. Swift took language ideas "from Objective-C, Rust, Haskell, Ruby, Python, C#, CLU, and far too many others to list". On June 2, 2014, the Worldwide Developers Conference (WWDC) application became the first publicly released app written in Swift. A beta version of the programming language was released to registered Apple developers at the conference, but the company did not promise that the final version of Swift would be source-compatible with the test version. Apple planned to make source code converters available if needed for the full release.
The Swift Programming Language, a free 500-page manual, was also released at WWDC, and is available on the iBooks Store.
Features
Swift is an alternative for the Objective-C language that employs contemporary programming lan-guage theory concepts and strives to present a simpler syntax. During its introduction, it was de-scribed simply as "Objective-C without the C".
By default, Swift does not expose pointers and other unsafe accessors, contrary to Objective-C, which uses pointers pervasively to refer to object instances. Additionally, Objective-C's use of a Smalltalk-like syntax for making method calls has been replaced with a dot-notation style and namespace sys-tem more familiar to programmers from other common object-oriented (OO) languages like Java or C#. Swift introduces true named parameters and retains key Objective-C concepts, including proto-cols, closures and categories, often replacing former syntax with cleaner versions and allowing these concepts to be applied to other language structures, like enums.

Generics
Generic code enables you to write flexible, reusable functions and types that can work with any type, subject to requirements that you define. You can write code that avoids duplication and expresses its intent in a clear, abstracted manner.
Generics are one of the most powerful features of Swift, and much of the Swift standard library is built with generic code. In fact, you’ve been using generics throughout the Language Guide, even if you didn’t realize it. For example, Swift’s Array and Dictionary types are both generic collections. You can create an array that holds Int values, or an array that holds String values, or indeed an array for any other type that can be created in Swift. Similarly, you can create a dictionary to store values of any specified type, and there are no limitations on what that type can be.
		func swapTwoValues<T>(inout a: T, inout _ b: T) {
		    let temporaryA = a
		    a = b
		    b = temporaryA
}

inout parameters, pass by value, pass by reference
When you pass a variable to a function, you are passing a copy of its value to the function instead of your variable itself. If you modified the value of the variable in your function and you printed it when the function is done executing, you'd see the variable still has the original value you originally gave it.

An in-out parameter takes "the variable itself", instead of a copy. and as such you can modify it.

In out parameters are akin to references in C++.
Вопросы
Xcode, фреймворки
Cocoa (в пер. с англ. - какао) — родная объектно-ориентированная среда разработки приложе-ний для операционной системы Mac OS X производства компании Apple. Это один из пяти ос-новных API, доступных в Mac OS X, — Cocoa, Carbon, Toolbox (для работы старых приложений Mac OS 9), POSIX и Java. Такие языки, как Perl, Python и Ruby не считаются основными, так как на них пока что пишется не так много серьёзных приложений для Mac OS X.
Приложения, использующие Cocoa, обычно разрабатываются с помощью среды разработки Apple Xcode (в прошлом называвшегося Project Builder) и Interface Builder с использованием языка Objective-C. Однако, среда Cocoa также доступна и при разработке на других языках, та-ких как Ruby, Python и Perl с помощью связующих библиотек (MacRuby, PyObjC и CamelBones соответственно). Также можно писать Cocoa-программы на Objective-C в обычном текстовом редакторе и вручную компилировать их с помощью GCC или make-сценариев для GNUstep. 
Cocoa Touch — это фреймворк для создания приложений под iPhone, iPod touch, и iPad.
Библиотека Cocoa Touch предоставляет уровень абстракции для iOS (операционной системы iPhone, iPad и iPod touch). Cocoa Touch основана на классах фреймворка Cocoa, используемого в Mac OS X, и, аналогично ей, использует язык Objective-C. Cocoa Touch следует шаблону проек-тирования Model-View-Controller.
Инструменты для разработки приложений с использованием Cocoa Touch включены в iOS SDK. iOS-технологии можно рассматривать как набор слоев, где Cocoa Touch находится на самом высоком уровне, а Core OS и ядро Mac OS X — на более низких. Это позволяет реализовывать многие сложные задачи, сокращая объём работы, которую пришлось бы проделывать разра-ботчикам, работай они на более низком уровне. Тем не менее, некоторые низкие слои абстра-гирования могут быть доступны разработчикам по мере необходимости. Расположение слоев абстрагирования можно представить в следующем виде (от высшего к низшему):
•	Cocoa Touch
•	Media / Application Services
•	Core Services
•	Core OS / ядро Mac OS X
Core Animation
Используйте Core Animation для создания богатых пользовательских интерфейсов с легкой моделью программирования на основе композиции независимых слоев графики.
Core Audio
Core Audio является профессиональной технологией для воспроизведения, обработки и записи звука, что позволяет легко добавлять мощные звуковые функции к вашему приложению.
Core Data
Core Data обеспечивает объектно-ориентированное решение для управления данными, кото-рое легко в использовании и понимании, построено для обработки модели данных необходи-мых любому приложению, как большому так и маленькому.
Core Text is an advanced, low-level technology for laying out text and handling fonts.
 
Core Foundation (also called CF) is a C application programming interface (API) in Mac OS X & iOS, and is a mix of low-level routines and wrapper functions. Some types in Core Foundation are "toll-free bridged", or interchangeable with a simple cast, with those of their Foundation Kit counterparts. For example, one could create a CFDictionaryRef Core Foundation type, and then later simply use a standard C cast to convert it to its Objective-C counterpart, NSDictionary *, and then use the desired Objective-C methods on that object as one normally would.
Аудио и Видео
•	Core Audio
•	OpenAL
•	Media Library
•	AV Foundation
Графика и анимация
•	Core Animation
•	OpenGL ES
•	Quartz 2D
Прикладные программы
•	Address Book
•	Core Location
•	Map Kit
•	Store Kit
Управление данными
•	Core Data
•	SQLite
•	Сети и Интернет
•	Bonjour
•	WebKit
•	BSD Sockets

Core Foundation 
Is a library with a set of programming interfaces conceptually derived from the Objective-C-based Foundation framework but implemented in the C language. To do this, Core Foundation implements a limited object model in C. Core Foundation defines opaque types that encapsulate data and functions, hereafter referred to as “objects.” The programming interfaces of Core Foundation objects have been designed for ease of use and reuse. At a general level, Core Foundation:
•	Enables sharing of code and data among various frameworks and libraries
•	Makes some degree of operating-system independence possible
•	Supports internationalization with Unicode strings
•	Provides common API and other useful capabilities, including a plug-in architecture, XML property lists, and preferences
An "opaque type" is a type where you don't have a full definition for the struct or class. In C, C++ and Ob-jective-C, you can tell the compiler that a type will be defined later by using a forward declaration:
// forward declaration of struct in C, C++ and Objective-C
struct Foo;
// forward declaration of class in C++:
class Bar;
// forward declaration of class in Objective-C:
@class Baz;
The compiler doesn't have enough information to let you do anything directly with the struct or class except declare pointers to it, but this is frequently all you need to do. This allows library and framework creators to hide implementation details. Users of a library or framework then call helper functions to create, manipulate and destroy instances of a forward declared struct or class. For example, a framework creator could create these functions for struct Foo:
struct Foo *createFoo(void);
void addNumberToFoo(struct Foo *foo, int number);
void destroyFoo(struct Foo *foo);
As part of the Core Foundation framework, Apple makes common Objective-C classes like NSString, NSArray and NSBundle available to C programmers through opaque types. C programmers use pointers and helper functions to create, manipulate and destroy instances of these Objective-C classes. Apple calls this "toll-free bridging". They follow a common naming convention: "CF" prefix + class name + "Ref" suffix, where "CF" stands for "Core Foundation" and "Ref" is short for "Reference", meaning it's a pointer.
Core Foundation makes it possible for the different frameworks and libraries on OS X to share code and data. Applications, libraries, and frameworks can define C routines that incorporate Core Foundation types in their external interfaces; they can thus communicate data—as Core Foundation objects—to each other through these interfaces. Core Foundation also provides “toll-free bridging” between certain services and the Cocoa’s Foundation framework. Toll-free bridging enables you to substitute Cocoa objects for Core Foundation objects in function parameters and vice versa.
Some Core Foundation types and functions are abstractions of things that have specific imple-mentations on different operating systems. Code that makes use of these APIs is thus easier to port to different platforms. Date and number types abstract time utilities and offers facilities for converting between absolute and Gregorian measures of time. It also abstracts numeric values and provides facilities for converting between different internal representations of those values.
One of the major benefits Core Foundation brings to application development is internationalization support. Through its String objects, Core Foundation facilitates easy, robust, and consistent interna-tionalization across all OS X and Cocoa programming interfaces and implementations. The essential part of this support is a type, CFString, instances of which represent an array of 16-bit Unicode characters. A CFString object is flexible enough to hold megabytes worth of characters and yet simple and low-level enough for use in all programming interfaces communicating character data. It accomplishes this with performance not much different than that associated with standard C strings.
CFAllocator CFArray CFAttributedString CFBag CFBinaryHeap CFBitVector CFBoolean CFBundle
CFCalendar CFCharacterSet CFData CFDate CFDateFormatter CFDictionary CFError CFFileDescriptor CFLocale CFMachPort CFMessagePort CFMuta-bleArray CFMutableAttributedString CFMutableBag CFMutableBitVector CFMutableCharacterSet CFMutableData CFMutableDictionary CFMutableSet CFMutableString CFNotificationCenter CFNull CFNumber CFNumberFormatter CFPlugIn CFPlugInInstance CFPropertyList CFReadStream CFRunLoop CFRunLoopObserver CFRunLoopSource CFRunLoopTimer CFSet CFSocket CFString CFStringTokenizer CFTimeZone CFTree CFType CFURL CFUserNotifi-cation CFUUID CFWriteStream CFXMLNode CFXMLParser CFXMLTree
In a technical sense, yes, it is faster, for exactly that reason. In a practical sense, no, it's not faster. For one thing, the speed dif-ference is tiny. We're talking milliseconds saved over the life of the entire process.
The savings might be bigger on the iPhone, but it's still pretty much the tiniest speed gain you can get. Your time is much better spent profiling your app in Instruments and going where it tells you and ironing out the hot spots in your own code. And that's where Foundation becomes faster: Your time. Code that uses Foundation's autorelease feature whenever feasible saves you a lot of time and headaches by avoiding easily-avoidable memory leaks (namely, forgetting to write or failing to reach release messages). CF does not have autorelease, so you have to remember to explicitly CFRelease everything you create or copy with it—and when you forget or fail to reach that code (and I do mean when—I speak from experience), you will spend much more time hunting down the memory leak. The static analyzer helps, but it will never be able to catch everything. (You technically can autorelease CF objects, but the code to do so is terribly ugly and you're only watering down your already-minuscule speed gain.)
So, stick to Foundation as much as possible. Don't go overboard with the autorelease; even in pure Cocoa, there are still times when explicitly releasing objects is warranted (mostly tight loops), and this goes double for Cocoa Touch (since iOS will kill your app if you allocate too much memory, so you'll want to release big objects like images as soon as possible). But usually, autorelease saves you far more time than CF will ever save your users. The non-time-related reason is that Objective-C code, with argument names (from the message selector) mixed in with values, is far easier to read than C function-based code. This may not make your work go any faster, but it certainly makes it more fun.

Core Foundation is a set of foundational APIs for some very well used and basic functionalities in the system. Their existence in C is partially historical, and partially to promote use in tools, such as command line utilities, which were historically considered difficult to program in Cocoa. Many iOS programmers never directly use Core Foundation APIs, because much of the func-tionality is available in the Cocoa or Cocoa Touch Foundation framework classes. However, you cannot write an iOS (or OS X) application without Cocoa or Cocoa Touch. From my experience, it is good to understand the concepts behind both Core Foun-dation and the Cocoa/Cocoa Touch Foundation frameworks and especially their interactions (toll-free bridging and memory management at the interface between the two in an ARC environment), but for many people, the Core Foundation pieces can be left until later. Personally, I would suggest that a basic understanding of the concepts above is a good idea to anyone pro-gramming the Mac or iOS.

History: The Foundation dates to ~1993/1994 and the APIs therein were a part of the OpenStep APIs published by NeXT.
What is the purpose of CoreFoundation framework?
CF was created during the transition of Mac OS to Mac OS X to help support that transition. Initially, it was done both for speed and to allow purely non-Objective-C programs to be written. Over time, that has proven to be a non-issue and CF has more and more bits that are implemented in Objective-C (have a look at the CoreFoundation binary using something like otool).
CFLite is a light-weight, portable, pure-C (IIRC) variant.
Doesn't the Cocoa Framework provide every thing that's needed already?
More or less. And, certainly moreso for building GUI applications on either iOS or OS X.
Does the CoreFoundation Framework provide any advantages that the CocoaFramework does not provide?
Several, but generally at a cost of decreased simplicity and increased fragility.
For example, the CF collections allow you to completely customize how memory is managed and objects are identified; you can provide custom allocation/free/hashing/comparison hooks. Through this, you can "easily" encapsulate non-Objective-C types in CF collections.

UIKit
The UIKit framework provides the classes needed to construct and manage an application’s user interface for iOS. It provides an application object, event handling, drawing model, windows, views, and controls specifically designed for a touch screen interface.
The UIKit framework defines a number of functions, many of them used in graphics and drawing operations.
   
 

AddressBook
The Address Book framework provides access to a centralized contacts database, called the Address Book database, that stores a user’s contacts. Applications such as Mail and Messages use this database to present information about known and unknown persons. The Address Book technology for iOS provides a way to store people’s contact information and other personal information in a centralized database, and to share this information between applications. The technology has several parts:
•	The Address Book framework provides access to the contact information.
•	The Address Book UI framework provides the user interface to display the information.
•	The Address Book database stores the information.
•	The Contacts application provides a way for users to access their contact information.
When you add this technology to your application, users will be able to use the contact information that they use in other applications, such as Mail and Text, in your application. This document tells you how to do the following:
•	Access the user’s Address Book database
•	Prompt the user for contact information
•	Display contact information to the user
•	Make changes to the user’s Address Book database
 

CFNetwork
CFNetwork is a low-level, high-performance framework that gives you the ability to have detailed control over the protocol stack. It is an extension to BSD sockets, the standard socket abstraction API that provides objects to simplify tasks such as communicating with FTP and HTTP servers or resolving DNS hosts. CFNetwork is based, both physically and theoretically, on BSD sockets.
Just as CFNetwork relies on BSD sockets, there are a number of Cocoa classes that rely on CFNetwork (NSURL, for example). In addition, the Web Kit is a set of Cocoa classes to display web content in win-dows. Both of these classes are very high level and implement most of the details of the networking protocols by themselves.
 
When to Use CFNetwork
CFNetwork has a number of advantages over BSD sockets. It provides run-loop integration, so if your application is run loop based you can use network protocols without implementing threads. CFNet-work also contains a number of objects to help you use network protocols without having to imple-ment the details yourself. For example, you can use FTP protocols without having to implement all of the details with the CFFTP API. If you understand the networking protocols and need the low-level control they provide but don't want to implement them yourself, then CFNetwork is probably the right choice.
There are a number of advantages of using CFNetwork instead of Foundation-level networking APIs. CFNetwork is focused more on the network protocols, whereas the Foundation-level APIs are focused more on data access, such as transferring data over HTTP or FTP. Although Foundation APIs do pro-vide some configurability, CFNetwork provides a lot more. 
Now that you understand how CFNetwork interacts with the other OS X networking APIs, you're ready to become familiar with the CFNetwork APIs along with two APIs that form the infrastructure for CFNetwork.
CFNetwork Infrastructure
Before learning about the CFNetwork APIs, you must first understand the APIs which are the foundation for the majority of CFNetwork. CFNetwork relies on two APIs that are part of the Core Foundation framework, CFSocket and CFStream. Understanding these APIs is essential to using CFNetwork.
CFSocket API
Sockets are the most basic level of network communications. A socket acts in a similar manner to a telephone jack. It allows you to connect to another socket (either locally or over a network) and send data to that socket. The most common socket abstraction is BSD sockets. CFSocket is an abstraction for BSD sockets. With very little overhead, CFSocket provides almost all the functionality of BSD sockets, and it integrates the socket into a run loop. CFSocket is not limited to stream-based sockets (for example, TCP), it can handle any type of socket. You could create a CFSocket object from scratch using the CFSocketCreate function, or from a BSD socket using the CFSocketCreateWithNative function. Then, you could create a run-loop source using the function CFSocketCreateRunLoopSource and add it to a run loop with the function CFRunLoopAddSource. This would allow your CFSocket callback function to be run whenever the CFSocket object receives a message.
CFStream API
Read and write streams provide an easy way to exchange data to and from a variety of media in a device-independent way. You can create streams for data located in memory, in a file, or on a network (using sockets), and you can use streams without loading all of the data into memory at once.
A stream is a sequence of bytes transmitted serially over a communications path. Streams are one-way paths, so to communicate bidirectionally an input (read) stream and output (write) stream are necessary. Except for file-based streams, you cannot seek within a stream; once stream data has been provided or consumed, it cannot be retrieved again from the stream. CFStream is an API that provides an abstraction for these streams with two new CFType objects: CFReadStream and CFWriteStream. Both types of stream follow all of the usual Core Foundation API conventions. CFStream is built on top of CFSocket and is the foundation for CFHTTP and CFFTP. As you can see in Figure 1-2, even though CFStream is not officially part of CFNetwork, it is the basis for almost all of CFNetwork.
 

QuartzCore
Quartz 2D is an API of the Core Graphics framework that implements drawing.
Quartz Core is a framework that includes APIs for animation and image processing.
Quartz frameworks and their APIs
•	CoreGraphics.framework
•	Quartz 2D API manages the graphic context and implements drawing.
•	Quartz Services API provides low level access to the window server. This includes display hardware, resolution, refresh rate, and others.
•	QuartzCore.framework
•	Core Animation: Objective-C API to do 2D animation.
•	Core Image: image and video processing (filters, warp, transitions).iOS 5
Quartz.framework OS X only
•	Image Kit: display and edit images.
•	PDF Kit: display and edit PDFs.
•	Quartz Composer: display Quartz Composer compositions.
•	QuickLookUI: preview media elements.
All three frameworks use OpenGL underneath because all drawing in iOS or OS X goes through OpenGL at some point. OpenGL (Open Graphics Library — открытая графическая библиотека, гра-фический API) — спецификация, определяющая независимый от языка программирования платформонезависимый программный интерфейс для написания приложений, использующих двумерную и трёхмерную компьютерную графику. Включает более 250 функций для рисова-ния сложных трёхмерных сцен из простых примитивов. Используется при создании компью-терных игр, САПР, виртуальной реальности, визуализации в научных исследованиях. На плат-форме Windows конкурирует с DirectX.

CoreText
Core Text is for apps that need a low-level text-handling technology correlating with the Core Graphics framework (Quartz). If you work directly with Quartz and you need to draw some text, use Core Text. If, for example, you have your own page layout engine—you have some text and you know where it needs to go in your view—you can use Core Text to generate the glyphs and position them relative to each other with all the features of fine typesetting, such as kerning, ligatures, line-breaking, hyphenation, and justification.
Core Text Lays Out Text
Core Text generates glyphs (from character codes and font data) and positions them relative to each other in glyph runs. It breaks glyph runs into lines, and it assembles lines into multiline frames (such as paragraphs). Core Text also provides glyph- and layout-related data, such as glyph locations and measurement of lines and frames. It handles character attributes and paragraph styles, including various types of tab styles and positioning.
You Can Manage Fonts With Core Text
The Core Text font API provides fonts, font collections, font descriptors, and easy access to font data. It also provides support for multiple master fonts, font variations, font cascading, and font linking. Core Text provides an alternative to Quartz for loading your own fonts into the current process, that is, font activation.
 
PhoneGap (называемый также Apache Callback, Apache Cordova) — бесплатный open-source фреймворк для создания мобильных приложений, созданный Nitobi Software. Позволяет создать приложения для мобильных устройств используя JavaScript, HTML5 и CSS3, без необходимости знания «родных» языков программирования (например, Objective-C), под все мобильные операционные системы (iOS, Android, Bada и т. д.). Готовое приложение компилируется в виде установочных пакетов для каждой мобильной операционной системы.
Appcelerator is a privately held mobile technology company based in Mountain View, California. Its main products are Titanium, an open-source software development kit for cross-platform mobile development, and the Appcelerator Platform, an enterprise software suite for mobile app development, testing, deployment, and analytics.
Templates в Xcode, структура проекта, код?	
main.m - "стартовая точка" программы. Содержит объект приложения, который, среди прочего, устанавливает цикл выполнения (Run Loop – цикл выполнения регистрирует вводимый код и делает возможной работу вводимых событий в приложении). Большая часть этой работы вы-полняется функцией UIApplicationMain, которая представлена платформой UIKit и вызывается автоматически в исходном файле вашего проекта main.m. При запуске приложение runtime вы-зывает функцию main, которой передаются два аргумента: int argc (argument count – число ар-гументов, вводимых в командной строке), const char *argv[] (argument vector – массив указате-лей на символьные значения).
#import <Foundation/Foundation.h>
int main(int argc, const char * argv[]) {
    		@autoreleasepool {
        	return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
    		}
}
Prefix.pch - файл, содержащий список хэдеров для прекомпиляции. По сути, это необходимо для ускорения компиляции программы.
Info.plist - файл конфигурации
AppDelegate - это класс, который присутствует в каждом iOS-приложении. Он отвечает за реак-цию на различные глобальные события, которые операционная система посылает нашему приложению - например, о входящем звонке, о малом количестве памяти, о том, что пользова-тель собирается свернуть приложение и т.д.
iOS
iPhone OS 1 — 29 июня 2007
iPhone OS 2 — 11 июля 2008
iPhone OS 3 — 17 июня 2009
iOS 4 — 21 июня 2010
iOS 5 — 12 октября 2011
iOS 6 — 11 июня 2012
iOS 7 — июнь 2013
iOS 8 — 2 июня 2014
iOS 9 — June 8, 2015

IPhone, resolution, pixels vs points?
 

A pixel on iOS is the full resolution of the device, which means if I have an image that is 100x100 pixels in length, then the phone will render it 100x100 pixels on a standard non-retina device. However, because newer iPhones have a quadrupled pixel density, that same image will render at 100x100 pixels, but look half that size. The iOS engineers solved this a long time ago (way back in OS X with Quartz) when they introduced Core Graphics' point system. A point is a standard length equivalent to 1x1 pixels on a non-retina device, and 2x2 pixels on a retina device. That way, your 100x100 image will render twice the size on a retina device and basically normalize what the user sees.
It also provides a standard system of measurement on iOS devices because no matter how the pixel density chanes, there have always been 320x480 points on an iPhone screen and 768x1024 points on an iPad screen.*
But at the same time, you can basically disregard the documentation considering that retina devices were introduced with iOS 4 at a minimum, and I don't know of too many people still running iOS 3 on a newer iPhone. But if such a case arises, your UIImage would need to be rendered at exactly twice it's dimensions in pixels on a retina iPhone to make up for the pixel density difference.

Файловая система iOS
 

App lifecycle
 
 

Возможные состояния программы
•	Not running (не запущенное) — приложение не было запущено или его работа была пре-кращена
•	Inactive (неактивное) — приложение работает, но не принимает события (например, когда пользователь заблокировал телефон при запущенном приложении)
•	Active (активное) — нормальное состояние приложения при его работе
•	Background (фоновое) — приложение больше не на дисплее, но оно все еще выполняет код
•	Suspended (приостановленное) — приложение занимает память, но не выполняет код
 
 

Жизненный цикл UIViewController
 


Представления
The UIView (UIResponder : NSObject) Объект, рисующий контент в прямоугольной области экрана и управляющий событиями, вызванными касаниями экрана пользователем. Представ-ление также может содержать другие представления, называемые субпредставлениями. При добавлении субпредставления к представлению контейнер называется родительским пред-ставлением, а его субпредставление называется дочерним представлением. Сочетание роди-тельского представления, его дочерних представлений (а так же их дочерних представлений, если таковые имеются) образует иерархию представлений. 
Интерфейс состоит из представлений (UIView).  
UIWindow (UIView : UIResponder : NSObject) – единственный экземпляр  в приложении, который играет роль контейнера для всех представлений. class defines an object known as a window that manages and coordinates the views an app displays on a device screen. Unless an app can display content on an external device screen, an app has only one window. The two principal functions of a window are 
1.	to provide an area for displaying its views 
2.	to distribute events to the views
To change the content your app displays, you can change the window’s root view; you don’t create a new window. A window belongs to a level—typically, UIWindowLevelNormal—that represents where it sits on the z-axis relative to other windows. For example, a system alert window appears above normal app windows.
UIViewController – управление единственным экраном приложения. 
UINavigationController – управляет стеком из массива UIViewController. 
Root View Controller – Корневой контроллер, находится внизу стека, самый последний.   
CGRect – структура, которая содержит переменные для хранения координат и размеров.
frame – это прямоугольник описываемый положением location(x, y) и размерами size (width, height) вьюхи относительно ее superview в которой оа содержится. 
bounds – это прямоугольник описываемый положением location(x, y) и размерами size (width, height) вьюхи относительно ее собственной системы координат (0, 0).

 
// 1. CGRect получение координат и границ экрана.
CGRect screen=[[UIScreen mainScreen] bounds];
// 2. получение границ и координат фрейма для программы.
CGRect appFrame=[[UIScreen mainScreen] applicationFrame];
// 3. создаем новое окно.
self.window=[UIWindow alloc] initWithFrame: appFrame];
// 4. создаем вью с параметрами appFrame.
UIView *view=[[UIView alloc]initWithFrame: appFrame];
// 5. добавляем вью в окно с помощью метода addSubView.
[ window addSubView: view];
// 6. делаем окно видимым
[ window makeKeyAndVisible];

	@implementation AppDelegate
	- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    		self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
		// Override point for customization after application launch.
		self.window.backgroundColor = [UIColor whiteColor];
		[self.window makeKeyAndVisible];
		return YES; 
	}

MEMORY MANAGEMENT
Memory management – процесс выделения памяти под объекты, и освобождение ее после ис-пользования. 
•	"manual retain-release" (ручное сохранение-освобождение) или MRR – вы явно управляете памятью, отслеживая объекты, которые у вас есть. Это реализуется с помощью модели, известной как подсчет ссылок, что Foundation класса NSObject обеспечивает совместно со средой выполнения.
•	В Automatic Reference Counting (автоматическом подсчете ссылок), или ARC, система использует тот же подсчет ссылок, что и система MRR, но он вставляет соответствующий вызов метода управления памятью за вас во время компиляции. 
•	В garbage collection (сборе мусора), система автоматически отслеживает, какие объекты владеют другими объектами. Затем она автоматически освобождает (или собирает мусор) объекты, на которые больше не ссылаются. Метод использует другой механизм, нежели, чем у используемых в MRR и ARC, и поддерживается только в среде выполнения на Mac OS X, а не IOS. 
Отличие ARC от GC: 
GC работает во время выполнения программы с помощью кода, который переодически запус-кается и проверяет объекты. ARC работает во время компиляции и вставляет retain и release автоматически в код.
 
Память в стеке и в куче
 
 
Stack

The stack is a region of memory which contains storage for local variables, as well as internal temporary values and housekeeping. On a modern system, there is one stack per thread of execution. When a function is called, a stack frame is pushed onto the stack, and function-local data is stored there. When the function returns, its stack frame is destroyed. All of this happens automatically, without the programmer taking any explicit action other than calling a function.

Heap

The heap is, essentially, everything else in memory. (Yes, there are things other than the stack and heap, but let's ignore that for this discussion.) Memory can be allocated on the heap at any time, and destroyed at any time. You have to explicitly request for memory to be allocated from the heap, and if you aren't using garbage collection, explicitly free it as well. This is where you store things that need to outlive the current function call. The heap is what you access when you call malloc and free.

Stack vs Heap Objects

Given that, what's a stack object, and what's a heap object?
First, we must understand what an object is in general. In Objective-C (and many other languages), an object is simply a contiguous blob of memory with a particular layout. (If you're interested in just what it contains and how it's laid out, check out my intro to the Objective-C runtime.)
The precise location of that memory is less important. As long as you have some memory somewhere with the right contents, it's a working Objective-C object. In Objective-C, objects are usually created on the heap:

NSObject *obj = [[NSObject alloc] init];

The storage for the obj variable itself is on the stack, but the object it points to is in the heap. The [NSObject alloc] call allocates a chunk of heap memory, and fills it out to match the layout needed for an NSObject.

A stack object is just an object where the memory for that object is allocated on the stack. Objective-C doesn't have any support for this directly, but you can construct one manually without too much trouble:

struct {
Class isa;
} fakeNSObject;
fakeNSObject.isa = [NSObject class];
    
NSObject *obj = (NSObject *)&fakeNSObject;
NSLog(@"%@", [obj description]);

This works fine, although you shouldn't depend on it, as it depends on replicating the internal layout of the class.

Advantages of Stack Objects

It's obviously possible to have stack objects in general. Aside from the above hack, real languages like C++ have language support for stack objects. In C++, you can create objects on the stack or the heap:
std::string stackString;
std::string *heapString = new std::string;
Stack objects have two compelling advantages:
•	Speed: Allocating memory on the stack is really fast. All of the bookkeeping is done by the compiler when you build your program. At runtime, the function prolog just carves out the amount of space it needs for all local variables, and the code knows what goes where because it was all computed in advance. Stack allocations are essentially free, whereas heap allocations can be quite expensive.
•	Simplicity: Stack objects have a defined lifetime. You can never leak one, because it always gets destroyed at the end of the scope where it was declared.
Disadvantages of Stack Objects
The strictly defined lifetime of a stack object is a disadvantage as well, and a major one. In Objective-C (and C++, and many other languages), it is impos-sible to move an object after it's created. The reason for this is because there may be many pointers to that object, and those pointers are not tracked. They would all need to be updated to track the move, but there's no way to accomplish this.
(Note: it's not an impossibility in general, and many languages move objects around as a matter of course, often as part of garbage collection schemes. However, this requires more runtime smarts and a stricter type system than you get in Objective-C.)
As used in Cocoa, Objective-C uses a reference counting system for memory management. The advantage of this system is that any single object can have multiple "owners", and the system won't allow the object to be destroyed until all owners have relinquished ownership.
Stack allocated objects inherently have a single owner, the function which created them. If Objective-C had stack objects, what would happen if you passed it to some other code which then tried to keep it around by retaining it? There's no way to prevent the object from being destroyed when the function which created it returns, so the retain can't work. The code which tries to keep the object around will fail, end up with a dangling reference, and will crash.
Another problem is that stack objects are not very flexible. It's not uncommon in Objective-C to implement an initializer which destroys the original object and returns a new one instead. How could you do that with a stack object? You really couldn't. Much of the runtime flexibility of Objective-C depends on having heap objects.
Actual Stack Objects in Objective-C

It turns out that Objective-C does have stack objects, truly and officially, as of 10.6!
Don't get too excited, though. It's only supported for a single kind of object: blocks. When you write a block inside a function using the ^{} syntax, the result of that expression is a stack object!
Manual retain-release
Используйте методы доступа (акцессоры), чтобы сделать управление памятью проще. Рас-смотрим счетчик объекта, количество которого вы хотите установить.
@interface Counter : NSObject {
NSNumber *_count;
}
@property (nonatomic, retain) NSNumber *count;
@end;
В свойстве объявляется два метода доступа. Как правило, вы должны попросить компилятор для синтезации методов, однако, поучительно посмотреть, как они могли бы быть реализова-ны. В "get" акцессоре, вы просто возвращаете переменную экземпляра, так что нет необходи-мости в retain или release:
- (NSNumber *)count { 
return _count;
}
В "set" методе, если все остальные играют по тем же правилам, вы должны принять новое зна-чение счетчика, которое может быть удалено в любое время, поэтому вам придется взять на себя ответственность объектно-, отправив ему retain сообщение, чтобы убедиться что его не будет. Вы должны также отказаться от права владения на старый объект, отправив ему release сообщение. (Отправка сообщения к nil допускается в Objective-C, так что реализация все равно будет работать, если _count до сих пор не установлена.) Вы должны послать это после [newCount retain] на случай, если два и более объекта захотят, ненароком ее освободить.
- (void)setCount:(NSNumber *)newCount {
[newCount retain];
[_count release];
// Make the new assignment.
_count = newCount;
}
Использование методов доступа для установки значений свойств
Предположим, вы хотите реализовать метод для сброса счетчика. У вас есть несколько вари-антов. Первая реализация создает экземпляр NSNumber с alloc, который вы балансируете release-ом.
- (void)reset {
    	NSNumber *zero = [[NSNumber alloc] initWithInteger:0];
[self setCount:zero];
[zero release];
}
Второй использует удобство конструктора для создания нового объекта NSNumber. Он уже существует поэтому нет необходимости в retain или release
- (void)reset {
NSNumber *zero = [NSNumber numberWithInteger:0];
[self setCount:zero];
}
Обратите внимание, что оба используют set метод акцессора.
Следующий код почти наверняка работает правильно для простых случаев, но как заманчиво бы это не выглядело, чтобы отказаться от методов доступа, сделав это почти наверняка в бу-дущем приведет к ошибке на определенном этапе (например, если вы забыли сохранить или освободить, или если изменится семантика управления памятью для переменной экземпляра).
- (void)reset {
NSNumber *zero = [[NSNumber alloc] initWithInteger:0];
[_count release];
_count = zero;
}
Отметим также, что если вы используете методику ключ-значение (KVO), то изменение пере-менной, таким путем, не совместимо с KVO.
•	Не используйте методы доступа в методах инициализаторов и dealloc
Единственные места, где вы не должны использовать методы доступа для установки пере-менной экземпляра находятся в методах - инициализаторе и dealloc. Для инициализации счет-чика объекта со значением нуль, вы можете реализовать метод инициализации следующим образом:
- init {
self = [super init];
if (self) {
_count = [[NSNumber alloc] initWithInteger:0];
}
return self;
}
Чтобы позволить счетчику при инициализации принимать значение отличное от нуля, вы мо-жете реализовать метод initWithCount: следующим образом:
- initWithCount:(NSNumber *)startingCount {
self = [super init];
if (self) {
_count = [startingCount copy];
}
return self;
}
Так как переменная счетчика класса - экземпляр объекта, необходимо также реализовать dealloc метод. Следует отказаться от владения любыми переменными экземпляра, отправив им сообщение release, и в конечном счете он должн вызывать реализацию супер класса:
- (void)dealloc {
[_count release];
[super dealloc];
}
•	Используйте weak (слабые) ссылки чтобы избежать сохранения циклов
Сохранение объекта создает сильную ссылку на этот объект. Объект не может быть освобож-ден, пока все его сильные ссылки не будут освобождены. Проблема, известная как сохранность цикла, может возникнуть, если два объекта имеют циклические ссылки, то есть, у них есть сильные ссылки друг на друга (либо непосредственно, либо через цепочку других объектов, каждый из которых имеет сильную ссылку на следующую ведущую к первой).
•	Не освобождайте объекты, которые используете
•	Не используйте dealloc для управления ограниченными ресурсами
Вы должны управлять как правило, не ограниченными ресурсами, такими как дескрипторы файлов, сетевые подключения, и буферы или кэш в dealloc методе. В частности, вы не должны проектировать классы так, чтобы dealloc был вызван, когда вы думаете, он будет вызван. Вы-зов dealloc, может быть отложен или обойден, либо из-за ошибки или из-за падения приложе-ния.

Коллекции собственных объектов
При добавлении объекта в коллекцию (например, массив, словарь, или набор), коллекция ста-новится его владельцем. Коллекция откажется от владения объектом, когда объект удаляется из коллекции или коллекця будет освобождена. Так, например, если вы хотите создать массив чисел вы можете выполнить одно из следующих действий:
NSMutableArray *array = <#Получаем изменяемый массив#>;
NSUInteger i;
// ...
for (i = 0; i < 10; i++) {
NSNumber *convenienceNumber = [NSNumber numberWithInteger:i];
[array addObject:convenienceNumber];
}
В этом случае вы не вызываете alloc, так что нет необходимости вызывать release. Значит нет необходимости вызова retain для новых номеров (convenienceNumber), так как массив это сде-лает.
Базовая модель используемая для управления памятью со счетчиком ссылок обеспечивается сочетанием методов, определенных в протоколе NSObject и стандартными методами именова-ния. Класс NSObject также определяет метод dealloc, который вызывается автоматически, когда объект будет освобожден.
Вы владеете каким-либо объектом вами созданным: Вы можете создать объект, используя ме-тод, имя которого начинается с "alloc", "new", "copy", или "mutableCopy".
Вы можете стать владельцем объекта, используя retain: Полученный объект, как правило, га-рантированно остается в силе в течение выполнения метода, в котором он был получен, и этот метод также может безопасно вернуть объект к вызвовшему его методу. Вы используете retain в двух случаях: (1) В реализации метода доступа или инициализации метода, чтобы стать вла-дельцем объекта, который нужно сохранить как значение свойства, (2) Для предотвращения освобождения объекта как побочного эффекта от некоторых других операций
Если объект вам больше не нужен, вы должны отказаться от права собственности на него: Вы отказываетесь от права собственности на объект, послав ему сообщение release или autorelease сообщение. В Cocoa терминологии, из отказа от права владения объектом, как пра-вило следует, "освобождение" объекта.
Вы не должны отказаться от права владения объектом, которого у вас нет: Это всего лишь следствие предыдущих правил политики, заявиленных в явном виде.
Используйте autorelease для Отправки отложенного release.
Вы не являетесь владельцем объектов, возвращаемых по ссылке: Некоторые методы в Cocoa указавают, что объект возвращается по ссылке (то есть, они не имеют аргумента типа ClassName ** или id *). Данная закономерность заключается в использовании NSError объекта, который содержит информацию об ошибках, если они происходит, о чем свидетельствуют initWithContentsOfURL:options:error: (NSData) и initWithContentsOfFile:encoding:error: (NSString). В этих случаях применяются те же правила, как уже было описано. При вызове любого из этих методов, вы не создаете NSError объект, так что вы не являетесь его владельцем.
Реализация dealloc для отказа от права владения объектами: Класс NSObject определяет метод dealloc, который вызывается автоматически, когда объект не имеет владельцев и его память будет утилизирована, в терминологии Cocoa это называется "освободил" или "освобождена". Роль dealloc метода заключается в освобождении собственной памяти объекта, и распоряжением любыми ресурсами которыми он располагает, в том числе любыми переменными экземпляра объекта, которыми он владеет.
Важно: 
•	Вы никогда не должны ссылаться на dealloc метод другого объекта непосредственно.
•	Вы должны вызвать реализацию суперкласса в конце вашей реализации.
•	Вы не должны привязывать управление системными ресурсами, как к объектам кон-тролируемым временем жизни.
Automatic Reference Counting.
Автоматический подсчет ссылок является компиляторной функцией, которая обеспечивает автоматическое управление памятью в Objective-C объектах. Вместо того, чтобы думать о со-хранении и освобождении объектов, ARC позволяет сосредоточиться на непосредственном ко-де Вашего приложения. ARC работает путем добавления кода во время компиляции, чтобы время жизни объекта было ровно столько, сколько необходимо, но не более того. Концепту-ально, это то же управление памятью, что и ручной подсчет ссылок (описанное в практическом управлении памятью) путем добавления соответствующего кода управления памятью, за вас. ARC поддерживается начиная с Xcode 4.2 для Mac OS X v10.6 и v10.7 (64-bit applications), а также iOS 4 и iOS 5. Слабые (weak) ссылки не поддерживаются в Mac OS X v10.6 и iOS 4 и более ранних.
Существует несколько ограничений на использование механизма ARC.
•	Нельзя использовать свойство, имя которого начинается со слова “new”. Например, не допускается объявление 
@property NSString *newString;
•	Нельзя использовать свойство только для чтения без атрибутов управления памятью. Если вы не используете механизм ARC, то можете использовать объявление 
@property (readonly) NSString *title;
Но если вы используете механизм ARC, то должны указать, кто управляет памятью, так что достаточно просто вставить ключевое слово unsafe_unretained, потому что по умол-чанию используется атрибут assign. 
ARC only works with retainable object pointers (ROPs). There are three kinds of retainable object pointers:
1)  Block pointers 
2)  Objective-C object pointers 
3)  Typedefs marked with __attribute__((NSObject)) 
All other pointer types, such as char * and CF objects such as CFStringRef, are not ARC compatible. If you use pointers that aren’t handled by ARC, you’ll have to manage them yourself. That’s OK, because ARC interoperates with manually managed memory.
Модификаторы
Для свойств
 

readwrite (по-умолчанию) и readonly
генерируются одновременно сеттеры и геттеры (setters/getters) или только геттеры

assign (по-умолчанию)
просто присваивает переданное значение. 
•	assign is the default and simply performs a variable assignment
•	assign is a property attribute that tells the compiler how to synthesize the property's setter implementation
•	I would use assign for C primitive properties and weak for weak references to Objective-C ob-jects.

retain
посылает release текущему значению переменной экземпляра, потом посылает retain новому объекту, и присваивает новое значение переменной экземпляра. 
•	it is retained, old value is released and it is assigned retain specifies the new value should be sent
•	retain on assignment and the old value sent -release
•	retain is the same as strong.
•	apple says if you write retain it will auto converted/work like strong only.
•	methods like alloc include an implicit retain

copy
посылает release текущему значению переменной экземпляра, затем copy новому объекту и присваивает новый объект переменной экземпляра. В последних двух случаях, вы должны по-слать release (или присвоить nil) свойству при dealloc. Атрибут сору создает копию объекта и переводит на нее указатель. Атрибут сору чаще всего используется с объектными типами, имеющими изменяемые субклассы. Например, NSString имеет субкласс с именем NSMutаblеString. 

assign (по-умолчанию), retain, copy — применяются только для свойств, которые могут быть безопасно приведены к id. 

atomic (по-умолчанию) и nonatomic
свойства с ключевым словом atmoic — потокобезопасны, с nonatomic — могут быть проблемы при многопоточном доступе. Доступ к nonatomic свойствам обычно быстрее чем к atomic, по-этому они часто используются в однопоточных приложениях.

strong (ARC)
это синоним для retain
•	it says "keep this in the heap until I don't point to it anymore"
•	in other words "I'am the owner, you cannot dealloc this before aim fine with that same as re-tain"
•	you use strong only if you need to retain the object.
•	by default all instance variables and local variables are strong pointers.
•	we generally use strong for UIViewController (UI item's parents)
•	strong is used with ARC and it basically helps you, by not having to worry about the retain count of an object. ARC automatically releases it for you when you are done with it. Using the keyword strong means that you own the object.

weak (ARC)
синоним assign, с одним лишь исключением, что свойство с weak автоматически устанавливается в nil когда объект уничтожается. Также следует учитывать, что ключ weak доступен только начиная с iOS 5 и Mac OS X 10.7 (Lion). Если переменная указатель сохраняет адрес объекта, этот объект является активным и имеет владельца – сильная ссылка (strong). Если переменная не принимает владения объектом – слабая ссылка (weak, __weak). Родитель может владеть своим потомком, но потомок – родителем не должен.
•	it says "keep this as long as someone else points to it strongly"
•	the same thing as assign, no retain or release
•	a weak reference is a reference that you do not retain.
•	we generally use weak for IBOutlets (UIViewController's Childs). This works because the child object only needs to exist as long as the parent object does.
•	a weak reference is a reference that does not protect the referenced object from collection by a garbage collector.
•	weak is essentially assign, a unretained property. Except the when the object is deallocated the weak pointer is automatically set to nil

unsafe_unretained (по умолчанию) 
всегда используется для свойств, содержащих не-объектные значения. Что делать, если вы хо-тите использовать механизм ARC в более старых операционных системах, в которых обнуляе-мые слабые ссылки недоступны? Компания Apple предлагает использовать ключевое слово __unsafe_unretained и атрибут unsafe_unretained, которые сообщают механизму ARC, что ука-занная ссылка является слабой. 

Strong & Weak Explanation:
Imagine our object is a dog, and that the dog wants to run away (be deallocated). Strong pointers are like a leash on the dog. As long as you have the leash attached to the dog, the dog will not run away. If five people attach their leash to one dog, (five strong pointers to one object), then the dog will not run away until all five leashes are detached. Weak pointers, on the other hand, are like little kids pointing at the dog and saying "Look! A dog!" As long as the dog is still on the leash, the little kids can still see the dog, and they'll still point to it. As soon as all the leashes are detached, though, the dog runs away no matter how many little kids are pointing to it. As soon as the last strong pointer (leash) no longer points to an object, the object will be deallocated, and all weak pointers will be zeroed out. When we use weak? The only time you would want to use weak, is if you wanted to avoid retain cycles (e.g. the parent retains the child and the child retains the parent so neither is ever released).

Если делать все стронг - то если нам понадобится сослать друг на друга два класса - то есть в класса А завести проперти класса В, а в нем - ссылку но этот объект - то они не освободятся. Я обычно предпочитаю, чтобы стронг ссылки были только в одном экземпляре - Особенно в коде, где об одном объекте знает несколько сущностей

Для переменных
Generally speaking, these extra qualifiers don’t need to be used very often. You might first encounter these qualifiers and others when using the migration tool. For new projects however, you generally you won’t need them and will mostly use strong/weak with your declared properties.
 

__strong
по умолчанию. Объект остается "живым", если на него есть сильный указатель. This means any object created using alloc/init is retained for the lifetime of its current scope. The “current scope” usually means the braces in which the variable is declared (i.e. a method, for loop, if block, etc…)

__weak
указывается (слабая) ссылка, которая не сохраняет указанный объект живым. Слабая ссылка устанавливается в nil, когда на объект нет сильных ссылок. This is only useful if the object is somehow strongly referenced somewhere else. When destroyed, a variable with __weak is set to nil. Будьте осторожны с применением __weak слабых ссылок, так, если Вы создадите объект только со слабой ссылкой, то нет никакой гарантии, что он доживет до своего применения и не освободится. 

__unsafe_unretained
указывается ссылка, которая не сохраняет указанный объект живым и не устанавливается в nil, когда нет сильных ссылок на объект. Если объект, на который она ссылается, будет осво-божден, то указатель остается болтаться со значением, которого уже нет. Можете использо-вать __unsafe_unretained вместо __weak. Это создаст слабую ссылку, которая НЕ будет обнулена. Но вы должны быть уверены, что не используете этот указатель (предпочтительно, чтобы вы об-нулили его вручную) ПОСЛЕ того, как объект, на который он указывает, был уничтожен. Ис-пользуется только тогда, когда недоступен weak.

__autoreleasing
используется для обозначения аргументов, которые передаются по ссылке (id *) и autoreleased по возвращении. not to be confused with calling autorelease on an object before returning it from a method, this is used for passing objects by reference, for example when passing NSError objects by reference such as 
[myObject performOperationWithError:&tmp];

Что такое property?
Упрощенный способ для определения и создания методов доступа, обращающихся к суще-ствующим переменным экземплярам. Классы, которые подставляют переменные экземпляра, могут использовать обозначение свойства вместо того, чтобы использовать синтаксис getter и setter.

Написать сеттер и геттер для свойства, с ARC и без.
ARC
- (void)setNumerator:(int)n {
numerator = n;
}

- (int)numerator {
return numerator;
}
MRR
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

В каких случаях лучше использовать strong, а в каких copy для NSString? Почему?
@property (nonatomic, strong) NSString *someString;
@property (nonatomic, copy) NSString *anotherString;
сopy используется только для объектов, реализующих протокол <NSCopying>. Обычно его ис-пользуют с mutable объектами или со свойствами, представляющими какое-то значение (value).

autorelease vs release?
Autorelease pool это — механизм отложеного отказа от ответсвенности. Это означет что вы больше не хотите владеть объектом и он вам в общем-то не нужен, но не хотите чтобы он уда-лился прямо сейчас. Зачастую вам не нужно создавать свой пул, просто используется NSAutoreleasePool и то даже не напрямую. Чтобы поместить объект в autorelease pool нужно отправить ему сообщение autorelease (один объект может быть добавлен в пул несколько раз) и на следующем цикле сообщений autorelease pool отправит всем этим объектам сообщение release, так как сам получит dealloc после чего будет создан новый autorelease pool. Таким об-разом Cocoa ожидает, что как минимум один autorelease pool будет всегда, и автоматически со-здает его в main.
Autorelease pool добавляются по принципу стека, самый последний добавленый пул будет в самом верху стека авторелиз пулов в текущем потоке. Создание пула осуществляется стан-дартным alloc и init, удаление drain. Если послать сообщение drain не самому верхнему пулу, то все пулы над ним тоже получат это сообщение и соответсвенно удалят все из себя. Оффици-альная документация показывает нам вот такой пример использования своего пула:
NSArray *urls = <# An array of file URLs #>;
for (NSURL *url in urls) {
NSAutoreleasePool *loopPool = [[NSAutoreleasePool alloc] init];
   	NSError *error = nil;
    	NSString *fileContents = [[[NSString alloc] initWithContentsOfURL:url
      encoding:NSUTF8StringEncoding 
error:&error] autorelease];
    	/* Process the string, creating and autoreleasing more objects. */
    	[loopPool drain];
}
Мы тут видим, что был создан свой пул (он разместился вверху стека пулов и будет освобож-ден первым), в него добавляются NSString *fileContents и потом пул освобождается (а так как он самый верхний — освобождается только он).

Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC?
1 способ: Edit – Refactor – Convert to ObjC ARC
2 способ: App – Targets – Build Phases – Compile Sources – поставить флаг -fno-objc-arc 

Основные темы управления памятью, такие как владение retain/release/autorelease
•	Что случится если вы добавите только что созданный объект в Mutable Array, и пошлете ему сообщение release? //объект останется в массиве
•	Что случится если послать сообщение release массиву? //массив удалится
•	Что случится если вы удалите объект из массива и попытаетесь его использовать? // объект удалится из массива, использовать объект дальше можно

Вопрос о циклах в графах владения, и почему свойства delegate (предоставляющие до-ступ к делегату) обычно задаются как assign?
A creates B;
A sets itself as B’s delegate;
[A release];
if B retained A => leak;
 

Что произойдет если сначала нажать на кнопку 1 а потом на кнопку 2?
- (IBAction)btn1DidTouch:(id)sender {
_string = [[[NSString alloc] initWithFormat:@"v=%i", rand()] autorelease];
}
- (IBAction)btn2DidTouch:(id)sender {
NSLog(@"_string is equal to ‘%@’", _string);
}
Крэш, т.к utoreleasepool создается в начале обработки события и уничтожается в конце. т.е. нажали на первую кнопку — началась обработка события, нажали на вторую — кнопку — за-кончилась обработка первого события, очистлся autoreleasepool а вместе с ним и объект уда-лился, а ссылка осталась. Затем началась обработка второго события и мы обращаемся к заде-алоченному объекту, результат — крэш.

Нужно ли ретейнить (посылать сообщение retain) делегат для CAAnimation? 
Да. Это одно из редких исключений в политике управления памятью. Specific task that has some sort of “finished” state. Также нужно ритейнить NSURLConnection.

Что произойдет при исполнении следующего кода? 
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];
Впоследствии это вызовет крэш. Потому что объект дважды добавляется в пул автоосвобож-дения, и release вызовется дважды.

Реализуйте следующие методы: retain, release, autorelease
-(id)retain {
   		NSIncrementExtraRefCount(self);
    		return self;
}	
-(void)release {
    		if(NSDecrementExtraRefCountWasZero(self)) {
         		NSDeallocateObject(self);
    		}
}
-(id)autorelease {  
// Add the object to the autorelease pool
    		[NSAutoreleasePool addObject:self];
    		return self;
}

Если я вызову performSelector:withObject:afterDelay: – объекту пошлется сообщение re-tain? 
Да. Это создает таймер который вызывает селектор в RunLoop'е текущего потока (thread).

Вы можете объяснить, что происходит когда вы посылаете объекту сообщение autore-lease? 
Когда вы посылаете объекту сообщение autorelease, его счетчик ссылок уменьшится на 1 в определенный момент в будущем. Объект будет добавлен в autorelease pool (пул автоосвобождения) в текущем потоке (thread). Цикл главного потока (main thread loop "NSRunLoop") создает autorelease pool в начале функции и освобождает его в конце. Это устанавливает pool на время выполнения задачи. Это также означает что авторелизные (объекты помещенные в пул) объекты созданные в течение выполнеения задачи не будут уничтожены пока задача не завершится. Это может привести к излишнему потреблению памяти для задачи (объекты будут уже не нужны но освободятся только в конце задачи). Вы также можете попробовать создать вложенный пул и освободить его раньше, или использовать NSOperationQueue с его собственным пулом.

Объясните что такое подсчет ссылок (retain count)? 
Подсчет ссылок (retain count) — это механизм с помощью которого в obj-c реализовано управ-ление памятью. Когда вы создаете объект, его счетчик ссылок (retain count) установлен на 1. Когда вы посылаете объекту сообщение retain , его счетчик ссылок увеличивается на 1. Когда вы посылаете объекту сообщение release , его счетчик ссылок уменьшается на 1. Когда вы по-сылаете объекту сообщение autorelease , его счетчик ссылок уменьшится на 1 в определенный момент в будующем. Когда счетчик ссылок объекта становится равным 0 то объект уничтожа-ется (dealloc).

Паттерны проектирования
Повторимая архитектурная конструкция, представляющая собой решение проблемы проекти-рования в рамках некоторого часто возникающего контекста. Популярные: MVC, делегат, син-глтон, наблюдатель. Редкие паттерны: строитель, мост, фасад. 
Порождающий шаблон – абстрагирует процесс инстанцирования (создания экземпляра клас-са). Шаблон, порождающий класс – наследуется. Шаблон, порождающий объект – делегирует. Позволяет сделать систему независимой от способа создания, композиции и представления объектов. 
Примеры: абстрактная фабрика, строитель, ленивая загрузка, singleton. 
How Cocoa Adapts Design Patterns
You can find adaptations of design patterns throughout Cocoa, in both its OS X and iOS versions. Mechanisms and architectures based on patterns are common in Cocoa frameworks and in the Objective-C runtime and language. Cocoa often puts its own distinctive spin on a pattern because its designs are influenced by factors such as language capabilities or existing architectures.
This section contains summaries of most of the design patterns cataloged in Design Patterns: Ele-ments of Reusable Object-Oriented Software. Each section not only summarizes the pattern but dis-cusses the Cocoa implementations of it. Only patterns that Cocoa implements are listed, and each de-scription of a pattern in the following sections pertains to a particular Cocoa context.
Implementations of design patterns in Cocoa come in various forms. Some of the designs described in the following sections—such as protocols and categories—are features of the Objective-C language. In other cases, the “instance of a pattern” is implemented in one class or a group of related classes (for example, class clusters and singleton classes). And in other cases the pattern adaptation is a major framework architecture, such as the responder chain. Some of the pattern-based mechanisms you get almost “for free” while others require some work on your part. And even if Cocoa does not implement a pattern, you are encouraged to do so yourself when the situation warrants it; for example, object composition (Decorator pattern) is often a better technique than subclassing for extending class behavior.
Two design patterns are reserved for later sections, Model-View-Controller (MVC) and object model-ing. MVC is a compound, or aggregate pattern, meaning that it is based on several catalog patterns. Object modeling has no counterpart in the Gang of Four catalog, instead originating from the domain of relational databases. Yet MVC and object modeling are perhaps the most important and pervasive design patterns in Cocoa, and to a large extent they are interrelated patterns. They play a crucial role in the design of several technologies, including bindings, undo management, scripting, and the document architecture. To learn more about these patterns, see The Model-View-Controller Design Pattern and Object Modeling.
Communication Patterns
 
Концепция Model–View–Controller
MVC
Модель состоит из классов, в которых хранятся данные приложения. 
Представление создает дизайн. 
Контроллер связывает модель и представление и организует логику приложения. 
Пассивная модель — модель не имеет никаких способов воздействовать на представление или контроллер, и используется ими в качестве источника данных для отображения. Все измене-ния модели отслеживаются контроллером и он же отвечает за перерисовку представления, если это необходимо. Такая модель чаще используется в структурном программировании, так как в этом случае модель представляет просто структуру данных, без методов их обрабатыва-ющих.
Активная модель — модель оповещает представление о том, что в ней произошли изменения, а представления, которые заинтересованы в оповещении, подписываются на эти сообщения. Это позволяет сохранить независимость модели как от контроллера, так и от представления.

 
MVC 
View может общаться с Моделью
M не воздействует на V или C. Контроллер следить за моделью сам и принимает решения.
MVP 
View не может общаться с моделью, только через Presenter
Активная MVC – Model оповещает Presenter об изменениях, а Presenter подписан на обновле-ния => независимость модели от View и Presenter.
Passive view
Supervising contoller
MVVM 
View и Model в связке. View Model – абстракция представления, с другой стороны – обертка мо-дели. Содержит модель, готовую к представлению, а также команды представления для того, чтобы влиять на модель.
MVCS
Store – класс для хранения и обработки данных (save / load logic)
Делегирование 
(англ. Delegation) — основной шаблон проектирования, в котором объект внешне выражает некоторое поведение, но в реальности передаёт ответственность за выполнение этого пове-дения связанному объекту. Паттерн хорош тем, что нам не нужно хранить всю логику в одном месте и позволяет лучше переиспользовать код. Рассматривайте делегат как обычный обьект, который может выполнять некоторые функции. Например, возьмем NSTableView delegate. Вы хотите отрисовать ячейку таблицы как-то по своему. NSTableView своему делегату пошлет со-общение о том, что он сейчас будет рисовать данную ячейку и делегат уже сам решает что с ней делать (рисовать по своему, не трогать вообще и т.д.). Это, грубо говоря, способ получения и предоставления информации, о которой NSTableView не знает вообще ничего.
Или же пример создания собственных делегатов. Представьте, что у вас есть свой класс, кото-рый выполняет некоторую функцию. Для выполнения некоторых задач ему необходима ин-формация из другого класса, о котором сейчас не известно ровным счетом ничего, кроме того, что он существует. Тогда создается конструкция вида:
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
Как видно из примера — наш делегат, это просто указатель на какой-либо обьект. Ну и предо-ставлены геттер и сеттер. Для того, чтобы делегат выполнил некоторое действие для нас, где-то внутри нашего Class1 мы пошлем сообщение вида 
[delegate doSomeWork];
Обьект же, который мы назначили делегатом для данного класса в свою очередь получит это сообщение и начнет выполнять какое-то действие. 
В принципе и все. Достаточно просто. Делегирование преследует простую цель — сохранять объекты слабо связанными. Таким образом, вы можете отправлять сообщения делегату, не зная какой именно это объект. А сам делегат, при этом, может выполнять разные действия в зависимости от своей реализации. Так что тут мы имеем одно из проявлений полиморфизма. То есть, грубо говоря, делегирующий объект говорит объекту-делегату ЧТО делать, но его не волнует КАК именно это будет сделано.
Плюс, делегирование порой может быть более удобной альтернативой наследованию — вме-сто того, чтобы плодить иерархию классов, вы определяете необходимый интерфейс для деле-гатов и используете их.
Кластеры
Class clusters are a design pattern that the Foundation framework makes extensive use of. Class clus-ters group a number of private concrete subclasses under a public abstract superclass. The grouping of classes in this way simplifies the publicly visible architecture of an object-oriented framework without reducing its functional richness. Class clusters are based on the Abstract Factory design pat-tern.
 
NSMutableArray is not a concrete class, it is just the abstract superclass of a class cluster. The documenta-tion for NSMutableArray does have information about how to subclass, but also strongly advises you not to! Only subclass if you have a special need for actual storage. A class cluster means that the actual class will be chosen at run-time. An array created empty, may not use the same class as an array created with 1000 items. The run-time can do smart choices of what implementation to use for you. In practice NSMutableArray will be a bridged CFArray. Nothing you need to worry about, but you might see it if you inspect the type of your arrays in the debugger, you will never see NSArray, but quite often NSCFArray. As mentioned before, subclassing is not the same as extending a class. Objective-C has the concept of categories. A category is similar to what other programming languages call mix-ins. If you for example want a convenience method on NSMutableArray to sort all members on a property, then define the category interface in a .h file. 
Синглтон
Существует в системе в единственном экземпляре => не может быть повторно создан. Объект, к которому обращаются много объектов. Примеры синглтонов в системе:
[NSUserDefaults standardUserDefaults];
[UIApplication sharedApplication];
[UIScreen mainScreen];
[NSFileManager defaultManager];
Non thread safe
@implementation Singleton
static Singleton *sharedSingleton_ = nil;
+ (Singleton *) sharedInstance {
if (sharedSingleton_ == nil) {
sharedSingleton_ = [[Singleton alloc] init]; 
}
return sharedSingleton_; 
}
@end
However this is wrong on several levels. Firstly, this isn't thread safe, so what happens if multiple threads all try to access this at the same time? There is no reason 1 thread couldn't be in the middle of allocating the object while the other one is trying to access the object. This is actually what Apple shows in its documentation.
If you must use singletons, use dispatch_once()
dispatch_once() solves the problem of safely being able to create a singleton in that (1) it guarantees that the code in the block will only be called once for the lifetime of the application (2) its thread safe as I noted in a previous article and (3) its faster than other methods like using @synchronize(),etc...
"If called simultaneously from multiple threads, this function waits synchronously until the block has completed." So you should be writing it like this...
Thread safe
+ (MyClass *)singleton {
static dispatch_once_t pred;
static MyClass *shared = nil;
dispatch_once(&pred, ^{
shared = [[MyClass alloc] init];
});
return shared;
}

Criticism:

1.	It violates the single responsibility principle because of its quality of controlling its own crea-tion and lifecycle.
2.	It introduces global state to your application. I would say global state is very bad because any code can change its value. So at the time of debugging it's really hard to find which portion of the code has made the current stage of global variable.
3.	Singleton is generally a bad idea if you are doing unit testing, and it's generally a bad idea not to perform unit testing.

Adapter
The Adapter design pattern converts the interface of a class into another interface that clients expect. Adapter lets classes work together that couldn’t otherwise because of incompatible interfaces. It decouples the client from the class of the targeted object.
Protocols
A protocol is a language-level (Objective-C) feature that makes it possible to define interfaces that are instances of the Adapter pattern. A protocol is essentially a series of method declarations unassociated with a class. (In Java, interface is synonymous with protocol.) If you want a client object to communicate with another object, but the objects’ incompatible interfaces make that difficult, you can define a protocol. The class of the other object then formally adopts the protocol and “conforms” to it by implementing one or more of the methods of the protocol. The protocol may require the conforming class to implement some of its methods and may leave the implementation of others optional. The client object can then send messages to the other object through the protocol interface.
Protocols make a set of method declarations independent of the class hierarchy. They make it possible to group objects on the basis of conformance to a protocol as well as class inheritance. The NSObject method conformsToProtocol: permits you to verify an object’s protocol affiliation.
Cocoa has informal protocols as well as formal protocols. An informal protocol is a category on the NSObject class, thus making any object a potential implementer of any method in the category (see Categories). The methods in an informal protocol can be selectively implemented. Informal protocols are part of the implementation of the delegation mechanism in OS X (see Delegation).
Note that the design of protocols does not perfectly match the description of the Adapter pattern. But it achieves the goal of the pattern: allowing classes with otherwise incompatible interfaces to work together.
Uses and Limitations
You use a protocol primarily to declare an interface that hierarchically unrelated classes are expected to conform to if they want to communicate. But you can also use protocols to declare an interface of an object while concealing its class. The Cocoa frameworks include many formal protocols that enable custom subclasses to communicate with them for specific purposes. For example, the Foundation framework includes the NSObject, NSCopying, and NSCoding protocols, which are all very important ones. AppKit protocols include NSDraggingInfo, NSTextInput, and NSChangeSpelling. UIKit protocols include UITextInputTraits, UIWebViewDelegate, and UITableViewDataSource.
Formal protocols implicitly require the conforming class to implement all declared methods. However, they can mark single methods or groups of methods with the @optional directive, and the con-forming class may choose to implement those. They are also fragile; once you define a protocol and make it available to other classes, future changes to it (except for additional optional methods) can break those classes.
Command
The Command design pattern encapsulates a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations. The request object binds together one or more actions on a specific receiver. The Command pattern separates an object making a request from the objects that receive and execute that request.
Invocation Objects
An instance of the NSInvocation class encapsulates an Objective-C message. An invocation object con-tains a target object, method selector, and method parameters. You can dynamically change the target of the message dispatched by the invocation object as well as its parameters; once the invocation is executed, you can also obtain the return value from the object. With a single invocation object, you can repeatedly invoke a message with multiple variations in target and parameters.
The creation of an NSInvocation object requires an NSMethodSignature object, which is an object that encapsulates type information related to the parameters and return value of a method. An NSMethodSignature object, in turn, is created from a method selector. The implementation of NSInvocation also makes use of functions of the Objective-C runtime.
Uses and Limitations
NSInvocation objects are part of the programmatic interfaces of distributed objects, undo manage-ment, message forwarding, and timers. You can also use invocation objects in similar contexts where you need to decouple an object sending a message from the object that receives the message.
The distributed objects technology is for interprocess communication. See Proxy for more on distrib-uted objects.
The Target-Action Mechanism
The target-action mechanism enables a control object—that is, an object such as a button, slider, or text field—to send a message to another object that can interpret the message and handle it as an application-specific instruction. The receiving object, or the target, is usually a custom controller object. The message—named an action message—is determined by a selector, a unique runtime identifier of a method.
In the AppKit framework, the cell object that a control owns typically encapsulates the target and ac-tion. When the user clicks or otherwise activates the control, the control extracts the information from its cell and sends the message. (A menu item also encapsulates target and action, and sends an action message when the user chooses it.) The target-action mechanism can work on the basis of a selector (and not a method signature) because the signature of an action method in AppKit by convention is always the same.
In UIKit, the target-action mechanism does not rely on cells. Instead, a control maps a target and ac-tion to one or more multitouch events that can occur on the control.
Uses and Limitations
When creating a Cocoa application, you can set a control’s action and target through the Interface Builder application. You thereby let the control initiate custom behavior without writing any code for the control itself. The action selector and target connection are archived in a nib file and are restored when the nib is unarchived. You can also change the target and action dynamically by sending the control or its cell setTarget: and setAction: messages.
A Cocoa application for OS X can use the target-action mechanism to instruct a custom controller ob-ject to transfer data from the user interface to a model object, or to display data in a model object. The Cocoa bindings technology obviates the need to use target-action for this purpose.
Composite
The Composite design pattern composes related objects into tree structures to represent part-whole hierarchies. The pattern lets clients treat individual objects and compositions of objects uniformly.
The Composite pattern is part of the Model-View-Controller aggregate pattern, which is describe in The Model-View-Controller Design Pattern.
View Hierarchy
The views in a window are internally structured into a view hierarchy. At the root of the hierarchy is a window and its content view, a transparent view that fills the window’s content rectangle. Views that are added to the content view become subviews of it, and they become the superviews of any views added to them. Except for the content view, a view has one (and only one) superview and zero or any number of subviews. You perceive this structure as containment: a superview contains its subviews. 
 
The view hierarchy is a structural architecture that plays a part in both drawing and event handling. A view has two bounding rectangles, its frame and its bounds, that affect how graphics operations with the view take place. The frame is the exterior boundary; it locates the view in its superview’s coordinate system, defines its size, and clips drawing to the view’s edges. The bounds, the interior bounding rectangle, defines the internal coordinate system of the surface where the view draws itself.
When a window is asked by the windowing system to prepare itself for display, superviews are asked to render themselves before their subviews. When you send some messages to a view—for example, a message that requests a view to redraw itself—the message is propagated to subviews. You can thus treat a branch of the view hierarchy as a unified view.
The view hierarchy is also used by the responder chain for handling events and action messages. See the summary of the responder chain in Chain of Responsibility.
Uses and Limitations
You create or modify a view hierarchy whenever you add a view to another view, either programmatically or using Interface Builder. The AppKit framework automatically handles all the relationships associated with the view hierarchy.
Decorator
The Decorator design pattern attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality. As does subclassing, adaptation of the Decorator pattern allows you to incorporate new behavior without modifying existing code. Decorators wrap an object of the class whose behavior they extend. They implement the same interface as the object they wrap and add their own behavior either before or after delegating a task to the wrapped object. The Decorator pattern expresses the design principle that classes should be open to extension but closed to modification.
General Comments
Decorator is a pattern for object composition, which is something that you are encouraged to do in your own code. Cocoa, however, provides some classes and mechanisms of its own that are based on the pattern. In these implementations, the extending object does not completely duplicate the inter-face of the object that it wraps, and the implementations use different techniques for interface shar-ing.
Cocoa uses the Decorator pattern in the implementation of several of its classes, including NSAttributedString, NSScrollView, UIDatePicker. The latter two classes are examples of compound views, which group together simple objects of other view classes and coordinate their interaction.
Delegation
Delegation is a mechanism by which a host object embeds a weak reference (weak in the sense that it’s a simple pointer reference, unretained) to another object—its delegate—and periodically sends messages to the delegate when it requires its input for a task. The host object is generally an “off-the-shelf” framework object (such as an a target="_self" NSWindow/a or a target="_self" NSXMLParser/a object) that is seeking to accomplish something, but can only do so in a generic fashion. The delegate, which is almost always an instance of a custom class, acts in coordination with the host object, supplying program-specific behavior at certain points in the task (see Figure 4-3). Thus delegation makes it possible to modify or extend the behavior of another object without the need for subclassing.
 
Delegation, in the simple sense of one object delegating a task to another object, is a common tech-nique in object-oriented programming. However, Cocoa implements delegation in a unique way. A host class uses a formal protocol or an informal protocol to define an interface that the delegate object may choose to implement. All the methods in the informal protocol are optional, and the formal protocol may declare optional methods, allowing the delegate to implement only some of the methods in the protocol. Before it attempts to send a message to its delegate, the host object determines whether it implements the method (via a respondsToSelector: message) to avoid runtime exceptions. For more on formal and informal protocols, see Protocols.
Some classes in the Cocoa frameworks also send messages to their data sources. A data source is identical in all respects to a delegate, except that the intent is to provide the host object with data to populate a browser, a table view, or similar user-interface view. A data source, unlike a delegate, may also be required to implement some methods of the protocol.
Delegation is not a strict implementation of the Decorator pattern. The host (delegating) object does not wrap an instance of the class it wants to extend; indeed, it’s the other way around, in that the delegate is specializing the behavior of the delegating framework class. There is no sharing of interface either, other than the delegation methods declared by the framework class.
Delegation in Cocoa is also part of the Template Method pattern (Template Method).
Uses and Limitations
Delegation is a common design in the Cocoa frameworks. Many classes in the AppKit and UIKit frameworks send messages to delegates, including NSApplication, UIApplication, UITableView, and several subclasses of NSView. Some classes in the Foundation framework, such as NSXMLParser and a NSStream, also maintain delegates. You should always use a class’s delegation mechanism instead of subclassing the class, unless the delegation methods do not allow you to accomplish your goal.
Although you can dynamically change the delegate, only one object can be a delegate at a time. Thus if you want multiple objects to be informed of a particular program event at the same time, you cannot use delegation. However, you can use the notification mechanism for this purpose. A delegate automatically receives notifications from its delegating framework object as long as the delegate implements one or more of the notification methods declared by the framework class. See the discussion of notifications in the Observer pattern.
Delegating objects in AppKit do not retain their delegates or data sources. 
Categories
A category is a feature of the Objective-C language that enables you to add methods (interface and implementation) to a class without having to make a subclass. There is no runtime difference—within the scope of your program—between the original methods of the class and the methods added by the category. The methods in the category become part of the class type and are inherited by all the class’s subclasses.
As with delegation, categories are not a strict adaptation of the Decorator pattern, fulfilling the intent but taking a different path to implementing that intent. The behavior added by categories is a compile-time artifact, and is not something dynamically acquired. Moreover, categories do not encapsulate an instance of the class being extended.
Uses and Limitations
The Cocoa frameworks define numerous categories, most of them informal protocols (which are summarized in Protocols). Often they use categories to group related methods. You may implement categories in your code to extend classes without subclassing or to group related methods. However, you should be aware of these caveats: you cannot add instance variables to the class. If you override existing methods of the class, your application may behave unpredictably.
Facade
The Facade design pattern provides a unified interface to a set of interfaces in a subsystem. The pat-tern defines a higher-level interface that makes the subsystem easier to use by reducing complexity and hiding the communication and dependencies between subsystems.
NSImage
The NSImage class of the AppKit framework provides a unified interface for loading and using images that can be bitmap-based (such as those in JPEG, PNG, or TIFF format) or vector-based (such as those in EPS or PDF format). NSImage can keep more than one representation of the same image; each representation is a kind of NSImageRep object. NSImage automates the choice of the representation that is appropriate for a particular type of data and for a given display device. It also hides the details of image manipulation and selection so that the client can use many different underlying representations interchangeably.
Uses and Limitations
Because NSImage supports several different representations of what an image is, some requested attributes might not apply. For example, asking an image for the color of a pixel does not work if the underlying image representation is vector-based and device-independent.

Iterator
The Iterator design pattern provides a way to access the elements of an aggregate object (that is, a collection) sequentially without exposing its underlying representation. The Iterator pattern transfers the responsibility for accessing and traversing the elements of a collection from the collection itself to an iterator object. The Iterator defines an interface for accessing collection elements and keeps track of the current element. Different iterators can carry out different traversal policies.
Enumerators
The NSEnumerator class in the Foundation framework implements the Iterator pattern. The private, concrete subclass of the abstract NSEnumerator class returns enumerator objects that sequentially traverse collections of various types—arrays, sets, dictionaries (values and keys)—returning objects in the collection to clients.
NSDirectoryEnumerator is a distantly related class. Instances of this class recursively enumerate the contents of a directory in the file system.
Uses and Limitations
The collection classes such as NSArray, NSSet, and NSDictionary include methods that return an enu-merator appropriate to the type of collection. All enumerators work in the same manner. You send a nextObject message to the enumerator object in a loop that exits when nil is returned instead of the next object in the collection.
You can also use fast enumeration to access the elements of a collection; this language feature is de-scribed in Fast Enumeration.
Mediator
The Mediator design pattern defines an object that encapsulates how a set of objects interact. Media-tor promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently. These objects can thus remain more reusable.
A "mediator object” in this pattern centralizes complex communication and control logic between ob-jects in a system. These objects tell the mediator object when their state changes and, in turn, respond to requests from the mediator object.
Memento
The Memento pattern captures and externalizes an object’s internal state—without violating encapsulation—so that the object can be restored to this state later. The Memento pattern keeps the important state of a key object external from that object to maintain cohesion.
Archiving
Archiving converts the objects in a program, along with those objects’ properties (attributes and rela-tionships) into an archive that can be stored in the file system or transmitted between processes or across a network. The archive captures the object graph of a program as an architecture-independent stream of bytes that preserves the identity of the objects and the relationships among them. Because an object’s type is stored along with its data, an object decoded from a stream of bytes is normally instantiated using the same class of the object that was originally encoded.
Uses and Limitations
Generally, you want to archive those objects in your program whose state you want to preserve. Mod-el objects almost always fall into this category. You write an object to an archive by encoding it, and you read that object from an archive by decoding it. Encoding and decoding are operations that you perform using an NSCoder object, preferably using the keyed archiving technique (requiring you to invoke methods of the NSKeyedArchiver and NSKeyedUnarchiver classes). The object being encoded and decoded must conform to the NSCoding protocol; the methods of this protocol are invoked during archiving.
Property List Serialization
A property list is a simple, structured serialization of an object graph that uses only objects of the fol-lowing classes: NSDictionary, NSArray, NSString, NSData, NSDate, and NSNumber. These objects are commonly referred to as property list objects. Several Cocoa framework classes offer methods to seri-alize these property list objects and define special formats for the data stream recording the contents of the objects and their hierarchical relationship. The NSPropertyListSerialization class provides class methods that serialize property list objects to and from an XML format or an optimized binary format.
Uses and Limitations
If the objects in an object graph are simple, property list serialization is a flexible, portable, and ade-quate means to capture and externalize an object and its state. However, this form of serialization has its limitations. It does not preserve the full class identity of objects, only the general kind (array, dictionary, string, and so on). Thus an object restored from a property list might be of a different class than its original class. This is especially an issue when the mutability of an object can vary. Property list serialization also doesn’t keep track of objects that are referenced multiple times in an object, potentially resulting in multiple instances upon deserialization that was a single instance in the original object graph.
Core Data
Core Data is a Cocoa framework that defines an architecture for managing object graphs and making them persistent. It is this second capability—object persistence—that makes Core Data an adaptation of the Memento pattern.
In the Core Data architecture, a central object called the managed object context manages the various model objects in an application's object graph. Below the managed object context is the persistence stack for that object graph—a collection of framework objects that mediate between the model objects and external data stores, such as XML files or relational databases. The persistence-stack objects map between data in the store and corresponding objects in the managed data context and, when there are multiple data stores, present them to the managed object context as a single aggregate store.
The design of Core Data is also heavily influenced by the Model-View-Controller and object modeling patterns.
Uses and Limitations
Core Data is particularly useful in the development of enterprise applications where complex graphs of model objects must be defined, managed, and transparently archived and unarchived to and from data stores. The Xcode development environment includes project templates and design tools that reduce the programming effort required to create the two general types of Core Data applications, those that are document-based and those that are not document-based. The Interface Builder application also includes configurable Core Data framework objects in its library.
Proxy
The Proxy design pattern provides a surrogate, or placeholder, for another object in order to control access to that other object. You use this pattern to create a representative, or proxy, object that con-trols access to another object, which may be remote, expensive to create, or in need of securing. This pattern is structurally similar to the Decorator pattern but it serves a different purpose; Decorator adds behavior to an object whereas Proxy controls access to an object.
NSProxy
The NSProxy class defines the interface for objects that act as surrogates for other objects, even for objects that don’t yet exist. A proxy object typically forwards a message sent to it to the object that it represents, but it can also respond to the message by loading the represented object or transforming itself into it. Although NSProxy is an abstract class, it implements the NSObject protocol and other fundamental methods expected of a root object; it is, in fact, the root class of a hierarchy just as the NSObject class is.
Concrete subclasses of NSProxy can accomplish the stated goals of the Proxy pattern, such as lazy in-stantiation of expensive objects or acting as sentry objects for security. NSDistantObject, a concrete subclass of NSProxy in the Foundation framework, implements a remote proxy for transparent dis-tributed messaging. NSDistantObject objects are part of the architecture for distributed objects. By acting as proxies for objects in other processes or threads, they help to enable communication be-tween objects in those threads or processes.
NSInvocation objects, which are an adaptation of the Command pattern, are also part of the distributed objects architecture (see Invocation Objects).
Uses and Limitations
Cocoa employs NSProxy objects only in distributed objects. The NSProxy objects are specifically in-stances of the concrete subclasses NSDistantObject and NSProtocolChecker. You can use distributed objects not only for interprocess messaging (on the same or different computers) but you can also use it to implement distributed computing or parallel processing. If you want to use proxy objects for other purposes, such as the creation of expensive resources or security, you have to implement your own concrete subclass of NSProxy.
Ленивая загрузка 	
Приём в программировании, когда некоторая ресурсоёмкая операция (создание объекта, вы-числение значения) выполняется непосредственно перед тем, как будет использован её ре-зультат. Таким образом, инициализация выполняется «по требованию», а не заблаговременно. Аналогичная идея находит применение в самых разных областях: например, компиляция «на лету» и логистическая концепция «Точно в срок». Частный случай ленивой инициализации — создание объекта в момент обращения к нему — является одним из порождающих шаблонов проектирования.
Достоинства
•	Инициализация выполняется только в тех случаях, когда она действительно необходима;
•	Ускоряется начальная инициализация.
Недостатки
•	Невозможно явным образом задать порядок инициализации объектов;
•	Возникает задержка при первом обращении к объекту.
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
static NSString *CellIdentifier = @"CellIdentifier";
	cell = [tableView dequeueReusableCellWithIdentifier:CellIdentifier];
	if (cell == nil) {
cell = [[UITableViewCell alloc] initWithStyle:UITableViewCellStyleDefault
reuseIdentifier:CellIdentifier];
	}
	cell.textLabel.text = someText;
	return cell;
}
Observer 
Определяет одно-ко-многим отношение между объектами, и если изменения происходят в объекте – все подписанные на него объекты тут же узнают про это изменение. Идея проста: объект который мы называем Subject – дает возможность другим объектам, которые реализу-ют интерфейс Observer, подписываться и отписываться от изменений происходящик в Subject. Когда изменение происходит – всем заинетерсованным объектам высылается сообщение, что изменение произошло. В нашем случае – Subject – это издатель газеты, Observer это мы с вами – те кто подписывается на газету, ну и собсвтенно изменение – это выход новой газеты, а опо-вещение – отправка газеты всем кто подписался.
Когда используется паттерн:
•	Когда Вам необходимо сообщить всем объектам подписанным на изменения, что изме-нение произошло, при этом вы не знаете типы этих объектов. 
Изменения в одном объекте требуют чтоб состояние изменилось в других объектах, при чем количество объектов может быть разное. 

Notification
Notificaiton – механизм использования возможностей NotificationCenter самой операционной системы. Использование NSNotificationCenter позволяет объектам коммуницировать, даже не зная друг про друга. Это очень удобно использовать когда у вас в паралельном потоке пришел push-notification, или же обновилась база, и вы хотите дать об этом знать активному на даный момент View.
Чтобы послать такое сообщение стоит использовать конструкцию типа:
NSNotification *broadCastMessage = 
[NSNotification notificationWithName:@"broadcastMessage" object:self]; 
NSNotificationCenter *notificationCenter = [NSNotificationCenter defaultCenter];
Как видим, мы создали объект типа NSNotification, в котором мы указали имя нашего опове-щения: “broadcastMessage”, и, собственно, сообщили о нем через NotificationCenter.
Чтобы подписаться на событие в объекте который заинтересован в изменении стоит исполь-зовать следующую конструкцию:
NSNotificationCenter *notificationCenter = [NSNotificationCenter defaultCenter]; 
[notificationCenter addObserver:self
                 selector:@selector(update:) 
                     name:@"broadcastMessage" 
                   object:nil];
Собственно, из кода все более-менее понятно: мы подписываемся на событие, и вызывается метод который задан в свойстве selector.

KVC
Key-value coding is a mechanism for accessing an object’s properties indirectly, using strings to iden-tify properties, rather than through invocation of an accessor method or accessing them directly through instance variables. In essence, key-value coding defines the patterns and method signatures that your application’s accessor methods implement.
Implementing key-value coding compliant accessors in your application is an important design prin-ciple. Accessors help to enforce proper data encapsulation, isolatememory management to centralized locations, and facilitate integration with other technologies such as key-value observing, Core Data, Cocoa bindings, and scriptability.
Соответствующие методы определены в NSObject, поэтому каждый объект
поддерживает данную возможность.
[a setProductName:@"Washing Machine"];
C использованием KVC:	
[a setValue:@"Washing Machine" forKey:@"productName"];
Запись «ключ-значение» также позволяет прочитать значение переменной. Каждый раз, когда стандартная библиотека записывает данные в ваши объекты, она использует setValue:forKey:. Каждый раз, когда стандартная библиотека читает данные из ваших объектов, она использует valueForKey:. Например, библиотека СоrеData упрощает сохранение объектов в базе данных SQLite и их последующую загрузку. Для работы с пользовательским объектами, содержащими данные, используется запись «ключ- значение». 
double totalSalary = 0.0;
for (Employee *employee in employees) {
totalSalary += [employee.salary doubleValue];
}
double averageSalary = totalSalary / [employees count];
эквивалентно
[employees valueForKeyPath:@"@avg.salary"];

KVC Collection Operators allows actions to be performed on a collection using key path notation in valueForKeyPath:. Any time you see @ in a key path, it denotes a particular aggregate function whose result can be returned or chained, just like any other key path. Collection Operators fall into one of three different categories, according to the kind of value they return:
1.	Simple Collection Operators return strings, numbers, or dates, depending on the operator.
2.	Object Operators return an array. 
3.	Array and Set Operators return an array or set, depending on the operator.

Simple Collection Operators
@count
Returns the number of objects in the collection as an NSNumber.
@sum
Converts each object in the collection to a double, computes the sum, and returns the sum as an NSNumber.
@avg
Takes the double value of each object in the collection, and returns the average value as an NSNumber.
@max
Determines the maximum value using compare:. Objects must support comparison with one another for this to work.
@min
Same as @max, but returns the minimum value in the collection.

KVO
Еще одна реализация патерна наблюдатель. В этом случае наблюдатель следит не за событиями, а за конкретным свойством (property) объекта. Когда значение этого свойства меняется, наблюдателю приходит уведомление и он соответствующим образом реагируют.
По сравнению со многими другими языками реализация KVO в objective c радуют довольно простым синтаксисом. Так в коде наблюдателя достаточно написать: 
[company_a addObserver:self 
            forKeyPath:@"people" 
               options:NSKeyValueObservingOptionNew 
               context:nil];
И каждый раз когда в company_a будет изменяться значение переменной people наблюдатель будет уведомляться с помощью вызова метода 
observeValueForKeyPath:(NSString *)keyPath 
              ofObject:(id)object 
                change:(NSDictionary *)change 
               context:(void *)context 
и надо лишь реализовать код, который будет реагировать на уведомление.
 
Плюсы
•	Минимализм кода (достаточно написать всего лишь несколько строчек, чтобы полно-стью реализовать паттерн наблюдатель)
•	Возможность слежения за любыми свойствами(property) любых классов как написан-ными нами, так и чужими. Фактически внешние переменные всегда оформляются через свойства, что позволяет с легкостью следить любыми изменениями.
Недостатки
•	Первая и очень важная проблема — это заметное падение производительности при обильном использовании KVO. Не стоит писать код, где ваши объекты общаются в ос-новном через KVO. Рассматривайте KVO как вспомогательно средство для работы с чу-жим кодом, а не как основной инструмент.
•	Второй проблемой является необходимость очень аккуратно писать код при использо-вании KVO. Так как строковые идентификаторов не проверяются компилятором на ва-лидность, то это может привести к ошибкам при переименовании переменных. Также, KVO очень чувствительно к порядку добавления / удаления наблюдателей. Так, если наблюдатель пытается отписаться от наблюдаемого, на который наблюдатель в дан-ный момент не подписан, то происходит крэш. Если же, наоброт, наблюдатель не отпи-шется до того, как наблюдаемый будет уничтожен, то произойдет утечка памяти. Все это приводит к тому, что легко прострелить себе ногу при добавлении / удалении наблюдателей из разных мест кода. Наиболее простой способ обезопасить себя – это хранить в наблюдателе ссылку на объект наблюдения, метод присвоения которой опи-сан следующим образом:
- (void) setObservable:(id)observable {
[_observable addObserver:self 
                    forKeyPath:@"property" 
                             options:NSKeyValueObservingOptionNew 
                             context:nil];
    		_observable = observable;
    		[_observable removeObserver:self forKeyPath:@"property"];
}
Таким образом соотношение между добавлением и удалением строго равно единице и нет необходимости тщательно следить где именно добавляется / удаляется наблюде-ние. Вызов деструктора также больше не является проблемой, так как перед уничтоже-нием объекта в свойство запишется nil, попутно завершив наблюдение за объектом.
•	Always handle nil and other unusual values gracefully
•	Don't use accessors (or dot notation) in init or dealloc
Цепочка ответственности
Responder (ответчик) – объект, который может реагировать на события и обрабатывать их.
responderObject : UIResponder; // or NSResponder in MacOS
Цепочка ответственности (chain of responsibility) – позволяет вам передавать объекте по це-почке объектов-обработчиков, пока не будет найден необходимый объект обработчик. 
First responder -> next responder -> …
Первый ответчик – ответчик, получивший события первым (например view).
Когда использовать этот паттерн:
•	У вас более чем один объект-обработчик.

•	У вас есть несколько объектов обработчика, при этом вы не хотите специфицировать, который объект должен обрабатывать в даный момент времени.
Примеры:
[foo becomeFirstResponder];
[foo resignFirstResponder];
[foo respondsToSelector:@selector(methodName:)];

 


Анти-паттерны в объектно-ориентированном программировании
Базовый класс-утилита (BaseBean): Наследование функциональности из класса-утилиты вместо делегирования к нему
Вызов предка (CallSuper): Для реализации прикладной функциональности методу класса-потомка требуется в обязательном порядке вызывать те же методы класса-предка
Ошибка пустого подкласса (Empty subclass failure): Создание класса (в Perl), который не проходит «проверку пустоты подкласса» («Empty Subclass Test») из-за различного поведения по сравнению с классом, который наследуется от него без изменений
Божественный объект (God object): Концентрация слишком большого количества функций в одной части системы (классе)
Объектная клоака (Object cesspool): Переиспользование объектов, находящихся в непригодном для переиспользования состоянии
Полтергейст (Poltergeist): Объекты, чьё единственное предназначение — передавать информацию другим объектам
Проблема йо-йо (Yo-yo problem): Чрезмерная размытость сильно связанного кода (например, выполняемого по порядку) по иерархии классов
Одиночество (Singletonitis): Неуместное использование паттерна одиночка
Приватизация (Privatisation): Сокрытие функциональности в приватной секции (private), что затрудняет его расширение в классах-потомках
Френд-зона (Friend zone): Неуместное использование дружественных классов и дружественных функций в языке с++

Какая разница между использованием делагатов и нотификейшенов?
Уведомление инкапсулирует информацию о событиях, таких как получения фокуса окном или закрытие сетевого соединения. Объекты, которым необходимо знать об этих событиях, реги-стрируются в центре уведомлений, и при возникновении зарегистрированного события, центр уведомлений информирует все зарегистрированные объекты об событии.
Делегат может модифицировать операцию или отказаться от нее, нотификейшн – прямой приказ. 
Основные правила:
•	Центры оповещений не владеют своими наблюдателями. Если объект является наблюда-телем, он обычно удаляется из центра оповещений в своем методе dealloc:
- (void)dealloc {
[[NSNotificationCenter defaultCenter] removeObserver:self];
}
•	Объекты не владеют своими делегатами и источниками данных. Если вы создаете объект, который является делегатом или источником данных, он должен «попрощаться» в своем методе dealloc: 
- (void)dealloc {
[windowThatBossesMeAround setDelegate:nil];
[tableViewThatBegsForData setDataSource:nil];
}
•	Объекты не владеют своими приемниками. Если вы создаете объект, который является приемником, он должен обнулить указатель на приемник в своем методе dealloc:
- (void)dealloc {
[buttonThatKeepsSendingMeMessages setTarget:nil];
}

Делегат
Плюсы
•	Very strict syntax. All events to be heard are clearly defined in the delegate protocol.
•	Compile time Warnings / Errors if a method is not implemented as it should be by a delegate.
•	Protocol defined within the scope of the controller only.
•	Very traceable, and easy to identify flow of control within an application.
•	Ability to have multiple protocols defined one controller, each with different delegates.
•	No third party object required to maintain / monitor the communication process.
•	Ability to receive a returned value from a called protocol method. This means that a delegate can help provide information back to a controller.
•	Распределение кода,  переиспользование => слабосвязанные объекты. Мой объект ничего не знает о делегате, но отправляет ему сообщение.
Минусы
•	Many lines of code required to define: 1. the protocol definition, 2. the delegate property in the controller, and 3. the implementation of the delegate method definitions within the delegate itself.
•	Need to be careful to correctly set delegates to nil on object deallocation, failure to do so can cause memory crashes by calling methods on deallocated objects.
•	Although possible, it can be difficult and the pattern does not really lend itself to have multiple delegates of the same protocol in a controller (telling multiple objects about the same event)

Нотификейшн
Плюсы
•	Easy to implement, with not many lines of code.
•	Can easily have multiple objects reacting to the same notification being posted.
•	Controller can pass in a context (dictionary) object with custom information (userInfo) related to the notification being posted.
Минусы
•	No compile time to checks to ensure that notifications are correctly handled by observers.
•	Required to un-register with the notification center if your previously registered object is deallocated.
•	Not very traceable. Attempting to debug issues related to application flow and control can be very difficult.
•	Third party object required to manage the link between controllers and observer objects.
•	Notification Names, and UserInfo dictionary keys need to be known by both the observers and the controllers. If these are not defined in a common place, they can very easily become out of sync.
•	No ability for the controller to get any information back from an observer after a notification is posted.

Наблюдение
Плюсы
•	Can provide an easy way to sync information between two objects. For example, a model and a view.
•	Allows us to respond to state changes inside objects that we did not create, and don’t have ac-cess to alter the implementations of (SKD objects).
•	Can provide us with the new value and previous value of the property we are observing.
•	Can use key paths to observe properties, thus nested objects can be observed.
•	Complete abstraction of the object being observed, as it does not need any extra code to allow it to be observed.
Минусы
•	The properties we wish to observe, must be defined using strings. Thus no compile time warnings or checking occurs.
•	Re-factoring of properties can leave our observation code no longer working.
•	Complex “IF” statements required if an object is observing multiple values. This is because all observation code is directed through a single method.
•	Need to remove the observer when it is deallocated.
Runtime

  
The heart of this power is the Objective-C runtime, provided by libobjc. The Objective-C runtime is a collection of functions that provides the dynamic features of Objective-C. It includes such core func-tions
as objc_msgSend, which is called every time you use the [object message]; syntax. It also includes functions to allow you to inspect and modify the class hierarchy at runtime, including creating new classes and methods. Библиотека времени выполнения. Objective-C is a runtime-oriented language. Now the question that arises is, what is a runtime language? A runtime language is a language that decides what to implement in a function and other decisions during the runtime of the applications. Is Objective-C a runtime language? NO. It is a runtime-oriented language, which means that whenever it is possible, it defers decisions from compile and link time to the time when the code in the application is actually being executed. Функции и структуры Runtime-библиотеки определены в нескольких заголовочных файлах: NSObjCRuntime.h, objc.h, runtime.h и message.h. 
Система вызова методов в Objective-C реализована через посылку сообщений объекту. Каждый вызов метода транслируется в соответствующий вызов функции objc_msgSend:
// Вызов метода
[array insertObject:foo atIndex:1];
// Соответствующий ему вызов Runtime-функции
objc_msgSend(array, @selector(insertObject:atIndex:), foo, 1);
Вызов objc_msgSend инициирует процесс поиска реализации метода, соответствующего селекто-ру, переданному в функцию. Реализация метода ищется в так называемой таблице диспетче-ризации класса. Поскольку этот процесс может быть достаточно продолжительным, с каждым классом ассоциирован кеш методов. После первого вызова любого метода, результат поиска его реализации будет закеширован в классе. Если реализация метода не найдена в самом классе, дальше поиск продолжается вверх по иерархии наследования — в суперклассах данного класса. Если же и при поиске по иерархии результат не достигнут, в дело вступает механизм динамического поиска — вызывается один из специальных методов: resolveInstanceMethod или resolveClassMethod (динамическое переопределение методов).

Что такое указатель isa? Для чего он нужен?
Каждый объект Objective-C содержит в себе атрибут isa - указатель на class object для данного объекта. class object автоматически создается компилятором и существует как один экземпляр, на который через isa ссылаются все экземпляры данного класса. 
First there is a pointer to your class definition. Then each of your superclasses’ ivars (instance varia-bles) are laid out as struct properties, and then your class’s ivars are laid out as struct properties. This structure is called objc_object, and a pointer to it is called id:
typedef struct objc_object {
Class isa;
} *id;
The Class structure contains a metaclass pointer (more on that in a moment), a superclass pointer, and data about the class. The data of particular interest are the name, ivars, methods, properties, and protocols. Don’t worry too much about the internal structure of Class. There are public functions to access all the information you need. Каждый объект в Objective-C должен начинаться с Class isa, даже объекты классов. Так что же это такое?
Как следует из названия и типа, переменная isa указывает, какому классу принадлежит тот или иной объект. Каждый объект в Objective-C должен начинаться с isa, иначе runtime не будет знать, что же с ним делать. Вся информация о типе каждого конкретного объекта скрывается за этим крохотным указателем. Оставшийся кусок объекта, с точки зрения runtime, представ-ляет из себя просто огромный BLOB (массив двоичных данных), не дающий никакой информа-ции. Только лишь классы могут придать этому куску какой-то смысл.
 

Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?
Форвардинг
If you send a message to an object that does not handle that message, before announcing an error the runtime sends the object a forwardInvocation: message with an NSInvocation object as its sole argument—the NSInvocation object encapsulates the original message and the arguments that were passed with it. You can implement a forwardInvocation: method to give a default response to the message, or to avoid the error in some other way. As its name implies, forwardInvocation: is commonly used to forward the message to another object.

Как в C можно описать вызов метода [someObject someMethod:someArgument]? 
objc_msgSend(someObject, @selector(someMethod:), someArgument);
Что такое Run Loop?
Циклы выполнения – часть инфраструктуры, используемой для управления событиями при-бывающими асинхронно в потоке. Ждет данные от одного или нескольких источников, чтобы запустить код на исполнение. Циклы выполнения работают по мониторингу одного или не-скольких источников событий для потока. Как только события прибыли, система пробуждает поток и отправляет события на цикл выполнения, который затем передает их указанным об-работчикам. Если нет событий готовых быть обработанными, цикл выполнения ставит поток в режим сна.
Одна из опасностей потокового программирования, это конфликты ресурсов между несколь-кими потоками. Если несколько потоков пытаются использовать или модифицировать один и тот же ресурс в одно и то же время, то могут возникнуть проблемы. Один из способов решить проблему заключается в устранении общего ресурса в целом и убедиться, что каждый поток имеет свой собственный набор ресурсов, на котором он работает. Поддержание совершенно разных ресурсов, это не вариант, и придется, для синхронизации доступа к ресурсу прибегать к помощи замков, условий, атомарных операций, и других методов.
Замки обеспечивают грубую форму силы для защиты кода, который может быть выполнен только одним потоком одновременно. Наиболее распространенный тип блокировки взаимного исключения блокировки, также известный как мьютекс. Кроме замков, система обеспечивает поддержку для условий, которые обеспечивают надлежащую последовательность задач в рамках вашего приложения. Условие действует как привратник, блокируя определенный по-ток до приведения определенного состояния в значение истина. Когда это произойдет, поток освобождается и продолжает выполняться. И POSIX и Foundation framework оба оказывают прямую поддержку условий.
Что такое классы в Objective-C (структура классов)? 
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
Чем объект Objective-c отличается от структуры С, что такое структура в C? 
Структура – специальный тип данных языка C, который содержит в себе другие типы данных в одном блоке и группрует их под одним именем. 
struct point {
int x;
int у;
};
Объекты в ObjС представляют собой структуры cо своими данными и в которых имеется ссыл-ка isa на объект класса.
Вопрос о методах isKindOfClass, isMemberOfClass, etc…
Протокол <NSObject>, методы тестирования наследования:
1.	isKindOfClass:
2.	isMemberOfClass:
3.	respondsToSelector:
4.	conformsToProtocol:

isKindOfClass:
Возвращает логическое значение, указывающее, является ли приемник экземпляром заданно-го класса или экземпляром любого класса, который наследует от этого класса. (обязательный).
- (BOOL)isKindOfClass:(Class)aClass
Аргументы:
aClass Объект класс, представляющий Objective-C класс для тестирования.
Возвращаемое значение:
YES, если получатель является экземпляром aClass или экземпляром любого класса, который наследует от aClass, в противном случае NO.

isMemberOfClass:
Возвращает логическое значение, указывающее, является ли приемник экземпляром заданно-го класса (обязательный).
- (BOOL)isMemberOfClass:(Class)aClass
Аргументы:
aClass Объект класс, представляющий Objective-C класс для тестирования.
Возвращаемое значение:
YES, если получатель является экземпляром aClass, в противном случае NO.

respondsToSelector:
Возвращает логическое значение, указывающее, что приемник реализует или наследует ме-тод, который может реагировать на указанное сообщение. (обязательный).
- (BOOL)respondsToSelector:(SEL)aSelector
Аргументы:
aSelector Селектор, который идентифицирует сообщение.
Возвращаемое значение:
YES, если приемник реализует или наследует метод, который может реагировать на aSelector, в противном случае NO.

conformsToProtocol:
Возвращает логическое значение, указывающее, что приемник соответствует заданному про-токолу. (обязательный).
- (BOOL)conformsToProtocol:(Protocol *)aProtocol
Аргументы:
aProtocol Объект протокола, который представляет определенный протокол.
Возвращаемое значение:
YES, если приемник поддерживает aProtocol, в противном случае NO.
Рассмотрение:
Этот метод работает идентично методу класса conformsToProtocol: объявленному в NSObject. Это сделано для удобства, так чтобы вам не нужно было получать объект класса, чтобы узнать, может ли экземпляр ответить на заданный набор сообщений.
Тип id
1.	Что случится во время компиляции если мы посылаем сообщение объекту типа id?
2.	Что случится во время выполнения если этот метод существует?
3.	Что произойдет здесь? 
NSString *s = [NSNumber numberWithInt:3]; 
int i = [s intValue];

Переменная типа id фактически является указателем на произвольный объект. Для обозначе-ния нулевого указателя на объект используется константа nil (= NULL). При этом вместо id можно использовать и более привычное обозначение с явным указанием класса. В частности последнее позволяет компилятору осуществлять некоторую проверку поддержки сообщения объектами — если компилятор из типа переменной не может сделать вывод о поддержке объ-ектом данного сообщения, то он выдаст предупреждение. Тем самым язык поддерживает про-верку типов, но в нестрогой форме (то есть найденные несоответствия возвращаются как пре-дупреждения, а не ошибки). 
MyArray *array = [MyArray arrayWithObjects:@(1), @(2), nil];
Теперь вы видите, почему возвращаемый тип arrayWithObjects: должен быть id. Если бы это был (NSArray *), то подклассы потребует, чтобы они были приведены к необходимому классу.
 
 
Директивы компилятора
@implementation 
Определяет начало определения (реализации) класса или категории.

@class 
Используется для предварительного объявления класса. При использовании этой директивы класс помечается как известный, даже без загрузки заголовочного файла.

@protocol 
Используются для объявления протокола. Кроме того, протокол может адаптировать другие протоколы.
@required (по-умолчанию) 
Определяет методы, которые следуют после директивы как обязательные.
@optional
Определяет методы, которые следуют после директивы как необязательные. Классы, которые поддерживают протокол, могут сами решать — реализовывать эти методы или нет. Классы, которые используют необязательные методы протокола, должны делать проверку на суще-ствование.

@public
Определяет, что переменные экземпляра, следующие за директивой будут доступны публич-но. Публичные переменные могут быть прочтены и изменены с помощью следующей кон-струкции: someObject->aPublicVariable = 10;

@package 
Определяет, что переменные экземпляра, следующие за директивой будут публично доступны в библиотеке, которая определяет класс, но закрытыми за пределами этой библиотеки. Важное замечание, это справедливо только для 64-разрядных систем. На 32-разрядных системах имеет то же значение, что и @public

@protected (по умолчанию)
Определяет, что переменные экземпляра, следующие за директивой, будут доступны только для класса и его потомков.

@private 
Определяет, что переменные экземпляра, следующие за директивой, будут доступны только в пределах данного класса

@property
Определяет свойство, которое может быть использовано с помощью точечной нотации. За ди-рективой @property могут следовать необязательные круглые скобки, которые содержат до-полнительные ключевые слова (модификаторы), которые определяют поведение свойства. 

@synthesize
Дает указание компилятору, что необходимо автоматически сгенерировать сеттеры и геттеры для данных (разделенных запятой) свойств. Сеттеры и геттеры автоматически создаются со-гласно указанным в объявлении свойства директивам. Если переменные экземпляра называ-ются не так, как указано после директивы @property, вы можете соединить их с помощью знака равенства

@dynamic
Cообщает компилятору, что требуемые сеттеры и геттеры для данных свойств будут реализо-ваны вручную или динамически во время выполнения. При доступе к таким свойствам, ком-пилятор не будет выдавать предупреждений, даже если требуемые сеттеры и геттеры не реализованы. Вы можете использовать такие свойства, когда хотите, чтобы сеттеры и геттеры выполняли какой-то специфичный для вас код.

@try
Defines a block of code that will be tested to determine if an exception should be thrown.

@catch()
Defines a block of code for handling a thrown exception. Takes an argument, typically of type NSEx-ception, but can be of other types. 
@finally
Defines a block of code that gets executed whether an exception is thrown or not. This code will al-ways be executed. 
@throw
Throws an exception.
Earlier, we mentioned that you can throw exceptions from objects other than NSException instances, but that you should avoid doing so. The reason is that not every Cocoa framework catches exceptions thrown by objects other than NSExcep-tion. To ensure that Cocoa works right with your exceptions, you should throw NSException objects only. Think of it like the old saying that you don’t have to floss all your teeth, just the ones you want to keep. You’ll typically use @try, @catch, and @finally together in one structure. It goes a little something like this:
@try {
    // code you want to execute that might throw an exception.
}
@catch (NSException *exception)
{
    // code to execute that handles exception
}
@finally {
    // code that will always be executed. Typically for cleanup.
}

@synchronized 
Заключает блок кода в мьютекс. Обеспечивает гарантию того, что блок кода и объект блоки-ровки будут доступны только из одного потока в момент времени.

@autoreleasepool 
В тех приложения, в которых вы используете автоматический подсчет ссылок (ARC), вы долж-ны использовать @autoreleasepool как замену для NSAutoreleasePool. И вообще, @autoreleasepool примерно в 6 раз быстрее, чем NSAutoreleasePool, поэтому Apple рекомендует использовать его даже для не-ARC приложений. Кроме того, вы не должны определять переменную внутри блока @autoreleasepool и затем продолжать использовать ее после. Подобный код должен быть исклю-чен.

@selector 
Возвращает специальный тип селекторов SEL выбранного метода Objective-C. Генерирует пре-дупреждение компилятора, если метода не объявлен или не существует. Это имя метода зако-дированное специальным образом, используемым objective-c для быстрого поиска. Указание компилятору на селектор происходит при помощи директивы @selector(methodName)

@encode 
Возвращает кодировку типа.

@compatibility_alias 
Позволяет вам задать псевдоним для существующего класса. Первый параметр — имя псевдо-нима для имени класса, класса с таким именем не должно существовать. Второй параметр — имя существующего класса, для которого создается псевдоним.

@"some text"; 
Объявляет константный объект класса NSString. Для таких строк не требуется вызывать retain или release.

@import 
Модуль прекомпилированных заголовков, позволяющий экономить время по сравнению с компиляцией заголовков при #import. Не надо линковать фреймворк. 
#import <Cocoa/Cocoa.h> = @import Cocoa

Concurrency
Threads are subunits of processes, which can be scheduled independently by the operating system scheduler. Virtually all concurrency APIs are built on top of threads under the hood – that’s true for both Grand Central Dispatch and operation queues. You can either use the POSIX thread API, or the Objective-C wrapper around this API, NSThread, to create your own threads.
 

 
POSIX Threads
usually referred to as Pthreads, is a POSIX standard for threads defines an API for creating and ma-nipulating threads. Pthreads defines a set of C programming language types, functions and constants. It is implemented with a pthread.h header and a thread library. There are around 100 Pthreads procedures, all prefixed "pthread_" and they can be categorized into four groups:
•	Thread management - creating, joining threads etc.
•	Mutexes
•	Condition variables
•	Synchronization between threads using read/write locks and barriers
Implementations of the API are available on many Unix-like POSIX-conformant operating systems such as FreeBSD, NetBSD, OpenBSD, GNU/Linux, Mac OS X and Solaris. DR-DOS and Microsoft Win-dows implementations also exist.
NSThread 
is a simple Objective-C wrapper around pthreads. This makes the code look more familiar in a Cocoa environment. For example, you can define a thread as a subclass of NSThread, which encapsulates the code you want to run in the background.
GCD (Grand Central Dispatch) 
With GCD you don’t interact with threads directly anymore. Instead you add blocks of code to queues, and GCD manages a thread pool behind the scenes. GCD decides on which particular thread your code blocks are going to be executed on, and it manages these threads according to the available system resources. This alleviates the problem of too many threads being created, because the threads are now centrally managed and abstracted away from application developers. The other important change with GCD is that you as a developer think about work items in a queue rather than threads. This new mental model of concurrency is easier to work with. GCD exposes five different queues: the main queue running on the main thread, three background queues with different priorities, and one background queue with an even lower priority, which is I/O throttled. Furthermore, you can create custom queues, which can either be serial or concurrent queues. While custom queues are a powerful abstraction, all blocks you schedule on them will ultimately trickle down to one of the system’s global queues and its thread pool(s).
 
 
 
Плюсы
•	Визуально — он самый короткий и простой в реализации. Он возоможен с использова-нием блоков. Этот подход тоже очень гибкий (хотя отменять блок поставленный в оче-редь нельзя стандартными способами). В GCD можно настраивать приоритеты, блоки захватывают переменные из окружения блока.
NSOperationQueue
Operation queues are a Cocoa abstraction of the queue model exposed by GCD. While GCD offers more low-level control, operation queues implement several convenient features on top of it, which often makes it the best and safest choice for application developers. The NSOperationQueue class has two different types of queues: the main queue and custom queues. The main queue runs on the main thread, and custom queues are processed in the background. In any case, the tasks which are processed by these queues are represented as subclasses of NSOperation.
Плюсы
•	Можно для каждой очереди настраивать приоритет и количество одновременно выпол-няющихся операций. NSOperationQueue самостоятельно создает и поддерживает пул по-токов, в которых исполняются NSOperation. Так же NSOperation предоставляет возмож-ность отменять операции, приостанавливать всю очередь, запускать ее снова и много чего прочего.
NSObject instance methods
- (void)performSelector:(SEL)aSelector onThread:(NSThread *)thread withObject:(id)arg waitUntilDone:(BOOL)wait;
- (void)performSelector:(SEL)aSelector onThread:(NSThread *)thread withObject:(id)arg waitUntilDone:(BOOL)wait mo-des:(NSArray *)array;
- (void)performSelector:(SEL)aSelector withObject:(id)anArgument afterDelay:(NSTimeInterval)delay;
- (void)performSelector:(SEL)aSelector withObject:(id)anArgument afterDelay:(NSTimeInterval)delay inModes:(NSArray *)modes;
- (void)performSelectorInBackground:(SEL)aSelector withObject:(id)arg;
- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait;
- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait modes:(NSArray *)array;
Это один из самых простых и распространенных вариантов. Он требует только указать метод, который будет исполнять этот поток.
•	Because these methods are running on their own threads, you must create an autorelease pool for Cocoa objects. The main autorelease pool is associated with the main thread.
•	The methods must not return any values and must either take no arguments or have one object as an argument. In other words, the methods must have one of the following signatures:
- (void)myMethod;
- (void)myMethod:(id)myObject;
Плюсы
•	Он подходит для простых задач
Минусы
•	Нужно упаковывать все параметры для передачи, и бедные возможности по управле-нию очередностью, количеством одновременных задач, их приоритетом. На каждый вы-зов performSelectorInBackground будет создаваться отдельный поток. При быстром скролли-ровании большой таблицы можно довести число потоков до очень большой величины.
Run Loops
Run loops are not technically a concurrency mechanism like GCD or operation queues, because they don’t enable the parallel execution of tasks. However, run loops tie in directly with the execution of tasks on the main dispatch/operation queue and they provide a mechanism to execute code asyn-chronously. Run loops can be a lot easier to use than operation queues or GCD, because you don’t have to deal with the complexity of concurrency and still get to do things asynchronously.
A run loop is always bound to one particular thread. The main run loop associated with the main thread has a central role in each Cocoa and CocoaTouch application, because it handles UI events, timers, and other kernel events. Whenever you schedule a timer, use a NSURLConnection or call per-formSelector:withObject:afterDelay:, the run loop is used behind the scenes in order to perform these asyn-chronous tasks. Whenever you use a method which relies on the run loop, it is important to remember that run loops can be run in different modes. Each mode defines a set of events the run loop is going to react to. This is a clever way to temporarily prioritize certain tasks over others in the main run loop. A typical example of this is scrolling on iOS. While you’re scrolling, the run loop is not running in its default mode, and therefore, it’s not going to react to, for example, a timer you have scheduled before. Once scrolling stops, the run loop returns to the default mode and the events which have been queued up are executed. If you want a timer to fire during scrolling, you need to add it to the run loop in the NSRunLoopCommonModes mode. The main thread always has the main run loop set up and running. Other threads though don’t have a run loop configured by default. You can set up a run loop for other threads too, but you will rarely need to do this. Most of the time it is much easier to use the main run loop. If you need to do heavier work that you don’t want to execute on the main thread, you can still dispatch it onto another queue after your code is called from the main run loop. 
You can think of a Run Loop to be an event processing for-loop associated to a thread. This is provided by the system for every thread, but it's only run automatically for the main thread. Note that running run loops and executing a thread are two distinct concepts. You can execute a thread without running a run loop, when you're just performing long calculations and you don't have to respond to various events. If you want to respond to various events from a secondary thread, you retrieve the run loop associated to the thread by [NSRunLoop currentRunLoop]; and run it. The events run loops can handle is called input sources. You can add input sources to a run-loop.

In general, you should use the highest level of abstraction that suits your needs. This means that you should usually use NSOperationQueue instead of GCD, unless you need to do something that NSOperationQueue doesn't support.

Что такое мьютекс?
@synchronized
Замки являются одним из наиболее часто используемых инструментов синхронизации. Вы можете использовать замки для защиты критической секции вашего кода, который является сегментом кода, к которому разрешен доступ только одному потоку одновременно. Взаимоис-ключающая (или мьютекс) блокировка действует как защитный барьер вокруг ресурса. Мьютекс является одним из видов семафора, который предоставляет доступ одновременно только одному потоку. Если мьютекс используется и другой поток пытается получить его, что поток блокируется до тех пор пока мьютекс не освободится от своего первоначального вла-дельца. Если несколько потоков соперничают за одни и те же мьютексы, только одному будет разрешен к нему доступ.

Что такое deadlock?
Каждый поток захватывает ресурс и ждет, пока другой не осводит второй ресурс. Таким обра-зом, они ждут друг друга вечно. Deadlock is an unhappy condition in which two or more competing tasks are each waiting on the other to finish. You can observe this in real life when cars arrive simul-taneously at a four-way stop.
Что такое livelock?
Система не застревает, но занимается бесполезной работой. 
A livelock occurs when a request for an exclusive lock is repeatedly denied because a series of overlapping shared locks keep interfering. It is an endless loop in program execution. This could be a case when two threads exit allowing each other to write to or update record(s) in a database.

Что такое семафор?
Семафор позволяет выполнять какой-либо участок кода одновременно только конкретному количеству потоков. В основе семафора лежит счетчик, который и определяет, можно ли вы-полнять участок кода текущему потоку или нет. Если счетчик больше нуля — поток выполняет код, в противном случае — нет. Семафор в GCD представлен типом dispatch_semaphore_t. Для со-здания семафора существует функция dispatch_semaphore_create, которая принимает один аргумент — число потоков, которые могут одновременно выполнять участок кода.

Чем отличается dispatch_async от dispatch_sync?
Когда это возможно, асинхронное выполнение с использованием dispatch_async и dispatch_async_f функций предпочтительнее, чем синхронный вариант. При добавлении объек-та блока или функции в очередь, нет никакого способа узнать, когда этот код будет выпол-няться. В результате, добавляя блоки или функции асинхронно позволяет запланировать вы-полнение кода и продолжать делать другую работу из вызывающего потока. Это особенно важно, если вы планировании задачу из основного потока приложения, возможно, в ответ на некоторые пользовательские события.
Хотя вы должны добавлять задачи асинхронно по мере возможности, все же могут быть слу-чаи, когда вам нужно добавить задачу синхронно, чтобы предотвратить гонку условий или другие ошибки синхронизации. В этих случаях можно использовать функции dispatch_sync и dispatch_sync_f для добавления задачи в очередь. Эти функции блокируют текущий поток ис-полнения до завершения выполнения указанной задачи.
Важно: Вы никогда не должны вызывать функции dispatch_sync или dispatch_sync_f из задачи, которая выполняется в той же очереди, в которой вы планируете переход к функции. Это осо-бенно важно для последовательных очередей, которые гарантированно приведут к deadlock, но также следует избегать одновременных очередей.
Следующий прaимер показывает, как использовать блочные варианты для отправки задачи асинхронно и синхронно:
dispatch_queue_t myCustomQueue;
myCustomQueue = dispatch_queue_create("com.example.MyCustomQueue", NULL);
dispatch_async(myCustomQueue, ^{
printf("Сделайте некую работу здесь.\n");
});
printf("Первый блок может работать или может не работать.\n");
dispatch_sync(myCustomQueue, ^{
printf("Сделайте еще некую работу здесь.\n");
});
printf("Оба блока были завершены.\n");

Для чего при разработке под iOS использовать POSIX-потоки? 
Use POSIX calls if cross-platform portability is required. If you are writing networking code that runs exclusively in OS X and iOS, you should generally avoid POSIX networking calls, because they are harder to work with than higher-level APIs. However, if you are writing networking code that must be shared with other platforms, you can use the POSIX networking APIs so that you can use the same code everywhere.

Как многопоточность работает с UIKit?
One of the most common mistakes even experienced iOS/Mac developers make is accessing parts of UIKit/AppKit on background threads. It’s very easy to make the mistake of setting properties like image from a background thread, because their content is being requested from the network in the background anyway. Apple’s code is performance-optimized and will not warn you if you change properties from different threads.
For the most part, UIKit classes should be used only from an application’s main thread. This is particularly true for classes derived from UIResponder or that involve manipulating your application’s user interface in any way.

Выведется ли в дебагер «Hello world»? Почему? 
Нет, deadlock?
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
dispatch_sync(dispatch_get_main_queue(), ^{
NSLog(@"Hello world");
});
/* Another implementation */
return YES;
}

Что выведется в консоль?
NSObject *object = [NSObject new];
dispatch_async(dispatch_get_main_queue(), ^ {
NSLog(@"A %d", [object retainCount]);
dispatch_async(dispatch_get_main_queue(), ^ {
NSLog(@"B %d", [object retainCount]);
});
NSLog(@"C %d", [object retainCount]);
});
NSLog(@"D %d", [object retainCount]);

D 2
A 2
C 3
B 2

Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?
Cинхронизировать чтение/запись между потоками или нет. Atomic – thread safe.
Тут все сложнее и неоднозначнее, есть ряд способов как сделать threadsafe аксессоры к про-пертям.
Самый простой способ это сделать – добавить конструкцию @synchronized :
- (NSString *)foo {
    	@synchronized(self) {
       	return foo;
    	}
}
- (void)setFoo:(NSString)newFoo {
    	@synchronized(self) {
       	if (foo!=newFoo) {
          		[foo release];
          		foo = [newFoo retain];
       	}
    	}
}
Таким образом используя @synchronized мы лочим по ключу self доступ к foo, однако у такого метода есть очевидный недостаток, если в классе будет две переменные (или 100500) к кото-рым нужен одновременный доступ с разных потоков, то они будут лочиться и друг относи-тельно друга, т.к self для них один и тот же, в таких случаях нужно использовать другие мето-ды лока, как NSLock, NSRecursiveLock etc, постараюсь написать отдельную статью по мульти-поточности в ближайшее время.
Network
Преимущества и недостатки синхронного и асинхронного соединения?
NSURLConnection поддерживает синхронное и асинхронное выполнение запросов. Для выпол-нения синхронных запросов используется sendSynchronousRequest:returningResponse:error:
Использование такого запроса не рекомендуется. Работа приложения остановится, пока дан-ные не будут получены полностью, не произойдёт ошибка или истечет тайм-аут соединения. При использовании синхронного запроса есть и другие ограничения.
Для асинхронных запросов используется 
- (id)initWithRequest:(NSURLRequest *)request 
             delegate:(id <NSURLConnectionDelegate>)delegate 
либо 
initWithRequest:delegate:startImmediately:

Что означает http, tcp?
Transmission Control Protocol (TCP) (протокол управления передачей) — один из основных протоколов передачи данных Интернета, предназначенный для управления передачей данных в сетях и подсетях TCP/IP.
HTTP (англ. HyperText Transfer Protocol — «протокол передачи гипертекста») — протокол при-кладного уровня передачи данных (изначально — в виде гипертекстовых документов). Осно-вой HTTP является технология «клиент-сервер», то есть предполагается существование по-требителей (клиентов), которые инициируют соединение и посылают запрос, и поставщиков (серверов), которые ожидают соединения для получения запроса, производят необходимые действия и возвращают обратно сообщение с результатом. Этот протокол описывает взаимо-действие между двумя компьютерами (клиентом и сервером), построенное на базе сообщений, называемых запрос (Request) и ответ (Response). Каждое сообщение состоит из трех частей: стартовая строка, заголовки и тело. При этом обязательной является только стартовая строка.

Какие различия между HEAD, GET, POST, PUT? 
GET
Используется для запроса содержимого указанного ресурса. С помощью метода GET можно также начать какой-либо процесс. В этом случае в тело ответного сообщения следует включить информацию о ходе выполнения процесса.
Клиент может передавать параметры выполнения запроса в URI целевого ресурса после сим-вола «?»:

GET /path/resource?param1=value1&param2=value2 HTTP/1.1
Для выполнения GET запросов в Objective-C можно использовать NSURLConnection.
HEAD
Аналогичен методу GET, за исключением того, что в ответе сервера отсутствует тело. Запрос HEAD обычно применяется для извлечения метаданных, проверки наличия ресурса (валида-ция URL) и чтобы узнать, не изменился ли он с момента последнего обращения.
Заголовки ответа могут кэшироваться. При несовпадении метаданных ресурса с соответству-ющей информацией в кэше копия ресурса помечается как устаревшая.
POST
Применяется для передачи пользовательских данных заданному ресурсу. Например, в блогах посетители обычно могут вводить свои комментарии к записям в HTML-форму, после чего они передаются серверу методом POST и он помещает их на страницу. При этом передаваемые данные (в примере с блогами — текст комментария) включаются в тело запроса. Аналогично с помощью метода POST обычно загружаются файлы на сервер.
В отличие от метода GET, метод POST не считается идемпотентным[4], то есть многократное повторение одних и тех же запросов POST может возвращать разные результаты (например, после каждой отправки комментария будет появляться одна копия этого комментария).
Отправить POST-запрос не так тяжело как кажется. Достаточно подготовить «правильный» NSURLRequest.
NSString* params = @"param=value&number=1"; // задаем параметры POST запроса
NSURL* url = [NSURL URLWithString:@"http://server.com"]; // куда отправлять
NSMutableURLRequest* request = [NSMutableURLRequest requestWithURL:url];
request.HTTPMethod = @"POST";
request.HTTPBody = [params dataUsingEncoding:NSUTF8StringEncoding]; 
// следует обратить внимание на кодировку
// теперь можно отправить запрос синхронно или асинхронно
[NSURLConnection sendSynchronousRequest:request returningResponse:nil error:nil];
PUT
Применяется для загрузки содержимого запроса на указанный в запросе URI. Если по заданно-му URI не существовало ресурса, то сервер создаёт его и возвращает статус 201 (Created). Если же был изменён ресурс, то сервер возвращает 200 (Ok) или 204 (No Content). Сервер не должен игнорировать некорректные заголовки Content-*, передаваемые клиентом вместе с сообщением. Если какой-то из этих заголовков не может быть распознан или не допустим при текущих условиях, то необходимо вернуть код ошибки 501 (Not Implemented).
Фундаментальное различие методов POST и PUT заключается в понимании предназначений URI ресурсов. Метод POST предполагает, что по указанному URI будет производиться обработ-ка передаваемого клиентом содержимого. Используя PUT, клиент предполагает, что загружае-мое содержимое соответствует находящемуся по данному URI ресурсу.
Единый указатель ресурсов (англ. URL — Uniform Resource Locator) — единообразный лока-тор (определитель местонахождения) ресурса. URL — это стандартизированный способ записи адреса ресурса в сети Интернет.
URI (англ. Uniform Resource Identifier) — унифицированный (единообразный) идентифика-тор ресурса. URI — это символьная строка, позволяющая идентифицировать какой-либо ре-сурс: документ, изображение, файл, службу, ящик электронной почты и т. д. Прежде всего, речь идёт, конечно, о ресурсах сети Интернет и Всемирной паутины. 
URL это частный случай URI. Понятие URI включает в себя, помимо URL, например, ссылки на адреса электронной почты и т.п. URL указывает на Веб-ресурс, вроде сайта, страницы или кон-кретного файла, расположенных на интернет-серверах.

Что такое REST  архитектура?
REST (Representational state transfer) – это стиль архитектуры программного обеспечения для распределенных систем, таких как World Wide Web, который, как правило, используется для построения веб-служб. Термин REST был введен в 2000 году Роем Филдингом, одним из авто-ров HTTP-протокола. Системы, поддерживающие REST, называются RESTful-системами.
В общем случае REST является очень простым интерфейсом управления информацией без ис-пользования каких-то дополнительных внутренних прослоек. Каждая единица информации однозначно определяется глобальным идентификатором, таким как URL. Каждая URL в свою очередь имеет строго заданный формат. 
Вот как это будет выглядеть на примере:

GET /book/ — получить список всех книг
GET /book/3/ — получить книгу номер 3
PUT /book/ — добавить книгу (данные в теле запроса)
POST /book/3 — изменить книгу (данные в теле запроса)
DELETE /book/3 — удалить книгу

REST (сокр. от англ. Representational State Transfer — «передача репрезентативного состояния») — метод взаимодействия компонентов распределённого приложения в сети Интернет, при котором вызов удаленной процедуры представляет собой обычный HTTP-запрос (обычно GET или POST; такой запрос называют REST-запрос), а необходимые данные передаются в качестве параметров запроса. Этот способ является альтернативой более сложным методам, таким как SOAP, CORBA и RPC.
В широком смысле REST означает концепцию построения распределённого приложения, при которой компоненты взаимодействуют наподобие взаимодействия клиентов и серверов во Всемирной паутине.
Хотя данная концепция лежит в самой основе Всемирной паутины, но термин REST был введён Роем Филдингом, одним из создателей протокола HTTP, лишь в 2000 году. В своей диссерта-ции в Калифорнийском университете в Ирвайне он подвёл теоретическую основу под метод взаимодействия клиентов и серверов во Всемирной паутине, абстрагировав его и назвав «пе-редачей репрезентативного состояния». Филдинг описал концепцию построения распреде-лённого приложения, при которой каждый запрос (REST-запрос) клиента к серверу содержит в себе исчерпывающую информацию о желаемом ответе сервера (желаемом репрезентативном состоянии), и сервер не обязан сохранять информацию о состоянии клиента («клиентской сессии»).
Архитектура REST
Как необходимые условия для построения распределенных REST-приложений Филдинг пере-числил следующие:
1.	Клиент-серверная архитектура.
2.	Сервер не обязан сохранять информацию о состоянии клиента.
3.	В каждом запросе клиента должно явно содержаться указание о возможности кэширо-вания ответа и получения ответа из существующего кэша
4.	Клиент может взаимодействовать не напрямую с сервером, а с произвольным количе-ством промежуточных узлов. При этом клиент может не знать о существовании проме-жуточных узлов, за исключением случаев передачи конфиденциальной информации.
5.	Унифицированный программный интерфейс сервера. Филдинг приводил URI в качестве примера формата запросов к серверу, а в качестве примера ответа сервера форматы HTML, XML и JSON, различаемые с использованием идентификаторов MIME.
Филдинг указывал, что приложения, не соответствующие приведённым условиям, не могут называться REST-приложениями. Если же все условия соблюдены, то, по его мнению, прило-жение получит следующие преимущества:
•	надёжность (за счет отсутствия необходимости сохранять информацию о состоянии клиента, которая может быть утеряна);
•	производительность (за счет использования кэша);
•	масштабируемость;
•	прозрачность системы взаимодействия, особенно необходимую для приложений об-служивания сети;
•	простоту интерфейсов;
•	портативность компонентов;
•	легкость внесения изменений;
•	способность эволюционировать, приспосабливаясь к новым требованиям (на примере Всемирной паутины).

Как загрузить что-то из интернета? (NSURL, NSURLSession, NSURLConnection, NSURLRe-quest)
The iOS SDK allows us to connect to the Internet and retrieve and send data using the NSURLConnection class. JSON serialization and deserialization will all be done using the NSJSONSerialization class. XML parsing will be done using NSXMLParser, and the Twitter connectivity will be done using the Twitter framework.
The iOS 7 SDK brings along new classes that we can take advantage of in this chapter. One of these classes is the NSURLSession, which manages the connectivity to web serv‐ ices in a more thorough way than the NSURLConnection class does. В чем разница?
- (void)getImageFromURL:(NSString *)url {
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
        NSURL *myUrl = [NSURL URLWithString:url];
        NSData *data = [NSData dataWithContentsOfURL:myUrl];
        dispatch_sync(dispatch_get_main_queue(), ^{
            self.cityPicture = [UIImage imageWithData:data];
        });
    });
}

Парсинг (JSON, HTML, XML).
Парсинг – обработка данных, разбор входной последовательности с целью получения токенов. 
Токен – лексема, минимальная единица языка, имеющая самостоятельный смысл (имя, знак операции, ключевое слово)
Регулярные выражения – формальный язык поиска и осуществления манипуляций с подстро-ками в тексте, основанный на использовании метасимволов (символов-джокеров, англ. wildcard characters). По сути это строка-образец (англ. pattern, по-русски её часто называют «шаблоном», «маской»), состоящая из символов и метасимволов и задающая правило поиска. The NSRegularExpression class is used to represent and apply regular expressions to Unicode strings. An instance of this class is an immutable representation of a compiled regular expression pattern and various option flags. Example use the regular expression \\b(a|b)(c|d)\\b . This snippet creates a regular expression to match two-letter words, in which the first letter is “a” or “b” and the second letter is “c” or “d”. Specifying NSRegularExpressionCaseInsensitive means that matches will be case-insensitive, so this will match “BC”, “aD”, and so forth, as well as their lower-case equivalents.
NSError *error = NULL;
NSRegularExpression *regex = [NSRegularExpression regularExpressionWithPattern:@"\\b(a|b)(c|d)\\b"
                                                                       options:NSRegularExpressionCaseInsensitive
                                                                         error:&error];



Для парсинга XML в Objective-C существует класс NSXMLParser. О нахождении каких-либо эле-ментов парсер уведомляет свой делегат. Делегат должен следовать протоколу NSXMLParserDele-gate.
HTML (HyperText Markup Language) is a markup language (it’s in the name!) that tells browsers how to layout a web page. By its very nature, this content is in a hierarchy that defines where within the page a piece of information is to be displayed. You may also be aware of XML (eXtensible Markup Language). This also defines a hierarchy of information, and you may at this point be thinking that perhaps HTML is related to XML. You’d be right to think that, and also wrong!
There are two flavors of HTML: the one that is pure XML, and the original, where-it-all-started HTML. HTML is “sort of” an XML document, but with more relaxed rules.
 
Represent object in a stream, JSON better then HTML or XML.
JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language, Standard ECMA-262 3rd Edition - December 1999. JSON is a text format that is completely language independent but uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python, and many others. These properties make JSON an ideal data-interchange language.
{"menu": {
"id": "file",
  		"value": "File",
  		"popup": {
    			"menuitem": [
      			{"value": "New", "onclick": "CreateNewDoc()"},
      			{"value": "Open", "onclick": "OpenDoc()"},
      			{"value": "Close", "onclick": "CloseDoc()"}
    			]
  	    	}
}}

<menu id="file" value="File">
<popup>
<menuitem value="New" onclick="CreateNewDoc()" />
    		<menuitem value="Open" onclick="OpenDoc()" />
    		<menuitem value="Close" onclick="CloseDoc()" />
  	</popup>
</menu>

Data
Что такое Core Data?
Apple предоставляет гибкий фрэймворк для работы с хранимыми на устройстве данными — Core Data. Большинство деталей по работе с хранилищем данных Core Data скрывает, позволяя вам сконцентрироваться на том, что действительно делает ваше приложение веселым, уникальным и удобным в использовании. Не смотря на то, что Core Data может хранить данные в реляционной базе данных вроде SQLite, Core Data не является СУБД. По-правде, Core Data в качестве хранилища может вообще не использовать реляционные базы данных. Core Data скорее является оболочкой/фрэймворком для работы с данными, которая позволяет работать с сущностями и их связями (отношениями к другим объектами), атрибутами, в том виде, который напоминает работы с объектным графом в обычном объектно-ориентированном программировании. 

В каких случаях лучше использовать SQLite, а в каких Core Data?
Реляционная база данных — база данных, основанная на реляционной модели данных. Слово «реляционный» происходит от англ. relation (отношение). Для работы с реляционными БД применяют реляционные СУБД. Реля-ционная модель данных (РМД) — логическая модель данных, прикладная теория построения баз данных, кото-рая является приложением к задачам обработки данных таких разделов математики как теории множеств и ло-гика первого порядка. Термин «реляционный» означает, что теория основана на математическом понятии отно-шение (relation). В качестве неформального синонима термину «отношение» часто встречается слово таблица. Необходимо помнить, что «таблица» есть понятие нестрогое и неформальное и часто означает не «отношение» как абстрактное понятие, а визуальное представление отношения на бумаге или экране. Некорректное и нестрогое использование термина «таблица» вместо термина «отношение» нередко приводит к недопониманию. Наиболее частая ошибка состоит в рассуждениях о том, что РМД имеет дело с «плоскими», или «двумерными» таблицами, тогда как таковыми могут быть только визуальные представления таблиц. Отношения же являются абстракциями, и не могут быть ни «плоскими», ни «неплоскими». ORM – Object-relational mapping, объектно-реляционное отображение – преобразование данных между ООП и реляционными базами данных. SQL – Структурированный язык запросов (Structed Query Language) – является информационно-логическим языком, предназначенным для описания, изменения и извлечения данных, хранимых в реляционных базах данных (relation, отношение).

Целесообразность использования Core Data.
Core Data уменьшает количество кода, написанного для поддержки модели слоя приложения, как правило, на 50% - 70%, измеряемое в строках кода. Core Data имеет зрелый код, качество которого обеспечивается путем юнит-тестов, и используется ежедневно миллионами клиентов в широком спектре приложений. Структура была оптимизирована в течение нескольких версий. Она использует информацию, содержащуюся в модели и выполненяет функции, как правило, не работающие на уровне приложений в коде. Кроме того, в дополнение к отличной безопасности и обработке ошибок, она предлагает лучшую масштабируемость при работе с памятью, относительно любого конкурирующего решения. Другими словами: вы могли бы по-тратить долгое время тщательно обрабатывая Ваши собственные решения оптимизации для конкретной предметной области, вместо того, чтобы получить преимущество в производи-тельности, которую Core Data предоставляет бесплатно для любого приложения.

Когда нецелесообразно использовать Core Data
•	если планируется использовать очень небольшой объем данных. В этом случае проще воспользоваться для хранения Ваших данных объектами коллекций - массивами или словарями и сохранять их в .plist файлы.
•	если используется кросс-платформерная архитектура или требуется доступ к строго определенному формату файла с данными (хранилищу), например SQLite.
•	использование баз данных клиент-сервер, например MySQL или PostgreSQL.

SQL	
•	Максимальный объем хранимых данных базы SQLite составляет 2 терабайта.
•	Чтение из базы данных может производиться одним и более потоками, например не-сколько процессов могут одновременно выполнять SELECT. Однако запись в базу дан-ных может осуществляться, только, если база в данный момент не занята другим про-цессом.
•	SQLite не накладывает ограничения на типы данных. Любые данные могут быть занесе-ны в любой столбец. Ограничения по типам данных действуют только на INTEGER PRIMARY KEY, который может содержать только 64-битное знаковое целое.
SQLite версии 3.0 и выше позволяет хранить BLOB данные в любом поле, даже если оно объявлено как поле другого типа.
Обращение к SQLite базе из двух потоков одновременно неизбежно вызовет краш. Выхода два:
1.	Синхронизируйте обращения при помощи директивы @synchronized. Это если поздно менять архитектуру, как было у меня;
2.	Если задача закладывается на этапе проектирования, завести менеджер запросов на ос-нове NSOperationQueue. Он страхует от ошибок автоматически, а то, что делается авто-матически, часто делается без ошибок.

Что такое Managed object context?
Управляемый объект контекста служит в качестве шлюза для основной коллекции объектов, известных под общим названием сохранение стека, некиим посредником между объектами приложения и внешним хранилищем данных. В нижней части стека постоянное хранилище объекта.
 
Если вы хотите сохранить сделанные вами изменения, контекст гарантирует, что ваши объек-ты находятся в допустимом состоянии. Если это так, то изменения будут записаны в постоян-ное хранилище (или хранилища), добавит новые записи для объектов, созданных и удалит записи для объектов, которые удалены.

Что такое Persistent store coordinator?
В верхней части стека управляемый объект контекста, в нижней части стека постоянное хра-нилище объекта. Между управляемым объектом контекста и постоянным хранилищем объек-та есть постоянный координатор хранилища. По сути, постоянный координатор хранилища определяет стек. Координатор предназначен для представления фасада для управляемого контекстом объекта, так что группа постоянных хранилищ выглядит как единое совокупное хранилище. Управляемый объект контекста может создать граф объектов на основе объеди-нения всех хранилищ данных координатора. Координатор может быть связан только с одной управляемой объектной моделью. Если Вы хотите положить различные субъекты в различные хранилища, вы должны разделить вашу модель, определяя конфигурацию в управляемой модели объекта. 

Какие есть нюансы при использовании Core Data в разных потоках? Как синхронизиро-вать данные между потоками?
1.	Create a separate managed object context for each thread and share a single persistent store coordinator. This is the typically-recommended approach. 
2.	Create a separate managed object context and persistent store coordinator for each thread. This approach provides for greater concurrency at the expense of greater complexity (particularly if you need to communicate changes between different contexts) and increased memory usage.

Какие типы хранилищ поддерживает CoreData?
Persistent Store
•	SQLite
•	Binary
•	XML
Atomic Store (custom type)

Что такое ленивая загрузка (lazy loading)? Что ее связывает с CoreData? Опишите ситуа-ция когда она может быть полезной?
Для загрузки данных из БД в память приложения удобно пользоваться загрузкой не только данных об объекте, но и о сопряжённых с ним объектах. Это делает загрузку данных проще для разработчика: он просто использует объект, который, тем не менее вынужден загружать все данные в явном виде. Но это ведёт к случаям, когда будет загружаться огромное количе-ство сопряжённых объектов, что плохо скажется на производительности в случаях, когда эти данные реально не нужны. Паттерн Lazy Loading (Ленивая Загрузка) подразумевает отказ от загрузки дополнительных данных, когда в этом нет необходимости. Вместо этого ставится маркер о том, что данные не загружены и их надо загрузить в случае, если они понадобятся. Как известно, если Вы ленивы, то вы выигрываете в том случае, если дело, которое вы не де-лали на самом деле и не надо было делать.

Что такое fetch result controller?
Данные сами по себе может быть и представляют какую-либо ценность, но, обычно их нужно использовать. Одним из элементов представления данных в iOS служат таблицы (объекты класса UITableView), которые через объект класса NSFetchedResultsController можно привязать к CoreData. После этого при изменении данных в CoreData будет актуализироваться информа-ция в таблице. Так же, с помощью таблицы можно управлять данными в хранилище.
NSFetchedResultsController — контроллер результатов выборки. Создается, обычно один эк-земпляр на ViewController, но вполне может работать и без оного, внутрь которого помещается исключительно для того, что бы было проще привязать данные к виду. 

Тестирование
Unit Tests
Tests the smallest unit of functionality, typically a method/function (e.g. given a class with a particular state, calling x method on the class should cause y to happen). Unit tests should be focussed on one particular feature (e.g., calling the pop method when the stack is empty should throw an InvalidOperationException). Everything it touches should be done in memory; this means that the test code and the code under test shouldn't:
1.	Call out into (non-trivial) collaborators
2.	Access the network
3.	Hit a database
4.	Use the file system
5.	Spin up a thread
etc.
Any kind of dependency that is slow / hard to understand / initialise / manipulate should be stubbed/mocked/whatevered using the appropriate techniques so you can focus on what the unit of code is doing, not what its dependencies do.
In short, unit tests are as simple as possible, easy to debug, reliable (due to reduced external factors), fast to execute and help to prove that the smallest building blocks of your program function as intended before they're put together. The caveat is that, although you can prove they work perfectly in isolation, the units of code may blow up when combined which brings us to ...
Integration Tests
Integration tests build on unit tests by combining the units of code and testing that the resulting combination functions correctly. This can be either the innards of one system, or combining multiple systems together to do something useful. Also, another thing that differentiates integration tests from unit tests is the environment. Integration tests can and will use threads, access the database or do whatever is required to ensure that all of the code and the different environment changes will work correctly.
If you've built some serialization code and unit tested its innards without touching the disk, how do you know that it'll work when you are loading and saving to disk? Maybe you forgot to flush and dis-pose filestreams. Maybe your file permissions are incorrect and you've tested the innards using in memory streams. The only way to find out for sure is to test it 'for real' using an environment that is closest to production.
The main advantage is that they will find bugs that unit tests can't such as wiring bugs (e.g. an in-stance of class A unexpectedly receives a null instance of B) and environment bugs (it runs fine on my single-CPU machine, but my colleague's 4 core machine can't pass the tests). The main disadvantage is that integration tests touch more code, are less reliable, failures are harder to diagnose and the tests are harder to maintain.
Also, integration tests don't necessarily prove that a complete feature works. The user may not care about the internal details of my programs, but I do!
Functional Tests
Functional tests check a particular feature for correctness by comparing the results for a given input against the specification. Functional tests don't concern themselves with intermediate results or side-effects, just the result (they don't care that after doing x, object y has state z). They are written to test part of the specification such as, "calling function Square(x) with the argument of 2 returns 4".
Acceptance Tests
Acceptance testing seems to be split into two types:
Standard acceptance testing involves performing tests on the full system (e.g. using your web page via a web browser) to see whether the application's functionality satisfies the specification. E.g. "clicking a zoom icon should enlarge the document view by 25%." There is no real continuum of results, just a pass or fail outcome.
The advantage is that the tests are described in plain English and ensures the software, as a whole, is feature complete. The disadvantage is that you've moved another level up the testing pyramid. Ac-ceptance tests touch mountains of code, so tracking down a failure can be tricky.
Also, in agile software development, user acceptance testing involves creating tests to mirror the user stories created by/for the software's customer during development. If the tests pass, it means the software should meet the customer's requirements and the stories can be considered complete. An acceptance test suite is basically an executable specification written in a domain specific language that describes the tests in the language used by the users of the system.
Общие вопросы
Блоки 
http://rypress.com/tutorials/objective-c/blocks

Замыкание (англ. closure) в программировании — функция, в теле которой присутствуют ссылки на переменные, объявленные вне тела этой функции и не в качестве её параметров (а в окружающем коде). Говоря другим языком, замыкание — функция, которая ссылается на свобод-ные переменные в своём контексте. Замыкание, так же как и экземпляр объекта, есть способ представления функциональности и данных, связанных и упакованных вместе.
Лямбда-выражение (в программировании) — это специальный синтаксис для объявления анонимных функторов по месту их использования. Используя лямбда-выражения, можно объявлять функции в любом месте кода. Обычно лямбда-выражение допускает замыкание на лексиче-ский контекст, в котором это выражение использовано. Лямбда-выражения поддерживаются во многих языках программирования (C, Com-mon Lisp, Python, PHP, C#, F#, Visual Basic .NET, C++, Java и других).
Нестандартное расширение синтаксиса языков программирования C/C++/Objective-C, позво-ляющее инкапсулировать код и данные в один объект. Блоковые объекты это C-уровневые синтаксические функции. Они похожи на стандартные функции C, но в дополнение к исполня-емому коду они также могут содержать переменные привязанные к автоматической (стеку) или управляемой (куче) памяти. Поэтому блок может поддерживать набор состояний (дан-ные), которые он может использовать, чтобы повлиять на поведение при выполнении. Блоки особенно полезны в качестве обратного вызова, потому что блок несет как код, который будет выполняться на обратном вызове, так и данные, необходимые во время этого выполнения. 
 

As a local variable:
returnType (^blockName)(parameterTypes) = ^returnType(parameters) {...};

As a property:
@property (nonatomic, copy) returnType (^blockName)(parameterTypes);

As a method parameter:
- (void)someMethodThatTakesABlock:(returnType (^)(parameterTypes))blockName;

As an argument to a method call:
[someObject someMethodThatTakesABlock:^returnType (parameters) {...}];

As a typedef:
typedef returnType (^TypeName)(parameterTypes);
TypeName blockName = ^returnType(parameters) {...};

Обратный вызов
Ситуация, в которой код ожидает внешних событий, называется обратным вызовом. Для про-граммистов Objective-C существуют три основных формы обратного вызова. 
•	Приемник/действие: перед началом ожидания вы говорите: «Когда произойдет Х, отправь это конкретное сообщение этому конкретному объекту». Объект, получающий сообщение, называется приемником. Селектор сообщения и есть действие. 
•	Вспомогательные объекты: перед началом ожидания вы говорите: «Здесь имеется вспомо-гательный объект, поддерживающий твой протокол. Когда что-нибудь произойдет, от-правляй ему сообщения. Вспомогательные объекты часто называются делегатами или ис-точниками данных. 
•	Оповещения: имеется объект, называемый центром оповещений. Перед началом ожидания вы говорите ему: «Этот объект ожидает таких-то оповещений. При поступлении одного из них отправь объекту это сообщение». Когда происходит Х, объект отправляет оповещение центру оповещений, а последний пересылает его вашему объекту. 

Когда использовать блоки, делегаты, KVO и уведомления?
Block 
•	1–3 callbacks
•	Single observer
Delegate
•	Many callbacks
•	Single observer
•	Formal interface
KVO
•	Any number of observers
•	Just want to be notified of changes to state of an object
•	Simplistic updates, unrelated to behavior
Notifications
•	Multiple observers
•	Observer 'far away' from observee

Swift closures and functions
()->()
Closures in Swift are similar to blocks in C and Objective-C.
Closures are first-class objects, so that they can be nested and passed around (as do blocks in Objec-tive-C). In Swift, functions are just a special case of closures.

Defining a function:
You define a function with the func keyword. Functions can take and return none, one or multiple parameters (tuples).
Return values follow the -> sign.
func jediGreet(name: String, ability: String) -> (farewell: String, mayTheForceBeWithYou: String) {
return ("Good bye, \(name).", " May the \(ability) be with you.")
}

Calling a function:
let retValue = jediGreet("old friend", "Force")
println(retValue)
println(retValue.farewell)
println(retValue.mayTheForceBeWithYou)

Function types
Every function has its own function type, made up of the parameter types and the return type of the function itself.
For example the following function:
func sum(x: Int, y: Int) -> (result: Int) { return x + y }
has a function type of:
(Int, Int) -> (Int)
Function types can thus be used as parameters types or as return types for nesting functions.

Passing and returning functions
The following function is returning another function as its result which can be later assigned to a variable and called.
func jediTrainer () -> ((String, Int) -> String) {
func train(name: String, times: Int) -> (String) {
return "\(name) has been trained in the Force \(times) times"
  	}
  	return train
}
let train = jediTrainer()
train("Obi Wan", 3)

Variadic functions
Variadic functions are functions that have a variable number of arguments (indicated by ... after the argument's type) that can be accessed into their body as an array.
func jediBladeColor (colors: String...) -> () {
for color in colors {
println("\(color)")
  	}
}
jediBladeColor("red","green")

Closures
{()->() in}

Defining a closure:
Closures are typically enclosed in curly braces { } and are defined by a function type () -> (), where -> separates the arguments and the return type, followed by the in keyword which separates the closure header from its body.
{ (params) -> returnType in
  statements
}
An example could be the map function applied to an Array:
let padawans = ["Knox", "Avitla", "Mennaus"]
padawans.map({
(padawan: String) -> String in
"\(padawan) has been trained!"
})

Closures with known types:
When the type of the closure's arguments are known, you can do as follows:
func applyMutliplication(value: Int, multFunction: Int -> Int) -> Int {
return multFunction(value)
}

applyMutliplication(2, {value in
value * 3
})

Closures shorthand argument names:
Closure arguments can be references by position ($0, $1, ...) rather than by name
applyMutliplication(2, {$0 * 3})
Furthermore, when a closure is the last argument of a function, parenthesis can be omitted as such:
applyMutliplication(2) {$0 * 3}

How Do I Declare a Closure in Swift?
As a variable:
var closureName: (parameterTypes) -> (returnType)
As an optional variable:
var closureName: ((parameterTypes) -> (returnType))?
As a type alias:
typealias closureType = (parameterTypes) -> (returnType)
As a constant:
let closureName: closureType = { ... }
As an argument to a function call:
func({(parameterTypes) -> (returnType) in statements})
As a function parameter:
array.sort({ (item1: Int, item2: Int) -> Bool in return item1 < item2 })
As a function parameter with implied types:
array.sort({ (item1, item2) -> Bool in return item1 < item2 })
As a function parameter with implied return type:
array.sort({ (item1, item2) in return item1 < item2 })
As the last function parameter:
array.sort { (item1, item2) in return item1 < item2 }
As the last parameter, using shorthand argument names:
array.sort { return $0 < $1 }
As the last parameter, with an implied return value:
array.sort { $0 < $1 }
As the last parameter, as a reference to an existing function:
array.sort(<)
As a function parameter with explicit capture semantics:
array.sort({ [unowned self] (item1: Int, item2: Int) -> Bool in return item1 < item2 })
As a function parameter with explicit capture semantics and inferred parameters / return type:
array.sort({ [unowned self] in return item1 < item2 })

Заполнить строку буквами А, чтобы не делать миллионы итераций: 
NSString *str = @"a";
for (int i = 0; i< 5000000; i++) {
str = [str stringByAppendingString:@"a"];
}
Ответ
str =[@"" stringByPaddingToLength:5000000 withString:@"a" startingAtIndex:0];

Написать процедуру, инвертирующую массив символов (первый элемент должен стать последним, второй пердпоследним и т.д.)?  
1-ый способ
// myString is "hi"
NSMutableString *reversedString = [NSMutableString string];
NSInteger charIndex = [myString length];
while (charIndex > 0) {
    		charIndex--;
    		NSRange subStrRange = NSMakeRange(charIndex, 1);
[reversedString appendString:[myString substringWithRange:subStrRange]];
}
NSLog(@"%@", reversedString); // outputs "ih"
2-ой способ
array.reverseObjectEnumerator.allObjects;
3-ий способ
#include <string.h>
/* reverse: переворачивает строку s (результат в s) */ 
void reverse(char s[]) 
{
int c, i, j;

for (i = 0, j = strlen(s) - 1; i < j; i++, j--) {
с = s[i];
        	s[i] = s[j];
        	s[j] = c;
} 	
}

Поверхностное и глубокое копирование?
Поверхностное копирование — это просто создание нового указателя на те же самые байты в куче. Тоесть, в результате мы можем получить два объекта, которые указывают на одно и тоже значение. 
Глубокое копирование:
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

Пример копирования массива: 
initWithArray:copyItems:(NO or YES)

Отличие while от for? 
Единственное отличие while от for в том, что в них проверяется условие выполнения: ни объ-явить, ни изменить переменную в конструкции while нельзя. Поэтому чтобы выйти из цикла нужно изменять переменные внутри самого цикла так, чтобы условие стало ложным.

Протокол? Что такое абстрактный класс? Чем абстрактный класс отличается от интер-фейса?
Базовый класс, который не предполагает создания экземпляров. Абстрактные классы реали-зуют на практике один из принципов ООП — полиморфизм. Абстрактный класс может содер-жать (и не содержать) абстрактные методы и свойства. Абстрактный метод не реализуется для класса, в котором объявлен, однако должен быть реализован для его неабстрактных по-томков. Абстрактные классы представляют собой наиболее общие абстракции, то есть имею-щие наибольший объём и наименьшее содержание.
В Objective-C есть родительский класс NSObject. В языке программирования он как точка в геометрии. Это идеальный класс: в нём нет ничего лишнего, он ничего конкретного делает, но из него можно создать всё что угодно. Такой вот кирпичик мироздания. 
Пример: «Примус» — может быть наследником абстрактного класса «Нагревательный при-бор»
Главное отличие класса от интерфейса — в том, что класс состоит из интерфейса и реализации. 
Язык Objective-C содержит полноценную поддержку протоколов (это аналог интерфейса в Java и абстрактного класса в C++, который также иногда принято называть интерфейсом). Прото-кол представляет собой просто список описаний методов. Объект реализует протокол, если он содержит реализации всех методов, описанных в протоколе. Абстрактные классы могут со-держать в себе реализацию некоторых методов, интерфейсы содержат только прототипы. 
Однажды кто-то сказал: «То, что ты есть, и то, что ты делаешь – не одно и то же». Это утверждение справедливо и для объектов: класс объекта не всегда совпадает с его ролью в ра-ботающей системе. Например, объект может быть экземпляром NSМutаblеАrrау, тогда как в приложении он может обеспечивать управление очередью заданий печати. Действительно хо-рошо написанный класс имеет более общую природу, которая не ограничивается его ролью в одном конкретном приложении. Это позволяет по разному использовать экземпляры данного класса (полиморфизм). Мы уже говорили о том, как определить класс. Возможно ли определить роль? В определенной степени для определения роли можно использовать конструкцию @protocol.

Какие существуют root классы в iOS? Для чего нужны root классы?
NSObject, NSProxy
A root class inherits from no other class and defines an interface and behavior common to all objects in the hierarchy below it. All objects in that hierarchy ultimately inherit from the root class. A root class is sometimes referred to as a base class. The root class of all Objective-C classes is NSObject, which is part of the Foundation framework. All objects in a Cocoa or Cocoa Touch application ultimately inherit from NSObject. This class is the primary access point whereby other classes interact with the Objective-C runtime. It also declares the fundamental object interface and implements basic object behavior, including introspection, memory management, and method invocation. Cocoa and Cocoa Touch objects derive the ability to behave as objects in large part from the root class. The Foundation framework defines another root class, NSProxy, but this class is rarely used in Cocoa applications and never in Cocoa Touch applications.

Чем категория отличается от расширения (extention, неименованная категория)?
Категория позволяет расширить функционал класса. При этом не требуется исходников класса и добавленные методы автоматически становятся доступными всем классам, унаследованным от изменяемого. Категория имеет свое имя, список методов и имя класса, который она расши-ряет. 
Описание категории имеет следующий вид:
#import "ClassName.h"
@interface ClassName (CategoryName)
объявление методов
@end
Реализация категории выглядит следующим образом:
#import "CategoryName.h"
@implementation ClassName (CategoryName)
реализация методов
@end
Что делают категории?
1.	Позволяют разбить определение класса по нескольким файлам. В идеале класс должен выполнять одну конкретную роль, но иногда это не так, например в случае реализации фасада и некоторых других шаблонов. В этом случае удобно описать его в нескольких файлах
2.	Позволяют действительно элегантно добавить отсутствующую функциональность к существующему классу
3.	Создают опережающие ссылки для закрытых методов
4.	Позволяют добавление неформального протокола
Подводные камни
•	Невозможность добавления переменных
•	Возможная коллизия имен с самим классом, поэтому необходимо использовать ориги-нальные префиксы в наименовании своих методов.
•	Невозможно вызвать [super method]; из категории
Расширение
Одна из разновидностей категорий. Они по сути являются категориями с тем отличием, что интерфейс расширения описывается в имплементации основного класса до @implementation, а реализация прописывается в основном в любом месте имплементации класса и не пишется название категории. В отличии от категорий, расширения используются для собственных классов для сокрытия части реализации. 
A class extension bears some similarity to a category, but it can only be added to a class for which you have the source code at compile time (the class is compiled at the same time as the class extension).
@interface SomeClass ()
- (void) anAdditionalMethod;
@end

Можно ли добавить ivar в категорию?
Директива @interface для категорий не может добавлять переменных экземпляра. Однако, она может определять, что категория поддерживает дополнительные протоколы.

Когда лучше использовать категорию, а когда наследование?
В отличие от наследования, категории не могут добавлять новые переменные в класс. Однако, вы можете переопределять существующие методы в классе, но должны быть очень осторож-ны. Запомните, что все изменения сделанные в классе через категории повлияют на все эк-земпляры данного объекта в программе.

Формальные и неформальные протоколы
Цели для которых используются протоколы:
•	Ожидание, что класс поддерживающий протокол выполнит описанные в протоколе функции
•	Поддержка протокола на уровне объекта, не раскрывая методы и реализацию самого класса (в противоположность наследованию)
•	В виду отсутствия множественного наследования - объединить общие черты нескольких классов
Формальные протоколы
Объявление формального протокола гарантирует, что все методы объявленные протоколом будут реализованы классом
Неформальные протоколы
Добавление категории к классу NSObject называется созданием неформального протокола. При работе с неформальными протоколами мы реализуем только те методы, которые хотим.
Узнать поддержевает ли класс какой либо метод можно с помощью селекторов
@selector(метод)
First *f = [[First alloc] init];
if ([f respondsToSelector:@selector(setName:)]) {
  	NSLog (@"Метод поддерживается");
}
Подводные камни
•	[NSObject self] may return a class, or an object
•	[NSObject super] is undefined

Есть ли приватные или защищенные методы в Objective-C?
Нет. Использовать расширение.
Для имитации private методов с помощью расширения, нужно в .m файле, перед @implementation добавить безымянную категорию. Для класса Something ее определение бу-дет выглядеть как @interface Something () ... @end. Стоит обратить особое внимание на пустые скобки — они показывают, что мы определяем именно безымянную категорию. После этого, мы можем добавлять в категорию методы, которые будут для нас считаться private. За счет то-го, что категория безымянная, имплементация данных методов может находиться рядом с им-плементацией основных методов в разделе @implementation .. @end и нет необходимости со-здавать отдельные разделы для имплементации категорий. А за счет того, что она находится в .m файле, которые никто не подключает через #import (вы ведь их не подключаете, да?), ви-димость методов для автодополнения ограничена текущим файлом. Конечно, послать объекту это сообщение извне все равно возможно, но от случайного вызова вы точно застрахованы.

Что не так с этим кодом? Зачем нужны инициализаторы? [[[SomeClass alloc] init] init];
У тебя есть класс A, который имеет поле NSString *b и в ините ты делаешь _b = @"somestring"; Стринг b не хранится в памяти выделенной под A – в этой памяти хранится лишь ссылка на b, а сам объект создается во вне. При повторном ините соответственно стринг просто пересоздастся не стерев старый и получим утекший стринг. Вообще, такая ситуация есть далеко не везде, и далеко не всегда вызовет проблемы. Но кастомные повторные инициализации реально могут вызывать утечки памяти зависит от конкретного типа объекта. Двойной инит может вызвать утечку. А может не вызвать. Каждый конкретный класс - отдельный вопрос. Я бы на собеседовании ответил - в каких случаях и для какого класса вы собираетесь вызывать двойную инициализацию?
Класс NSObject содержит метод с именем init. После выделения памяти новому экземпляру от-правляется сообщение init, чтобы экземпляр мог инициализировать собой переменные экзем-пляров реальными значениями. Таким образом, alloc выделяет память для объекта, а init гото-вит объект к работе. Использование init выглядит примерно так:
NSMutableArray *things = [[NSMutableArray alloc] init];
Следует учитывать, что init является методом экземпляра, который возвращает адрес инициа-лизированного объекта. Он обеспечивает инициализацию NSObject.

Что такое назначеный инициализатор (designated initializer), напишите любой элемен-тарный инициализатор, почему он так выглядит? if (self  = [super...]) 
Класс содержит только один основной инициализатор. Если класс содержит другие инициали-заторы, то их реализация должна вызывать (прямо или косвенно) основной инициализатор. 
•	Если класс имеет несколько инициализаторов, только один из них должен выполнять ре-альную работу. Этот метод называется основным инцициалuзатором. Все остальные инициа-лизаторы должны вызывать основной инициализатор (прямо или косвенно). 
•	Основной инициализатор вызывает основной инициализатор суперкласса перед инициа-лизацией своих переменных экземпляров. 
•	Если имя основного инициализатора вашего класса отличается от имени основного иници-ализатора его супер класса, вы должны переопределить основной инициализатор суперк-ласса, чтобы он вызывал новый основной инициализатор. 
•	Если класс содержит несколько инициализаторов, четко укажите в заголовочном файле, какой из них является основным. 
Установившейся практикой в таком случае является выделение среди всех init-методов одного, называемого designated initializer. Все остальные init-методы должны вызывать его и только он вызывает унаследованный init метод.
- initWithName: (const char *) theName {  // designated initializer 
[super init];                       // call inherited method
name = strdup(theName);
}
- init {
return [self initWithName:@"name"];
}

Какой метод вызовется: класса A или класса B? Как надо изменить код, чтобы вызвался метод класса A?
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
A *a = [B new]; //Вызовется метод класса B. A *a = [A new]; ???
[a someMethod]; 
}
@end

Что выведется в консоль? Почему?
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
При касте из NSUInteger в BOOL проверяется на равенство нулю последний несущий байт чис-ла, который равен нулю, если число кратно 256.

Как работают push нотификации?
iOS-приложения не могут долгое время находиться в фоновом режиме. В целях сохранения за-ряда батареи приложениям, работающим в фоне, разрешено выполнять ограниченный набор действий. Вместо того, чтобы беспрерывно проверять события или производить какие-либо действия в фоновом режиме, вы можете создать серверную сторону приложения, которая бу-дет выполнять эти действия. А когда наступит интересующее событие, серверная сторона сможет отправить приложению push-уведомление! Абсолютно любое push-уведомление мо-жет выполнять следующие три действия:
•	Показать короткое текстовое сообщение.
•	Воспроизвести короткий звуковой сигнал.
•	Установить число на бейдже иконки приложения.
 
APNS cервер – Apple Push Notification Server.

Memory warning
iOS 2.0 and later.
Your app never calls this method directly. Instead, this method is called when the system determines that the amount of available memory is low. You can override this method to release any additional memory used by your view controller. If you do, your implementation of this method must call the super implementation at some point.
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
Если на устройстве заканчивается память в центр уведомлений приходит сообще-ние UIApplicationDidReceiveMemoryWarningNotification, наш обьект может об этом узнать через уведомления и что-либо сделать, например почистить кеш или сохранить данные.

Как лучше всего загрузить UIImage c диска (с кеша)?
Кеширование уменьшает количество необходимых обращений к сети, улучшает впечатление от работы с программой во время полного отсутствия интернета или проблем с сетевым со-единением. После загрузки ответа сервера, его копия сохраняется в локальном кеше. В следу-ющий раз при посылке такого же запроса, ответ будет возвращен мгновенно, без обращения к сети. NSURLCache прозрачным для пользователя образом вернет закешированные данные. Для использования NSURLCache нужно установить значение синглтона sharedURLCache. Это можно сделать в методе application:didFinishLaunchingWithOptions:
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
NSURLCache *URLCache = [[NSURLCache alloc] 
initWithMemoryCapacity:4 * 1024 * 1024 
    diskCapacity:20 * 1024 * 1024 
                                           diskPath:nil];
[NSURLCache setSharedURLCache:URLCache];
}
NSArray *paths = NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES);
NSString *cachePath = [paths objectAtIndex:0];
NSURL *fileURL = [NSURL fileURLWithPath:[cachePath stringByAppendingPathComponent:@"Matsedl.pdf"]];

Какой контент лучше хранить в Documents, а какой в Cache?
Кеш - это специальный буфер (контейнер), содержащий информацию. Эта информация может быть запрошена с наибольшей вероятностью. Соответственно, доступ к этому буферу должен быть очень быстрым, он должен быть быстрее чем доступ к сети или к данным на жестком диске. В операционной системе iOS присутствует функция кэширования, но прямого доступа к данным в кэше нету. Для получения доступа следует использовать класс NSCache, о котором и пойдет речь в данном примере.
•	Only documents and other data that is user-generated, or that cannot otherwise be recreated by your application, should be stored in the <Application_Home>/Documents directory and will be automatically backed up by iCloud.
•	Data that can be downloaded again or regenerated should be stored in the <Application_Home>/Library/Caches directory. Examples of files you should put in the Caches directory include database cache files and downloadable content, such as that used by magazine, newspaper, and map applications.
•	Data that is used only temporarily should be stored in the <Application_Home>/tmp directory. Although these files are not backed up to iCloud, remember to delete those files when you are done with them so that they do not continue to consume space on the user’s device.
•	Use the "do not back up" attribute for specifying files that should remain on device, even in low storage situations. Use this attribute with data that can be recreated but needs to persist even in low storage situations for proper functioning of your app or because customers expect it to be available during offline use. This attribute works on marked files regardless of what directory they are in, including the Documents directory. These files will not be purged and will not be included in the user's iCloud or iTunes backup. Because these files do use on-device storage space, your app is responsible for monitoring and purging these files periodically.

Как из строки вытащить подстроку?
С помощью методов: substringToIndex:, substringFromIndex: и substringWithRange:. Можно так-же разделить строку на подстроки (основано на разделителе строки) методом componentsSeparatedByString:
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

NSCoding, archiving? 
NSCoder — это абстрактный класс который преобразует поток данных. Используется для архи-вации и разархивации объектов.
Протокол <NSCoding> позволяет реализовать архивирование или разархивирование данных. Например у нас есть обьект мы его можем сохранить, а при следующей загрузке приложения подгрузить обратно. Часто программе требуется хранить состояние объектов в файле для дальнейшего их полного либо частичного восстановления, а также работы с ними. Такой про-цесс называют сериализацией. Многие современные языки и фреймворки предоставляют для этого вспомогательные средства. Рассмотрим, что нам предоставляет Cocoa Framework для Objective-C.
Сериализованный объект – объект, преобразованный в поток байтов для сохранения в файле или передачи по сети. NS(M)Array, NS(M)Dictionary, NS(M)Data, NS(M)String, NSNumber, NSDate. Сохранить состояние объекта в Cocoa Framework можно двумя способами при помощи:
1.	архивации (archivation) 
2.	сериализации (serialization)
Каждый из них имеет свои области применения. Так, при помощи сериализации нельзя сохра-нить объект пользовательского класса. Рассмотрим подробнее оба способа. Протокол <NSCo-ding> объявляет два метода, которые должен реализовать класс, так что экземпляры этого класса могут быть закодированы и декодированы. Эта возможность обеспечивает основу для архивирования (где объекты и другие структуры хранятся на диске) и распространения (где объекты копируются в разные адресные пространства). 
encodeWithCoder:
Кодирует приемник с помощью данного архиватора. (обязательный)
- (void)encodeWithCoder:(NSCoder *)encoder
initWithCoder:
Возвращает объект инициализированный из данных в данном разархиваторе. (обязательный)
- (id)initWithCoder:(NSCoder *)decoder
Создание архивов
Самый простой способ создать архив - использовать метод archiveRootObject:toFile: архиватора. Этот метод класса создает временный экземпляр архиватора и записывает объект в файл.
MapView *myMapView;
result = [NSKeyedArchiver archiveRootObject:myMapView toFile:@"/tmp/MapArchive"];
Чтение архивов
Для чтения архивов, также как и для записи (см. выше), можно использовать 2 метода. 
Первый - простой и пригодный для большинства случаев - с использованием метода класса:
MapView *myMapView;
myMapView = [NSKeyedUnarchiver unarchiveObjectWithFile:@"/tmp/MapArchive"];
Второй метод предполагает создание экземпляра объекта NSKeyedUnarchiver.

Как работает UITableView?
UITableView : 
UIScrollView <NSCoding> : 
UIView <NSCoding> : 
UIResponder <NSCoding, UIAppearance, UIAppearanceContainer, UIDynamicItem> : 
NSObject

UITableViewController : 
UIViewController <UITableViewDelegate, UITableViewDataSource> : 
UIResponder <NSCoding, UIAppearanceContainer> : 
NSObject
 
 

Ячейки table view, которые больше не отображаются на экране, не выкидываются. Их можно адаптировать под повторное использование, указав идентификатор в процессе инициализа-ции. Когда ячейка table view, отмеченная для повторного использования, пропадает с экрана, table view помещает ее в очередь для повторного использования в дальнейшем. Когда объект table view dataSource запрашивает у table view новую ячейку и указывает идентификатор, table view сначала проверяет очередь ячеек для повторного использования на предмет наличия не-обходимой ячейки. Если ячейка table view не была обнаружена, то table view создает новую, передавая ее затем объекту dataSource.
UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:CellIdentifier forIndexPath:indexPath];

Константы, typedef, enum, #define
typedef используется для объявления нового типа данных – это команда компилятору и предпо-лагает символьный тип данных.
#define – команда препроцессору и может содержать числовые значения.

Переменные, значения которых не изменяются (как, например, математическая постоянная pi), Такие данные называются константами. В Objective-C существует два распространенных способа определения констант: 
•	#define 
•	глобальные переменные

#define M_PI 3.14159265358979323846264338327950288
Директива #define приказывает препропессору: «Каждый раз, когда ты встречаешь Х, замени его на У еще до того, как компилятор увидит код».

Вместо #define программисты Objective-C обычно используют для хранения постоянных зна-чений глобальные переменные. При написании масса NSLocale эта глобальная переменная встречалась в двух местах. В файле NSLocale.h переменная была объявлена примерно так
extern NSString const *NSLocaleCurrencyCode;

Ключевое слово соnst говорит о том, что указатель не будет изменяться в течение всего жиз-ненного цикла программы. Ключевое слово extern означает: «Я гарантирую, что это существу-ет, но оно определяется в другом файле». И действительно, файл NSLocale.m содержит строку следующего вида: 
NSString const *NSLocaleCurrencyCode = @"currency";

#define и глобальные переменные
Если для определения констант можно использовать как #define, так и глобальные перемен-ные (включая enum), почему программисты Objective-C обычно используют
глобальные переменные? Иногда глобальные переменные повышают быстродействие про-граммы. Например, при работе с глобальной переменной для сравнения строк можно исполь-зовать == вместо isEqual: (а математическая операция выполняется быстрее отправки сообще-ния). Кроме того, с глобальными переменными удобнее работать в отладчике. Используйте для констант глобальные переменные и enum, а не #define.

enum
Часто в программе требуется определить набор констант. Допустим, вы программируете блендер с пятью рабочими режимами. Ваш класс Blender содержит метод setSpeed:. Было бы хорошо, если бы тип аргумента указывал, что допустимыми являются только пять конкретных значений. Для этого в программе определяется перечисляемый тип, или перечисление:
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
Чтобы разработчикам не приходилось постоянно вводить enum BlenderSpeed, они часто опре-деляют сокращенную запись с использованием
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
Часто для программиста совершенно неважно, какими числами представлены пять скоростей - лишь бы они отличались друг от друга. Значения элементов перечисления можно не указы-вать, в этом случае компилятор сгенерирует их автоматически:
typedef enum {
BlenderSpeedStir,
BlenderSpeedChop,
BlenderSpeedLiquify,
BlenderSpeedPulse,
BlenderSpeedIceCrush
} BlenderSpeed;
 
 
Объявление структуры
Как правило, объявление структуры используется в программе многократно,
поэтому для типа структур обычно создается typedef - псевдоним для объявления типа, позво-ляющий использовать его как обычный тип данных.
typedef struct {
float heightInMeters;
int weightInKilos;
} Person;

Что такое awakeFromNib?
NSNibAwaking Protocol Reference
(informal protocol)
Prepares the receiver for service after it has been loaded from an Interface Builder archive, or nib file.
- (void)awakeFromNib;
An awakeFromNib message is sent to each object loaded from the archive, but only if it can respond to the message, and only after all the objects in the archive have been loaded and initialized. When an object receives an awakeFromNib message, it is guaranteed to have all its outlet instance variables set.
Note: During Interface Builder’s test mode, this method is also sent to objects instantiated from loaded palettes, which include executable code for the objects. It is not sent to objects created using the Classes display of the nib file window in Interface Builder.
An example of how you might use awakeFromNib is shown below. Suppose your nib file has two custom views that must be positioned relative to each other at runtime. Trying to position them at initialization time might fail because the other view might not yet be unarchived and initialized yet. However, you can position both of them in the nib file owner’s awakeFromNib method. In the code below, firstView and secondView are outlets of the file’s owner.
Когда объекты из .nib разархивированы:
 

Что происходит когода мы пытаемся вызвать метод у nil указателя? Разница между nil и Nil. 
На самом деле, в контексте указателей применим как NULL, так и 0, ввиду того что первый — не более чем макрос-обёртка для второго:
#define NULL ((void *)0)
nil это указатель на нулевой объект: 
#if !defined(nil)
#define nil (id)0
#endif
Но и это ещё не всё: в дополнение к четырём вышеперечисленным мнемоникам, Foundation определяет макрос Nil (не путать с nil) — нулевой указатель типа Class:
#if !defined(Nil)
#define Nil (Class)0
#endif
NSNull используется внутри фреймворка Foundation и некоторых других для того, чтобы обой-ти ограничение стандартных коллекций, вроде NSArray или NSDictionary, заключающееся в том, что они не могут содержать в себе значения nil.
•	0 = 0 Ноль — он везде ноль
•	NULL = (void *)0 Нулевой указатель в языке Си
•	nil = (id)0 Нулевой указатель на объект Objective-C
•	Nil = (Class)0 Нулевой указатель типа Class в Objective-C
•	NSNull = [NSNull null] Синглтон класса NSNull — обёртки над nil и Null
Иногда разработчики той или иной функции (метода) допускают возможность, что не все входные параметры могут быть заданы пользователем. Например, метод -capitalizedStringWithLocale: класса NSString принимает в качестве аргумента локаль (объект класса NSLocale), либо nil — в последнем случае при изменении регистра строки будет исполь-зоваться каноническая декомпозиция (NFD) Unicode-символов независимо от настроек локали на компьютере пользователя (то есть, данный метод будет эквивалентен методу -capitalizedString).
Инициализация и «опустошение» объектов (например, для того, чтобы сообщить об ошибке): 

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
В ответ на посылаемое ему сообщение nil не бросает исключение, а попросту игнорирует это сообщение. То есть, nil из Objective-C ведёт себя как "черная дыра". Это пустота. Это ничто. При посылке к nil-у любого сообщения, всё что вы получите назад - это nil. Не будет никаких ис-ключений, никаких возвращенных значений. Ничего. 

Что такое неформальный протокол?
Категория с описанными, но не реализованными методами называется неформальным прото-колом. Неформальные протоколы часто определяются для корневого класса NSObject, при этом они не имеют реализации в самом классе. Каждый подкласс будет отвечать на сообщения описанные в категории, но при этом будут делать что-то полезное только реализованные методы. Методы, по мере необходимости, могут быть реализованы в подклассах, при этом реализуемые методы должны быть объявлены в секции @interface.

В чем разница между NSString и char? (Что значит приставка NS в общем?)
Приставка NS это абревиатура от NextStep операционной системы на основе которой и создана часть MAC OS. Apple в свое время купил и использует до сих пор.
сhar *myCharPtr = "This is a string.";
//In memory: myCharPtr contains an address, e.g. |0x27648164|
//at address 0x27648164: |T|h|i|s| |i|s| |a| |s|t|r|i|n|g|.|\0|

NSString *myStringPtr = @"This is an NSString.";
//In memory: myStringPtr contains e.g. |0x27648164|
//at address 0x27648164: |Object data|length|You don't know what else|UTF-16 data|etc.|

Опишите иерархию классов от UIButton до NSObject. 
UIButton : UIControl : UIView : UIResponder : NSObject

Что такое контекст (context)? 
Все рисование происходит в контексте (context), который определяет, где происходит рисова-ние. Чтобы получить context используется Си-функция UIGraphicsGetCurrentContext. В iOS центр координат при рисовании находится в левом верхнем углу, а не в левом нижнем, как у Mac OS X.
- (void)drawRect:(CGRect)rect {
// Получим context 
CGContextRef context = UIGraphicsGetCurrentContext();
CGContextClearRect(context, rect); // Очистим context
CGContextSetRGBFillColor(context, 255, 0, 0, 1);
CGContextFillRect(context, CGRectMake(20, 20, 100, 100));
}
[NSArray arrayWithObjects: a, b, c, nil]; зачем nil вконце?
Чтобы закончить список объектов, которые содержит массив. Этим значением мы даем знать компилятору, что массив окончен.

Сработает ли таймер? Что нужно чтобы сработал?
	void startTimer(void *threadId) {
			[NSTimer scheduleTimerWithTimeInterval:10.0f  
			                                target:aTarget 
			                              selector:@selector(tick:) 
			                              userInfo:nil 
			                               repeats:NO];
	}
	pthread_create(&thread, NULL, startTimer, (void *)t);

Что такое xib и storyboard, в чем отличие, что лучше использовать?

Nib файл содержит интерфейс программы посредством xml (один экран). Это не просто храни-лище интерфейса программы, но и хранит связи между объектами, а также инициализирует многие из них без дополнительного кода. 
File's owner – объект, владеющий копией ниб файла. 
First Responder – первый реагирующий объект, с которым взаимодействует пользователь. 
Outlet – переменная–указатель, ссылающаяся на объект в ниб-файле. 
Action – связь объекта интерфейса с методами в классе контроллера.

StoryBoard
Вместо nib файла для каждого view controller, ваше приложение использует единый storyboard который включает в себя дизайн всех view controller и связей между ними.
Storyboard имеет массу преимуществ перед nib-ами. 
Плюсы:
•	Storyboard — лучшее понимание концепта работы всех экранов и связей. Проще следить когда все в одном, чем открывать множество nib.
•	Storyboard описывает переходы между разными экранами. Эти переходы называются “segue” (сегвей) и вы создаете их путем ctrl-перетаскивания с одного view controller на другой. Спасибо segue — теперь требуется меньше кода для написания UI.
•	Storyboards делают работу с table view много легче, с новыми фичами prototype cell and static cell. Вы можете проектировать table view почти полностью в storyboard editor, что значительно сокращает требуемый код.
Минусы:
•	Не все так гладко, конечно, и у storyboard есть ограничения. Storyboard Editor пока не такой мощный как Interface Builder, есть кое-что что IB может, а Storyboard Editor нет.
сториборд? - это структурное задание связи между ксибками. Например я обычно на сториборд накидываю несколько вьюшек, как хотят дизайнеры, причем половина вьюшек грузятся из соответ-ствующих ксибок, а половина генерятся программно. В результате 80 процентов правок вносятся в течении минуты в сториборде, еще 15 в течении 3 минут в ксибке, а те, которые требуют измене-ния кода - редкие и им простительно уделить побольше внимания
 

что такое void *? 
а что означает просто void?

в чем разница между void * и id?

что такое id? 
как определен id?
можно ли создать структуру и привести к id?

id vs instancetype

что значит root класс? 
можно ли создать свой root класс?
какие есть еще root классы кроме NSObject и NSProxy?

можно ли использовать NSObject вместо NSProxy?
если ответ «да», то зачем тогда нужен NSProxy?

как происходит выравнивание указателей на объекты в objc? 
с чем это связано? 
какие оптимизации с этим связаны при хранении данных?
почему нельзя делать свою реализацию?

что такое bridge и зачем это нужно?

все эти методы допустимы? если нет то какие и почему?
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

что такое мета-класс?

objc_msgSend, что это за функция? 
как это связано с [obj foo]? какие еще есть связанные функции?

что такое dispatch table?

как происходит отправка сообщения?
всегда ли сообщения отправляются с одинаковой скоростью?

что будет если метод не найден в dispatch table?

есть ли в objc приватные методы?
как протестировать метод, не объявленный в публичном интерфейсе

exception отправки сообщения, кто выбрасывает?
что такое NSInvocation. Привести пример использования

что такое swizzling?

можно ли сделать private ivar как property, через категорию?
какие проблемы могут быть?
как в категории сделать свою property?

target-action, передается селектор, как сделать так, чтобы по селектору был вызван не метод, а блок?

что такое селектор?

что такое блок? 
какие типы блоков бывают? 
от какого класса наследуются?

всегда ли использование self внутри блока означает retain cycle?

почему внутри блока используется неявное const?

как работает __block?

как происходит вызов блока?

внутри блока используется assert, какие проблемы возникают? 
как их устранить без выделения в отдельный метод?

что такое assert и когда использовать?

что такое __autoreleasing?

что такое autorelease pool?

что такое run loop?

как связаны NSTimer и run loop? 
как запустить таймер на отдельном потоке? 
что будет если запустить таймер и держать UIScrollView? 
как это исправить? 

как связаны run loop и autorelease pool?

почему в этом коде утечка памяти и как устранить?
    NSString *str;
        while (YES) {
            str = [NSString stringWithFormat:@"hello world"];
        }

какие типы управления памятью есть в objc?

garbage collection vs reference counting?

отличия ARC от MRC? 
как работает ARC? магически определяет когда удалять объект?
напишите реализацию сеттера на MRC

чем отличается weak от strong и почему так много runtime функций для этого?

почему weak невозможно использовать на некоторых классах? 
на каких именно? 
как быть в этом случае?

ARC, как работает dealloc? 
когда расставляются release сообщения для ivar?

причина выполнения true ветки? причина выполнения false ветки? от чего зависит результат?
  BOOL b = 1024;
        if (b) {
            NSLog(@"true");
        } else {
            NSLog(@"false");
        }

одинаковую ли память занимают эти структуры и почему так?
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

что такое union?

а сколько памяти занимают эти структура и что это вообще такое?
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

что такое volatile?

что такое inline функции?

в чем отличие потока от процесса?

NSThread vs pthread

сокет, как это связано с вопросами выше? 
tcp, udp когда что применять?

гонка потоков, методы синхронизации, защита критической секции, семафор, мьютекс, барь-ер, что это и зачем нужно?
что такое OSSpinLock?

как передавать данные между NSOperation?
когда операция отправленная в NSOperationQueue начинает выполняться, можно ли отло-жить выполнение?

как тестировать асинхронные методы?
как написать синхронную обертку для асинхронного метода?

что такое стек вызовов и как это работает?
в чем отличие стека от кучи?
int8_t matrix[2048][2024], допустимо ли?

рекурсивные функции и хвостовая рекурсия, любая ли рекурсия может быть хвостовой?

что происходит со счетчиком ссылок когда объект добавляется в array, dictionary, set? 
если нужно другое поведение, что использовать? 
можно ли узнать, какой объект сколько раз был добавлен в set? (bag)

как использовать свой класс как ключ?

в чем плюсы использования immutable? 
в чем минусы?
зачем нужен атрибут copy для property и какую проблему решает?

почему и как работает KVC? 
key-path, хаки для коллекций

зачем нужен NSMapTable, какие отличия от NSHashTable

проблемы при работе с KVO и как это все работает

frame, bounds, center, как все это между собой связано? 
как изменятся свойства, если применить поворот на 45º? 
как передвинуть все subviews на 3 pt вверх и влево?

отличие view от layer?

responder принцип работы
как отправить сообщение по responder chain?

как работают категории?
в какой момент происходит влияние на классы?
что будет если категории пересекутся?
зачем у категории есть имя?

зачем нужен NSCache? В чем от реализации кэша на NSDictionary?
поддерживает ли NSURLConnection протокол HTTP/2?

какая типизация у objc? Сильная/слабая, явная/не явная, статическая/динамическая?
в чем отличие QoS User-interactive и user-initiated?
в чем отличие nil/Nil/NULL/NSNull?

Задачи
Задача про банерокрутилку
Из заданного списка вывести поочередно, рандомно, а главное, без повторений, все его эле-менты.
import java.util.Random;
class Banner
{
	public static void main(String[] args)
	{
		Random r = new Random();
		int[] list = new int[100];// в угоду наглядности в дебри линкедлистов лезть не будем
		for (int i = 0; i < 100; ++i)
		{
			list[i] = i;
		}
		/*А теперь главное - логика алгоритма*/
		int index = 99;
		int number;
		while (index > 0)
		{
			number = r.nextInt(index);
			System.out.println(list[number]);
			list[number] = list[index];
			--index;
		}
	}
}
Теперь кратко и по сути, что здесь происходит. Пока в списке есть элементы, мы берем слу-чайное число в пространстве длины массива, выводим его, потом последний элемент ставим на место только что выведенного, а индекс длины уменьшаем на единицу, пока не останется ничего.

Задача на регулярное выражение
В системе авторизации есть следующее ограничение на формат логина: он должен начинаться с латинской буквы, может состоять из латинских букв, цифр, точки и минуса и должен закан-чиваться латинской буквой или цифрой. Минимальная длина логина — 1 символ. Максимальная — 20 символов.
BOOL loginTester(NSString* login) {
    NSError *error = NULL;
    NSRegularExpression *regex = [NSRegularExpression 
        regularExpressionWithPattern:@"\\A[a-zA-Z](([a-zA-Z0-9\\.\\-]{0,18}[a-zA-Z0-9])|[a-zA-Z0-9]){0,1}\\z"
        options:NSRegularExpressionCaseInsensitive error:&error];
    // Здесь надо бы проверить ошибки, но если регулярное выражение оттестированное и 
    // не из пользовательского ввода - можно пренебречь.
    NSRange rangeOfFirstMatch = [regex rangeOfFirstMatchInString:login options:0 range:NSMakeRange(0, [login length])];
    return (BOOL)(rangeOfFirstMatch.location!=NSNotFound);
}

Метод, возвращающий N наиболее часто встречающихся слов во входной строке.
-(NSArray*)mostFrequentWordsInString:(NSString*)string count:(NSUInteger)count {
    // получаем массив слов.
    // такой подход для человеческих языков будет работать хорошо.
    // для языков, вроде китайского, или когда язык заранее не известен, 
    // лучше использовать enumerateSubstringsInRange с опцией NSStringEnumerationByWords
    NSMutableCharacterSet *separators = [[NSCharacterSet whitespaceAndNewlineCharacterSet] mutableCopy];
    [separators formUnionWithCharacterSet:[NSCharacterSet punctuationCharacterSet]];
    NSArray *words = [string componentsSeparatedByCharactersInSet:separators];
    
    NSCountedSet *set = [NSCountedSet setWithArray:words];
    
    // тут бы пригодился enumerateByCount, но его нет.
    // будем строить вручную
    NSMutableArray *selectedWords = [NSMutableArray arrayWithCapacity:count];
    NSMutableArray *countsOfSelectedWords = [NSMutableArray arrayWithCapacity:count];
    
    for (NSString *word in set) {
        NSUInteger wordCount = [set countForObject:word];
        NSNumber *countOfFirstSelectedWord = [countsOfSelectedWords count] ? 
            [countsOfSelectedWords objectAtIndex:0] : nil; // в iOS 7 появился firstObject
        if ([selectedWords count] < count || wordCount >= [countOfFirstSelectedWord unsignedLongValue]) {
            NSNumber *wordCountNSNumber = [NSNumber numberWithUnsignedLong:wordCount];
            NSRange range = NSMakeRange(0, [countsOfSelectedWords count]);
            NSUInteger indexToInsert = [countsOfSelectedWords indexOfObject:wordCountNSNumber inSortedRange:range 
                options:NSBinarySearchingInsertionIndex 
                usingComparator:^(NSNumber *n1, NSNumber *n2) 
            {
                NSUInteger _n1 = [n1 unsignedLongValue];
                NSUInteger _n2 = [n2 unsignedLongValue];
                if (_n1 == _n2)
                    return NSOrderedSame;
                else if (_n1 < _n2)
                    return NSOrderedAscending;
                else
                    return NSOrderedDescending;
            }];
            [selectedWords insertObject:word atIndex:indexToInsert];
            [countsOfSelectedWords insertObject:wordCountNSNumber atIndex:indexToInsert];
            // если слов уже есть больше чем нужно, удаляем то что с наименьшим повторением
            if ([selectedWords count] > count) {
                [selectedWords removeObjectAtIndex:0];
                [countsOfSelectedWords removeObjectAtIndex:0];
            }
        }
    }
    return [selectedWords copy]; 
    // можно было бы сразу вернуть selectedWords, 
    // но возвращать вместо immutable класса его mutable сабклас нехорошо - может привести к багам
}
// очень интересный метод для юнитестов: правильный результат может быть разным и зависит от порядка слов в строке.
Я бы именно такой подход и использовал, если бы мне нужно было решить эту задачу в реальном iOS приложении, при условии, что я понимаю, откуда будут браться входные данные для поиска и предполагаю, что размеры входной строки не будут больше нескольких мегабайт. Вполне разумное допущение для iOS приложения, на мой взгляд. Иначе на входе не было бы строки, а был бы файл. При реально больших входных данных прийдется попотеть над регулярным выражением для перебора слов, чтоб избавиться от одного промежуточного массива. Такое регулярное выражение очень зависит от языка — то что сработает для русского не проканает для китайского. А вот что делать со словами дальше — кроме прямолинейного алгоритма в голову ничего не приходит. Если бы нужно было выбрать одно наиболее часто встречающееся слово — это Fast Majority Voting. Но вся красота этого алгоритма в том, что он работает для выбора одного значения. Модификаций алгоритма для выбора N значений мне не известны. Самому модифицировать не получилось.

Используя NSURLConnection, напишите метод для асинхронной загрузки текстового документа по HTTP. Приведите пример его использования.
-(void)pullTextFromURLString:(NSString*)urlString completion:(void(^)(NSString*text))callBack {
    NSURLRequest *request = [NSURLRequest requestWithURL: [NSURL URLWithString:urlString] 
        cachePolicy:NSURLRequestUseProtocolCachePolicy timeoutInterval:60.0];
    [NSURLConnection sendAsynchronousRequest:request 
        queue:[NSOperationQueue mainQueue] 
        completionHandler:^(NSURLResponse *response, NSData *data, NSError *error) 
    {
        if (error) {
            NSLog(@"Error %@", error.localizedDescription);
        } else {
            // вообще, не мешало бы определить кодировку, чтоб не было неприятностей
            callBack( [[NSString alloc]initWithData:data encoding:NSUTF8StringEncoding] );
        }
    }];
}

Перечислите все проблемы, которые вы видите в приведенном ниже коде. Предложите, как их исправить.
NSOperation *operation = [NSBlockOperation blockOperationWithBlock:^{
    for (int i = 0; i < 1000; ++i) {
        if ([operation isCancelled]) return;
        process(data[i]);
    }
}];
[queue addOperation:operation];
Лично я вижу проблему в том, что переменная operation, «захваченная» блоком при создании блока, еще не проинициализирована до конца. Какое реально значение этой переменной будет в момент «захвата», зависит от того, используется ли этот код в методе класса или в простой функции. Вполне возможно, что сгенерированный код будет вполне работоспособен и так, но мне этот код не ясен. Как выйти из ситуации? Так:
NSBlockOperation *operation = [[NSBlockOperation alloc] init];
[operation addExecutionBlock:^{
    for (int i = 0; i < 1000; ++i) {
        if ([operation isCancelled]) return;
        process(data[i]);
    }
}];
[queue addOperation:operation];
Возможно, достаточно было бы просто добавить модификатор __block в объявление перемен-ной operation. Но так, как в коде выше — наверняка. Некоторые даже создают __weak копию переменной operation и внутри блока используют ее. Хорошо подумав я решил, что в данном конкретном случае, когда известно время жизни переменной operation и блока — это из-лишне. Ну и я бы подумал, стоит ли использовать NSBlockOperation для таких сложных кон-струкций. Разумных доводов привести не могу — вопрос личных предпочтений. 
Что еще с этим кодом не так? Я не люблю разных магических констант в коде и вместо 1000 использовал бы define, const, sizeof или что-то в этом роде. 
В длинных циклах в objective-c нужно помнить об autoreleased переменных и, если такие пере-менные используются в функции или методе process, а сам этот метод или функция об этом не заботится, нужно завернуть этот вызов в @autoreleasepool {}. Создание нового пула при каж-дой итерации цикла может оказаться накладным или излишним. Если не используется ARC, можно создавать новый NSAutoreleasePool каждые, допустим, 10 итераций цикла. Если исполь-зуется ARC, такой возможности нет. Кстати, это, наверное, единственный довод не использо-вать ARC. 
По коду не ясно, меняются ли данные в процессе обработки, обращается ли кто-то еще к этим данным во время обработки из других потоков, какие используются структуры данных, забо-тится ли сам process о монопольном доступе к данным тогда когда это нужно. Может понадо-биться позаботиться о блокировках.

Doh. Dear future googlers: of course operation is nil when copied by the block, but it doesn't have to be copied. It can be qualified with __block like so:
//THIS MIGHT LEAK! See the update below.
__block NSBlockOperation *operation = [NSBlockOperation blockOperationWithBlock:^{
   while( ! [operation isCancelled]){
      //do something...
   }
}];
UPDATE:
Upon further meditation, it occurs to me that this will create a retain cycle under ARC. In ARC, I be-lieve __block storage is retained. If so, we're in trouble, because NSBlockOperation also keeps a strong references to the passed in block, which now has a strong reference to the operation, which has a strong reference to the passed in block, which…
It's a little less elegant, but using an explicit weak reference should break the cycle:

NSBlockOperation *operation = [[NSBlockOperation alloc] init];
__weak NSBlockOperation *weakOperation = operation;
[operation addExecutionBlock:^{
   while(![weakOperation isCancelled]){
      //do something...
   }
}];

Anyone that has ideas for a more elegant solution, please comment!

Напишите запрос, возвращающий названия треков, скачанных более 1000 раз.
CREATE TABLE tracks (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  PRIMARY KEY (id)
)

CREATE TABLE track_downloads (
  download_id BIGINT(20) NOT NULL AUTO_INCREMENT,
  track_id INT NOT NULL,
  download_time TIMESTAMP NOT NULL DEFAULT 0,
  ip INT NOT NULL,
  PRIMARY KEY (download_id)
) 

Вот такой запрос справляется с задачей замечательно:
select name from tracks where id in 
    (select track_id from 
        (select track_id, count(*) as track_download_count from track_downloads 
            group by track_id order by track_download_count desc) 
where track_download_count > 1000)

Autolayout

"Use Auto Layout" determines whether a storyboard uses the Auto Layout fea-tures introduced in iOS 6 to automatically layout your interface using constraints.
"Use Size Classes" enables a new Xcode 6 feature called size classes that lets you use Auto Layout to build one interface for all devices and customize constraint constants, and certain views and constraints for different interface idioms while reusing the general layout. It saves the work and repetitiveness of having to build and maintain both MainiPhone and MainiPad storyboards.

External Changes
External changes occur when the size or shape of your superview changes.

Internal Changes
Internal changes occur when the size of the views or controls in your user interface change.

There are three main approaches to laying out a user interface. 
1.	you can programmatically lay out the user interface
2.	you can use autoresizing masks to automate some of the responses to external change
3.	you can use Auto Layout.

The frame defined the view’s origin, height, and width in the superview’s coordinate system.
















The layout of your view hierarchy is defined as a series of linear equations. Each constraint represents a single equation. Your goal is to declare a series of equations that has one and only one possible solution.










When using Auto Layout, the goal is to provide a series of equations that have one and only one possible solution. Ambiguous constraints have more than one possible solution. Unsatisfiable constraints don’t have valid solutions.
When calculating solutions, Auto Layout attempts to satisfy all the constraints in pri-ority order from highest to lowest. If it cannot satisfy an optional constraint, that con-straint is skipped and it continues on to the next constraint.
Some views have a natural size given their current content. This is referred to as their intrinsic content size.
The content hugging pulls the view inward so that it fits snugly around the content. The compression resistance pushes the view outward so that it does not clip the content.




		// Compression Resistance
		View.height >= 0.0 * NotAnAttribute + IntrinsicHeight
		View.width >= 0.0 * NotAnAttribute + IntrinsicWidth
		 
		// Content Hugging
		View.height <= 0.0 * NotAnAttribute + IntrinsicHeight
		View.width <= 0.0 * NotAnAttribute + IntrinsicWidth

These properties only take effect for views which define an intrinsic content size, otherwise there is no content size defined that could resist compression or be hugged.
The top and bottom layout guides represent the upper and lower edge of the visible content area for the currently active view controller.

Auto Layout does not operate on views’ frame, but on their alignment rect. It’s easy to forget the subtle difference, because in many cases they are the same.

Unsatisfiable layouts occur when the system cannot find a valid solution for the current set of constraints. Two or more required constraints conflict, because they cannot all be true at the same time.
When the system detects a unsatisfiable layout at runtime, it performs the following steps:
1.	Auto Layout identifies the set of conflicting constraints. 
2.	It breaks one of the conflicting constraints and checks the layout. The system continues to break constraints until it finds a valid layout. 
3.	Auto Layout logs information about the conflict and the broken constraints to the console.
As soon as you know about the error, the solution is typically very straightforward. Either remove one of the constraints, or change it to an optional constraint.

Ambiguous layouts occur when the system of constraints has two or more valid solutions. There are two main causes:
1.	The layout needs additional constraints to uniquely specify the position and loca-tion of every view. After you determine which views are ambiguous, just add constraints to uniquely specify both the view’s position and its size. 
2.	The layout has conflicting optional constraints with the same priority, and the sys-tem does not know which constraint it should break. 
Here, you need to tell the system which constraint it should break, by changing the priorities so that they are no longer equal. The system breaks the constraint having the lowest priority first.
When an ambiguous layout occurs at runtime, Auto Layout chooses one of the possible solutions to use. This means the layout may or may not appear as you expect. Furthermore, there are no warnings written to the console, and there is no way to set a breakpoint for ambiguous layouts.
There are a few methods you can call to help identify ambiguous layouts. All of the-se methods should be used only for debugging. Set a breakpoint somewhere where you can access the view hierarchy, and then call one of the following methods from the console:
		hasAmbiguousLayout
Available for both iOS and OS X. Call this method on a misplaced view. It returns YES if the view’s frame is ambiguous. Otherwise, it returns NO. 

		exerciseAmbiguityInLayout
Available for both iOS and OS X. Call this method on a view with ambiguous layout. This will toggle the system between the possible valid solutions. 

		constraintsAffectingLayoutForAxis:
Available for iOS. Call this method on a view. It returns an array of all the constraints affecting that view along the specified axis. 

		constraintsAffectingLayoutForOrientation
 Available for OS X. Call this method on a view. It returns an array of all the con-straints affecting that view along the specified orientation. 

		_autolayoutTrace
Available as a private method in iOS. Call this method on a view. It returns a string with diagnostic information about the entire view hierarchy containing that view. Ambiguous views are labeled, and so are views that have translatesAutoresizingMaskIntoConstraints set to YES.

Four of these are the Final size classes: 
1.	Compact-Compact 
2.	Compact-Regular
3.	Regular-Compact
4.	Regular-Regular

Base size classes: 
5.	Compact-Any
6.	Regular-Any
7.	Any-Compact
8.	Any-Regular
9.	Any-Any

It is typically easiest to work from the most general size class to the most specific. Select the default layout for your app, and design this layout in the Any-Any size class. Then modify the other Base or Final size classes as needed.

Compared to working with springs and struts, Auto Layout introduces two additional steps to the process before views can be displayed: 
•	updating constraints 
•	laying out views 
Each step is dependent on the one before; display depends on layout, and layout depends on updating constraints.

The first step – updating constraints – can be considered a “measurement pass.” It happens bottom-up (from subview to super view) and prepares the information needed for the layout pass to actually set the views’ frame. You can trigger this pass by calling setNeedsUpdateConstraints. Any changes you make to the system of constraints itself will automatically trigger this. However, it is useful to notify Auto Layout about changes in custom views that could affect the layout. Speaking of cus-tom views, you can override updateConstraints to add the local constraints needed for your view in this phase.

The second step – layout – happens top-down (from super view to subview). This layout pass actually applies the solution of the constraint system to the views by setting their frames (on OS X) or their center and bounds (on iOS). You can trigger this pass by calling setNeedsLayout, which does not actually go ahead and apply the layout immediately, but takes note of your request for later. This way you don’t have to worry about calling it too often, since all the layout requests will be coalesced into one layout pass.
To force the system to update the layout of a view tree immediately, you can call layoutIfNeeded/layoutSubtreeIfNeeded (on iOS and OS X respectively). This can be helpful if your next steps rely on the views’ frame being up to date. In your custom views you can override layoutSubviews/layout to gain full control over the layout pass. We will show use cases for this later on.

Finally, the display pass renders the views to screen and is independent of whether you’re using Auto Layout or not. It operates top-down and can be triggered by calling setNeedsDisplay, which results in a deferred redraw coalescing all those calls. Overriding the familiar drawRect: is how you gain full control over this stage of the display process in your custom views.

Since each step depends on the one before it, the display pass will trigger a layout pass if any layout changes are pending. Similarly, the layout pass will trigger updat-ing the constraints if the constraint system has pending changes.

It’s important to remember that these three steps are not a one-way street. Con-straint-based layout is an iterative process. The layout pass can make changes to the constraints based on the previous layout solution, which again triggers updating the constraints following another layout pass. This can be leveraged to create advanced layouts of custom views, but you can also get stuck in an infinite loop if every call of your custom implementation of layoutSubviews results in another layout pass.

