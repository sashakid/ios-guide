<img src="https://github.com/sashakid/ios-guide/blob/master/Images/ios_guide_logo.png">
### Оглавление

- [Основные понятия программирования](#основные-понятия-программирования)
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
- [Коллекции в Objective-C](#коллекции-в-objective-c)
	- [Разница между Set и Array](#разница-между-set-и-array)
	- [Difference between NSArray and CFArray](#difference-between-nsarray-and-cfarray)
	- [Enumeration](#enumeration)
	- [Filtering](#filtering)
	- [Sorting](#sorting)
- [Алгоритмы](#алгоритмы)
	- [Нотация «большое О»](#нотация-большое-о)
	- [Последовательный поиск](последовательный-поиск)
	- [Бинарный поиск](#бинарный-поиск)
	- [Последовательный поиск](#последовательный-поиск)
	- [Сортировка вставками](#сортировка-вставками)
	- [How to merge two sorted arrays into a sorted array](#how-to-merge-two-sorted-arrays-into-a-sorted-array)
	- [Рекурсивная функция](#рекурсивная-функция)
	- [Факториал](#факториал)
	- [Последовательность Фибоначчи](#последовательность-фибоначчи)
- [Программирование](#программирование)
- [Язык СИ](#язык-си)
	- [Битовые операции](#битовые-операции)
	- [Примеры битовых операций](#примеры-битовых-операций)
	- [Что такое указатель и ссылка и в чем разница](#что-такое-указатель-и-ссылка-и-в-чем-разница)
	- [Почему (NSError **) использует указатель на указатель](#почему-nserror-использует-указатель-на-указатель)
	- [How to return 2+ values from a function](#how-to-return-2+-values-from-a-function)
	- [What is the difference between char* const and const char*](#what-is-the-difference-between-char-const-and-const-char)
	- [Что значит n&(n – 1)](#что-значит-n-n–1)
- [ООП](#ооп)
	- [История ООП](#история-ооп)
	- [Основные понятия ООП: абстракция, инкапсуляция, наследование, полиморфизм](#основные-понятия-ооп)
	- [Другие понятия ООП](#другие-понятия-ооп)
	- [В чем плюсы и минусы ООП](#в-чем-плюсы-и-минусы-ооп)
- [Паттерны проектирования](#паттерны-проектирования)
	- [Что такое SOLID?](#что-такое-solid)
	- [Архитектурные паттерны](#архитектурные-паттерны)
		- [MVC](#mvc)
		- [MVP](#mvp)
		- [MVVM](#mvvm)
		- [VIPER](#viper)
	- [Порождающие шаблоны](#порождающие-паттерны)
		- [Abstract factory](#abstract-factory)
		- [Factory method](#factory-method)
		- [Lazy initialization](#lazy-initialization)
		- [Singleton](#singleton)
	- [Структурные шаблоны](#структурные-паттерны)
		- [Adapter](#adapter)
		- [Decorator](#decorator)
		- [Proxy](#proxy)
		- [Facade](#facade)
		- [Кластеры](#кластеры)
		- [Composite](#composite)
	- [Communication Patterns](#communication-patterns)
		- [Observer](#observer)
		- [Делегирование](#делегирование)
		- [KVC](#kvc)
		- [KVO](#kvo)
		- [Notification](#notification)
	- [Поведенческие шаблоны](#поведенческие-шаблоны)
		- [Chain of responsibility](#chain-of-responsibility)			
		- [The Target-Action Mechanism](#the-target-action-mechanism)
		- [Command](#command)
		- [Iterator](#iterator)
		- [Mediator](#mediator)
		- [Memento](#memento)
		- [State](#state)
	- [Анти-паттерны в объектно-ориентированном программировании](#анти-паттерны-в-объектно-ориентированном-программировании)
	- [Какая разница между использованием делагатов и нотификейшенов?](#какая-разница-между-использованием-делагатов-и-нотификейшенов?)
- [Xcode, фреймворки](#xcode-фреймворки)
	- [Core Foundation](#core-foundation)
	- [UIKit](#uikit)
	- [CFNetwork](#cfnetwork)
	- [QuartzCore](#quartzcore)
- [iOS](#ios)
	- [IPhone, resolution, pixels vs points](#iphone,-resolution,-pixels-vs-points)
	- [Файловая система iOS](#файловая-система-iOS)
	- [App lifecycle](#app-lifecycle)
	- [Возможные состояния программы](#возможные-состояния-программы)
	- [Жизненный цикл UIViewController](#жизненный-цикл-uiviewController)
	- [UIView](#uiview)
- [Objective-C](#objective-c)
	- [Transparent and opaque data types](#transparent-and-opaque-data-types)
	- [Toll-Free Bridged Types](#toll-free-bridged-types)
- [MEMORY MANAGEMENT](#memory-management)
	- [Память в стеке и в куче](#память-в-стеке-и-в-куче)
	- [Manual retain-release](#manual-retain-release)
	- [Automatic Reference Counting](#automatic-reference-counting)
	- [Модификаторы](#модификаторы)
	    - [Для свойств](#для-свойств)
	    - [Для переменных](#для-переменных)
	- [Что такое property](#что-такое-property)
	- [Написать сеттер и геттер для свойства, с ARC и без](#написать-сеттер-и-геттер-для-свойства,-с-arc-и-без)
	- [В каких случаях лучше использовать strong, а в каких copy для NSString? Почему?](#в-каких-случаях-лучше-использовать-strong,-а-в-каких-copy-для-nsstring?-почему?)
	- [autorelease vs release](#autorelease-vs-release)
	- [Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC](#что-делать,-если-проект-написан-с-использованием-arc,-а-нужно-использовать-классы-сторонней-библиотеки-написанной-без-arc)
	- [Основные темы управления памятью, такие как владение retain/release/autorelease](#основные-темы-управления-памятью,-такие-как-владение-retain/release/autorelease)
	- [Вопрос о циклах в графах владения, и почему свойства delegate обычно задаются как assign?](#вопрос-о-циклах-в-графах-владения,-и-почему-свойства-delegate-обычно-задаются-как-assign?)
	- [Что произойдет если сначала нажать на кнопку 1 а потом на кнопку 2?](#что-произойдет-если-сначала-нажать-на-кнопку-1-а-потом-на-кнопку-2?)
	- [Нужно ли ретейнить делегат для CAAnimation?](#нужно-ли-ретейнить-делегат-для-caanimation?)
	- [Что произойдет при исполнении следующего кода?](#что-произойдет-при-исполнении-следующего-кода?)
	- [Реализуйте следующие методы: retain, release, autorelease](#реализуйте-следующие-методы:-retain,-release,-autorelease)
	- [Если я вызову performSelector:withObject:afterDelay: объекту пошлется сообщение retain?](#если-я-вызову-performSelector:withObject:afterDelay:–объекту-пошлется-сообщение-retain?)
	- [Что происходит когда вы посылаете объекту сообщение autorelease?](#что-происходит-когда-вы-посылаете-объекту-сообщение-autorelease?)
	- [Объясните что такое retain count?](#объясните-что-такое-retain count?)
- [Runtime](#runtime)
	- [Что такое указатель isa? Для чего он нужен?](#что-такое-указатель-isa?-для-чего-он-нужен?)
	- [Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?](#что-происходит-с-методом-после-того,-как-он-не-нашелся-в-объекте-класса,-которому-его-вызвали?)
	- [Что такое классы в Objective-C, структура классов?](#что-такое-классы-в-objective-c,-структура-классов)?)
	- [Чем объект Objective-c отличается от структуры С, что такое структура в C?](#чем-объект-objective-c-отличается-от-структуры-c,-что-такое-структура-в-c?)
	- [Вопрос о методах isKindOfClass, isMemberOfClass](#вопрос-о-методах-iskindofclass,-ismemberofclass)
	- [Тип id](#тип-id)
	- [Директивы компилятора](#директивы-компилятора)
- [Multithreading](#multithreading)
	- [POSIX Threads](#posix-threads)
	- [NSThread](#nsthread)
	- [Run Loops](#run-loops)
	- [Для чего при разработке под iOS использовать POSIX-потоки?](#для-чего-при-разработке-под-ios-использовать-posix-потоки?)
- [Concurrency](#сoncurrency)
	- [GCD](#gcd)
	- [NSOperationQueue](#nsoperationqueue)
	- [NSObject instance methods](#nsobject-instance-methods)
	    - [Что такое мьютекс?](#что-такое-мьютекс?)
	    - [Что такое deadlock?](#что-такое-deadlock?)
	    - [Что такое livelock?](#что-такое-livelock?)
	    - [Что такое семафор?](#что-такое-семафор?)
	    - [Чем отличается dispatch_async от dispatch_sync?](#чем-отличается-dispatch_async-от-dispatch_sync?)
	    - [Как многопоточность работает с UIKit?](#как-многопоточность-работает-с-uikit?)
	    - [Выведется ли в дебагер «Hello world»? Почему?](#выведется-ли-в-дебагер-«hello-world»?-почему?)
	    - [Что выведется в консоль?](#что-выведется-в-консоль?)
    	- [Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?](#atomic-vs-nonatomic.-чем-отличаются?-как-вручную-переопределить-atomic/nonatomic-сеттер-в-не-arc-коде?)
- [Networking](#networking)
	- [Преимущества и недостатки синхронного и асинхронного соединения?](#преимущества-и-недостатки-синхронного-и-асинхронного-соединения?)
	- [Протоколы передачи данных](#протоколы-передачи-данных)
	- [Какие различия между HEAD, GET, POST, PUT?](#какие-различия-между-head,-get,-post,-put? )
	- [Что такое REST архитектура?](#что-такое-rest-архитектура?)
	- [Как загрузить что-то из интернета? NSURL, NSURLSession, NSURLConnection, NSURLRequest](#как-загрузить-что-то-из-интернета? nsurl, nsurlsession, nsurlconnection, nsurlrequest)
	- [Парсинг JSON, HTML, XML](#парсинг json, html, xml)
- [Data](#data)
	- [Что такое Core Data?](#что-такое-core-data?)
	- [Опишите стек Core Data](#опишите-стек-core-data)
	- [В каких случаях лучше использовать SQLite, а в каких Core Data?](#в-каких-случаях-лучше-использовать-sqlite,-а-в-каких-core-data?)
	- [Какие есть нюансы при использовании Core Data в разных потоках? Как синхронизировать данные между потоками?](#какие-есть-нюансы-при-использовании-core-data-в-разных-потоках?-как-синхронизировать-данные-между-потоками?)
	- [Какие типы хранилищ поддерживает CoreData?](#какие-типы-хранилищ-поддерживает-core-data?)
	- [Что такое ленивая загрузка? Что ее связывает с Core Data? Опишите ситуация когда она может быть полезной? Что такое faulting?](#что-такое-ленивая-загрузка?-что-ее-связывает-с-core-data?-опишите-ситуация-когда-она-может-быть-полезной?-что-такое-faulting?)
	- [Что такое fetch result controller?](#что-такое-fetch-result-controller?)
- [Тестирование](#тестирование)
- [Блоки](#блоки)
	- [When and why block captures self and when they don't?](#when-and-why-block-captures-self-and-when-they-don't?)
	- [Примеры объявления и использования блоков](#примеры-объявления-и-использования-блоков)
	- [В чем отличие блока от лямбды и замыкания](#в-чем-отличие-блока-от-лямбды-и-замыкания)
	- [Обратный вызов](#обратный-вызов)
	- [Когда использовать блоки, делегаты, KVO и уведомления?](#когда-использовать-блоки,-делегаты,-kvo-и-уведомления?)
	- [Swift closures and functions](#swift-closures-and-functions)
	- [Closures](#closures)
	- [How Do I Declare a Closure in Swift?](#how-do-i-declare-a-closure-in-swift?)
	- [Чем отличаются лямбда, замыкание и блок?](#чем-отличаются-лямбда,-замыкание-и-блок?)
- [Autolayout](#autolayout)
- [Swift](#swift)
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
	- [Напишите запрос, возвращающий названия треков, скачанных более 1000 раз](#напишите-запрос,-возвращающий-названия-треков,-скачанных-более-1000-раз)

***

# Основные понятия программирования

### Бит и байт
Информация –– мера разрешения неопределенности.
Бит (Binary digIT, bit – кусочек) выбран как мера неопределенности с двумя возможными состояниями: истина | ложь, да | нет, 1 | 0. Любые данные в компьютере представлены в виде последовательности битов. Цифровая информация хранится благодаря различию между разными величинами какой-либо физической характеристики (ток, напряжение) => чем больше велечин, которые нужно различать, тем меньше различий между смежными величинами => тем менее надежна память. В двоичной системе следует различать всего два состояния => это самый надеждный метод кодирования информации.
Байт — совокупность битов, обрабатываемая компьютером одномоментно. В современных вычислительных системах байт состоит из восьми битов и, соответственно, может принимать одно из 256 (`2^8 = 256`) различных значений (состояний, кодов).
### Память
Сверхоперативная, оперативная и внешняя. Некоторые регистры сверхоперативной памяти, в которые могут помещаться аргументы арифметических операций, находятся в ЦП. Также они используются для хранения текущих или следующих команд. Оперативная память служит для запоминания более постоянной информации. Каждая ячейка оперативной памяти имеет свой идентификатор (адрес) в массиве ячеек памяти. Самая маленькая ячейка имеет размер 8 бит (байт). Внешняя память служит для долговременного хранения информации, используется для хранения самих программ.
### Тип данных
Тип данных характеризует одновременно:
- множество допустимых значений, которые могут принимать данные, принадлежащие к этому типу;
- набор операций, которые можно осуществлять над данными, принадлежащими к этому типу.

Распространённые типы данных:
- Логический
- Целочисленный
- Числа с плавающей запятой
- Строковый
- Указатели

Тип данных указывает, как будут использоваться определенные наборы битов. Функция задает операции, выполняемые над данными. Структура служит для группировки порций информации. Указатели – для непрямой ссылки на информацию. Абстрактный тип данных – тип данных с доступом через интерфейс, реализация которого скрыта. Доступ к переменным – через операции, определенные в интерфейсе.

### Структура данных
Пространственное понятие: схема организации информации в компьютере. Множество элементов данных и множество связей между ними. От выбора структуры данных зависит производительность программы. Тип структуры данных определяет:

- Как хранятся данные в структуре (выделение памяти, представление данных)
- Множество допустимых значений, который принимает объект в структуре данных
- Множество операций, которые могут применяться к объекту

Операции над структурами данных – __CRUD__:
- CREATE
- READ
- UPDATE
- DELETE

Структура данных в ООП реализуется в виде классов, данные хранятся в переменных класса, системе предписаний соответстует набор методов класса.
- ПРОСТЫЕ БАЗОВЫЕ (числовые, символьные, логические, перечисление, интервал, указатели)
- СТАТИЧЕСКИЕ (вектор, массив, множество, запись, таблица)
- ПОЛУСТАТИЧЕСКИЕ (стек, очередь, дек, строка)
- ДИНАМИЧЕСКИЕ (связный список, граф, дерево)

### Алгоритмы
«Рецепт расчета» – метод, разработанный для решения задачи, пригодный для реализации в компьютерной программе. Сам алгоритм является абстракцией, но его представление – конкретно и может меняться в зависимости от архитектуры компьютера, языка программирования и т. д. Представление алгоритма конструируется из блоков – примитивов. Набор примитивов и правил, как комбинировать эти примитивы для воплощения более сложных идей организуют язык программирования. Примитив состоит из синтаксической и семантической части. Описание алгоритма на низком уровне – неудобно, поэтому используются абстракции для примитивов более высокого уровня, которые состоят из примитивов низкого. Итерационная структура – выполнение набора инструкций в циклическом режиме. Рекурсивная – каждая стадия повторения цикла реализуется как подзадача предыдущей стадии. Чтобы оценить производительность нужно подсчитать количество операций. Различают временную сложность и пространственную (используемая память).

`О` – (сложность в наихудшем случае), асимптотическая верхняя оценка количества операций => времени работы (худший вариант). При оценке берется количество операций, возрастающих быстрее всего.

`Ω` – сложность в лучшем случае

`Θ` – сложность в среднем, когда оценка `Ω = О`

Наилучшая оценка алгоритма – `О(1)`, константная, когда алгоритм без циклов и рекурсии.
### Язык программирования
Служит для точного описания абстрактных структур данных и алгоритмов. Компилятор транслирует текст программы на языке программирования в машинный код, связывая каждый идентификатор (имя) с адресом памяти.
### Программа
Структуры данных и алгоритмы – это материалы, из которых строятся программы и сам компьютер. В основе работы компьютера – умение работать с двоичными данными, битами, под командами центрального процессора в виде специальных инструкций – алгоритмов. Задачи редко выражаются в виде битов: они выражаются в виде чисел, символов, строк и более сложных структур – последовательностей, списков, деревьев и т. д. Задача, которую решает программа – преобразование входных данных в выходные.
### Объект
Сущность в  виртуальном пространстве, которой можно посылать сообщения и которая может на них реагировать, используя свои данные, появляющаяся при создании экземпляра класса или копирования прототипа, обладающая определённым состоянием и поведением, имеющая заданные значения свойств (атрибутов) и операций над ними (методов). Как правило, при рассмотрении объектов выделяется то, что объекты принадлежат одному или нескольким классам, которые определяют поведение или роль (являются моделями) объекта. Объект, наряду с понятием класс, является важным понятием объектно-ориентированного подхода. Объекты обладают свойствами наследования, инкапсуляции и полиморфизма.
### Прототип
Объект-образец, по образу и подобию которого создаются другие объекты. Объекты-копии могут сохранять связь с родительским объектом, автоматически наследуя изменения в прототипе.
### Класс
Модель еще не существующей сущности (объекта). Описывает устройство объекта, является как бы чертежом объекта.
### Метод
Это функция или процедура, принадлежащая какому-то классу или объекту. Методы предоставляют интерфейс, при помощи которого осуществляется доступ к данным объекта некоторого класса, тем самым, обеспечивая инкапсуляцию данных. Метод класса может использоваться для создания новых объектов и называется фабричным методом.
### Глобальная переменная
Объявляется в начале программы вне любого метода, значение которой можно использовать из любого места модуля или другого файла.
### Локальная переменная 	
Существует только во время выполнения метода и доступ к ним может выполняться только внутри метода, в котором она определена.
### Статическая переменная
Сохраняет свое значение при нескольких вызовах метода, в отличие от локальной переменной. Инициализируется только один раз в начале выполнения программы.
### Переменная экземпляра, instance variable, ivar
Данные, которые может содержать объект класса. Каждый раз создавая новый объект, создается и новый, причем уникальный, набор переменных экземпляра объекта. Поэтому, если у вас имеется два экземпляра объекта класса `Fraction`, к примеру, `fractionA` и `fractionB`, то каждый из них будет иметь свой собственный набор переменных. То есть, `fractionA` и `fractionB` будут иметь свои собственные `numerator` и `denominator`.
### Абстракция
Смысловая конструкция, кратко описывающая структуру данных и операции над ними для упрощения понимания. Отделение объекта от его реализации (данные обрабатываются функцией высокого уровня с помощью функции низкого уровня). Существует из-за неудобства описания операций на низком уровне.
### Инкапсуляция
Сокрытие методов и переменных от других объектов и частей программы.
### Наследование
Процесс при котором один объект приобретает свойства и методы другого объекта.
### Полиморфизм
Возможность объектов с одинаковой спецификацией иметь различную реализацию.

***
# Структуры данных

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/data_structures_kinds1.png">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/data_structures_kinds2.png">

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

### Ассоциативный массив
_associative array, map, symbol table, dictionary_

An associative array, map, symbol table, or dictionary is an abstract data type composed of a collection of pairs, such that each possible key appears at most once in the collection.
Operations associated with this data type allow:
* the addition of pairs to the collection
* the removal of pairs from the collection
* the modification of the values of existing pairs
* the lookup of the value associated with a particular key

Ассоциативный массив еще называют нагруженным множеством (data + info), где data – ключ, а нагрузка – значение ключа.

#### Хеш-таблица
_hash table, hash map_

Ассоциативный массив, хранит пары  в виде связанного списка (open hash, closed address) или массива пар (closed hash, open address). Индекс элемента равен хеш-функции от ключа i = hash(key). Разбиение множества на подмножества происходит с помощью хеш функции (пример: телефонная книга).

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/hash_table.png">

## Множество
_set_

A set is an abstract data structure that can store certain values, without any particular order, and no repeated values. It is a computer implementation of the mathematical concept of a finite set. Unlike most other collection types, rather than retrieving a specific element from a set, one typically tests a value for membership in a set. Some set data structures are designed for static or frozen sets that do not change after they are constructed. Static sets allow only query operations on their elements — such as checking whether a given value is in the set, or enumerating the values in some arbitrary order. Other variants, called dynamic or mutable sets, allow also the insertion and deletion of elements from the set.

## Список
_list_

Простейшая динамическая структура, упорядоченное множество с переменным числом элементов.

### Связный список
_linked list_

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/singly_linked_list.png">

### Двусвязный список
_doubly linked list_

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/doubly_linked_list.png">

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

## Очередь
_queue_

Абстрактный тип данных с дисциплиной доступа к элементам «первый пришёл — первый вышел» (FIFO, first-in-first-out). Добавление элемента (принято обозначать словом enqueue — поставить в очередь) возможно лишь в конец очереди, выборка — только из начала очереди (что принято называть словом dequeue — убрать из очереди), при этом выбранный элемент из очереди удаляется.

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

### Дек
_double ended queue, dequeue_

Очередь с двумя концами, включение и исключение из любого конца (левого или правого).

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/dequeue.png">

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

## Граф
_graph_

Фигура, состоящая из вершин и ребер, соединяющих вершины. Направленный и ненаправленный.

## Дерево
_tree_

Связаный граф без циклов. Выделена одна вершина – корень. Остальные – сыновья. Если нет ребенка – терминальная вершина

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tree.png">

### Бинарное дерево поиска
_binary search tree_

Состоит из узлов (записей) вида `data`, `left`, `right`, где
```
key[left[x]] < key[x] <= key[right[x]]
```
Ключ данных родительского узла больше левого сына и нестрого меньше правого.

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

# Коллекции в Objective-C
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/objc_collections.png">

__Mutability__

Most collection classes exist in two versions: mutable and immutable (default). What’s the big advantage? Thread safety. Immutable collections are fully thread safe and can be iterated from multiple threads at the same time, without any risk of mutation exceptions. Of course there’s a cost when going from immutable and mutable and back - the object has to be copied twice, and all objects within will be retained/released. Sometimes it’s more efficient to hold an internal mutable collection and return a copied, immutable object on access. Notably, some of the more modern collection classes like `NSHashTable`, `NSMapTable`, and `NSPointerArray` are mutable by default and don’t have immutable counterparts.

## Core Foundation:
* `CFMutableArray`
An object of opaque type `CFArray` — is an ordered, compact container of values. The values are in sequential order and the key for accessing these values is their index, an integer specifying a value’s position in the sequence. The range of indexes is from 0 to `n-1` where n is the number of values in the array. An index of `0` identifies the first value in the array. You can think of arrays as numbered slots. An array is said to be compact because, with mutable arrays, deleting a value does not leave a gap in the array.
* `CFMutableDictionary`
An object of the CFDictionary type — is a hashing-based collection whose keys for accessing its values are arbitrary, program-defined pieces of data (or pointers to data). Although the key is usually a string (or, in Core Foundation, a `CFString` object), it can be anything that can fit into the size of a pointer—an integer, a reference to a Core Foundation object, even a pointer to a data structure (unlikely as that might be). The keys of dictionaries are unlike the keys of the other collection objects in that, conceptually, they are also contained by the collection along with the values. Dictionaries are primarily useful for holding and organizing data that can be labeled, such as values extracted from text fields in the user interface.
In Core Foundation, a dictionary differs from an array in that the key used to access a particular value in the dictionary remains the same as values are added to or removed from the dictionary—that is, until a value associated with a particular key is replaced or removed. In an array, the key (that is, the index) that is used to retrieve a particular value can change over time as values are added to or deleted from the array. Also, unlike an array, a dictionary does not put its values in any order. To enable later retrieval of a value, the key of the key-value pair should be constant (or be treated as constant); if the key changes after being used to put a value in the dictionary, the value might not be retrievable. The keys of a dictionary form a set; in other words, keys are guaranteed to be unique in a dictionary.
The access time for a value in the dictionary is guaranteed to be at worst `O(N)` for any implementation, current and future, but will often be `O(1)` (constant time). Insertion or deletion operations will typically be constant time as well, but are `O(N^2)` in the worst case in some implementations. Access of values through a key is faster than accessing values directly (if there are any such operations). Dictionaries will tend to use significantly more memory than a array with the same number of values.
* `CFSet / CFMutableSet`
A set, both in its mathematical sense and in the implementation of CFSet, is an unordered collection of distinct elements. CFSet creates static sets and CFMutableSet creates dynamic sets.
* `CFBag / CFMutableBag`
Sets and bags are related types of collections. What they have in common is that the key for accessing a value in the collection is the value itself. The difference between sets and bags is the membership “rule” for values. With sets, if the value already exists in the collection, an identical value cannot be added to the set; conversely, you can add any value to a bag even if the bag already holds that value.
This “uniquing” functionality (or lack thereof) can have many uses. Say, for example, that your program is searching the Internet and you want to keep all qualifying URLs but don’t want duplicates; a set would work nicely for this purpose. A bag could be useful for statistical sampling; you could put all collected values in it and after you finish collecting data, you could query it for the frequency of each value.
* `CFBinaryHeap`
Implements a container that stores values sorted using a binary search algorithm. All binary heaps are mutable; there is not a separate immutable variety. Binary heaps can be useful as priority queues.
* `CFBitVector / CFMutableBitVector`
For managing bit vectors - ordered collections of bit values, which are either `0` or `1`
* `CFTree / CFMutableTree`
You use CFTree to create tree structures that represent hierarchical organizations of information. In such structures, each tree node has exactly one parent tree (except for the root tree, which has no parent) and can have multiple children.

## Foundation:
__Ordered Collections__
* `NSArray / NSMutableArray`
Управляет упорядоченной коллекцией элементов, называемой массивом. Вы можете использовать объекты этого класса для создания неизменяемых массивов. Это значит, что все элементы объектов класса `NSArray` доступны только для чтения. Имеется возможность доступа к элементам массива по индексу. Массивы могут хранить элементы различных типов. Массивы поддерживают сортировку и поиск элементов, а также сравнение самих массивов между собой.
The most interesting part is that Apple doesn’t guarantee `O(1)` access time on individual object access - as you can read in the note about Computational Complexity in the `CFArray.h` `CoreFoundation` header: The access time for a value in the array is guaranteed to be at worst `O(lg N)` for any implementation, current and future, but will often be `O(1)` (constant time). Linear search operations similarly have a worst case complexity of `O(Nlg N)`, though typically the bounds will be tighter, and so on. Insertion or deletion operations will typically be linear in the number of values in the array, but may be `O(Nlg N)` clearly in the worst case in some implementations. There are no favored positions within the array for performance; that is, it is not necessarily faster to access values with low indices, or to insert or delete values with high indices, or whatever.

__Массив в СИ__
Количество элементов массива определено заранее при объявлении массива. Все элементы упорядочены – каждому присвоен порядковый номер, который называется индексом. Доступ к конкретному элементу массива осуществляется с помощью индекса. В языке Cи все массивы располагаются в отдельной непрерывной области памяти. Первый элемент массива имеет наименьший адрес, а последний – наибольший. Элементы массива могут быть как простыми переменными, так и составными. Элемент массива может иметь несколько индексов. Количество индексов переменной определяет размерность массива. Размерность массивов в языке Cи не ограничена, но чаще используются одномерные и двумерные массивы. Начальное значение индекса элемента массива для каждого измерения в Cи — нуль.

__Collections of Keys and Values__
* `NSDictionary / NSMutableDictionary`
Следует использовать когда требуется удобный и эффективный способ хранения данных, ассоциированных с ключом. Объекты класса `NSDictionary` позволяют хранить неизменяемые пары объектов “ключ/значение” различных типов. Ключи в словаре `NSDictionary` не могут дублироваться, повторение значений допускается. Типы ключей и значений могут, но не обязаны совпадать. Особенно эффективными по скорости будут операции поиска по ключу, так как словарь специально оптимизирован для них. Because the dictionary copies each key, keys must conform to the NSCopying protocol. Bear this in mind when choosing what objects to use as keys. Although you can use any object that adopts the NSCopying protocol and implements the hash and isEqual: methods, it is typically bad design to use large objects, such as instances of NSImage, because doing so may incur performance penalties.

__Unordered Collections of Objects__
* `NSSet / NSMutableSet`
Объекты представляют неупорядоченные множества различных объектов. Вы можете использовать множества в качестве альтернативы массивам, когда порядок элементов не важен, но требуется быстрое определение `O(1)` принадлежности объекта множеству. Операция определения принадлежности выполняется значительно быстрее в сравнении с массивами. `NSSet` can only work efficiently if the hashing method used is balanced; if all objects are in the same hash bucket, then `NSSet` is not much faster in object-existence checking than `NSArray`. Variants of `NSSet` are also `NSCountedSet`, and the non-toll-free counter-variant `CFBag / CFMutableBag`.

* `NSOrderedSet / NSMutableOrderedSet` – объявляет программный интерфейс для упорядоченного множества объектов. Вы задаёте записи неизменяемого множества на этапе его создания, после этого записи не могут быть изменены. Вы можете использовать упорядоченные множества как альтернативу массивам, когда порядок элементов является важным и требуется высокая скорость поиска элементов в коллекции. Класс `NSMutableOrderedSet` объявляет программный интерфейс к изменяемому упорядоченному множеству различных объектов. Объекты класса `NSMutableOrderedSet` объекты не похожи на массивы языка Си. Во время создания такого множества вы можете указать размер, но реальный размер всё равно будет равен `0`.

* `NSCountedSet` – объявляет программный интерфейс к изменяемой, неупорядоченной коллекции нечетких объектов. Счётное множество также известно как `Bag`. Каждый отдельный объект, вставленный в `NSCountedSet`, имеет счётчик, связанный с ним. Объект `NSCountedSet` отслеживает количество раз, когда объекты были вставлены, и требует, чтобы объекты были удалены такое же количество раз. В то же время, внутри объекта `NSSet` существует только один экземпляр вставляемого объекта, даже если этот объект был добавлен в множество несколько раз.

__Storing Indexes into an Array__
* `NSIndexSet / NSMutableIndexSet` – represents an immutable collection of unique unsigned integers, known as indexes because of the way they are used. This collection is referred to as an index set. You use index sets in your code to store indexes into some other data structure. For example, given an `NSArray` object, you could use an index set to identify a subset of objects in that array. You should not use index sets to store an arbitrary collection of integer values because index sets store indexes as sorted ranges. This makes them more efficient than storing a collection of individual integers. It also means that each index value can only appear once in the index set. The designated initializers of the `NSIndexSet` class are: `init`, `initWithIndexesInRange:`, and `initWithIndexSet:`. You must not subclass the `NSIndexSet` class. The mutable subclass of `NSIndexSet` is `NSMutableIndexSet`.

* `NSIndexPath` – представляет путь к конкретному узлу в виде дерева вложенных массивов коллекций. Этот путь известен как индексный путь. Каждый индекс в индексном пути представляет индекс в массиве дочерних элементов от одного узла в дереве к другому.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/complexity.png">

__Pointer collection classes__

The pointer collection classes allow you to further customize the collection to tailor it to your memory and storage needs. The options specified by `NSPointerFunctionsOptions` provide a convenient interface for customizing how the collection manages the pointers it contains.

* `NSPointerArray` – mutable collection modeled after `NSArray` but it can also hold `NULL` values, which can be inserted or extracted (and which contribute to the object’s count). Moreover, unlike traditional arrays, you can set the count of the array directly. You can use an NSPointerArray object when you want an ordered collection that uses weak references. For example, suppose you have a global array that contains some objects. Because global objects are never collected, none of its contents can be deallocated unless they are held weakly. Pointer arrays configured to hold objects weakly do not own their contents. If there are no strong references to objects within such a pointer array, those objects can be deallocated.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/pointerarray.png">

* `NSMapTable` – is a general-purpose analogue of `NSDictionary`. Contrasted with the behavior of `NSDictionary / NSMutableDictionary`, `NSMapTable` has the following characteristics:
- `NSDictionary` / `NSMutableDictionary` copies keys, and holds strong references to values.
- `NSMapTable` is mutable, without an immutable counterpart.
- `NSMapTable` can hold keys and values with weak references, in such a way that entries are removed when either the key or value is deallocated.
- `NSMapTable` can copy its values on input.
- `NSMapTable` can contain arbitrary pointers, and use pointer identity for equality and hashing checks.

* `NSHashTable` – в отличие от NSSet, поддерживает слабые ссылки. Он может содержать слабые ссылки на объекты. Объекты класса NSHashTable могут содержать произвольные указатели, хранимые объекты не ограничиваются объектами классов. Можно настроить экземпляр `NSHashTable` для работы с произвольными указателями, а не только с объектами классов. Благодаря своим свойствам, класс `NSHashTable` это не множество, потому что он может вести себя по-другому.

_`NSArray` is the best choice to use for a list of items if you're going to iterate over them in sequence, or access directly by index. They are also efficient to use as a queue or stack, as adding or removing items from either the beginning or is `O(1)`. Checking to see if an object exists in the array using `containsObject:` is an `O(N)` operation, as it may take up to `N` comparisons to find the match._
_`NSSet` is a great choice for checking `containsObject:` due to efficient hashing algorithms. Adding/removing items is always `O(1)`. In addition, you have fast set arithmetic operations._
_`NSDictionary` is a great choice if you have a natural key you can use to access objects. This has no inherent order, but if you know the key you can retrieve any object as `O(1)`._

## Разница между Set и Array
`NSSet` предназначен для создания несортированных массивов данных (например каких-либо объектов). Стоит обратить внимание, что объект, который хранится в `NSSet`, встречается только один раз. Т.е. все элементы `NSSet` — уникальные.
Добавить дубликат элемента в `NSMutableSet` у вас также не получится. Для создания несортированного массива, в котором можно использовать неуникальные элементы, можно использовать `NSCountedSet`. Основным преимуществом `NSCountedSet` перед использованием классического массива `NSArray` является то, что элемент может быть продублирован огромное количество раз и при этом занимать памяти как один элемент. Это объясняется тем, что `NSCountedSet` хранит в памяти только одну копию элемента и запоминает сколько раз этот элемент встречается. Если для вас не важен порядок элементов внутри массива и вы используете действительно большие объемы информации, то использование `NSSet` повысит производительность приложения за счет снижения потребляемой памяти. Несмотря на то, что количество элементов хранящихся в памяти будет одинаковым, `NSSet` не тратит память на то, чтобы помнить в какой последовательности хранятся элементы.

## Difference between NSArray and CFArray
What's the point of them both existing? There are a few reasons.

* If you want to provide a C API, like the Carbon API, and you need things like arrays and dictionaries of referenced-counted objects, you want a library like Core Foundation (which provides CFArray), and of course it needs to have a C API.
* If you want to write libraries for third-parties to use on Windows (for example), you need to provide a C API.
* If you want to write a low-level library, say for interfacing with your operating system's kernel, and you want avoid the overhead of Objective-C messaging, you need a C API.

So those are good reasons for having Core Foundation, a pure C library.

But if you want to provide a higher-level, more pleasant API in Objective-C, you want Objective-C objects that represent arrays, dictionaries, reference-counted objects, and so on. So you need Foundation, which is an Objective-C library.

When should you use one or the other? Generally, you should use the Objective-C classes (e.g. `NSArray`) whenever you can, because the Objective-C interface is more pleasant to use: `myArray.count` (or `[myArray count]`) is easier to read and write than `CFArrayGetCount(myArray)`. You should use the Core Foundation API only when you really need to: when you're on a platform that doesn't have Objective-C, or when you need features that the Core Foundation API provides but the Objective-C objects lack. For example, you can specify callbacks when creating a `CFArray` or a `CFDictionary` that let you store non-reference-counted objects. The `NSArray` and `NSDictionary` classes don't let you do that - they always assume you are storing reference-counted objects.
Are the CF objects just legacy objects? Not at all. In fact, Nextstep existed for years with just the Objective-C Foundation library and no Core Foundation library. When Apple needed to support both the Carbon API and the Cocoa API on top of the same lower-level operating system facilities, they created Core Foundation support both.

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

## Sorting
__Сортировка массивов__

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



***

# Алгоритмы
## Нотация «большое О»
Performance is usually described with the Big O Notation. It defines the limiting behavior of a function and is often used to characterize algorithms on their performance. O defines the upper bound of the growth rate of the function. To see just how big the difference is, see commonly used O notations and the number of operations needed.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/big_o_complexity.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/algo_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/algo_2.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/algo_3.png">

For example, if you sort an array with 50 elements, and your sorting algorithm has a complexity of `O(n^2)`, there will be 2,500 operations necessary to complete the task. Furthermore, there’s also overhead in internal management and calling that method - so it’s 2,500 operations times constant. `O(1)` is the ideal complexity, meaning constant time. Good sorting algorithms usually need `O(n log n)` time.

>нужно найти гифки

## Последовательный поиск
Для неупорядоченного массива – перебор всех элементов, пока либо не найдется элемент, либо не закончится массив.
```c
//O(n)
int linearSearch(int array[], int size, int x) {
	for (int i = 0; i < size; i++) {
		if (x == array[i]) {
			return x;
		}
	}
	return -1;
}
```
```c
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
```

## Бинарный поиск
`log(n), отсортированный массив`

Алгоритм двоичного поиска похож на то, как мы ищем слово в словаре. Открываем словарь посередине, смотрим в какой из половин будет нужное нам слово. Допустим, в первой. Открываем первую часть посередине, продолжаем половинить, пока не найдем  нужное слово. С массивами так: есть упорядоченный массив, берем число из середины массива, сравниваем с искомым. Если оно оказалось больше, значит искомое число в первой половине массива, если меньше — во второй. Продолжаем делить оставшуюся половину, когда находим нужное число возвращаем его индекс, если не находим возвращаем `null`.
```c
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
```
`NSArray` has come with built-in binary search since iOS 4 / Snow Leopard:
```objectivec
typedef NS_OPTIONS(NSUInteger, NSBinarySearchingOptions) {
	NSBinarySearchingFirstEqual     = (1UL << 8),
	NSBinarySearchingLastEqual      = (1UL << 9),
	NSBinarySearchingInsertionIndex = (1UL << 10),
};

- (NSUInteger)indexOfObject:(id)obj
              inSortedRange:(NSRange)range
                    options:(NSBinarySearchingOptions)options
            usingComparator:(NSComparator)cmp;
```
Why would you want to use this? Methods like `containsObject:` and `indexOfObject:` start at index `0` and search every object until the match is found - they don’t require the array to be sorted but have a performance characteristic of `O(n)`. Binary search, on the other hand, requires the array to be sorted, but only needs `O(log n)` time. Thus, for one million entries, binary search requires, at most, 21 comparisons, while the naive linear search would require an average of 500,000 comparisons.

__Time to search for 1000 entries within 1000000 objects.__
```
Linear: 54130.38[ms].
Binary: 7.62[ms]
```
For comparison, the search for a specific index with `NSOrderedSet` took 0.23 ms - that’s more than 30 times faster, even compared to binary search. Keep in mind that sorting is expensive as well. Apple uses merge sort, which takes `O(n*log n)`, so if you just have to call `indexOfObject:` once, there’s no need for binary search.

## Сортировка вставками
`O(n^2), частично отсортированный массив`

Суть его заключается в том что, на каждом шаге алгоритма мы берем один из элементов массива, находим позицию для вставки и вставляем. Стоит отметить что массив из 1-го элемента считается отсортированным.

*	Устойчив
*	Может сортировать массив по мере его поступления

```c
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
```

## Сортировка пузырьком
`O(n^2)`

Алгоритм состоит из повторяющихся проходов по сортируемому массиву. За каждый проход элементы последовательно сравниваются попарно и, если порядок в паре неверный, выполняется обмен элементов. Проходы по массиву повторяются `N-1` раз или до тех пор, пока на очередном проходе не окажется, что обмены больше не нужны, что означает — массив отсортирован. При каждом проходе алгоритма по внутреннему циклу, очередной наибольший элемент массива ставится на своё место в конце массива рядом с предыдущим «наибольшим элементом», а наименьший элемент перемещается на одну позицию к началу массива («всплывает» до нужной позиции как пузырёк в воде, отсюда и название алгоритма).

* Эффективен для небольших массивов из-за сложности
```c
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
```

## Сортировка выбором
`O(n^2)`

На каждом шаге алгоритма мы выбираем один из элементов входных данных и вставляем его на нужную позицию в уже отсортированном списке, до тех пор, пока набор входных данных не будет исчерпан. Метод выбора очередного элемента из исходного массива произволен; может использоваться практически любой алгоритм выбора. Обычно (и с целью получения устойчивого алгоритма сортировки), элементы вставляются по порядку их появления во входном массиве. Приведенный ниже алгоритм использует именно эту стратегию выбора.

Плюсы:

* эффективен на небольших наборах данных, на наборах данных до десятков элементов может оказаться лучшим;
* эффективен на наборах данных, которые уже частично отсортированы;
* это устойчивый алгоритм сортировки (не меняет порядок элементов, которые уже отсортированы);
* может сортировать список по мере его получения;
* использует `O(1)` временной памяти, включая стек.

Минусы:

* может быть и устойчивым, и неустойчивым
```c
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
```

## Быстрая сортировка
`O(n*log(n)), разделяй и властвуй`

QuickSort является существенно улучшенным вариантом алгоритма сортировки с помощью прямого обмена (его варианты известны как «Пузырьковая сортировка» и «Шейкерная сортировка»), известного, в том числе, своей низкой эффективностью. Принципиальное отличие состоит в том, что в первую очередь производятся перестановки на наибольшем возможном расстоянии и после каждого прохода элементы делятся на две независимые группы. Любопытный факт: улучшение самого неэффективного прямого метода сортировки дало в результате один из наиболее эффективных улучшенных методов.
Общая идея алгоритма состоит в следующем:

1. Выбрать из массива элемент, называемый опорным. Это может быть любой из элементов массива.
2. Сравнить все остальные элементы с опорным и переставить их в массиве так, чтобы разбить массив на три непрерывных отрезка, следующие друг за другом — «меньшие опорного», «равные» и «большие».
3. Для отрезков «меньших» и «больших» значений выполнить рекурсивно ту же последовательность операций, если длина отрезка больше единицы.

На практике массив обычно делят не на три, а на две части, например, «меньшие опорного» и «равные и большие». Такой подход в общем случае эффективнее, так как упрощает алгоритм разделения.

Достоинства:

* Один из самых быстродействующих (на практике) из алгоритмов внутренней сортировки общего назначения.
* Прост в реализации.
* Требует лишь `O(lg n)` дополнительной памяти для своей работы. (Не улучшенный рекурсивный алгоритм в худшем случае `O(n)` памяти)
* Хорошо сочетается с механизмами кэширования и виртуальной памяти.
* Допускает естественное распараллеливание (сортировка выделенных подмассивов в параллельно выполняющихся подпроцессах).
* Допускает эффективную модификацию для сортировки по нескольким ключам (в частности — алгоритм Седжвика для сортировки строк): благодаря тому, что в процессе разделения автоматически выделяется отрезок элементов, равных опорному, этот отрезок можно сразу же сортировать по следующему ключу.
* Работает на связных списках и других структурах с последовательным доступом, допускающих эффективный проход как от начала к концу, так и от конца к началу.

Недостатки:

* Сильно деградирует по скорости (до `Theta(n^2)`) в худшем или близком к нему случае, что может случиться при неудачных входных данных.
* Прямая реализация в виде функции с двумя рекурсивными вызовами может привести к ошибке переполнения стека, так как в худшем случае ей может потребоваться сделать `O(n)` вложенных рекурсивных вызовов.
* Неустойчив
```c
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
```

### How to merge two sorted arrays into a sorted array?
```c++
public static int[] merge(int[] a, int[] b) {
    int[] answer = new int[a.length + b.length];
    int i = 0, j = 0, k = 0;

    while (i < a.length && j < b.length) {
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
```

### Рекурсивная функция
Функция, вызывающая саму себя. Вопрос о желательности использования рекурсивных функций в программировании неоднозначен: с одной стороны, рекурсивная форма может быть структурно проще и нагляднее, в особенности, когда сам реализуемый алгоритм по сути рекурсивен. Кроме того, в некоторых декларативных или чисто функциональных языках (таких как Пролог или Haskell) просто нет синтаксических средств для организации циклов, и рекурсия в них — единственный доступный механизм организации повторяющихся вычислений. С другой стороны, обычно рекомендуется избегать рекурсивных программ, которые приводят (или в некоторых условиях могут приводить) к слишком большой глубине рекурсии. Так, широко распространённый в учебной литературе пример рекурсивного вычисления факториала является, скорее, примером того, как не надо применять рекурсию, так как приводит к достаточно большой глубине рекурсии и имеет очевидную реализацию в виде обычного циклического алгоритма.

Плюсы

* Наглядность
* Простота

Минусы

* Возможна большая глубина рекурсии, из-за которой может произойти быстрое переполнение стека и нехватка памяти.

__Факториал__
```c
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
```

__Последовательность Фибоначчи__
```c
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
```

# Программирование
__Программирование__ — процесс создания компьютерных программ.
В узком смысле (так называемое кодирование) под программированием понимается написание инструкций (программ) на конкретном языке программирования (часто по уже имеющемуся алгоритму — плану, методу решения поставленной задачи). В настоящее время активно используются интегрированные среды разработки (IDE), включающие в свой состав также редактор для ввода и редактирования текстов программ, отладчики для поиска и устранения ошибок, трансляторы с различных языков программирования, компоновщики для сборки программы из нескольких модулей и другие служебные модули. С помощью текстового редактора программист производит набор и редактирования текста создаваемой программы, который называют исходным кодом. Язык программирования определяет синтаксис и изначальную семантику исходного кода. Компилятор преобразует текст программы в машинный код, непосредственно исполняемый электронными компонентами компьютера. Интерпретатор создаёт виртуальную машину для выполнения программы, которая полностью или частично берёт на себя функции исполнения программ.
Код –> препроцессор (#define, etc. – развертывание, замена) –> компилятор –> машинный код

Язык программирования — формальная знаковая система, предназначенная для записи компьютерных программ.

Классы языков программирования:

* Функциональные

_Lisp, Erlang, Haskell, Scala_

На основе достаточно строгих абстрактных понятий и методов символьной обработки данных. Тексты программ на функциональных языках программирования описывают «как решить задачу», но не предписывают последовательность действий для решения.

* Процедурные (императивные)

_C, Basic, Pascal_

Последовательно выполняемые операторы можно собрать в подпрограммы, то есть более крупные целостные единицы кода, с помощью механизмов самого языка. Процедурное программирование является отражением архитектуры традиционных ЭВМ. Процедурный язык программирования предоставляет возможность программисту определять каждый шаг в процессе решения задачи. Особенность таких языков программирования состоит в том, что задачи разбиваются на шаги и решаются шаг за шагом. Используя процедурный язык, программист определяет языковые конструкции для выполнения последовательности алгоритмических шагов.

* Динамические

_Perl, Tcl, Python, PHP, Ruby, Smalltalk, JavaScript_

Позволяют определять типы данных и осуществлять синтаксический анализ и компиляцию «на лету», на этапе выполнения программы. Динамические языки удобны для быстрой разработки приложений. Динамическая типизация (при котором перемен-ная связывается с типом в момент присваивания значения, а не в момент объявления переменной. Таким образом, в различных участках программы одна и та же переменная мо-жет принимать значения разных типов) является основным, но не единственным критерием динамического языка программирования.


* Объектно-ориентированные

_C#, C++, Java. Objective-C, Perl, Python, Scala, Ruby, Smaltalk, PHP_

Язык, построенный на принципах объектно-ориентированного программирования. В основе концепции объектно-ориентированного программирования лежит понятие объекта — некой сущности, которая объединяет в себе поля (данные) и методы (выполняемые объектом действия).

__API__ – интерфейс программирования приложений (иногда интерфейс прикладного программирования) (application programming interface) — набор готовых классов, процедур, функций, структур и констант, предоставляемых приложением (библиотекой, сервисом) для использования во внешних программных продуктах. Используется программистами для написания всевозможных приложений. API операционных систем: Cocoa, Windows API. API не решение для системы (как фреймворк), а доступ к функциям другой системы.

__IDE__ - интегрированная среда разработки (integrated development environment) — система программных средств, используемая программистами для разработки программного обеспечения.
Обычно, среда разработки включает в себя:

* текстовый редактор
* компилятор и/или интерпретатор
* средства автоматизации сборки
* отладчик

__Высокоуровневый язык программирования__ — язык программирования, разработанный для быстроты и удобства использования программистом. Основная черта высокоуровневых языков — это абстракция, то есть введение смысловых конструкций, кратко описывающих такие структуры данных и операции над ними, описания которых на машинном коде (или другом низкоуровневом языке программирования) очень длинны и сложны для понимания.

__Компиляция__ — трансляция программы, составленной на исходном языке высокого уровня, в эквивалентную программу на низкоуровневом языке, близком машинному коду (абсолютный код, объектный модуль, иногда на язык ассемблера). Входной информацией для компилятора (исходный код) является описание алгоритма или программа на проблемно-ориентированном языке, а на выходе компилятора — эквивалентное описание алгоритма на машинно-ориентированном языке (объектный код). Компилировать — проводить трансляцию машинной программы с проблемно-ориентированного языка на машинно-ориентированный язык.

# Язык СИ.

* Лаконичность и быстрота (почти как Ассемблер)
* Переносимость на различные архитектуры
* Набор низкоуровневых средств
* Прямой доступ к памяти
* Операции над битами
* Адресная арифметика

Си – универсальный язык программирования, считается удобным для системного программирования, хотя он удобен и для написания прикладных программ. Среди преимуществ языка Си следует отметить переносимость программ на компьютеры различной архитектуры и из одной операционной системы в другую, лаконичность записи алгоритмов, логическую стройность программ, а также возможность получить программный код, сравнимый по скорости выполнения с программами, написанными на языке ассемблера. Последнее связано с тем, что хотя Си является языком высокого уровня, имеющим полный набор конструкций структурного программирования, он также обладает набором низкоуровневых средств, обеспечивающих доступ к аппаратным средствам компьютера.
Программа на Cи состоит из программных единиц одного типа – функций. Аргументы могут передаваться функциям посредством копирования значений этих аргументов; при этом вызванная функция не может изменить фактический аргумент в вызывающей подпрограмме.
Возможен иной вариант – передача параметра по ссылке, когда явно передается указатель, т.е. адрес, при этом функция сможет изменить объект, на который ссылается указатель.
В Си предусмотрен ряд операций низкого уровня: прямой доступ к памяти, операции над битами данных и адресной арифметики.
Программы на языке Си компактны и гибки. Язык Си доверяет программисту и разрешает ему практически все; из-за этого Си нельзя считать языком надежного программирования, и вся ответственность за качество программы лежит на программисте, который должен знать особенности языка и его реализации. Программа, написанная на языке Си, состоит из операторов. Каждый оператор вызывает выполнение некоторых действий на соответствующем шаге выполнения программы.
При написании операторов применяются латинские прописные и строчные буквы, цифры и специальные знаки. К таким знакам, например, относятся: точка `.`, запятая `,`, двоеточие `:`, точка с запятой `;` и др. Совокупность символов, используемых в языке, называется алфавитом языка. Программы оперируют с различными данными, которые могут быть простыми и структурированными. Простые данные - это целые и вещественные числа, символы и указатели (адреса объектов в памяти). Целые числа не имеют, а вещественные имеют дробную часть. Структурированные данные - это массивы и структуры.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/c_types.png">

## Битовые операции
В своих программах вы не адресуете отдельные биты, а имеете дело с группами битов - байтами. Если представить байт как 8-разрядное целое число без знака, его биты соответствуют последовательным степеням `2`.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/binary.png">

Однако компьютерам удобнее иметь дело со степенями `2`. Программисты часто используют шестнадцатеричную систему (`16 = 2^4`) - особенно при работе с отдельными разрядами целых чисел. В качестве дополнительных цифр в шестнадцатеричной системе используются буквы `а`, `b`, `с`, `d`, `е` и `f`. Таким образом, счет в шестнадцатеричной системе выглядит так: `0 1 2 3 4 5 6 7 8 9 а b с d е f 10 11 ...` Числа, записанные в шестнадцатеричной системе, обозначаются префиксом `0х`.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/hexadecimal.png">

Один байт всегда может быть представлен шестнадцатеричным числом из двух цифр (например, `3с`). По этой причине шестнадцатеричные числа удобны для работы с двоичными данными.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/numeral_system.png">

__Побитовое `И` (`AND`, `&`)__

`2` байта можно объединить поразрядной операцией `И` для создания третьего байта. В этом случае бит третьего байта равен `1` только в том случае, если оба соответствующих бита первых двух байтов равны `1`.
```
0011
0101
----
0001
```
Часто используется для обнуления некоторой группы разрядов. Например:
```c
n = n & 0177;
```
обнуляет в `n` все разряды, кроме младших семи.

__Побитовое `ИЛИ` (`OR`, `|`)__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/or_example.png">

Программа выдает результат объединения двух байтов поразрядной операцией `ИЛИ`:
```
Hex: 		03c0 | 0a90 = 0bd
Decimal: 	0600 | 01690 = 0189
```
```
0011
0101
----
0111
```
Применяют для установки разрядов; так,
```c
х = х | SET_ON;
```
устанавливает единицы в тех разрядах `х`, которым соответствуют единицы в `SET_ON`.

__Побитовое исключающее `ИЛИ` (сложение по модулю два, `XOR`, `^`)__

Исключающая операция `ИЛИ` объединяет два байта и создает третий байт. Бит результата равен `1` в том случае, если ровно один из двух соответствующих битов входных байтов равен `1`.
```
0011
0101
----
0110
```

__Побитовое отрицание (дополнение, унарный оператор `НЕ`, `NOT`, `~`)__

Дополнением к существующему байту называется байт, биты которого находятся в противоположном состоянии: все нули заменяются единицами, а все единицы заменяются нулями.
```
0011
----
1100
```
Унарный оператор `~` поразрядно "обращает" целое т.е. превращает каждый единичный бит в нулевой и наоборот. Например:
```c
х = х & ~077
```
обнуляет в `х` последние `6` разрядов. Заметим, что запись `х & ~077` не зависит от длины слова, и, следовательно, она лучше, чем `х & 0177700`, поскольку последняя подразумевает, что `х` занимает `16` битов. Не зависимая от машины форма записи `~077` не потребует дополнительных затрат при счете, так как `~077` — константное выражение, которое будет вычислено во время компиляции.

__Сдвиг влево `<<`__

При выполнении операции сдвига влево каждый бит смещается в направлении старшего бита. Биты, выходящие за пределы числа, теряются, а возникающие справа «пустоты» заполняются нулями.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/left_bitwise.png">

__Сдвиг вправо `>>`__

__Примеры битовых операций:__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/bit_example.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/bit_math_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/bit_math_2.png">

```
67 & 114 = 66
67 | 114 = 115
67 ^ 114 = 49
~67 = 188
```

## Что такое указатель и ссылка и в чем разница?
Есть два способа обращения к функции – вызов по значению и вызов по ссылке. При вызове по значению создается копия аргумента и передается вызываемой функции. Изменение копии не влияют на значение оригинала в операторе вызова. Один из минусов этого способа – если передается большой элемент данных, то на его копирование может уйти дополнительное время.

Ссылочный параметр – это псевдоним аргумента.
```c
int &count; //count является ссылкой на int.
```
В вызове функции достаточно указать имя переменной и она будет передана по ссылке, тогда упоминание в теле вызываемой функции переменной по имени ее параметра в действительности является обращением к исходной переменной в вызывающей функции и эта исходная переменная может быть изменена непосредственно вызываемой функцией. Для передачи больших объектов используется константный ссылочный параметр, чтобы обеспечить защиту параметра, как при вызове по значению, и в то же время избежать накладных расходов при передаче копии большого объекта:
```c
const int &count;
```
__Ссылка__ – это псевдоним для другой переменной и все операции, выполняемые с псевдонимом (ссылкой) выполняются на самом деле с истинной переменной. Псевдоним – другое имя переменной и для него не резервируется место в памяти.
Если возвращение ссылки переменной объявлено в функции, то эта переменная должна быть объявлена внутри функции как статическая, иначе ссылка адресуется автоматической переменной, которая после выполнения функции уничтожается.

__Указатель__ – переменная, которая содержит в качестве значения адрес памяти переменной, которая уже в свою очередь содержит значение. Т.о. имя переменной отсылает к значению прямо, а указатель – косвенно.
```c
int y = 5;
int *yPtr;
yPtr = &y;
```
Теперь `yPtr` указывает на `y`.
Операция `*` – операция косвенной адресации или операция разыменования.

Аргументы можно передавать в функцию тремя способами:

1. Вызов по значению
2. Вызов по ссылке с аргументами ссылками
3. Вызов по ссылке с аргументами указателями

Указатели как и ссылки тоже можно использовать для модификации одного или более значений переменных в вызывающем операторе, или передавать указатели на большие объекты данных, чтобы избежать расходов, сопутствующих передаче объектов по значению.

`const` с указателем значит, что значение переменной не изменяется.

## Почему (NSError **) использует указатель на указатель?
_Explanation 1:_
if you pass a pointer to an object to your function, the function can only modify what the pointer is pointing to.
if you pass a pointer to a pointer to an object then the function can modify the pointer to point to another object.
In the case of `NSError`, the function might want to create a new `NSError` object and pass you back a pointer to that `NSError` object. Thus, you need double indirection so that the pointer can be modified.

_Explanation 2:_
A pointer to a pointer is a form of multiple indirection, or a chain of pointers. Normally, a pointer contains the address of a variable. When we define a pointer to a pointer, the first pointer contains the address of the second pointer, which points to the location that contains the actual value as shown below.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/pointers.png">

A variable that is a pointer to a pointer must be declared as such. This is done by placing an additional asterisk in front of its name. For example, the following declaration declares a pointer to a pointer of type `int`: `int **var;`
When a target value is indirectly pointed to by a pointer to a pointer, accessing that value requires that the asterisk operator be applied twice, as is shown below in the example:
```c
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
   printf("Value of var = %d\n", var);
   printf("Value available at *ptr = %d\n", *ptr);
   printf("Value available at **pptr = %d\n", **pptr);

   return 0;
}
```
```
Value of var = 3000
Value available at *ptr = 3000
Value available at **pptr = 3000
```
with a regular parameter, say `int`, you get a local copy

with a pointer parameter, say `int*`, you can modify what it points to

with a double pointer parameter, say `int**`, you can modify the pointer itself, i.e. 'repoint' it

## How to return 2+ values from a function?

__In C:__

* Returning the address of the first element of a local array has undefined behavior (at least dereferencing it later is). You may use output parameters, that is, pass two pointers, and set the values inside:
```c
void Calculate(int x, int y, int* prod, int* quot) {
    *prod = x*y;
    *quot = x/y;
}
```
Usage:
```c
int x = 10, y = 2, prod, quot;
Calculate(x, y, &prod, &quot)
```
* Another thing you could do is pack your data into a struct

```c
typedef struct {
    int prod;
    int quot;
} product_and_quot;

product_and_quot Calculate(int x, int y) {
    product_and_quot p = {x*y, x/y};
    return p;
}
```
__in Objective-C:__

* Pointers

```objectivec
- (void)convertA:(float)a B:(float)b C:(float) intoX:(float *)xOut Y:(float *)yOut Z:(float)zOut {
    *xOut = 3*a + b;
    *yOut = 2*b;
    *zOut = a*b + 4*c;
}
```
and call it like this:
```objectivec
float x, y, z;
[self convertA:a B:b C:c intoX:&x Y:&y Z:&z];
```
* Another way is to create a struct and return it:

```objectivec
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
```
Call it like this:
```objectivec
struct XYZ output = [self xyzWithA:a B:b C:c];
```
* Double pointers with objects

If you want to return more than one new object, your function should take pointers to the object pointer, thus:
```objectivec
- (void)mungeFirst:(NSString **)stringOne andSecond:(NSString **)stringTwo {
    *stringOne = [NSString stringWithString:@"foo"];
    *stringTwo = [NSString stringWithString:@"baz"];
}
```
* Blocks

You can return two values with help of block:
```objectivec
- (void)getUIControlles:(void (^)(UITextField *objTextFiled, UIView *objView))completionBlock {
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

- (void)testMethod {
    // Call function with following way.
    [self getUIControlles:^(UITextField *objTextFiled, UIView *objView) {
		// objTextFiled = This is your textfiled object
		// objView = This is your view object
    }];
}
```
## What is the difference between char * const and const char *?

Существует четыре способа передачи в функцию указателя

1. Неконстантный указатель на неконстантные данные
2. Неконстнатный указатель на константные данные
3. Константный указатель на неконстантные данные
4. Константный указатель на константные данные

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/const_pointer.png">

## Что значит n&(n – 1)?
It's figuring out if `n` is either `0` or an exact power of two.
It works because a binary power of two is of the form `1000...000` and subtracting one will give you `111...111`. Then, when you `AND` those together, you get zero, such as with:
```
   1000 0000 0000 0000
&&  111 1111 1111 1111
   ==== ==== ==== ====
 = 0000 0000 0000 0000
 ```
Any non-power-of-two input value will not give you zero when you perform that operation.
For example, let's try all the 3-bit combinations:
```
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
```
You can see that only `0` and the powers of two (`1`, `2` and `4`) result in a `000-false` bit pattern, all others are non-zero or `true`.
See the full Bit Twiddling Hacks document for all sorts of other wonderful (or dastardly, depending on your viewpoint) hackery.

# ООП
## История ООП
ООП – парадигма программирования, в которой основными концепциями являются понятия объектов и классов. В центре ООП находится понятие объекта. Объект — это сущность, которой можно посылать сообщения, и которая может на них реагировать, используя свои данные. Объект — это экземпляр класса. Данные объекта скрыты от остальной программы. Сокрытие данных называется инкапсуляцией. Наличие инкапсуляции достаточно для объектности языка программирования, но ещё не означает его объектной ориентированности — для этого требуется наличие наследования. Но даже наличие инкапсуляции и наследования не делает язык программирования в полной мере объектным с точки зрения ООП. Основные преимущества ООП проявляются только в том случае, когда в языке программирования реализован полиморфизм; то есть возможность объектов с одинаковой спецификацией иметь различную реализацию. Первым языком программирования, в котором были предложены принципы объектной ориентированности, была Симула. В момент своего появления (в 1967 году), этот язык программирования предложил поистине революционные идеи: объекты, классы, виртуальные методы и др., однако это всё не было воспринято современниками как нечто грандиозное. Тем не менее, большинство концепций были развиты Аланом Кэйем и Дэном Ингаллсом в языке Smalltalk. Именно он стал первым широко распространённым объектно-ориентированным языком программирования. (C#, C++, Java, Ruby, PHP, Perl, Python). ООП дает возможность создавать расширяемые системы (extensible systems). Это одно из самых значительных достоинств ООП и именно оно отличает данный подход от традиционных методов программирования. Расширяемость (extensibility) означает, что существующую систему можно заставить работать с новыми компонентами, причем без внесения в нее каких-либо изменений. Компоненты могут быть добавлены на этапе выполнения. Smalltalk — объектно-ориентированный язык программирования с динамической типизацией, разработанный в Xerox PARC Аланом Кэйем, Дэном Ингаллсом, Тедом Кэглером, Адель Голдберг, и другими в 1970-х годах. Язык был представлен как Smalltalk-80. Smalltalk оказал большое влияние на развитие многих других языков, таких как: Objective-C, Actor, Java, Groovy и Ruby. Многие идеи 1980-х и 1990-х по написанию программ появились в сообществе Smalltalk. К ним можно отнести рефакторинг, шаблоны проектирования (применительно к ПО), карты «класс — обязанности — взаимодействие» и экстремальное программирование в целом. Си — язык программирования, разработанный в 1969—1973 годах сотрудниками Bell Labs Кеном Томпсоном и Деннисом Ритчи как развитие языка Би. Благодаря близости по скорости выполнения программ, написанных на Си, к языку ассемблера, этот язык получил широкое применение при создании системного программного обеспечения и прикладное программное обеспечение для решения широко круга задач. Язык программирования Си оказал существенное влияние на развитие индустрии программного обеспечения, а его синтаксис стал основой для таких языков программирования как C++, C# и Java.

## Основные понятия ООП: абстракция, инкапсуляция, наследование, полиморфизм.
__Абстракция__ – это придание объекту характеристик, которые чётко определяют его концептуальные границы, отличая от всех других объектов. Основная идея состоит в том, чтобы отделить способ использования составных объектов данных от деталей их реализации в виде более простых объектов, подобно тому, как функциональная абстракция разделяет способ использования функции и деталей её реализации в терминах более примитивных функций, таким образом, данные обрабатываются функцией высокого уровня с помощью вызова функций низкого уровня. (Пример: говорить о предметах, не упоминая материалы, из которых они сделаны). Абстракция позволяет задействовать концепцию, игнорируя ее некоторые детали и работая с разными деталями на разных уровнях. Имея дело с составным объектом, вы имеете дело с абстракцией. Если вы рассматриваете объект как «дом», а не как комбинацию стекла, древесины и гвоздей, вы прибегаете к абстракции. Если вы рассматриваете множество домов как «город», вы прибегаете к другой абстракции. Базовые классы представляют собой абстракции, позволяющие концентрироваться на общих атрибутах производных классов и игно-рировать детали конкретных классов при работе с базовым классом. Удачный интерфейс класса — это абстракция, позволяющая сосредоточиться на интерфейсе, не беспокоясь о внутренних механизмах работы класса. Мы используем абстракции на каждом шагу. Если б, открывая или закрывая дверь, вы должны были иметь дело с отдельными волокнами древесины, молекулами лака и стали, вы вряд ли смогли бы войти в дом или выйти из него. Абстракция — один из главных способов борьбы со сложностью реального мира.
Слой абстрагирования (или уровень абстракции) — это способ уйти от деталей реализации конкретного множества функций.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/abstraction.png">

__Инкапсуляция__ – скрытие методов и переменных от других методов или переменных или других частей программы. Сокрытие реализации целесообразно применять в следующих целях:

* При необходимости максимальной локализации предстоящих изменений, когда изменяется только работа объекта, а не программы;
* При необходимости предсказания предстоящих изменений и их последствий;
* При необходимости очистки глобальной области видимости.

Когда абстракция нас покидает, на помощь приходит инкапсуляция. Абстракция говорит: «Вы можете рассмотреть объект с общей точки зрения». Инкапсуляция добавляет: «Более того, вы не можете рассмотреть объект с иной точки зрения».
Продолжим нашу аналогию: инкапсуляция позволяет вам смотреть на дом, но не дает подойти достаточно близко, чтобы узнать, из чего сделана дверь. Инкапсуляция позволяет вам знать о существовании двери, о том, открыта она или заперта, но при этом вы не можете узнать, из чего она сделана (из дерева, стекловолокна, стали или другого материала), и уж никак не сможете рассмотреть отдельные волокна древесины.

__Наследование__ – процесс, посредством которого один объект может приобретать свойства другого. Точнее, объект может наследовать основные свойства другого объекта и добавлять к ним черты, характерные только для него. Польза наследования в том, что оно дополняет идею абстракции. Абстракция позволяет представить объекты с разным уровнем детальности. Если помните, на одном уровне мы рассматривали дверь как набор определенных типов молекул, на втором — как набор волокон древесины, а на третьем — как что􏰀то, что защищает нас от воров. Древесина имеет определенные свойства — скажем, вы можете распилить ее пилой или склеить столярным клеем, — при этом и плинтусы, и подоконники имеют общие свойства древесины, но вместе с тем и некоторые специфические свойства. Наследование упрощает программирование, позволяя создать универсальные методы для выполнения всего, что основано на общих свойствах дверей, и затем написать специфические методы для выполнения специфических операций над конкретными типами дверей. Некоторые операции, такие как `Open()` или `Close()`, будут универсальными для всех дверей: внутренних, входных, стеклянных, стальных — каких угодно. Поддержка языком операций вроде `Open()` или `Close()` при отсутствии информации о конкретном типе двери вплоть до периода выполнения называется полиморфизмом. Объектно-ориентированные языки, такие как C++, Java и более поздние версии Microsoft Visual Basic, поддерживают и наследование, и полиморфизм.
В объектно-ориентированном программировании под агрегированием (также называемом композицией или включением) подразумевают методику создания нового класса из уже существующих классов путём включения, называемого также делегированием. Об агрегировании также часто говорят как об «отношении принадлежности» по принципу «у машины есть корпус, колёса и двигатель». Вложенные объекты нового класса обычно объявляются закрытыми, что делает их недоступными для прикладных программистов, работающих с классом. С другой стороны, создатель класса может изменять эти объекты, не нарушая при этом работы существующего клиентского кода. Кроме того, замена вложенных объектов на стадии выполнения программы позволяет динамически изменять её поведение. Механизм наследования такой гибкостью не обладает, поскольку для производных классов устанавливаются ограничения, проверяемые на стадии компиляции. На базе агрегирования реализуется методика делегирования, когда поставленная перед внешним объектом задача перепоручается внутреннему объекту, специализирующемуся на решении задач такого рода.
Агрегация (агрегирование по ссылке) — отношение «часть-целое» между двумя равноправными объектами, когда один объект (контейнер) имеет ссылку на другой объект. Оба объекта могут существовать независимо: если контейнер будет уничтожен, то его содержимое — нет.
Композиция (агрегирование по значению) — более строгий вариант агрегирования, когда включаемый объект может существовать только как часть контейнера. Если контейнер будет уничтожен, то и включённый объект тоже будет уничтожен.
```objectivec
@interface Unicycle : NSObject {
	Pedal *pedal;
	Tire *tire;
}
@end
```
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/abstract_classes.png">
(Абстрактный класс белым цветом)

#### Как имитировать множественное наследование?
Композиция:
```objectivec
@interface ClassA : NSObject {
}
- (void)methodA;
@end

@interface ClassB : NSObject {
}

- (void)methodB;
@end

@interface MyClass : NSObject {
	ClassA *a;
	ClassB *b;
}
- (id)initWithA:(ClassA *)anA b:(ClassB *)aB;
- (void)methodA;
- (void)methodB;
@end
```
__Полиморфизм__ – возможность объектов с одинаковой спецификацией иметь различную реализацию (использование одного имени для решения двух или более схожих, но технически разных задач). Если функция описывает разные реализации (возможно, с различным поведением) для ограниченного набора явно заданных типов и их комбинаций, это называется ситуативным полиморфизмом (ad hoc polimorphism). Ситуативный полиморфизм поддерживается во многих языках посредством перегрузки функций и методов.
Если же код написан отвлеченно от конкретного типа данных и потому может свободно использоваться с любыми новыми типами, имеет место параметрический полиморфизм. Некоторые языки совмещают различные формы полиморфизма, порой сложным образом, что формирует самобытную идеологию в них и влияет на применяемые методологии декомпозиции задач. Например, в Smalltalk любой класс способен принять сообщения любого типа, и либо обработать его самостоятельно (в том числе посредством интроспекции), либо ретранслировать другому классу — таким образом, несмотря на широкое использование перегрузки функций, формально любая операция является неограниченно полиморфной и может применяться к данным любого типа.

### Другие понятия ООП
__Конструктор__

В объектно-ориентированном программировании конструктор класса (от англ. constructor, иногда сокращают ctor) — специальный блок инструкций, вызываемый при создании объекта.
Конструктор схож с методом, но отличается от метода тем, что не имеет явным образом определённого типа возвращаемых данных, не наследуется, и обычно имеет различные правила для рассматриваемых модификаторов. Конструкторы часто выделяются наличием одинакового имени с именем класса, в котором объявляется. Их задача — инициализировать члены объекта и определить инвариант класса, сообщив в случае некорректности инварианта. Корректно написанный конструктор оставит объект в «правильном» состоянии. Неизменяемые объекты тоже должны быть проинициализированы конструктором.
В большинстве языков конструктор может быть перегружен, что позволяет использовать несколько конструкторов в одном классе, причём каждый конструктор может иметь различные параметры.

__Деструктор__

Вызывается при уничтожении объекта. Он обычно используется для освобождения памяти.

__Виртуальный метод__

В объектно-ориентированном программировании метод (функция) класса, который может быть переопределён в классах-наследниках так, что конкретная реализация метода для вызова будет определяться во время исполнения. Таким образом, программисту необязательно знать точный тип объекта для работы с ним через виртуальные методы: достаточно лишь знать, что объект принадлежит классу или наследнику класса, в котором метод объявлен. Виртуальные методы — один из важнейших приёмов реализации полиморфизма. Они позволяют создавать общий код, который может работать как с объектами базового класса, так и с объектами любого его класса-наследника. При этом базовый класс определяет способ работы с объектами и любые его наследники могут предоставлять конкретную реализацию этого способа. В некоторых языках программирования, например в Java, нет понятия виртуального метода, данное понятие следует применять лишь для язы-ков, в которых методы родительского класса не могут быть переопределены по умолчанию, а только с помощью некоторых вспомогательных ключевых слов. В некоторых же (как, например, в Python), все методы — виртуальные.
Базовый класс может и не предоставлять реализации виртуального метода, а только декларировать его существование. Такие методы без реализации называются «чистыми виртуальными» (перевод англ.  pure virtual) или абстрактными. Класс, содержащий хотя бы один такой метод, тоже будет абстрактным. Объект такого класса создать нельзя (в некоторых языках допускается, но вызов абстрактного метода при-ведёт к ошибке). Наследники абстрактного класса должны предоставить реализацию для всех его абстрактных методов, иначе они, в свою очередь, будут абстрактными классами.
Для каждого класса, имеющего хотя бы один виртуальный метод, создаётся таблица виртуальных методов. Каждый объект хранит указатель на таблицу своего класса. Для вызова виртуального метода используется такой механизм: из объекта берётся указатель на соответствующую таблицу виртуальных методов, а из неё, по фиксированному смещению, — указатель на реализацию метода, используемого для данного класса. При использовании множественного наследования ситуация несколько усложняется за счёт того, что таблица виртуальных методов становится нелинейной.
__Принцип единственной обязанности__ (Single responsibility principle) обозначает, что каждый объект должен иметь одну обязанность и эта обязанность должна быть полностью инкапсулирована в класс. Все его сервисы должны быть направлены исключительно на обеспечение этой обязанности.

## В чем плюсы и минусы ООП?
__Общие положения__

_Преимущества_

* Классы позволяют проводить конструирование из полезных компонент, обладающих простыми инструментами, что дает возможность абстрагироваться от деталей реализации.

_Недостатки_

* ООП порождает огромные иерархии классов, что приводит к тому, что функциональность расползается или, как говорят, размывается по базовым и производным членам класса, и отследить логику работы того или иного метода становится сложно.

__Полиморфизм__

_Преимущества_

* Можно создавать новые классы с помощью протокола, «ведущие себя» аналогично родственным, что, в свою очередь, позволяет достигнуть расширяемости и модифицируемости, что помогает снижать сложность программ, разрешая использование того же интерфейса для задания единого класса действий. "Один интерфейс, множество методов"
* Возможность создавать переменные и методы с одинаковым именем, но ведущие себя по-разному в зависимости от контекста (локальные переменные и перекрытие методов)
* Обработка разнородных структур данных. Программы могут работать, не утруждая себя изучением вида объектов. Новые виды могут быть добавлены в любой момент.
```objectivec
for (id object in array) {
    NSLog(@"%@", object);
}
```
* Реализация родовых компонент. Алгоритмы можно обобщать до такой степени, что они уже смогут работать более, чем с одним видом объектов.
Доведение полуфабрикатов. Компоненты нет надобности подстраивать под определенное приложение. Их можно сохранять в библиотеке в виде полуфабрикатов (semifinished products) и расширять по мере необходимости до различных законченных продуктов.
Расширение фреймворка. Независимые от приложения части предметной области могут быть реализованы в виде фреймворка и в дальнейшем расширены за счет добавления частей, специфичных для конкретного приложения.

_Недостатки_

* На скорости выполнения программ может неблагоприятно сказаться реализация полиморфизма, которая основана на механизмах позднего связывания вызова метода с конкретной его реализацией в одном из производных классов.
* Многоразовое использование требует от программиста познакомиться с большими библиотеками классов. А это может оказаться сложнее, чем даже изучение нового языка программирования. Библиотека классов фактически представляет собой виртуальный язык, который может включать в себя сотни типов и тысячи операций.
* В некоторых языках все данные являются объектами, в том числе и элементарные типы, а это не может не приводить к дополнительным расходам памяти и процессорного времени.
* Изменение поведения во время выполнения. На этапе выполнения один объект может быть заменен другим. Это может привести к изменению алгоритма, в котором используется данный объект.

__Инкапсуляция__

_Преимущества_

* Сокрытие данных от несанкционированного доступа
* Инкапсуляция повышает надежность работы программного кода, поскольку гарантирует, что определенные данные не могут быть изменены за пределами содержащего их класса.

_Недостатки_

* Функции представляют собой черные ящики, которые трансформируют ввод в вывод. Если я понимаю ввод и вывод, то я понимаю функцию. Это не означает, что я могу написать эту функцию.
* В то время как состояние в языках программирования является нежелательным, реальный мир богат на состояния. Я очень интересуюсь состоянием моего банковского счета. И когда я вкладываю или снимаю с него деньги, я ожидаю, что его состояние будет корректно обновлено. Выбранный ООЯП подход “спрятать состояние от программиста” является наихудшим возможным выбором. Вместо показа состояния и поиска путей для минимизации неудобств от него, они прячут его поглубже.
* Очень трудно изучать классы, не имея возможности их «пощупать». Только с приобретением мало-мальского опыта можно уверенно себя почувствовать при работе с использованием ООП. Поэтому проектирование классов — задача куда более сложная, чем их использование. Проектирование класса, как и проектирование языка, требует большого опыта. Это итеративный процесс, где приходится учиться на своих же ошибках.

__Наследование__

_Преимущества_

* Когда вас почти устраивает какой-то класс, вы можете создать потомка и переопределить какую-то часть его функциональности.
* Лаконичность абстракции данных, созданной с помощью наследования, является преимуществом. Используя наследование, не обязательно писать весь код для доступа к функциям базового класса. По этой причине реализации с использованием наследования (как это было в нашем случае) значительно меньше по объему, если сравнить их с композицией.

_Недостатки_

* Унаследовавшись от одного предка, класс уже не может наследоваться от других. Изменение предка так же становится опасным.
* О степени понятности кода судить трудно. Чтобы точно знать, какие операции разрешены для новой структуры, программист должен рассмотреть объявление ис-ходной структуры. Трудность состоит в следующем: чтобы понять класс, сконструированный с помощью наследования, программист должен постоянно переключаться «взад-вперед» между двумя (или более) описаниями классов. Она известна как проблема «вверх-вниз». В сложных иерархиях классов поля и методы обычно наследуются с разных уровней. И не всегда легко определить, какие поля и методы фактически относятся к данному классу.
* Наследование – уничтожение инкапсуляции. Любой класс всегда неявно объявляет свой интерфейс — то, что доступно при использовании класса извне. Если у нас есть класс Ключ и у него публичный метод Открыть, который вызывает приватные методы Вставить, Повернуть и Вынуть, то интерфейс класса Ключ состоит из метода Открыть. Когда мы унаследуем какой-то класс от класса Ключ, он унаследует этот интерфейс. Кроме этого интерфейса, у класса есть также реализация — методы Вставить, Повернуть, Вынуть и их вызов в методе Открыть. Наследники Ключа наследуют вместе с интерфейсом и реализацию. И вот здесь таятся проблемы.

# Паттерны проектирования
Повторимая архитектурная конструкция, представляющая собой решение проблемы проектирования в рамках некоторого часто возникающего контекста.

__How Cocoa Adapts Design Patterns__

You can find adaptations of design patterns throughout Cocoa, in both its OS X and iOS versions. Mechanisms and architectures based on patterns are common in Cocoa frameworks and in the Objective-C runtime and language. Cocoa often puts its own distinctive spin on a pattern because its designs are influenced by factors such as language capabilities or existing architectures.
This section contains summaries of most of the design patterns cataloged in Design Patterns: Elements of Reusable Object-Oriented Software. Each section not only summarizes the pattern but discusses the Cocoa implementations of it. Only patterns that Cocoa implements are listed, and each description of a pattern in the following sections pertains to a particular Cocoa context.
Implementations of design patterns in Cocoa come in various forms. Some of the designs described in the following sections, such as protocols and categories, are features of the Objective-C language. In other cases, the “instance of a pattern” is implemented in one class or a group of related classes (for example, class clusters and singleton classes). And in other cases the pattern adaptation is a major framework architecture, such as the responder chain. Some of the pattern-based mechanisms you get almost “for free” while others require some work on your part. And even if Cocoa does not implement a pattern, you are encouraged to do so yourself when the situation warrants it; for example, object composition (Decorator pattern) is often a better technique than subclassing for extending class behavior.
Two design patterns are reserved for later sections, Model-View-Controller (MVC) and object modeling. MVC is a compound, or aggregate pattern, meaning that it is based on several catalog patterns. Object modeling has no counterpart in the Gang of Four catalog, instead originating from the domain of relational databases. Yet MVC and object modeling are perhaps the most important and pervasive design patterns in Cocoa, and to a large extent they are interrelated patterns. They play a crucial role in the design of several technologies, including bindings, undo management, scripting, and the document architecture. To learn more about these patterns, see The Model-View-Controller Design Pattern and Object Modeling.

## Что такое SOLID?
SOLID (сокр. от англ. Single responsibility, Open-closed, Liskov substitution, Interface segregation и Dependency inversion) - акроним, введённый Майклом Фэзерсом для первых пяти принципов, названных Робертом Мартином в начале 2000-х, которые означали пять основных принципов ООП и проектирования.
* Принцип единственной ответственности обозначает, что каждый объект должен иметь одну ответственность и эта ответственность должна быть полностью инкапсулирована в класс. Все его поведения должны быть направлены исключительно на обеспечение этой ответственности. Следующие приёмы позволяют соблюдать принцип единственной ответственности: разработка через тестирование, выделение класса, фасад, Proxy, DAO.
* Принцип открытости / закрытости означает, что программные сущности должны быть:
1. открыты для расширения: означает, что поведение сущности может быть расширено, путём создания новых типов сущностей.
2. закрыты для изменения: в результате расширения поведения сущности, не должны вносится изменения в код, которые эти сущности использует.
* Принцип подстановки Барбары Лисков даёт определение понятия замещения — если `S` является подтипом `T`, тогда объекты типа `T` в программе могут быть замещены объектами типа `S` без каких-либо изменений желательных свойств этой программы (например, корректность). Более простыми словами можно сказать, что поведение наследуемых классов не должно противоречить поведению, заданному базовым классом, то есть поведение наследуемых классов должно быть ожидаемым для кода, использующего переменную базового типа.
* Принцип разделения интерфейса Роберт Мартин определил так: «Клиенты не должны зависеть от методов, которые они не используют». Принцип разделения интерфейсов говорит о том, что слишком «толстые» интерфейсы необходимо разделять на более маленькие и специфические, чтобы клиенты маленьких интерфейсов знали только о методах, которые необходимы им в работе. В итоге, при изменении метода интерфейса не должны меняться клиенты, которые этот метод не используют.
* Принцип инверсии зависимостей — принцип, используемый для уменьшения зацепления в компьютерных программах.
1. Модули верхних уровней не должны зависеть от модулей нижних уровней. Оба типа модулей должны зависеть от абстракций.
2. Абстракции не должны зависеть от деталей. Детали должны зависеть от абстракций.

## Архитектурные паттерны
### MVC
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/mvc.png">
Модель состоит из классов, в которых хранятся данные приложения.
Представление создает дизайн.
Контроллер связывает модель и представление и организует логику приложения.
Пассивная модель — модель не имеет никаких способов воздействовать на представление или контроллер, и используется ими в качестве источника данных для отображения. Все изменения модели отслеживаются контроллером и он же отвечает за перерисовку представления, если это необходимо. Такая модель чаще используется в структурном программировании, так как в этом случае модель представляет просто структуру данных, без методов их обрабатывающих.
Активная модель — модель оповещает представление о том, что в ней произошли изменения, а представления, которые заинтересованы в оповещении, подписываются на эти сообщения. Это позволяет сохранить независимость модели как от контроллера, так и от представления.

### MVP
Шаблон проектирования, производный от MVC, который используется в основном для построения пользовательского интерфейса. Элемент Presenter в данном шаблоне берёт на себя функциональность посредника (аналогично контроллеру в MVC) и отвечает за управление событиями пользовательского интерфейса (например, использование мыши) так же, как в других шаблонах обычно отвечает представление. Был разработан для облегчения автоматического модульного тестирования и улучшения разделения ответственности в презентационной логике (отделения логики от отображения):
* Модель (англ. Model) — предоставляет данные для пользовательского интерфейса.
* Представление (англ. View) — реализует отображение данных (Модели) и маршрутизацию пользовательских команд или событий Presenterʼу.
* Presenter — управляет Моделью и Представлением. Например, извлекает данные из Модели и форматирует их для отображения в Представлении.
Обычно экземпляр Представления создаёт экземпляр Presenterʼа, передавая ему ссылку на себя. При этом Presenter работает с Представлением в абстрактном виде, через его интерфейс. Когда вызывается событие Представления, оно вызывает конкретный метод Presenterʼа, не имеющего ни параметров, ни возвращаемого значения. Presenter получает необходимые для работы метода данные о состоянии пользовательского интерфейса через интерфейс Представления и через него же передаёт в Представление данные из Модели и другие результаты своей работы.

### MVVM
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/mvc.png">
View и Model в связке. ViewModel – абстракция представления, с другой стороны – обертка Model. Содержит Model, готовую к представлению, а также команды представления для того, чтобы влиять на Model. Используется для разделения модели и её представления, что необходимо для изменения их отдельно друг от друга. Например, разработчик задает логику работы с данными, а дизайнер соответственно работает с пользовательским интерфейсом.

* is compatible with your existing MVC architecture
* makes your apps more testable
* works best with a binding mechanism

MVVM удобно использовать вместо классического MVC и ему подобных в тех случаях, когда в платформе, на которой ведётся разработка, присутствует «связывание данных». В шаблонах проектирования MVC/MVP изменения в пользовательском интерфейсе не влияют непосредственно на Mодель, а предварительно идут через Контроллер или Presenter.

### VIPER
* View: displays what it is told to by the Presenter and relays user input back to the Presenter.
* Interactor: contains the business logic as specified by a use case.
* Presenter: contains view logic for preparing content for display (as received from the Interactor) and for reacting to user inputs (by requesting new data from the Interactor).
* Entity: contains basic model objects used by the Interactor.
* Routing: contains navigation logic for describing which screens are shown in which order.

## Порождающие шаблоны
Шаблоны проектирования, которые абстрагируют процесс инстанцирования. Они позволяют сделать систему независимой от способа создания, композиции и представления объектов. Шаблон, порождающий классы, использует наследование, чтобы изменять инстанцируемый класс, а шаблон, порождающий объекты, делегирует инстанцирование другому объекту.

### Abstract factory
Предоставляет интерфейс для создания семейств взаимосвязанных или взаимозависимых объектов, не специфицируя их конкретных классов. Шаблон реализуется созданием абстрактного класса Factory, который представляет собой интерфейс для создания компонентов системы (например, для оконного интерфейса он может создавать окна и кнопки). Затем пишутся классы, реализующие этот интерфейс.
* Система не должна зависеть от того, как создаются, компонуются и представляются входящие в неё объекты.
* Входящие в семейство взаимосвязанные объекты должны использоваться вместе и вам необходимо обеспечить выполнение этого ограничения.
* Система должна конфигурироваться одним из семейств составляющих её объектов.
* Требуется предоставить библиотеку объектов, раскрывая только их интерфейсы, но не реализацию.

### Factory Method
Также известен как Виртуальный конструктор — порождающий шаблон проектирования, предоставляющий подклассам интерфейс для создания экземпляров некоторого класса. В момент создания наследники могут определить, какой класс создавать. Иными словами, Фабрика делегирует создание объектов наследникам родительского класса. Это позволяет использовать в коде программы не специфические классы, а манипулировать абстрактными объектами на более высоком уровне.

_Плюсы_

* позволяет сделать код создания объектов более универсальным, не привязываясь к конкретным классам (ConcreteProduct), а оперируя лишь общим интерфейсом (Product)
* позволяет установить связь между параллельными иерархиями классов

_Минусы_

* необходимость создавать наследника Creator для каждого нового типа продукта (ConcreteProduct). Впрочем, современные языки программирования поддерживают конструкции, что позволяет реализовать фабричный метод без иерархии классов Creator

### Lazy initialization
Приём в программировании, когда некоторая ресурсоёмкая операция (создание объекта, вычисление значения) выполняется непосредственно перед тем, как будет использован её результат. Таким образом, инициализация выполняется «по требованию», а не заблаговременно. Аналогичная идея находит применение в самых разных областях: например, компиляция «на лету» и логистическая концепция «Точно в срок». Частный случай ленивой инициализации — создание объекта в момент обращения к нему — является одним из порождающих шаблонов проектирования.

_Достоинства_

* Инициализация выполняется только в тех случаях, когда она действительно необходима
* Ускоряется начальная инициализация

_Недостатки_

* Невозможно явным образом задать порядок инициализации объектов
* Возникает задержка при первом обращении к объекту
```objectivec
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
	static NSString *CellIdentifier = @"CellIdentifier";
	cell = [tableView dequeueReusableCellWithIdentifier:CellIdentifier];
	if (cell == nil) {
		//ленивая загрузка
		cell = [[UITableViewCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:CellIdentifier];
	}
	cell.textLabel.text = someText;
	return cell;
}
```

### Singleton
Существует в системе в единственном экземпляре => не может быть повторно создан. Объект, к которому обращаются много объектов. Примеры синглтонов в системе:
```objectivec
[NSUserDefaults standardUserDefaults];
[UIApplication sharedApplication];
[UIScreen mainScreen];
[NSFileManager defaultManager];
```
_Non thread safe_
```objectivec
@implementation Singleton
static Singleton *sharedSingleton_ = nil;
+ (Singleton *)sharedInstance {
	if (sharedSingleton_ == nil) {
		sharedSingleton_ = [[Singleton alloc] init];
	}
	return sharedSingleton_;
}
@end
```
However this is wrong on several levels. Firstly, this isn't thread safe, so what happens if multiple threads all try to access this at the same time? There is no reason 1 thread couldn't be in the middle of allocating the object while the other one is trying to access the object. This is actually what Apple shows in its documentation.
If you must use singletons, use `dispatch_once()`
dispatch_once() solves the problem of safely being able to create a singleton in that (1) it guarantees that the code in the block will only be called once for the lifetime of the application (2) its thread safe as I noted in a previous article and (3) its faster than other methods like using `@synchronize()`,etc...
"If called simultaneously from multiple threads, this function waits synchronously until the block has completed." So you should be writing it like this...

_Thread safe_
```objectivec
+ (MyClass *)singleton {
	static dispatch_once_t pred;
	static MyClass *shared = nil;
	dispatch_once(&pred, ^{
		shared = [[MyClass alloc] init];
	});
	return shared;
}
```

__Criticism:__

1. It violates the single responsibility principle because of its quality of controlling its own creation and lifecycle.
2. It introduces global state to your application. I would say global state is very bad because any code can change its value. So at the time of debugging it's really hard to find which portion of the code has made the current stage of global variable.
3. Singleton is generally a bad idea if you are doing unit testing, and it's generally a bad idea not to perform unit testing.

## Структурные шаблоны
Определяют различные сложные структуры, которые изменяют интерфейс уже существующих объектов или его реализацию, позволяя облегчить разработку и оптимизировать программу.

### Adapter
The Adapter design pattern converts the interface of a class into another interface that clients expect. Adapter lets classes work together that couldn’t otherwise because of incompatible interfaces. It decouples the client from the class of the targeted object.

__Protocols__

A protocol is a language-level (Objective-C) feature that makes it possible to define interfaces that are instances of the Adapter pattern. A protocol is essentially a series of method declarations unassociated with a class. (In Java, interface is synonymous with protocol.) If you want a client object to communicate with another object, but the objects’ incompatible interfaces make that difficult, you can define a protocol. The class of the other object then formally adopts the protocol and “conforms” to it by implementing one or more of the methods of the protocol. The protocol may require the conforming class to implement some of its methods and may leave the implementation of others optional. The client object can then send messages to the other object through the protocol interface.
Protocols make a set of method declarations independent of the class hierarchy. They make it possible to group objects on the basis of conformance to a protocol as well as class inheritance. The `NSObject` method `conformsToProtocol:` permits you to verify an object’s protocol affiliation.
Cocoa has informal protocols as well as formal protocols. An informal protocol is a category on the `NSObject` class, thus making any object a potential implementer of any method in the category. The methods in an informal protocol can be selectively implemented. Informal protocols are part of the implementation of the delegation mechanism in OS X.
Note that the design of protocols does not perfectly match the description of the Adapter pattern. But it achieves the goal of the pattern: allowing classes with otherwise incompatible interfaces to work together.

_Uses and Limitations_

You use a protocol primarily to declare an interface that hierarchically unrelated classes are expected to conform to if they want to communicate. But you can also use protocols to declare an interface of an object while concealing its class. The Cocoa frameworks include many formal protocols that enable custom subclasses to communicate with them for specific purposes. For example, the Foundation framework includes the `NSObject`, `NSCopying`, and `NSCoding` protocols, which are all very important ones. AppKit protocols include `NSDraggingInfo`, `NSTextInput`, and `NSChangeSpelling`. `UIKit` protocols include `UITextInputTraits`, `UIWebViewDelegate`, and `UITableViewDataSource`.
Formal protocols implicitly require the conforming class to implement all declared methods. However, they can mark single methods or groups of methods with the `@optional` directive, and the conforming class may choose to implement those. They are also fragile; once you define a protocol and make it available to other classes, future changes to it (except for additional optional methods) can break those classes.

### Decorator
The Decorator design pattern attaches additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality. As does subclassing, adaptation of the Decorator pattern allows you to incorporate new behavior without modifying existing code. Decorators wrap an object of the class whose behavior they extend. They implement the same interface as the object they wrap and add their own behavior either before or after delegating a task to the wrapped object. The Decorator pattern expresses the design principle that classes should be open to extension but closed to modification.

_General Comments_

Decorator is a pattern for object composition, which is something that you are encouraged to do in your own code. Cocoa, however, provides some classes and mechanisms of its own that are based on the pattern. In these implementations, the extending object does not completely duplicate the interface of the object that it wraps, and the implementations use different techniques for interface sharing.
Cocoa uses the Decorator pattern in the implementation of several of its classes, including `NSAttributedString`, `NSScrollView`, `UIDatePicker`. The latter two classes are examples of compound views, which group together simple objects of other view classes and coordinate their interaction.

__Categories__

A category is a feature of the Objective-C language that enables you to add methods (interface and implementation) to a class without having to make a subclass. There is no runtime difference, within the scope of your program, between the original methods of the class and the methods added by the category. The methods in the category become part of the class type and are inherited by all the class’s subclasses.
As with delegation, categories are not a strict adaptation of the Decorator pattern, fulfilling the intent but taking a different path to implementing that intent. The behavior added by categories is a compile-time artifact, and is not something dynamically acquired. Moreover, categories do not encapsulate an instance of the class being extended.

_Uses and Limitations_

The Cocoa frameworks define numerous categories, most of them informal protocols (which are summarized in Protocols). Often they use categories to group related methods. You may implement categories in your code to extend classes without subclassing or to group related methods. However, you should be aware of these caveats: you cannot add instance variables to the class. If you override existing methods of the class, your application may behave unpredictably.

### Proxy
The Proxy design pattern provides a surrogate, or placeholder, for another object in order to control access to that other object. You use this pattern to create a representative, or proxy, object that controls access to another object, which may be remote, expensive to create, or in need of securing. This pattern is structurally similar to the Decorator pattern but it serves a different purpose; Decorator adds behavior to an object whereas Proxy controls access to an object.

__NSProxy__

The `NSProxy` class defines the interface for objects that act as surrogates for other objects, even for objects that don’t yet exist. A proxy object typically forwards a message sent to it to the object that it represents, but it can also respond to the message by loading the represented object or transforming itself into it. Although `NSProxy` is an abstract class, it implements the `NSObject` protocol and other fundamental methods expected of a root object; it is, in fact, the root class of a hierarchy just as the `NSObject` class is.
Concrete subclasses of `NSProxy` can accomplish the stated goals of the Proxy pattern, such as lazy instantiation of expensive objects or acting as sentry objects for security. `NSDistantObject`, a concrete subclass of `NSProxy` in the Foundation framework, implements a remote proxy for transparent distributed messaging. `NSDistantObject` objects are part of the architecture for distributed objects. By acting as proxies for objects in other processes or threads, they help to enable communication between objects in those threads or processes.
`NSInvocation` objects, which are an adaptation of the Command pattern, are also part of the distributed objects architecture.

_Uses and Limitations_

Cocoa employs `NSProxy` objects only in distributed objects. The `NSProxy` objects are specifically instances of the concrete subclasses `NSDistantObject` and `NSProtocolChecker`. You can use distributed objects not only for interprocess messaging (on the same or different computers) but you can also use it to implement distributed computing or parallel processing. If you want to use proxy objects for other purposes, such as the creation of expensive resources or security, you have to implement your own concrete subclass of `NSProxy`.

### Facade

The Facade design pattern provides a unified interface to a set of interfaces in a subsystem. The pattern defines a higher-level interface that makes the subsystem easier to use by reducing complexity and hiding the communication and dependencies between subsystems.

__NSImage__

The `NSImage` class of the AppKit framework provides a unified interface for loading and using images that can be bitmap-based (such as those in JPEG, PNG, or TIFF format) or vector-based (such as those in EPS or PDF format). NSImage can keep more than one representation of the same image; each representation is a kind of `NSImageRep` object. NSImage automates the choice of the representation that is appropriate for a particular type of data and for a given display device. It also hides the details of image manipulation and selection so that the client can use many different underlying representations interchangeably.

_Uses and Limitations_

Because `NSImage` supports several different representations of what an image is, some requested attributes might not apply. For example, asking an image for the color of a pixel does not work if the underlying image representation is vector-based and device-independent.


### Кластеры
Class clusters are a design pattern that the Foundation framework makes extensive use of. Class clusters group a number of private concrete subclasses under a public abstract superclass. The grouping of classes in this way simplifies the publicly visible architecture of an object-oriented framework without reducing its functional richness. Class clusters are based on the Abstract Factory design pattern.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/cluster.png">

`NSMutableArray` is not a concrete class, it is just the abstract superclass of a class cluster. The documentation for `NSMutableArray` does have information about how to subclass, but also strongly advises you not to! Only subclass if you have a special need for actual storage. A class cluster means that the actual class will be chosen at runtime. An array created empty, may not use the same class as an array created with 1000 items. The runtime can do smart choices of what implementation to use for you. In practice `NSMutableArray` will be a bridged `CFArray`. Nothing you need to worry about, but you might see it if you inspect the type of your arrays in the debugger, you will never see `NSArray`, but quite often `NSCFArray`. As mentioned before, subclassing is not the same as extending a class. Objective-C has the concept of categories. A category is similar to what other programming languages call mixins. If you for example want a convenience method on `NSMutableArray` to sort all members on a property, then define the category interface in a .h file.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/cluster_description.png">

### Composite
The Composite design pattern composes related objects into tree structures to represent part-whole hierarchies. The pattern lets clients treat individual objects and compositions of objects uniformly.
The Composite pattern is part of the Model-View-Controller aggregate pattern, which is describe in The Model-View-Controller Design Pattern.

__View Hierarchy__

The views in a window are internally structured into a view hierarchy. At the root of the hierarchy is a window and its content view, a transparent view that fills the window’s content rectangle. Views that are added to the content view become subviews of it, and they become the superviews of any views added to them. Except for the content view, a view has one (and only one) superview and zero or any number of subviews. You perceive this structure as containment: a superview contains its subviews.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/view_hierarchy.png">

The view hierarchy is a structural architecture that plays a part in both drawing and event handling. A view has two bounding rectangles, its frame and its bounds, that affect how graphics operations with the view take place. The frame is the exterior boundary; it locates the view in its superview’s coordinate system, defines its size, and clips drawing to the view’s edges. The bounds, the interior bounding rectangle, defines the internal coordinate system of the surface where the view draws itself.
When a window is asked by the windowing system to prepare itself for display, superviews are asked to render themselves before their subviews. When you send some messages to a view, for example, a message that requests a view to redraw itself, the message is propagated to subviews. You can thus treat a branch of the view hierarchy as a unified view.
The view hierarchy is also used by the responder chain for handling events and action messages.

## Communication Patterns

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/communication_patterns.png">

### Observer
Определяет одно-ко-многим отношение между объектами, и если изменения происходят в объекте – все подписанные на него объекты тут же узнают про это изменение. Идея проста: объект который мы называем Subject – дает возможность другим объектам, которые реализуют интерфейс Observer, подписываться и отписываться от изменений происходящик в Subject. Когда изменение происходит – всем заинетерсованным объектам высылается сообщение, что изменение произошло. В нашем случае – Subject – это издатель газеты, Observer это мы с вами – те кто подписывается на газету, ну и собственно изменение – это выход новой газеты, а оповещение – отправка газеты всем кто подписался.
Когда используется паттерн:

* Когда Вам необходимо сообщить всем объектам подписанным на изменения, что изменение произошло, при этом вы не знаете типы этих объектов.
Изменения в одном объекте требуют чтоб состояние изменилось в других объектах, при чем количество объектов может быть разное.

### Делегирование
(англ. Delegation) — основной шаблон проектирования, в котором объект внешне выражает некоторое поведение, но в реальности передаёт ответственность за выполнение этого поведения связанному объекту. Паттерн хорош тем, что нам не нужно хранить всю логику в одном месте и позволяет лучше переиспользовать код. Рассматривайте делегат как обычный обьект, который может выполнять некоторые функции. Например, возьмем `NSTableView` delegate. Вы хотите отрисовать ячейку таблицы как-то по своему. `NSTableView` своему делегату пошлет сообщение о том, что он сейчас будет рисовать данную ячейку и делегат уже сам решает что с ней делать (рисовать по своему, не трогать вообще и т.д.). Это, грубо говоря, способ получения и предоставления информации, о которой `NSTableView` не знает вообще ничего.
Или же пример создания собственных делегатов. Представьте, что у вас есть свой класс, который выполняет некоторую функцию. Для выполнения некоторых задач ему необходима информация из другого класса, о котором сейчас не известно ровным счетом ничего, кроме того, что он существует. Тогда создается конструкция вида:
```objectivec
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
```
Как видно из примера — наш делегат, это просто указатель на какой-либо обьект. Ну и предоставлены геттер и сеттер. Для того, чтобы делегат выполнил некоторое действие для нас, где-то внутри нашего `Class1` мы пошлем сообщение вида
```objectivec
[delegate doSomeWork];
```
Обьект же, который мы назначили делегатом для данного класса в свою очередь получит это сообщение и начнет выполнять какое-то действие.
В принципе и все. Достаточно просто. Делегирование преследует простую цель — сохранять объекты слабо связанными. Таким образом, вы можете отправлять сообщения делегату, не зная какой именно это объект. А сам делегат, при этом, может выполнять разные действия в зависимости от своей реализации. Так что тут мы имеем одно из проявлений полиморфизма. То есть, грубо говоря, делегирующий объект говорит объекту-делегату ЧТО делать, но его не волнует КАК именно это будет сделано.
Плюс, делегирование порой может быть более удобной альтернативой наследованию — вместо того, чтобы плодить иерархию классов, вы определяете необходимый интерфейс для делегатов и используете их.
Delegation is a mechanism by which a host object embeds a weak reference (weak in the sense that it’s a simple pointer reference, unretained) to another object, its delegate, and periodically sends messages to the delegate when it requires its input for a task. The host object is generally an “off-the-shelf” framework object (such as `NSWindow` or `NSXMLParser` object) that is seeking to accomplish something, but can only do so in a generic fashion. The delegate, which is almost always an instance of a custom class, acts in coordination with the host object, supplying program-specific behavior at certain points in the task. Thus delegation makes it possible to modify or extend the behavior of another object without the need for subclassing.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/delegation.png">

Delegation, in the simple sense of one object delegating a task to another object, is a common technique in object-oriented programming. However, Cocoa implements delegation in a unique way. A host class uses a formal protocol or an informal protocol to define an interface that the delegate object may choose to implement. All the methods in the informal protocol are optional, and the formal protocol may declare optional methods, allowing the delegate to implement only some of the methods in the protocol. Before it attempts to send a message to its delegate, the host object determines whether it implements the method (via a `respondsToSelector:` message) to avoid runtime exceptions. For more on formal and informal protocols, see Protocols.
Some classes in the Cocoa frameworks also send messages to their data sources. A data source is identical in all respects to a delegate, except that the intent is to provide the host object with data to populate a browser, a table view, or similar user-interface view. A data source, unlike a delegate, may also be required to implement some methods of the protocol.
Delegation is not a strict implementation of the Decorator pattern. The host (delegating) object does not wrap an instance of the class it wants to extend; indeed, it’s the other way around, in that the delegate is specializing the behavior of the delegating framework class. There is no sharing of interface either, other than the delegation methods declared by the framework class.
Delegation in Cocoa is also part of the Template Method pattern (Template Method).

__Uses and Limitations__

Delegation is a common design in the Cocoa frameworks. Many classes in the AppKit and UIKit frameworks send messages to delegates, including `NSApplication`, `UIApplication`, `UITableView`, and several subclasses of `NSView`. Some classes in the Foundation framework, such as `NSXMLParser` and a `NSStream`, also maintain delegates. You should always use a class’s delegation mechanism instead of subclassing the class, unless the delegation methods do not allow you to accomplish your goal.
Although you can dynamically change the delegate, only one object can be a delegate at a time. Thus if you want multiple objects to be informed of a particular program event at the same time, you cannot use delegation. However, you can use the notification mechanism for this purpose. A delegate automatically receives notifications from its delegating framework object as long as the delegate implements one or more of the notification methods declared by the framework class. See the discussion of notifications in the Observer pattern.
Delegating objects in AppKit do not retain their delegates or data sources.

### KVC
Key-value coding is a mechanism for accessing an object’s properties indirectly, using strings to identify properties, rather than through invocation of an accessor method or accessing them directly through instance variables. In essence, key-value coding defines the patterns and method signatures that your application’s accessor methods implement.
Implementing key-value coding compliant accessors in your application is an important design principle. Accessors help to enforce proper data encapsulation, isolate memory management to centralized locations, and facilitate integration with other technologies such as key-value observing, Core Data, Cocoa bindings, and scriptability.
Соответствующие методы определены в `NSObject`, поэтому каждый объект
поддерживает данную возможность.
```objectivec
[a setProductName:@"Washing Machine"];
```
C использованием KVC:
```objectivec
[a setValue:@"Washing Machine" forKey:@"productName"];
```
Запись «ключ-значение» также позволяет прочитать значение переменной. Каждый раз, когда стандартная библиотека записывает данные в ваши объекты, она использует `setValue:forKey:`. Каждый раз, когда стандартная библиотека читает данные из ваших объектов, она использует `valueForKey:`. Например, библиотека СоrеData упрощает сохранение объектов в базе данных SQLite и их последующую загрузку. Для работы с пользовательским объектами, содержащими данные, используется запись «ключ-значение».
```objectivec
double totalSalary = 0.0;
for (Employee *employee in employees) {
	totalSalary += [employee.salary doubleValue];
}
double averageSalary = totalSalary / [employees count];
```
эквивалентно
```objectivec
[employees valueForKeyPath:@"@avg.salary"];
```
KVC Collection Operators allows actions to be performed on a collection using key path notation in `valueForKeyPath:`. Any time you see `@` in a key path, it denotes a particular aggregate function whose result can be returned or chained, just like any other key path. Collection Operators fall into one of three different categories, according to the kind of value they return:

1. Simple Collection Operators return strings, numbers, or dates, depending on the operator.
2. Object Operators return an array.
3. Array and Set Operators return an array or set, depending on the operator.

Simple Collection Operators

`@count` Returns the number of objects in the collection as an `NSNumber`.

`@sum` Converts each object in the collection to a double, computes the sum, and returns the sum as an `NSNumber`.

`@avg` Takes the double value of each object in the collection, and returns the average value as an `NSNumber`.

`@max` Determines the maximum value using `compare:`. Objects must support comparison with one another for this to work.

`@min` Same as `@max`, but returns the minimum value in the collection.

### KVO
Еще одна реализация патерна наблюдатель. В этом случае наблюдатель следит не за событиями, а за конкретным свойством объекта. Когда значение этого свойства меняется, наблюдателю приходит уведомление и он соответствующим образом реагируют.
По сравнению со многими другими языками реализация KVO в objective c радуют довольно простым синтаксисом. Так в коде наблюдателя достаточно написать:
```objectivec
[company_a addObserver:self forKeyPath:@"people" options:NSKeyValueObservingOptionNew context:nil];
```
И каждый раз когда в `company_a` будет изменяться значение переменной `people` наблюдатель будет уведомляться с помощью вызова метода
`- observeValueForKeyPath:(NSString *)keyPath ofObject:(id)object change:(NSDictionary *)change context:(void *)context` и надо лишь реализовать код, который будет реагировать на уведомление.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/kvo.png">

__Плюсы__

* Минимализм кода (достаточно написать всего лишь несколько строчек, чтобы полностью реализовать паттерн наблюдатель)
* Возможность слежения за любыми свойствами любых классов как написанными нами, так и чужими. Фактически внешние переменные всегда оформляются через свойства, что позволяет с легкостью следить любыми изменениями.

__Недостатки__

* Первая и очень важная проблема — это заметное падение производительности при обильном использовании KVO. Не стоит писать код, где ваши объекты общаются в основном через KVO. Рассматривайте KVO как вспомогательно средство для работы с чужим кодом, а не как основной инструмент.
* Второй проблемой является необходимость очень аккуратно писать код при использовании KVO. Так как строковые идентификаторов не проверяются компилятором на валидность, то это может привести к ошибкам при переименовании переменных. Также, KVO очень чувствительно к порядку добавления / удаления наблюдателей. Так, если наблюдатель пытается отписаться от наблюдаемого, на который наблюдатель в данный момент не подписан, то происходит крэш. Если же, наоброт, наблюдатель не отпишется до того, как наблюдаемый будет уничтожен, то произойдет утечка памяти. Все это приводит к тому, что легко прострелить себе ногу при добавлении / удалении наблюдателей из разных мест кода. Наиболее простой способ обезопасить себя – это хранить в наблюдателе ссылку на объект наблюдения, метод присвоения которой описан следующим образом:
```objectivec
- (void) setObservable:(id)observable {
	[_observable addObserver:self forKeyPath:@"property" options:NSKeyValueObservingOptionNew context:nil];
    _observable = observable;
    [_observable removeObserver:self forKeyPath:@"property"];
}
```
Таким образом соотношение между добавлением и удалением строго равно единице и нет необходимости тщательно следить где именно добавляется / удаляется наблюдение. Вызов деструктора также больше не является проблемой, так как перед уничтожением объекта в свойство запишется `nil`, попутно завершив наблюдение за объектом.

* Always handle nil and other unusual values gracefully
* Don't use accessors (or dot notation) in init or dealloc

### Notification
Notificaiton – механизм использования возможностей `NotificationCenter` самой операционной системы. Использование `NSNotificationCenter` позволяет объектам коммуницировать, даже не зная друг про друга. Это очень удобно использовать когда у вас в паралельном потоке пришел push-notification, или же обновилась база, и вы хотите дать об этом знать активному на даный момент View.
Чтобы послать такое сообщение стоит использовать конструкцию типа:
```objectivec
NSNotification *broadCastMessage = [NSNotification notificationWithName:@"broadcastMessage" object:self];
NSNotificationCenter *notificationCenter = [NSNotificationCenter defaultCenter];
```
Как видим, мы создали объект типа `NSNotification`, в котором мы указали имя нашего оповещения: `“broadcastMessage”`, и, собственно, сообщили о нем через `NotificationCenter`.
Чтобы подписаться на событие в объекте который заинтересован в изменении стоит использовать следующую конструкцию:
```objectivec
NSNotificationCenter *notificationCenter = [NSNotificationCenter defaultCenter];
[notificationCenter addObserver:self selector:@selector(update:) name:@"broadcastMessage" object:nil];
```
Собственно, из кода все более-менее понятно: мы подписываемся на событие, и вызывается метод который задан в свойстве `selector`.

## Поведенческие шаблоны
Определяют взаимодействие между объектами, увеличивая таким образом его гибкость.

### Chain of responsibility
Responder (ответчик) – объект, который может реагировать на события и обрабатывать их.
`responderObject : UIResponder; // or NSResponder in MacOS`
Цепочка ответственности позволяет вам передавать объекте по цепочке объектов-обработчиков, пока не будет найден необходимый объект обработчик.
First responder -> next responder -> …
Первый ответчик – ответчик, получивший события первым (например view).
Когда использовать этот паттерн:

* У вас более чем один объект-обработчик.
* У вас есть несколько объектов обработчика, при этом вы не хотите специфицировать, который объект должен обрабатывать в даный момент времени.

Примеры:
```objectivec
[foo becomeFirstResponder];
[foo resignFirstResponder];
[foo respondsToSelector:@selector(methodName:)];
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/responder_chain.png">

### The Target-Action Mechanism

The target-action mechanism enables a control object, that is, an object such as a button, slider, or text field, to send a message to another object that can interpret the message and handle it as an application, specific instruction. The receiving object, or the target, is usually a custom controller object. The message, named an action message, is determined by a selector, a unique runtime identifier of a method.
In the AppKit framework, the cell object that a control owns typically encapsulates the target and action. When the user clicks or otherwise activates the control, the control extracts the information from its cell and sends the message. (A menu item also encapsulates target and action, and sends an action message when the user chooses it.) The target-action mechanism can work on the basis of a selector (and not a method signature) because the signature of an action method in AppKit by convention is always the same.
In UIKit, the target, action mechanism does not rely on cells. Instead, a control maps a target and action to one or more multitouch events that can occur on the control.

_Uses and Limitations_

When creating a Cocoa application, you can set a control’s action and target through the Interface Builder application. You thereby let the control initiate custom behavior without writing any code for the control itself. The action selector and target connection are archived in a nib file and are restored when the nib is unarchived. You can also change the target and action dynamically by sending the control or its cell `setTarget:` and `setAction:` messages.
A Cocoa application for OS X can use the target-action mechanism to instruct a custom controller object to transfer data from the user interface to a model object, or to display data in a model object. The Cocoa bindings technology obviates the need to use target-action for this purpose.

_Uses and Limitations_

You create or modify a view hierarchy whenever you add a view to another view, either programmatically or using Interface Builder. The AppKit framework automatically handles all the relationships associated with the view hierarchy.

### Command
The Command design pattern encapsulates a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations. The request object binds together one or more actions on a specific receiver. The Command pattern separates an object making a request from the objects that receive and execute that request.

_Invocation Objects_

An instance of the `NSInvocation` class encapsulates an Objective-C message. An invocation object contains a target object, method selector, and method parameters. You can dynamically change the target of the message dispatched by the invocation object as well as its parameters; once the invocation is executed, you can also obtain the return value from the object. With a single invocation object, you can repeatedly invoke a message with multiple variations in target and parameters.
The creation of an `NSInvocation` object requires an `NSMethodSignature` object, which is an object that encapsulates type information related to the parameters and return value of a method. An `NSMethodSignature` object, in turn, is created from a method selector. The implementation of `NSInvocation` also makes use of functions of the Objective-C runtime.

_Uses and Limitations_

`NSInvocation` objects are part of the programmatic interfaces of distributed objects, undo management, message forwarding, and timers. You can also use invocation objects in similar contexts where you need to decouple an object sending a message from the object that receives the message.
The distributed objects technology is for interprocess communication.

### Iterator

The Iterator design pattern provides a way to access the elements of an aggregate object (that is, a collection) sequentially without exposing its underlying representation. The Iterator pattern transfers the responsibility for accessing and traversing the elements of a collection from the collection itself to an iterator object. The Iterator defines an interface for accessing collection elements and keeps track of the current element. Different iterators can carry out different traversal policies.

__Enumerators__

The `NSEnumerator` class in the Foundation framework implements the Iterator pattern. The private, concrete subclass of the abstract `NSEnumerator` class returns enumerator objects that sequentially traverse collections of various types, arrays, sets, dictionaries (values and keys), returning objects in the collection to clients.
`NSDirectoryEnumerator` is a distantly related class. Instances of this class recursively enumerate the contents of a directory in the file system.

_Uses and Limitations_

The collection classes such as `NSArray`, `NSSet`, and `NSDictionary` include methods that return an enumerator appropriate to the type of collection. All enumerators work in the same manner. You send a `nextObject` message to the enumerator object in a loop that exits when `nil` is returned instead of the next object in the collection.
You can also use fast enumeration to access the elements of a collection; this language feature is described in Fast Enumeration.

### Mediator

The Mediator design pattern defines an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently. These objects can thus remain more reusable.
A "mediator object” in this pattern centralizes complex communication and control logic between objects in a system. These objects tell the mediator object when their state changes and, in turn, respond to requests from the mediator object.

### Memento

The Memento pattern captures and externalizes an object’s internal state, without violating encapsulation, so that the object can be restored to this state later. The Memento pattern keeps the important state of a key object external from that object to maintain cohesion.

__Archiving__

Archiving converts the objects in a program, along with those objects’ properties (attributes and relationships) into an archive that can be stored in the file system or transmitted between processes or across a network. The archive captures the object graph of a program as an architecture-independent stream of bytes that preserves the identity of the objects and the relationships among them. Because an object’s type is stored along with its data, an object decoded from a stream of bytes is normally instantiated using the same class of the object that was originally encoded.

_Uses and Limitations_

Generally, you want to archive those objects in your program whose state you want to preserve. Model objects almost always fall into this category. You write an object to an archive by encoding it, and you read that object from an archive by decoding it. Encoding and decoding are operations that you perform using an `NSCoder` object, preferably using the keyed archiving technique (requiring you to invoke methods of the `NSKeyedArchiver` and `NSKeyedUnarchiver` classes). The object being encoded and decoded must conform to the `NSCoding` protocol; the methods of this protocol are invoked during archiving.

### State

With the state pattern, a state machine is implemented by implementing each individual state as a derived class of the state pattern interface, and implementing state transitions by invoking methods defined by the pattern's superclass. The state pattern can be interpreted as a strategy pattern which is able to switch the current strategy through invocations of methods defined in the pattern's interface. This pattern is used in computer programming to encapsulate varying behavior for the same object based on its internal state. This can be a cleaner way for an object to change its behavior at runtime without resorting to large monolithic conditional statements and thus improve maintainability.

## Анти-паттерны в объектно-ориентированном программировании
__Базовый класс-утилита (BaseBean):__ Наследование функциональности из класса-утилиты вместо делегирования к нему

__Вызов предка (CallSuper):__ Для реализации прикладной функциональности методу класса-потомка требуется в обязательном порядке вызывать те же методы класса-предка

__Ошибка пустого подкласса (Empty subclass failure):__ Создание класса (в Perl), который не проходит «проверку пустоты подкласса» («Empty Subclass Test») из-за различного поведения по сравнению с классом, который наследуется от него без изменений

__Божественный объект (God object):__ Концентрация слишком большого количества функций в одной части системы (классе)

__Объектная клоака (Object cesspool):__ Переиспользование объектов, находящихся в непригодном для переиспользования состоянии

__Полтергейст (Poltergeist):__ Объекты, чьё единственное предназначение — передавать информацию другим объектам

__Проблема йо-йо (Yo-yo problem):__ Чрезмерная размытость сильно связанного кода (например, выполняемого по порядку) по иерархии классов

__Одиночество (Singletonitis):__ Неуместное использование паттерна одиночка

__Приватизация (Privatisation):__ Сокрытие функциональности в приватной секции (private), что затрудняет его расширение в классах-потомках

__Френд-зона (Friend zone):__ Неуместное использование дружественных классов и дружественных функций в языке C++

## Какая разница между использованием делагатов и нотификейшенов?
Уведомление инкапсулирует информацию о событиях, таких как получения фокуса окном или закрытие сетевого соединения. Объекты, которым необходимо знать об этих событиях, регистрируются в центре уведомлений, и при возникновении зарегистрированного события, центр уведомлений информирует все зарегистрированные объекты об событии.

Делегат может модифицировать операцию или отказаться от нее, нотификейшн – прямой приказ.

Основные правила:

* Центры оповещений не владеют своими наблюдателями. Если объект является наблюдателем, он обычно удаляется из центра оповещений в своем методе `dealloc`:
```objectivec
- (void)dealloc {
	[[NSNotificationCenter defaultCenter] removeObserver:self];
}
```
* Объекты не владеют своими делегатами и источниками данных. Если вы создаете объект, который является делегатом или источником данных, он должен «попрощаться» в своем методе `dealloc`:
```objectivec
- (void)dealloc {
	[windowThatBossesMeAround setDelegate:nil];
	[tableViewThatBegsForData setDataSource:nil];
}
```
* Объекты не владеют своими приемниками. Если вы создаете объект, который является приемником, он должен обнулить указатель на приемник в своем методе `dealloc`:
```objectivec
- (void)dealloc {
	[buttonThatKeepsSendingMeMessages setTarget:nil];
}
```

__Делегат__

_Плюсы_

* Very strict syntax. All events to be heard are clearly defined in the delegate protocol.
* Compile time Warnings / Errors if a method is not implemented as it should be by a delegate.
* Protocol defined within the scope of the controller only.
* Very traceable, and easy to identify flow of control within an application.
* Ability to have multiple protocols defined one controller, each with different delegates.
* No third party object required to maintain / monitor the communication process.
* Ability to receive a returned value from a called protocol method. This means that a delegate can help provide information back to a controller.
* Распределение кода,  переиспользование => слабосвязанные объекты. Мой объект ничего не знает о делегате, но отправляет ему сообщение.

_Минусы_

* Many lines of code required to define:

(1) the protocol definition

(2) the delegate property in the controller

(3) the implementation of the delegate method definitions within the delegate itself.

* Need to be careful to correctly set delegates to nil on object deallocation, failure to do so can cause memory crashes by calling methods on deallocated objects.
* Although possible, it can be difficult and the pattern does not really lend itself to have multiple delegates of the same protocol in a controller (telling multiple objects about the same event)

__Нотификейшн__

_Плюсы_

* Easy to implement, with not many lines of code.
* Can easily have multiple objects reacting to the same notification being posted.
* Controller can pass in a context (dictionary) object with custom information (userInfo) related to the notification being posted.

_Минусы_

* No compile time to checks to ensure that notifications are correctly handled by observers.
* Required to unregister with the notification center if your previously registered object is deallocated.
* Not very traceable. Attempting to debug issues related to application flow and control can be very difficult.
* Third party object required to manage the link between controllers and observer objects.
* Notification Names, and UserInfo dictionary keys need to be known by both the observers and the controllers. If these are not defined in a common place, they can very easily become out of sync.
* No ability for the controller to get any information back from an observer after a notification is posted.

__Наблюдение__

_Плюсы_

* Can provide an easy way to sync information between two objects. For example, a model and a view.
* Allows us to respond to state changes inside objects that we did not create, and don’t have access to alter the implementations of (SKD objects).
* Can provide us with the new value and previous value of the property we are observing.
* Can use key paths to observe properties, thus nested objects can be observed.
* Complete abstraction of the object being observed, as it does not need any extra code to allow it to be observed.

_Минусы_

* The properties we wish to observe, must be defined using strings. Thus no compile time warnings or checking occurs.
* Refactoring of properties can leave our observation code no longer working.
* Complex “IF” statements required if an object is observing multiple values. This is because all observation code is directed through a single method.
* Need to remove the observer when it is deallocated.

***

# Objective-C
Компилируемый язык программирования, используемый корпорацией Apple, построенный на основе языка Си и парадигм Smalltalk. В частности, объектная модель построена в стиле Smalltalk — то есть объектам посылаются сообщения. Язык Objective-C является надмножеством языка Си, поэтому Си-код полностью понятен компилятору Objective-C. Компилятор Objective-C доступен на большинстве основных платформ. Язык используется в первую очередь для Mac OS X (Cocoa) и GNUstep — реализаций объектно-ориентированного интерфейса OpenStep. Также язык используется для iOS (Cocoa Touch). Objective-C был создан Брэдом Коксом в начале 1980-х в его компании Stepstone. Он искал возможность собирать программы из готовых компонентов (объектов), подобно тому как сложные электронные устройства могут быть легко собраны из набора готовых интегральных микросхем. При этом такой язык должен быть достаточно простым и основанным на языке Си, чтобы облегчить переход разработчиков на него. Таким образом, Objective-C является именно расширением языка Си — в язык Си просто добавлены новые возможности для объектно-ориентированного программирования. При этом любая программа на Си является программой и на Objective-C.
* Мультипарадигма́льный язы́к программи́рования — как правило, язык программирования, который был разработан специально как инструмент мультипарадигмального программирования, то есть изобразительные возможности которого изначально предполагалось унаследовать от нескольких, чаще всего неродственных языков. Иногда термин мультипарадигмальный язык программирования определяют как «язык, который поддерживает больше чем одну парадигму программирования». Цель разработки мультипарадигмальных языков программирования состоит, как правило, в том, чтобы позволить программистам использовать лучший инструмент для работы, признавая, что никакая парадигма не решает все проблемы самым лёгким или самым эффективным способом.
* Рефлексивно-ориентированный – в информатике отражение или рефлексия (синоним интроспекция, англ. reflection) означает процесс, во время которого программа может отслеживать и модифицировать собственную структуру и поведение во время выполнения. Парадигма программирования, положенная в основу отражения, называется рефлексивным программированием. An object refers to its class to get various information about itself, particularly what code to run to handle each action.
* Message-oriented – вызовы метода интерпретируются не как вызов функции (хотя к этому обычно все сводится), а именно как посылка сообщения (с именем и аргументами) объекту, подобно тому, как это происходит в Smalltalk-е. Такой подход дает целый ряд плюсов — так, любому объекту можно послать любое сообщение. Объект может вместо обработки сообщения просто переслать его другому объекту для обработки (так называемое делегирование), в частности именно так можно легко реализовать распределенные объекты (то есть объекты, находящиеся в различных адресных пространствах и даже на разных компьютерах). The receiver is an object, and the message tells it what to do. In source code, the message is simply the name of a method and any arguments that are passed to it. When a message is sent, the runtime system selects the appropriate method from the receiver’s repertoire and invokes it. Object can contain state, which in practical terms means that they can contain data and references to other objects. In implementation and use, state usually consists of member variables, instance data, or whatever terminology you use. Can receive messages sent from other objects. Can send messages to other objects.
* Runtime-oriented – динамичность, целый ряд решений, обычно принимаемых на этапе компиляции, здесь откладывается непосредственно до этапа выполнения. Примеры использования библиотеки рантайма - не рефлексии напрямую - получения списка всех наследников класса, маппинг объекта в словарь, динамическое добавление свойства в объект для динамических баз данных (это уже совсем рефлексия), свиззлинг для добавления дополнительной логики для методов системных фреймворков.
* Dynamic Typing – The id type is completely nonrestrictive. By itself, it yields no information about an object, except that it is an object. At some point, a program needs to find more specific information about the objects it contains—what the object’s instance variables are, what methods it can perform, and so on. Since the id type designator can’t supply this information to the compiler, each object has to be able to supply it at runtime. This is possible because every object carries with it an isa instance variable that identifies the object’s class—what kind of object it is. Objects are thus dynamically typed at runtime. Whenever it needs to, the runtime system can find the exact class that an object belongs to, just by asking the object. Dynamic typing in Objective-C serves as the foundation for dynamic binding. A crucial difference between function calls and messages is that a function and its arguments are joined together in the compiled code, but a message and a receiving object aren’t united until the program is running and the message is sent. Therefore, the exact method that’s invoked to respond to a message can only be determined at runtime, not when the code is compiled. This dynamic binding of methods to messages works hand-in-hand with polymorphism to give object-oriented programming much of its flexibility and power. Since each object can have its own version of a method, a program can achieve a variety of results, not by varying the message itself, but by varying just the object that receives the message. This can be done as the program runs; receivers can be decided “on the fly” and can be made dependent on external factors such as user actions. The compiler creates just one accessible object for each class, a class object that knows how to build new objects belonging to the class. (For this reason it’s traditionally called a “factory object.”) The class object is the compiled version of the class; the objects it builds are instances of the class. The objects that do the main work of your program are instances created by the class object at runtime. Утиная типизация – границы использования объекта определяются его текущим набором методов и свойств, в противоположность наследованию от определённого класса. То есть считается, что объект реализует интерфейс, если он содержит все методы этого интерфейса, независимо от связей в иерархии наследования и принадлежности к какому-либо конкретному классу. «Если нечто выглядит как утка, плавает как утка и крякает как утка, то это, наверное, и есть утка»

## Transparent and opaque data types
In computer science, an opaque data type is a data type whose concrete data structure is not defined in an interface. This enforces information hiding, since its values can only be manipulated by calling subroutines that have access to the missing information. The concrete representation of the type is hidden from its users, and the visible implementation is incomplete. A data type whose representation is visible is called transparent.[1] Opaque data types are frequently used to implement abstract data types.
Some languages, such as C, allow the declaration of opaque records (structs), whose size and fields are hidden from the client. The only thing that the client can do with an object of such a type is to take its memory address, to produce an opaque pointer. If the information provided by the interface is sufficient to determine the type's size, then clients can declare variables, fields, and arrays of that type, assign their values, and possibly compare them for equality. This is usually the case for opaque pointers.

## Toll-Free Bridged Types
There are a number of data types in the Core Foundation framework and the Foundation framework that can be used interchangeably. Data types that can be used interchangeably are also referred to as toll-free bridged data types. This means that you can use the same data structure as the argument to a Core Foundation function call or as the receiver of an Objective-C message invocation. But not all data types are toll-free bridged, even though their names might suggest that they are. Through toll-free bridging, in a method where you see for example an `NSLocale *parameter`, you can pass a `CFLocaleRef`, and in a function where you see a `CFLocaleRef` parameter, you can pass an `NSLocale` instance. You also have to provide other information for the compiler: first, you have to cast one type to the other; in addition, you may have to indicate the object lifetime semantics. The compiler understands Objective-C methods that return Core Foundation types and follow the historical Cocoa naming conventions. For example, the compiler knows that, in iOS, the `CGColor` returned by the `CGColor` method of `UIColor` is not owned. You must still use an appropriate type cast, as illustrated by this example:
```objectivec
NSMutableArray *colors = [NSMutableArray arrayWithObject:(id)[[UIColor darkGrayColor] CGColor]];
[colors addObject:(id)[[UIColor lightGrayColor] CGColor]];
```
The compiler does not automatically manage the lifetimes of Core Foundation objects. You tell the compiler about the ownership semantics of objects using either a cast (defined in `objc/runtime.h`) or a Core Foundation-style macro (defined in `NSObject.h`):
* `__bridge` transfers a pointer between Objective-C and Core Foundation with no transfer of ownership
* `__bridge_retained` or `CFBridgingRetain` casts an Objective-C pointer to a Core Foundation pointer and also transfers ownership to you. You are responsible for calling `CFRelease` or a related function to relinquish ownership of the object.
* `__bridge_transfer` or CFBridgingRelease moves a non-Objective-C pointer to Objective-C and also transfers ownership to ARC. ARC is responsible for relinquishing ownership of the object.

# Xcode, фреймворки
Cocoa (в пер. с англ. - какао) — родная объектно-ориентированная среда разработки приложе-ний для операционной системы Mac OS X производства компании Apple. Это один из пяти ос-новных API, доступных в Mac OS X, — Cocoa, Carbon, Toolbox (для работы старых приложений Mac OS 9), POSIX и Java. Такие языки, как Perl, Python и Ruby не считаются основными, так как на них пока что пишется не так много серьёзных приложений для Mac OS X.
Приложения, использующие Cocoa, обычно разрабатываются с помощью среды разработки Apple Xcode (в прошлом называвшегося Project Builder) и Interface Builder с использованием языка Objective-C. Однако, среда Cocoa также доступна и при разработке на других языках, та-ких как Ruby, Python и Perl с помощью связующих библиотек (MacRuby, PyObjC и CamelBones соответственно). Также можно писать Cocoa-программы на Objective-C в обычном текстовом редакторе и вручную компилировать их с помощью GCC или make-сценариев для GNUstep.
Cocoa Touch — это фреймворк для создания приложений под iPhone, iPod touch, и iPad.
Библиотека Cocoa Touch предоставляет уровень абстракции для iOS (операционной системы iPhone, iPad и iPod touch). Cocoa Touch основана на классах фреймворка Cocoa, используемого в Mac OS X, и, аналогично ей, использует язык Objective-C. Cocoa Touch следует шаблону проектирования Model-View-Controller.
Инструменты для разработки приложений с использованием Cocoa Touch включены в iOS SDK. iOS-технологии можно рассматривать как набор слоев, где Cocoa Touch находится на самом высоком уровне, а Core OS и ядро Mac OS X — на более низких. Это позволяет реализовывать многие сложные задачи, сокращая объём работы, которую пришлось бы проделывать разра-ботчикам, работай они на более низком уровне. Тем не менее, некоторые низкие слои абстра-гирования могут быть доступны разработчикам по мере необходимости. Расположение слоев абстрагирования можно представить в следующем виде (от высшего к низшему):
* Cocoa Touch
* Media / Application Services
* Core Services
* Core OS / ядро Mac OS X

Аудио и Видео
* Core Audio
* OpenAL
* Media Library
* AV Foundation

Графика и анимация
* Core Animation
* OpenGL ES
* Quartz 2D

Прикладные программы
* Address Book
* Core Location
* Map Kit
* Store Kit

Управление данными
* Core Data
* SQLite
* Сети и Интернет
* Bonjour
* WebKit
* BSD Sockets

__Core Animation__

Используйте Core Animation для создания богатых пользовательских интерфейсов с легкой моделью программирования на основе композиции независимых слоев графики.

__Core Audio__

Core Audio является профессиональной технологией для воспроизведения, обработки и записи звука, что позволяет легко добавлять мощные звуковые функции к вашему приложению.

__Core Data__

Core Data обеспечивает объектно-ориентированное решение для управления данными, кото-рое легко в использовании и понимании, построено для обработки модели данных необходи-мых любому приложению, как большому так и маленькому.

__Core Text__ is an advanced, low-level technology for laying out text and handling fonts.
Core Text is for apps that need a low-level text-handling technology correlating with the Core Graphics framework (Quartz). If you work directly with Quartz and you need to draw some text, use Core Text. If, for example, you have your own page layout engine—you have some text and you know where it needs to go in your view—you can use Core Text to generate the glyphs and position them relative to each other with all the features of fine typesetting, such as kerning, ligatures, line-breaking, hyphenation, and justification.
Core Text Lays Out Text. Core Text generates glyphs (from character codes and font data) and positions them relative to each other in glyph runs. It breaks glyph runs into lines, and it assembles lines into multiline frames (such as paragraphs). Core Text also provides glyph- and layout-related data, such as glyph locations and measurement of lines and frames. It handles character attributes and paragraph styles, including various types of tab styles and positioning.
You Can Manage Fonts With Core Text
The Core Text font API provides fonts, font collections, font descriptors, and easy access to font data. It also provides support for multiple master fonts, font variations, font cascading, and font linking. Core Text provides an alternative to Quartz for loading your own fonts into the current process, that is, font activation.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/core_text.png">

## Core Foundation

Core Foundation (also called CF) is a C application programming interface (API) in Mac OS X & iOS, and is a mix of low-level routines and wrapper functions. Some types in Core Foundation are "toll-free bridged", or interchangeable with a simple cast, with those of their Foundation Kit counterparts. For example, one could create a CFDictionaryRef Core Foundation type, and then later simply use a standard C cast to convert it to its Objective-C counterpart, `(NSDictionary *)`, and then use the desired Objective-C methods on that object as one normally would.
Is a library with a set of programming interfaces conceptually derived from the Objective-C-based Foundation framework but implemented in the C language. To do this, Core Foundation implements a limited object model in C. Core Foundation defines opaque types that encapsulate data and functions, hereafter referred to as “objects.” The programming interfaces of Core Foundation objects have been designed for ease of use and reuse. At a general level, Core Foundation:
* Enables sharing of code and data among various frameworks and libraries
* Makes some degree of operating-system independence possible
* Supports internationalization with Unicode strings
* Provides common API and other useful capabilities, including a plug-in architecture, XML property lists, and preferences

An "opaque type" is a type where you don't have a full definition for the struct or class. In C, C++ and Ob-jective-C, you can tell the compiler that a type will be defined later by using a forward declaration:
```c
// forward declaration of struct in C, C++ and Objective-C
struct Foo;
// forward declaration of class in C++:
class Bar;
// forward declaration of class in Objective-C:
@class Baz;
```
The compiler doesn't have enough information to let you do anything directly with the struct or class except declare pointers to it, but this is frequently all you need to do. This allows library and framework creators to hide implementation details. Users of a library or framework then call helper functions to create, manipulate and destroy instances of a forward declared struct or class. For example, a framework creator could create these functions for `struct Foo`:
```c
struct Foo *createFoo(void);
void addNumberToFoo(struct Foo *foo, int number);
void destroyFoo(struct Foo *foo);
```
As part of the Core Foundation framework, Apple makes common Objective-C classes like `NSString`, `NSArray` and `NSBundle` available to C programmers through opaque types. C programmers use pointers and helper functions to create, manipulate and destroy instances of these Objective-C classes. Apple calls this "toll-free bridging". They follow a common naming convention: `CF` prefix + class name + `Ref` suffix, where `CF` stands for "Core Foundation" and `Ref` is short for "Reference", meaning it's a pointer.
Core Foundation makes it possible for the different frameworks and libraries on OS X to share code and data. Applications, libraries, and frameworks can define C routines that incorporate Core Foundation types in their external interfaces; they can thus communicate data—as Core Foundation objects—to each other through these interfaces. Core Foundation also provides “toll-free bridging” between certain services and the Cocoa’s Foundation framework. Toll-free bridging enables you to substitute Cocoa objects for Core Foundation objects in function parameters and vice versa.
Some Core Foundation types and functions are abstractions of things that have specific implementations on different operating systems. Code that makes use of these APIs is thus easier to port to different platforms. Date and number types abstract time utilities and offers facilities for converting between absolute and Gregorian measures of time. It also abstracts numeric values and provides facilities for converting between different internal representations of those values.
One of the major benefits Core Foundation brings to application development is internationalization support. Through its String objects, Core Foundation facilitates easy, robust, and consistent internationalization across all OS X and Cocoa programming interfaces and implementations. The essential part of this support is a type, CFString, instances of which represent an array of 16-bit Unicode characters. A CFString object is flexible enough to hold megabytes worth of characters and yet simple and low-level enough for use in all programming interfaces communicating character data. It accomplishes this with performance not much different than that associated with standard C strings.

_CFAllocator CFArray CFAttributedString CFBag CFBinaryHeap CFBitVector CFBoolean CFBundle
CFCalendar CFCharacterSet CFData CFDate CFDateFormatter CFDictionary CFError CFFileDescriptor CFLocale CFMachPort CFMessagePort CFMutableArray CFMutableAttributedString CFMutableBag CFMutableBitVector CFMutableCharacterSet CFMutableData CFMutableDictionary CFMutableSet CFMutableString CFNotificationCenter CFNull CFNumber CFNumberFormatter CFPlugIn CFPlugInInstance CFPropertyList CFReadStream CFRunLoop CFRunLoopObserver CFRunLoopSource CFRunLoopTimer CFSet CFSocket CFString CFStringTokenizer CFTimeZone CFTree CFType CFURL CFUserNotifi-cation CFUUID CFWriteStream CFXMLNode CFXMLParser CFXMLTree_

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

## UIKit
The UIKit framework provides the classes needed to construct and manage an application’s user interface for iOS. It provides an application object, event handling, drawing model, windows, views, and controls specifically designed for a touch screen interface.
The UIKit framework defines a number of functions, many of them used in graphics and drawing operations.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/uikit.png">

## CFNetwork
CFNetwork is a low-level, high-performance framework that gives you the ability to have detailed control over the protocol stack. It is an extension to BSD sockets, the standard socket abstraction API that provides objects to simplify tasks such as communicating with FTP and HTTP servers or resolving DNS hosts. CFNetwork is based, both physically and theoretically, on BSD sockets.
Just as CFNetwork relies on BSD sockets, there are a number of Cocoa classes that rely on CFNetwork (NSURL, for example). In addition, the Web Kit is a set of Cocoa classes to display web content in win-dows. Both of these classes are very high level and implement most of the details of the networking protocols by themselves.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/cfnetwork.png">

__When to Use CFNetwork__

CFNetwork has a number of advantages over BSD sockets. It provides run-loop integration, so if your application is run loop based you can use network protocols without implementing threads. CFNet-work also contains a number of objects to help you use network protocols without having to imple-ment the details yourself. For example, you can use FTP protocols without having to implement all of the details with the CFFTP API. If you understand the networking protocols and need the low-level control they provide but don't want to implement them yourself, then CFNetwork is probably the right choice.
There are a number of advantages of using CFNetwork instead of Foundation-level networking APIs. CFNetwork is focused more on the network protocols, whereas the Foundation-level APIs are focused more on data access, such as transferring data over HTTP or FTP. Although Foundation APIs do pro-vide some configurability, CFNetwork provides a lot more.
Now that you understand how CFNetwork interacts with the other OS X networking APIs, you're ready to become familiar with the CFNetwork APIs along with two APIs that form the infrastructure for CFNetwork.
CFNetwork Infrastructure
Before learning about the CFNetwork APIs, you must first understand the APIs which are the foundation for the majority of CFNetwork. CFNetwork relies on two APIs that are part of the Core Foundation framework, CFSocket and CFStream. Understanding these APIs is essential to using CFNetwork.

__CFSocket API__

Sockets are the most basic level of network communications. A socket acts in a similar manner to a telephone jack. It allows you to connect to another socket (either locally or over a network) and send data to that socket. The most common socket abstraction is BSD sockets. CFSocket is an abstraction for BSD sockets. With very little overhead, CFSocket provides almost all the functionality of BSD sockets, and it integrates the socket into a run loop. CFSocket is not limited to stream-based sockets (for example, TCP), it can handle any type of socket. You could create a CFSocket object from scratch using the CFSocketCreate function, or from a BSD socket using the CFSocketCreateWithNative function. Then, you could create a run-loop source using the function CFSocketCreateRunLoopSource and add it to a run loop with the function CFRunLoopAddSource. This would allow your CFSocket callback function to be run whenever the CFSocket object receives a message.

__CFStream API__

Read and write streams provide an easy way to exchange data to and from a variety of media in a device-independent way. You can create streams for data located in memory, in a file, or on a network (using sockets), and you can use streams without loading all of the data into memory at once.
A stream is a sequence of bytes transmitted serially over a communications path. Streams are one-way paths, so to communicate bidirectionally an input (read) stream and output (write) stream are necessary. Except for file-based streams, you cannot seek within a stream; once stream data has been provided or consumed, it cannot be retrieved again from the stream. CFStream is an API that provides an abstraction for these streams with two new CFType objects: CFReadStream and CFWriteStream. Both types of stream follow all of the usual Core Foundation API conventions. CFStream is built on top of CFSocket and is the foundation for CFHTTP and CFFTP. As you can see in Figure 1-2, even though CFStream is not officially part of CFNetwork, it is the basis for almost all of CFNetwork.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/cf.png">

## QuartzCore
Quartz 2D is an API of the Core Graphics framework that implements drawing.
Quartz Core is a framework that includes APIs for animation and image processing.
Quartz frameworks and their APIs
* CoreGraphics.framework
* Quartz 2D API manages the graphic context and implements drawing.
* Quartz Services API provides low level access to the window server. This includes display hardware, resolution, refresh rate, and others.
* QuartzCore.framework
* Core Animation: Objective-C API to do 2D animation.
* Core Image: image and video processing (filters, warp, transitions).iOS 5
Quartz.framework OS X only
* Image Kit: display and edit images.
* PDF Kit: display and edit PDFs.
* Quartz Composer: display Quartz Composer compositions.
* QuickLookUI: preview media elements.
All three frameworks use OpenGL underneath because all drawing in iOS or OS X goes through OpenGL at some point. OpenGL (Open Graphics Library — открытая графическая библиотека, гра-фический API) — спецификация, определяющая независимый от языка программирования платформонезависимый программный интерфейс для написания приложений, использующих двумерную и трёхмерную компьютерную графику. Включает более 250 функций для рисова-ния сложных трёхмерных сцен из простых примитивов. Используется при создании компью-терных игр, САПР, виртуальной реальности, визуализации в научных исследованиях. На плат-форме Windows конкурирует с DirectX.

# iOS

## IPhone, resolution, pixels vs points?

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/resolutions.png">

A pixel on iOS is the full resolution of the device, which means if I have an image that is 100x100 pixels in length, then the phone will render it 100x100 pixels on a standard non-retina device. However, because newer iPhones have a quadrupled pixel density, that same image will render at 100x100 pixels, but look half that size. The iOS engineers solved this a long time ago (way back in OS X with Quartz) when they introduced Core Graphics' point system. A point is a standard length equivalent to 1x1 pixels on a non-retina device, and 2x2 pixels on a retina device. That way, your 100x100 image will render twice the size on a retina device and basically normalize what the user sees.
It also provides a standard system of measurement on iOS devices because no matter how the pixel density chanes, there have always been 320x480 points on an iPhone screen and 768x1024 points on an iPad screen.*
But at the same time, you can basically disregard the documentation considering that retina devices were introduced with iOS 4 at a minimum, and I don't know of too many people still running iOS 3 on a newer iPhone. But if such a case arises, your UIImage would need to be rendered at exactly twice it's dimensions in pixels on a retina iPhone to make up for the pixel density difference.

## Файловая система iOS

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/file_system.png">

## App lifecycle

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/lifecycle.png">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/app_states.png">

Возможные состояния программы
* Not running (не запущенное) — приложение не было запущено или его работа была прекращена
* Inactive (неактивное) — приложение работает, но не принимает события (например, когда пользователь заблокировал телефон при запущенном приложении)
* Active (активное) — нормальное состояние приложения при его работе
* Background (фоновое) — приложение больше не на дисплее, но оно все еще выполняет код
* Suspended (приостановленное) — приложение занимает память, но не выполняет код

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/app_states_2.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/app_states_3.png">

## Жизненный цикл UIViewController

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/uiviewcontroller.png">

## UIView
The UIView (UIResponder : NSObject) Объект, рисующий контент в прямоугольной области экрана и управляющий событиями, вызванными касаниями экрана пользователем. Представ-ление также может содержать другие представления, называемые субпредставлениями. При добавлении субпредставления к представлению контейнер называется родительским пред-ставлением, а его субпредставление называется дочерним представлением. Сочетание роди-тельского представления, его дочерних представлений (а так же их дочерних представлений, если таковые имеются) образует иерархию представлений.
Интерфейс состоит из представлений (UIView).  
UIWindow (UIView : UIResponder : NSObject) – единственный экземпляр  в приложении, который играет роль контейнера для всех представлений. class defines an object known as a window that manages and coordinates the views an app displays on a device screen. Unless an app can display content on an external device screen, an app has only one window. The two principal functions of a window are
1. to provide an area for displaying its views
2. to distribute events to the views
To change the content your app displays, you can change the window’s root view; you don’t create a new window. A window belongs to a level—typically, UIWindowLevelNormal—that represents where it sits on the z-axis relative to other windows. For example, a system alert window appears above normal app windows.
UIViewController – управление единственным экраном приложения.
UINavigationController – управляет стеком из массива UIViewController.
Root View Controller – Корневой контроллер, находится внизу стека, самый последний.   
CGRect – структура, которая содержит переменные для хранения координат и размеров.
frame – это прямоугольник описываемый положением location(x, y) и размерами size (width, height) вьюхи относительно ее superview в которой оа содержится.
bounds – это прямоугольник описываемый положением location(x, y) и размерами size (width, height) вьюхи относительно ее собственной системы координат (0, 0).

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/uiview_frame.png">

```objectivec
// 1. CGRect получение координат и границ экрана.
CGRect screen = [[UIScreen mainScreen] bounds];
// 2. получение границ и координат фрейма для программы.
CGRect appFrame = [[UIScreen mainScreen] applicationFrame];
// 3. создаем новое окно.
self.window = [UIWindow alloc] initWithFrame: appFrame];
// 4. создаем вью с параметрами appFrame.
UIView *view = [[UIView alloc]initWithFrame: appFrame];
// 5. добавляем вью в окно с помощью метода addSubView.
[window addSubView:view];
// 6. делаем окно видимым
[window makeKeyAndVisible];

@implementation AppDelegate
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
	self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
	// Override point for customization after application launch.
	self.window.backgroundColor = [UIColor whiteColor];
	[self.window makeKeyAndVisible];
	return YES;
}
```

# MEMORY MANAGEMENT
Memory management – процесс выделения памяти под объекты, и освобождение ее после использования.
* __Manual Retain-Release__ (ручное сохранение-освобождение) или MRR – вы явно управляете памятью, отслеживая объекты, которые у вас есть. Это реализуется с помощью модели, известной как подсчет ссылок, что Foundation класса NSObject обеспечивает совместно со средой выполнения.
* В __Automatic Reference Counting__ (автоматическом подсчете ссылок), или ARC, система использует тот же подсчет ссылок, что и система MRR, но он вставляет соответствующий вызов метода управления памятью за вас во время компиляции.
* В __Garbage Collection__ (сборе мусора), система автоматически отслеживает, какие объекты владеют другими объектами. Затем она автоматически освобождает (или собирает мусор) объекты, на которые больше не ссылаются. Метод использует другой механизм, нежели, чем у используемых в MRR и ARC, и поддерживается только в среде выполнения на Mac OS X, а не IOS.

_Отличие ARC от GC:_

GC работает во время выполнения программы с помощью кода, который переодически запускается и проверяет объекты. ARC работает во время компиляции и вставляет retain и release автоматически в код.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/memory_management.png">

## Память в стеке и в куче

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/stack_explanataion_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/stack_explanataion_2.png">

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

## Automatic Reference Counting.
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

## Модификаторы
__Для свойств__

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/property_modifiers.png">

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

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/variable_modifiers.png">

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

## Что такое property?
Упрощенный способ для определения и создания методов доступа, обращающихся к существующим переменным экземплярам. Классы, которые подставляют переменные экземпляра, могут использовать обозначение свойства вместо того, чтобы использовать синтаксис getter и setter.

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
## В каких случаях лучше использовать strong, а в каких copy для NSString? Почему?
```objectivec
@property (nonatomic, strong) NSString *someString;
@property (nonatomic, copy) NSString *anotherString;
```
`сopy` используется только для объектов, реализующих протокол `<NSCopying>`. Обычно его используют с mutable объектами или со свойствами, представляющими какое-то значение (value).

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

## Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC?
1 способ: Edit – Refactor – Convert to ObjC ARC

2 способ: App – Targets – Build Phases – Compile Sources – поставить флаг `-fno-objc-arc`

## Основные темы управления памятью, такие как владение `retain` / `release` / `autorelease`
* Что случится если вы добавите только что созданный объект в `NSMutableArray`, и пошлете ему сообщение `release`?

//объект останется в массиве

* Что случится если послать сообщение `release` массиву?

//массив удалится

* Что случится если вы удалите объект из массива и попытаетесь его использовать?

//объект удалится из массива, использовать объект дальше можно

## Вопрос о циклах в графах владения, и почему свойства delegate обычно задаются как assign?
```
A creates B;
A sets itself as B’s delegate;
[A release];
if B retained A => leak;
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/retain_cycle.png">

## Что произойдет если сначала нажать на кнопку 1 а потом на кнопку 2?
```objectivec
- (IBAction)btn1DidTouch:(id)sender {
	_string = [[[NSString alloc] initWithFormat:@"v=%i", rand()] autorelease];
}
- (IBAction)btn2DidTouch:(id)sender {
	NSLog(@"_string is equal to ‘%@’", _string);
}
```
Крэш, т.к utoreleasepool создается в начале обработки события и уничтожается в конце. т.е. нажали на первую кнопку — началась обработка события, нажали на вторую — кнопку — закончилась обработка первого события, очистлся autoreleasepool а вместе с ним и объект удалился, а ссылка осталась. Затем началась обработка второго события и мы обращаемся к задеалоченному объекту, результат — крэш.

## Нужно ли ретейнить делегат для CAAnimation?
Да. Это одно из редких исключений в политике управления памятью. Specific task that has some sort of “finished” state. Также нужно ритейнить `NSURLConnection`.

## Что произойдет при исполнении следующего кода?
```objectivec
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];
```
Впоследствии это вызовет крэш. Потому что объект дважды добавляется в пул автоосвобождения, и `release` вызовется дважды.

## Реализуйте следующие методы: retain, release, autorelease
```objectivec
- (id)retain {
   	NSIncrementExtraRefCount(self);
    return self;
}

- (void)release {
    if (NSDecrementExtraRefCountWasZero(self)) {
         NSDeallocateObject(self);
    }
}

- (id)autorelease {  
// Add the object to the autorelease pool
    [NSAutoreleasePool addObject:self];
    return self;
}
```
## Если я вызову performSelector:withObject:afterDelay: объекту пошлется сообщение retain?
Да. Это создает таймер который вызывает селектор в RunLoop'е текущего потока (thread).

## Вы можете объяснить, что происходит когда вы посылаете объекту сообщение autorelease?
Когда вы посылаете объекту сообщение `autorelease`, его счетчик ссылок уменьшится на 1 в определенный момент в будущем. Объект будет добавлен в autorelease pool (пул автоосвобождения) в текущем потоке (thread). Цикл главного потока (main thread loop `NSRunLoop`) создает autorelease pool в начале функции и освобождает его в конце. Это устанавливает pool на время выполнения задачи. Это также означает что авторелизные (объекты помещенные в пул) объекты созданные в течение выполнеения задачи не будут уничтожены пока задача не завершится. Это может привести к излишнему потреблению памяти для задачи (объекты будут уже не нужны но освободятся только в конце задачи). Вы также можете попробовать создать вложенный пул и освободить его раньше, или использовать NSOperationQueue с его собственным пулом.

## Объясните что такое retain count?
Подсчет ссылок (retain count) — это механизм с помощью которого в Objective-C реализовано управление памятью. Когда вы создаете объект, его счетчик ссылок (retain count) установлен на `1`. Когда вы посылаете объекту сообщение `retain` , его счетчик ссылок увеличивается на `1`. Когда вы посылаете объекту сообщение `release` , его счетчик ссылок уменьшается на `1`. Когда вы посылаете объекту сообщение autorelease , его счетчик ссылок уменьшится на `1` в определенный момент в будующем. Когда счетчик ссылок объекта становится равным `0` то объект уничтожается (`dealloc`).

# Runtime
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/runtime_explanation1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/runtime_explanation2.png">

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

## Что такое указатель isa? Для чего он нужен?
Каждый объект Objective-C содержит в себе атрибут `isa` - указатель на class object для данного объекта. class object автоматически создается компилятором и существует как один экземпляр, на который через `isa` ссылаются все экземпляры данного класса.
First there is a pointer to your class definition. Then each of your superclasses’ ivars (instance variables) are laid out as struct properties, and then your class’s ivars are laid out as struct properties. This structure is called `objc_object`, and a pointer to it is called `id`:
```objectivec
typedef struct objc_object {
	Class isa;
} *id;
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/isa.png">

## Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?

_Форвардинг_

If you send a message to an object that does not handle that message, before announcing an error the runtime sends the object a forwardInvocation: message with an NSInvocation object as its sole argument—the NSInvocation object encapsulates the original message and the arguments that were passed with it. You can implement a forwardInvocation: method to give a default response to the message, or to avoid the error in some other way. As its name implies, forwardInvocation: is commonly used to forward the message to another object.

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

## Чем объект Objective-c отличается от структуры С, что такое структура в C?
Структура – специальный тип данных языка C, который содержит в себе другие типы данных в одном блоке и группрует их под одним именем.
```c
struct point {
	int x;
	int у;
};
```
Объекты в ObjС представляют собой структуры cо своими данными и в которых имеется ссылка isa на объект класса.

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

## Директивы компилятора
`@implementation` Определяет начало определения (реализации) класса или категории.

`@class` Используется для предварительного объявления класса. При использовании этой директивы класс помечается как известный, даже без загрузки заголовочного файла.

`@protocol` Используются для объявления протокола. Кроме того, протокол может адаптировать другие протоколы.

`@required` (по-умолчанию) Определяет методы, которые следуют после директивы как обязательные.

`@optional` Определяет методы, которые следуют после директивы как необязательные. Классы, которые поддерживают протокол, могут сами решать — реализовывать эти методы или нет. Классы, которые используют необязательные методы протокола, должны делать проверку на существование.

`@public` Определяет, что переменные экземпляра, следующие за директивой будут доступны публично. Публичные переменные могут быть прочтены и изменены с помощью следующей конструкции: `someObject->aPublicVariable = 10;`

`@package` Определяет, что переменные экземпляра, следующие за директивой будут публично доступны в библиотеке, которая определяет класс, но закрытыми за пределами этой библиотеки. Важное замечание, это справедливо только для 64-разрядных систем. На 32-разрядных системах имеет то же значение, что и `@public`

`@protected` (по умолчанию) Определяет, что переменные экземпляра, следующие за директивой, будут доступны только для класса и его потомков.

`@private` Определяет, что переменные экземпляра, следующие за директивой, будут доступны только в пределах данного класса

`@property` Определяет свойство, которое может быть использовано с помощью точечной нотации. За директивой `@property` могут следовать необязательные круглые скобки, которые содержат дополнительные ключевые слова (модификаторы), которые определяют поведение свойства.

`@synthesize` Дает указание компилятору, что необходимо автоматически сгенерировать сеттеры и геттеры для данных (разделенных запятой) свойств. Сеттеры и геттеры автоматически создаются согласно указанным в объявлении свойства директивам. Если переменные экземпляра называ-ются не так, как указано после директивы `@property`, вы можете соединить их с помощью знака равенства

`@dynamic` Cообщает компилятору, что требуемые сеттеры и геттеры для данных свойств будут реализованы вручную или динамически во время выполнения. При доступе к таким свойствам, компилятор не будет выдавать предупреждений, даже если требуемые сеттеры и геттеры не реализованы. Вы можете использовать такие свойства, когда хотите, чтобы сеттеры и геттеры выполняли какойто специфичный для вас код.

`@try` Defines a block of code that will be tested to determine if an exception should be thrown.

`@catch()` Defines a block of code for handling a thrown exception. Takes an argument, typically of type `NSException`, but can be of other types.

`@finally` Defines a block of code that gets executed whether an exception is thrown or not. This code will always be executed.

`@throw` Throws an exception. Earlier, we mentioned that you can throw exceptions from objects other than `NSException` instances, but that you should avoid doing so. The reason is that not every Cocoa framework catches exceptions thrown by objects other than `NSException`. To ensure that Cocoa works right with your exceptions, you should throw `NSException` objects only. Think of it like the old saying that you don’t have to floss all your teeth, just the ones you want to keep. You’ll typically use `@try`, `@catch`, and `@finally` together in one structure. It goes a little something like this:
```objectivec
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
```
`@synchronized` Заключает блок кода в мьютекс. Обеспечивает гарантию того, что блок кода и объект блокировки будут доступны только из одного потока в момент времени.

`@autoreleasepool` В тех приложения, в которых вы используете автоматический подсчет ссылок (ARC), вы должны использовать `@autoreleasepool` как замену для `NSAutoreleasePool`. И вообще, `@autoreleasepool` примерно в 6 раз быстрее, чем `NSAutoreleasePool`, поэтому Apple рекомендует использовать его даже для не-ARC приложений. Кроме того, вы не должны определять переменную внутри блока `@autoreleasepool` и затем продолжать использовать ее после. Подобный код должен быть исключен.

`@selector` Возвращает специальный тип селекторов SEL выбранного метода Objective-C. Генерирует предупреждение компилятора, если метода не объявлен или не существует. Это имя метода закодированное специальным образом, используемым Objective-C для быстрого поиска. Указание компилятору на селектор происходит при помощи директивы `@selector(methodName)`

`@encode` Возвращает кодировку типа.

`@compatibility_alias` Позволяет вам задать псевдоним для существующего класса. Первый параметр — имя псевдонима для имени класса, класса с таким именем не должно существовать. Второй параметр — имя существующего класса, для которого создается псевдоним.

`@"some text";` Объявляет константный объект класса NSString. Для таких строк не требуется вызывать `retain` или `release`.

`@import` Модуль прекомпилированных заголовков, позволяющий экономить время по сравнению с компиляцией заголовков при `#import`. Не надо линковать фреймворк.

```objectivec
#import <Cocoa/Cocoa.h> //is the same as
@import Cocoa;
```
# Multithreading
Although operation queues and dispatch queues are the preferred way to perform tasks concurrently, they are not a panacea. Depending on your application, there may still be times when you need to create custom threads. If you do create custom threads, you should strive to create as few threads as possible yourself and you should use those threads only for specific tasks that cannot be implemented any other way.
Threads are still a good way to implement code that must run in real time. Dispatch queues make every attempt to run their tasks as fast as possible but they do not address real time constraints. If you need more predictable behavior from code running in the background, threads may still offer a better alternative.
## POSIX Threads
usually referred to as Pthreads, is a POSIX standard for threads defines an API for creating and manipulating threads. Pthreads defines a set of C programming language types, functions and constants. It is implemented with a pthread.h header and a thread library. There are around 100 Pthreads procedures, all prefixed `pthread_` and they can be categorized into four groups:

* Thread management - creating, joining threads etc.
* Mutexes
* Condition variables
* Synchronization between threads using read/write locks and barriers

Implementations of the API are available on many Unix-like POSIX-conformant operating systems such as FreeBSD, NetBSD, OpenBSD, GNU/Linux, Mac OS X and Solaris. DR-DOS and Microsoft Windows implementations also exist.
## NSThread
is a simple Objective-C wrapper around pthreads. This makes the code look more familiar in a Cocoa environment. For example, you can define a thread as a subclass of `NSThread`, which encapsulates the code you want to run in the background.
## Run Loops
Циклы выполнения – часть инфраструктуры, используемой для управления событиями, прибывающими асинхронно в потоке. Ждет данные от одного или нескольких источников, чтобы запустить код на исполнение. Циклы выполнения работают по мониторингу одного или нескольких источников событий для потока. Как только события прибыли, система пробуждает поток и отправляет события на цикл выполнения, который затем передает их указанным обработчикам. Если нет событий готовых быть обработанными, цикл выполнения ставит поток в режим сна.
Одна из опасностей потокового программирования, это конфликты ресурсов между несколькими потоками. Если несколько потоков пытаются использовать или модифицировать один и тот же ресурс в одно и то же время, то могут возникнуть проблемы. Один из способов решить проблему заключается в устранении общего ресурса в целом и убедиться, что каждый поток имеет свой собственный набор ресурсов, на котором он работает. Поддержание совершенно разных ресурсов, это не вариант, и для синхронизации доступа к ресурсу придется прибегать к помощи замков, условий, атомарных операций, и других методов.
Замки обеспечивают грубую форму силы для защиты кода, который может быть выполнен только одним потоком одновременно. Наиболее распространенный тип блокировки взаимного исключения блокировки, также известный как мьютекс. Кроме замков, система обеспечивает поддержку для условий, которые обеспечивают надлежащую последовательность задач в рамках вашего приложения. Условие действует как привратник, блокируя определенный поток до приведения определенного состояния в значение истина. Когда это произойдет, поток освобождается и продолжает выполняться. И POSIX и Foundation framework оба оказывают прямую поддержку условий.
Run loops are not technically a concurrency mechanism like GCD or operation queues, because they don’t enable the parallel execution of tasks. However, run loops tie in directly with the execution of tasks on the main dispatch/operation queue and they provide a mechanism to execute code asynchronously. Run loops can be a lot easier to use than operation queues or GCD, because you don’t have to deal with the complexity of concurrency and still get to do things asynchronously.
A run loop is always bound to one particular thread. The main run loop associated with the main thread has a central role in each Cocoa and CocoaTouch application, because it handles UI events, timers, and other kernel events. Whenever you schedule a timer, use a `NSURLConnection` or call `performSelector:withObject:afterDelay`:, the run loop is used behind the scenes in order to perform these asynchronous tasks. Whenever you use a method which relies on the run loop, it is important to remember that run loops can be run in different modes. Each mode defines a set of events the run loop is going to react to. This is a clever way to temporarily prioritize certain tasks over others in the main run loop. A typical example of this is scrolling on iOS. While you’re scrolling, the run loop is not running in its default mode, and therefore, it’s not going to react to, for example, a timer you have scheduled before. Once scrolling stops, the run loop returns to the default mode and the events which have been queued up are executed. If you want a timer to fire during scrolling, you need to add it to the run loop in the `NSRunLoopCommonModes` mode. The main thread always has the main run loop set up and running. Other threads though don’t have a run loop configured by default. You can set up a run loop for other threads too, but you will rarely need to do this. Most of the time it is much easier to use the main run loop. If you need to do heavier work that you don’t want to execute on the main thread, you can still dispatch it onto another queue after your code is called from the main run loop.
You can think of a Run Loop to be an event processing for-loop associated to a thread. This is provided by the system for every thread, but it's only run automatically for the main thread. Note that _running run loops and executing a thread are two distinct concepts_. You can execute a thread without running a run loop, when you're just performing long calculations and you don't have to respond to various events. If you want to respond to various events from a secondary thread, you retrieve the run loop associated to the thread by `[NSRunLoop currentRunLoop];` and run it. The events run loops can handle is called input sources. You can add input sources to a run loop.

## Для чего при разработке под iOS использовать POSIX-потоки?
Use POSIX calls if cross-platform portability is required. If you are writing networking code that runs exclusively in OS X and iOS, you should generally avoid POSIX networking calls, because they are harder to work with than higher-level APIs. However, if you are writing networking code that must be shared with other platforms, you can use the POSIX networking APIs so that you can use the same code everywhere.

# Concurrency
Concurrency is the notion of multiple things happening at the same time. Threads are subunits of processes, which can be scheduled independently by the operating system scheduler. Virtually all concurrency APIs are built on top of threads under the hood – that’s true for both Grand Central Dispatch and operation queues. You can either use the POSIX thread API, or the Objective-C wrapper around this API, `NSThread`, to create your own threads.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/objc_threading.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/objc_threading_apis.png">

## GCD
With GCD you don’t interact with threads directly anymore. Instead you add blocks of code to queues, and GCD manages a thread pool behind the scenes. GCD decides on which particular thread your code blocks are going to be executed on, and it manages these threads according to the available system resources. This alleviates the problem of too many threads being created, because the threads are now centrally managed and abstracted away from application developers. The other important change with GCD is that you as a developer think about work items in a queue rather than threads. This new mental model of concurrency is easier to work with. GCD exposes five different queues: the main queue running on the main thread, three background queues with different priorities, and one background queue with an even lower priority, which is I/O throttled. Furthermore, you can create custom queues, which can either be serial or concurrent queues. While custom queues are a powerful abstraction, all blocks you schedule on them will ultimately trickle down to one of the system’s global queues and its thread pool(s).
Dispatch queues are a C-based mechanism for executing custom tasks. A dispatch queue executes tasks either serially or concurrently but always in a first-in, first-out order. (In other words, a dispatch queue always dequeues and starts tasks in the same order in which they were added to the queue.) A serial dispatch queue runs only one task at a time, waiting until that task is complete before dequeuing and starting a new one. By contrast, a concurrent dispatch queue starts as many tasks as it can without waiting for already started tasks to finish.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_queues_scheme.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_functions_1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/gcd_functions_2.png">

__Плюсы__

* Визуально — он самый короткий и простой в реализации. Он возоможен с использованием блоков. Этот подход тоже очень гибкий (хотя отменять блок поставленный в очередь нельзя стандартными способами). В GCD можно настраивать приоритеты, блоки захватывают переменные из окружения блока.

Types of dispatch queues

__Serial__

Serial queues (also known as private dispatch queues) execute one task at a time in the order in which they are added to the queue. The currently executing task runs on a distinct thread (which can vary from task to task) that is managed by the dispatch queue. Serial queues are often used to synchronize access to a specific resource.
You can create as many serial queues as you need, and each queue operates concurrently with respect to all other queues. In other words, if you create four serial queues, each queue executes only one task at a time but up to four tasks could still execute concurrently, one from each queue.

__Concurrent__

Concurrent queues (also known as a type of global dispatch queue) execute one or more tasks concurrently, but tasks are still started in the order in which they were added to the queue. The currently executing tasks run on distinct threads that are managed by the dispatch queue. The exact number of tasks executing at any given point is variable and depends on system conditions.
In iOS 5 and later, you can create concurrent dispatch queues yourself by specifying `DISPATCH_QUEUE_CONCURRENT` as the queue type. In addition, there are four predefined global concurrent queues for your application to use.

__Main dispatch queue__

The main dispatch queue is a globally available serial queue that executes tasks on the application’s main thread. This queue works with the application’s run loop (if one is present) to interleave the execution of queued tasks with the execution of other event sources attached to the run loop. Because it runs on your application’s main thread, the main queue is often used as a key synchronization point for an application.
Although you do not need to create the main dispatch queue, you do need to make sure your application drains it appropriately.

## NSOperationQueue
Operation queues are a Cocoa abstraction of the queue model exposed by GCD. While GCD offers more low-level control, operation queues implement several convenient features on top of it, which often makes it the best and safest choice for application developers. The `NSOperationQueue` class has two different types of queues: the main queue and custom queues. The main queue runs on the main thread, and custom queues are processed in the background. In any case, the tasks which are processed by these queues are represented as subclasses of `NSOperation`. Whereas dispatch queues always execute tasks in first-in, first-out order, operation queues take other factors into account when determining the execution order of tasks. Because the `NSOperation` class is essentially an abstract base class, you typically define custom subclasses to perform your tasks. However, the Foundation framework does include some concrete subclasses that you can create and use as is to perform tasks.

__Плюсы__

* Можно для каждой очереди настраивать приоритет и количество одновременно выполняющихся операций. `NSOperationQueue` самостоятельно создает и поддерживает пул потоков, в которых исполняются `NSOperation`. Так же `NSOperation` предоставляет возможность отменять операции, приостанавливать всю очередь, запускать ее снова и много чего прочего.

## NSObject instance methods
```objectivec
- (void)performSelector:(SEL)aSelector onThread:(NSThread *)thread withObject:(id)arg waitUntilDone:(BOOL)wait;
- (void)performSelector:(SEL)aSelector onThread:(NSThread *)thread withObject:(id)arg waitUntilDone:(BOOL)wait mo-des:(NSArray *)array;
- (void)performSelector:(SEL)aSelector withObject:(id)anArgument afterDelay:(NSTimeInterval)delay;
- (void)performSelector:(SEL)aSelector withObject:(id)anArgument afterDelay:(NSTimeInterval)delay inModes:(NSArray *)modes;
- (void)performSelectorInBackground:(SEL)aSelector withObject:(id)arg;
- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait;
- (void)performSelectorOnMainThread:(SEL)aSelector withObject:(id)arg waitUntilDone:(BOOL)wait modes:(NSArray *)array;
```
Это один из самых простых и распространенных вариантов. Он требует только указать метод, который будет исполнять этот поток.

* Because these methods are running on their own threads, you must create an autorelease pool for Cocoa objects. The main autorelease pool is associated with the main thread.
* The methods must not return any values and must either take no arguments or have one object as an argument. In other words, the methods must have one of the following signatures:
```objectivec
- (void)myMethod;
- (void)myMethod:(id)myObject;
```
__Плюсы__

* Он подходит для простых задач

__Минусы__

* Нужно упаковывать все параметры для передачи, и бедные возможности по управлению очередностью, количеством одновременных задач, их приоритетом. На каждый вызов `performSelectorInBackground` будет создаваться отдельный поток. При быстром скролле большой таблицы можно довести число потоков до очень большой величины.

In general, you should use the highest level of abstraction that suits your needs. This means that you should usually use `NSOperationQueue` instead of GCD, unless you need to do something that `NSOperationQueue` doesn't support.

### Что такое мьютекс?
`@synchronized`

Замки являются одним из наиболее часто используемых инструментов синхронизации. Вы можете использовать замки для защиты критической секции вашего кода, который является сегментом кода, к которому разрешен доступ только одному потоку одновременно. Взаимоисключающая (или мьютекс) блокировка действует как защитный барьер вокруг ресурса. Мьютекс является одним из видов семафора, который предоставляет доступ одновременно только одному потоку. Если мьютекс используется и другой поток пытается получить его, что поток блокируется до тех пор, пока мьютекс не освободится от своего первоначального владельца. Если несколько потоков соперничают за одни и те же мьютексы, только одному будет разрешен к нему доступ.

### Что такое deadlock?
Каждый поток захватывает ресурс и ждет, пока другой не осводит второй ресурс. Таким образом, они ждут друг друга вечно. Deadlock is an unhappy condition in which two or more competing tasks are each waiting on the other to finish. You can observe this in real life when cars arrive simultaneously at a four-way stop.

### Что такое livelock?
Система не застревает, но занимается бесполезной работой. A livelock occurs when a request for an exclusive lock is repeatedly denied because a series of overlapping shared locks keep interfering. It is an endless loop in program execution. This could be a case when two threads exit allowing each other to write to or update record(s) in a database.

### Что такое семафор?
Семафор позволяет выполнять какой-либо участок кода одновременно только конкретному количеству потоков. В основе семафора лежит счетчик, который и определяет, можно ли выполнять участок кода текущему потоку или нет. Если счетчик больше нуля — поток выполняет код, в противном случае — нет. Семафор в GCD представлен типом `dispatch_semaphore_t`. Для создания семафора существует функция `dispatch_semaphore_create`, которая принимает один аргумент — число потоков, которые могут одновременно выполнять участок кода.

### Чем отличается dispatch_async от dispatch_sync?
Когда это возможно, асинхронное выполнение с использованием `dispatch_async` и `dispatch_async_f` функций предпочтительнее, чем синхронный вариант. При добавлении объекта блока или функции в очередь, нет никакого способа узнать, когда этот код будет выполняться. В результате, добавляя блоки или функции асинхронно позволяет запланировать выполнение кода и продолжать делать другую работу из вызывающего потока. Это особенно важно, если вы планировали выполнить задачу из основного потока приложения, возможно, в ответ на некоторые пользовательские события.
Хотя вы должны добавлять задачи асинхронно по мере возможности, все же могут быть случаи, когда вам нужно добавить задачу синхронно, чтобы предотвратить гонку условий или другие ошибки синхронизации. В этих случаях можно использовать функции `dispatch_sync` и `dispatch_sync_f` для добавления задачи в очередь. Эти функции блокируют текущий поток исполнения до завершения выполнения указанной задачи.

__Важно:__ Вы никогда не должны вызывать функции `dispatch_sync` или `dispatch_sync_f` из задачи, которая выполняется в той же очереди, в которой вы планируете переход к функции. Это особенно важно для последовательных очередей, которые гарантированно приведут к deadlock, но также следует избегать одновременных очередей.

Следующий пример показывает, как использовать блочные варианты для отправки задачи асинхронно и синхронно:
```objectivec
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
```

### Как многопоточность работает с UIKit?
In Cocoa Touch, the `UIApplication` i.e. the instance of your application is attached to the main thread because this thread is created by `UIApplicatioMain()`, the entry point function of Cocoa Touch. It sets up main event loop, including the application’s run loop, and begins processing events. Application's main event loop receives all the UI events i.e. touches, gestures etc. These application UI events are further forwarded to `UIResponder`'s following the chain of responders usually like `UIApplication->UIWindow->UIViewController->UIView->subviews (UIButton, etc...)` Responders handle events like button press, tap, pinch zoom, swipe etc. which get translated as change in the UI. Hence as you can see these chain of events occur on main thread which is why UIKit, the framework which contains the responders should operate on main thread.
One of the most common mistakes even experienced iOS/Mac developers make is accessing parts of UIKit/AppKit on background threads. It’s very easy to make the mistake of setting properties like image from a background thread, because their content is being requested from the network in the background anyway. Apple’s code is performance-optimized and will not warn you if you change properties from different threads. For the most part, UIKit classes should be used only from an application’s main thread. This is particularly true for classes derived from `UIResponder` or that involve manipulating your application’s user interface in any way.

### Выведется ли в дебагер Hello world? Почему?
```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
	dispatch_sync(dispatch_get_main_queue(), ^{
		NSLog(@"Hello world");
	});
	/* Another implementation */
	return YES;
}
```
Нет. deadlock

### Что выведется в консоль?
```objectivec
NSObject *object = [NSObject new];
dispatch_async(dispatch_get_main_queue(), ^ {
	NSLog(@"A %d", [object retainCount]);
	dispatch_async(dispatch_get_main_queue(), ^ {
		NSLog(@"B %d", [object retainCount]);
	});
	NSLog(@"C %d", [object retainCount]);
});
NSLog(@"D %d", [object retainCount]);
```
```
D 2
A 2
C 3
B 2
```

### Atomic vs nonatomic. Чем отличаются? Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?
Cинхронизировать чтение/запись между потоками или нет.
Atomic – thread safe.
Тут все сложнее и неоднозначнее, есть ряд способов как сделать threadsafe аксессоры к пропертям. Самый простой способ это сделать – добавить конструкцию `@synchronized`:
```objectivec
- (NSString *)foo {
    @synchronized(self) {
       	return foo;
    }
}

- (void)setFoo:(NSString)newFoo {
    @synchronized(self) {
       	if (foo != newFoo) {
          	[foo release];
          	foo = [newFoo retain];
       	}
    }
}
```
Таким образом используя `@synchronized` мы лочим по ключу `self` доступ к `foo`, однако у такого метода есть очевидный недостаток, если в классе будет две переменные (или 100500) к которым нужен одновременный доступ с разных потоков, то они будут лочиться и друг относительно друга, т.к `self` для них один и тот же, в таких случаях нужно использовать другие методы лока, как `NSLock`, `NSRecursiveLock`,...

# Networking
## Преимущества и недостатки синхронного и асинхронного соединения?
`NSURLConnection` поддерживает синхронное и асинхронное выполнение запросов. Для выполнения синхронных запросов используется `sendSynchronousRequest:returningResponse:error:`
Использование такого запроса не рекомендуется. Работа приложения остановится, пока данные не будут получены полностью, не произойдёт ошибка или истечет таймаут соединения. При использовании синхронного запроса есть и другие ограничения.
Для асинхронных запросов используется `- (id)initWithRequest:(NSURLRequest *)request delegate:(id <NSURLConnectionDelegate>)delegate` либо `initWithRequest:delegate:startImmediately:``

## Протоколы передачи данных
Transmission Control Protocol (TCP) (протокол управления передачей) — один из основных протоколов передачи данных Интернета, предназначенный для управления передачей данных в сетях и подсетях TCP/IP.
HTTP (англ. HyperText Transfer Protocol — «протокол передачи гипертекста») — протокол прикладного уровня передачи данных (изначально — в виде гипертекстовых документов). Основой HTTP является технология «клиент-сервер», то есть предполагается существование потребителей (клиентов), которые инициируют соединение и посылают запрос, и поставщиков (серверов), которые ожидают соединения для получения запроса, производят необходимые действия и возвращают обратно сообщение с результатом. Этот протокол описывает взаимодействие между двумя компьютерами (клиентом и сервером), построенное на базе сообщений, называемых запрос (Request) и ответ (Response). Каждое сообщение состоит из трех частей: стартовая строка, заголовки и тело. При этом обязательной является только стартовая строка.

## Какие различия между HEAD, GET, POST, PUT?
`GET` Используется для запроса содержимого указанного ресурса. С помощью метода `GET` можно также начать какой-либо процесс. В этом случае в тело ответного сообщения следует включить информацию о ходе выполнения процесса. Клиент может передавать параметры выполнения запроса в URI целевого ресурса после символа `?`:
```
GET /path/resource?param1=value1&param2=value2 HTTP/1.1
```

`HEAD` Аналогичен методу `GET`, за исключением того, что в ответе сервера отсутствует тело. Запрос HEAD обычно применяется для извлечения метаданных, проверки наличия ресурса (валидация URL) и чтобы узнать, не изменился ли он с момента последнего обращения.
Заголовки ответа могут кэшироваться. При несовпадении метаданных ресурса с соответствующей информацией в кэше копия ресурса помечается как устаревшая.

`POST` Применяется для передачи пользовательских данных заданному ресурсу. Например, в блогах посетители обычно могут вводить свои комментарии к записям в HTML-форму, после чего они передаются серверу методом `POST` и он помещает их на страницу. При этом передаваемые данные (в примере с блогами — текст комментария) включаются в тело запроса. Аналогично с помощью метода `POST` обычно загружаются файлы на сервер. В отличие от метода `GET`, метод `POST` не считается идемпотентным, то есть многократное повторение одних и тех же запросов `POST` может возвращать разные результаты (например, после каждой отправки комментария будет появляться одна копия этого комментария).
Отправить `POST`-запрос не так тяжело как кажется. Достаточно подготовить «правильный» `NSURLRequest`.
```objectivec
NSString *params = @"param=value&number=1"; // задаем параметры POST запроса
NSURL *url = [NSURL URLWithString:@"http://server.com"]; // куда отправлять
NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:url];
request.HTTPMethod = @"POST";
request.HTTPBody = [params dataUsingEncoding:NSUTF8StringEncoding];
// следует обратить внимание на кодировку
// теперь можно отправить запрос синхронно или асинхронно
[NSURLConnection sendSynchronousRequest:request returningResponse:nil error:nil];
```
`PUT` Применяется для загрузки содержимого запроса на указанный в запросе URI. Если по заданному URI не существовало ресурса, то сервер создаёт его и возвращает статус `201` (Created). Если же был изменён ресурс, то сервер возвращает `200` (Ok) или `204` (No Content). Сервер не должен игнорировать некорректные заголовки `Content-*`, передаваемые клиентом вместе с сообщением. Если какой-то из этих заголовков не может быть распознан или не допустим при текущих условиях, то необходимо вернуть код ошибки `501` (Not Implemented).
Фундаментальное различие методов `POST` и `PUT` заключается в понимании предназначений URI ресурсов. Метод `POST` предполагает, что по указанному URI будет производиться обработка передаваемого клиентом содержимого. Используя `PUT`, клиент предполагает, что загружаемое содержимое соответствует находящемуся по данному URI ресурсу.

Единый указатель ресурсов (англ. __URL__ — Uniform Resource Locator) — единообразный локатор (определитель местонахождения) ресурса. URL — это стандартизированный способ записи адреса ресурса в сети Интернет.

__URI__ (англ. Uniform Resource Identifier) — унифицированный (единообразный) идентификатор ресурса. URI — это символьная строка, позволяющая идентифицировать какой-либо ресурс: документ, изображение, файл, службу, ящик электронной почты и т. д. Прежде всего, речь идёт, конечно, о ресурсах сети Интернет и Всемирной паутины.
URL это частный случай URI. Понятие URI включает в себя, помимо URL, например, ссылки на адреса электронной почты и т.п. URL указывает на Веб-ресурс, вроде сайта, страницы или кон-кретного файла, расположенных на интернет-серверах.

## Что такое REST архитектура?
REST (Representational state transfer) – это стиль архитектуры программного обеспечения для распределенных систем, таких как World Wide Web, который, как правило, используется для построения веб-служб. Термин REST был введен в 2000 году Роем Филдингом, одним из авторов HTTP-протокола. Системы, поддерживающие REST, называются RESTful-системами.
В общем случае REST является очень простым интерфейсом управления информацией без использования каких-то дополнительных внутренних прослоек. Каждая единица информации однозначно определяется глобальным идентификатором, таким как URL. Каждый URL в свою очередь имеет строго заданный формат.
Вот как это будет выглядеть на примере:
```
GET /book/ — получить список всех книг
GET /book/3/ — получить книгу номер 3
PUT /book/ — добавить книгу (данные в теле запроса)
POST /book/3 — изменить книгу (данные в теле запроса)
DELETE /book/3 — удалить книгу
```
REST (сокр. от англ. Representational State Transfer — «передача репрезентативного состояния») — метод взаимодействия компонентов распределённого приложения в сети Интернет, при котором вызов удаленной процедуры представляет собой обычный HTTP-запрос (обычно GET или POST; такой запрос называют REST-запрос), а необходимые данные передаются в качестве параметров запроса. Этот способ является альтернативой более сложным методам, таким как SOAP, CORBA и RPC.
В широком смысле REST означает концепцию построения распределённого приложения, при которой компоненты взаимодействуют наподобие взаимодействия клиентов и серверов во Всемирной паутине.
Хотя данная концепция лежит в самой основе Всемирной паутины, но термин REST был введён Роем Филдингом, одним из создателей протокола HTTP, лишь в 2000 году. В своей диссертации в Калифорнийском университете в Ирвайне он подвёл теоретическую основу под метод взаимодействия клиентов и серверов во Всемирной паутине, абстрагировав его и назвав «передачей репрезентативного состояния». Филдинг описал концепцию построения распределённого приложения, при которой каждый запрос (REST-запрос) клиента к серверу содержит в себе исчерпывающую информацию о желаемом ответе сервера (желаемом репрезентативном состоянии), и сервер не обязан сохранять информацию о состоянии клиента («клиентской сессии»).

__Архитектура REST__

Как необходимые условия для построения распределенных REST-приложений Филдинг перечислил следующие:

1. Клиент-серверная архитектура.
2. Сервер не обязан сохранять информацию о состоянии клиента.
3. В каждом запросе клиента должно явно содержаться указание о возможности кэширования ответа и получения ответа из существующего кэша
4. Клиент может взаимодействовать не напрямую с сервером, а с произвольным количеством промежуточных узлов. При этом клиент может не знать о существовании промежуточных узлов, за исключением случаев передачи конфиденциальной информации.
5. Унифицированный программный интерфейс сервера. Филдинг приводил URI в качестве примера формата запросов к серверу, а в качестве примера ответа сервера форматы HTML, XML и JSON, различаемые с использованием идентификаторов MIME.

Филдинг указывал, что приложения, не соответствующие приведённым условиям, не могут называться REST-приложениями. Если же все условия соблюдены, то, по его мнению, приложение получит следующие преимущества:

* надёжность (за счет отсутствия необходимости сохранять информацию о состоянии клиента, которая может быть утеряна);
* производительность (за счет использования кэша);
* масштабируемость;
* прозрачность системы взаимодействия, особенно необходимую для приложений обслуживания сети;
* простоту интерфейсов;
* портативность компонентов;
* легкость внесения изменений;
* способность эволюционировать, приспосабливаясь к новым требованиям (на примере Всемирной паутины).

## Как загрузить что-то из интернета? NSURL, NSURLSession, NSURLConnection, NSURLRequest
The iOS SDK allows us to connect to the Internet and retrieve and send data using the `NSURLConnection` class. JSON serialization and deserialization will all be done using the `NSJSONSerialization` class. XML parsing will be done using `NSXMLParser`, and the Twitter connectivity will be done using the Twitter framework.
The iOS 7 SDK brings along new classes that we can take advantage of in this chapter. One of these classes is the `NSURLSession`, which manages the connectivity to web services in a more thorough way than the `NSURLConnection` class does.
```objectivec
- (void)getImageFromURL:(NSString *)url {
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
        NSURL *myUrl = [NSURL URLWithString:url];
        NSData *data = [NSData dataWithContentsOfURL:myUrl];
        dispatch_sync(dispatch_get_main_queue(), ^{
            self.cityPicture = [UIImage imageWithData:data];
        });
    });
}
```

## Парсинг JSON, HTML, XML
Парсинг – обработка данных, разбор входной последовательности с целью получения токенов.
Токен – лексема, минимальная единица языка, имеющая самостоятельный смысл (имя, знак операции, ключевое слово)
Регулярные выражения – формальный язык поиска и осуществления манипуляций с подстроками в тексте, основанный на использовании метасимволов (символов-джокеров, англ. wildcard characters). По сути, это строка-образец (англ. pattern, по-русски её часто называют «шаблоном», «маской»), состоящая из символов и метасимволов и задающая правило поиска. The NSRegularExpression class is used to represent and apply regular expressions to Unicode strings. An instance of this class is an immutable representation of a compiled regular expression pattern and various option flags. Example use the regular expression `\\b(a|b)(c|d)\\b`. This snippet creates a regular expression to match two-letter words, in which the first letter is “a” or “b” and the second letter is “c” or “d”. Specifying `NSRegularExpressionCaseInsensitive` means that matches will be case-insensitive, so this will match “BC”, “aD”, and so forth, as well as their lower-case equivalents.
```objectivec
NSError *error = NULL;
NSRegularExpression *regex = [NSRegularExpression regularExpressionWithPattern:@"\\b(a|b)(c|d)\\b" options:NSRegularExpressionCaseInsensitive error:&error];
```
Для парсинга XML в Objective-C существует класс `NSXMLParser`. О нахождении каких-либо элементов парсер уведомляет свой делегат. Делегат должен следовать протоколу `NSXMLParserDelegate`.
HTML (HyperText Markup Language) is a markup language, that tells browsers how to layout a web page. By its very nature, this content is in a hierarchy that defines where within the page a piece of information is to be displayed. You may also be aware of XML (eXtensible Markup Language). This also defines a hierarchy of information, and you may at this point be thinking that perhaps HTML is related to XML. You’d be right to think that, and also wrong!
There are two flavors of HTML: the one that is pure XML, and the original, where-it-all-started HTML. HTML is “sort of” an XML document, but with more relaxed rules.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/html_parsing.png">

Represent object in a stream, JSON better then HTML or XML.
JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language, Standard ECMA-262 3rd Edition - December 1999. JSON is a text format that is completely language independent but uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python, and many others. These properties make JSON an ideal data-interchange language.
```json
{  
   "menu":{  
      "id":"file",
      "value":"File",
      "popup":{  
         "menuitem":[  
            {  
               "value":"New",
               "onclick":"CreateNewDoc()"
            },
            {  
               "value":"Open",
               "onclick":"OpenDoc()"
            },
            {  
               "value":"Close",
               "onclick":"CloseDoc()"
            }
         ]
      }
   }
}
```
```xml
<?xml version="1.0" encoding="UTF-8"?>
<menu id="file" value="File">
   <popup>
      <menuitem value="New" onclick="CreateNewDoc()" />
      <menuitem value="Open" onclick="OpenDoc()" />
      <menuitem value="Close" onclick="CloseDoc()" />
   </popup>
</menu>
```

# Data
## Что такое Core Data?
Apple предоставляет гибкий фреймворк для работы с хранимыми на устройстве данными — Core Data. Большинство деталей по работе с хранилищем данных Core Data скрывает, позволяя вам сконцентрироваться на том, что действительно делает ваше приложение веселым, уникальным и удобным в использовании. Не смотря на то, что Core Data может хранить данные в реляционной базе данных вроде SQLite, Core Data не является СУБД (системой управления БД). По-правде, Core Data в качестве хранилища может вообще не использовать реляционные базы данных. Core Data скорее является оболочкой для работы с данными, которая позволяет работать с сущностями и их связями (отношениями к другим объектами), атрибутами, в том виде, который напоминает работы с объектным графом в обычном объектно-ориентированном программировании.

## Опишите стек Core Data

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/nsmanagedobjectcontext.png">

_NSManagedObjectModel_

The `NSManagedObjectModel` instance describes the data that is going to be accessed by the Core Data stack. During the creation of the Core Data stack, the `NSManagedObjectModel` (often referred to as the “mom”) is loaded into memory as the first step in the creation of the stack. The example code above resolves an `NSURL` from the main application bundle using a known filename (in this example `DataModel.momd`) for the `NSManagedObjectModel`. Once the `NSManagedObjectModel` object is initialized, the `NSPersistentStoreCoordinator` object is constructed.

_NSPersistentStoreCoordinator_

The `NSPersistentStoreCoordinator` sits in the middle of the Core Data stack. The coordinator is responsible for realizing instances of entities that are defined inside of the model. It creates new instances of the entities in the model, and it retrieves existing instances from a persistent store (`NSPersistentStore`). The persistent store can be on disk or in memory. Depending on the structure of the application, it is possible, although uncommon, to have more than one persistent store being coordinated by the `NSPersistentStoreCoordinator`.

Whereas the `NSManagedObjectModel` defines the structure of the data, the `NSPersistentStoreCoordinator` realizes objects from the data in the persistent store and passes those objects off to the requesting `NSManagedObjectContext`. The `NSPersistentStoreCoordinator` also verifies that the data is in a consistent state that matches the definitions in the `NSManagedObjectModel`.

Координатор предназначен для представления фасада для управляемого контекстом объекта, так что группа постоянных хранилищ выглядит как единое совокупное хранилище. Управляемый объект контекста может создать граф объектов на основе объединения всех хранилищ данных координатора. Координатор может быть связан только с одной управляемой объектной моделью. Если Вы хотите положить различные субъекты в различные хранилища, вы должны разделить вашу модель, определяя конфигурацию в управляемой модели объекта.

_NSManagedObjectContext_

The managed object context (`NSManagedObjectContext`) is the object that your application will be interacting with the most, and therefore it is the one that is exposed to the rest of your application. Think of the managed object context as an intelligent scratch pad. When you fetch objects from a persistent store, you bring temporary copies onto the scratch pad where they form an object graph (or a collection of object graphs). You can then modify those objects however you like. Unless you actually save those changes, however, the persistent store remains unaltered.

All managed objects must be registered with a managed object context. You use the context to add objects to the object graph and remove objects from the object graph. The context tracks the changes you make, both to individual objects’ attributes and to the relationships between objects. By tracking changes, the context is able to provide undo and redo support for you. It also ensures that if you change relationships between objects, the integrity of the object graph is maintained.

If you choose to save the changes you have made, the context ensures that your objects are in a valid state. If they are, the changes are written to the persistent store (or stores), new records are added for objects you created, and records are removed for objects you deleted.

Without Core Data, you have to write methods to support archiving and unarchiving of data, to keep track of model objects, and to interact with an undo manager to support undo. In the Core Data framework, most of this functionality is provided for you automatically, primarily through the managed object context.

## В каких случаях лучше использовать SQLite, а в каких Core Data?
_Реляционная база данных_ — база данных, основанная на реляционной модели данных. Слово «реляционный» происходит от англ. relation (отношение). Для работы с реляционными БД применяют реляционные СУБД.

_Реляционная модель данных (РМД)_ — логическая модель данных, прикладная теория построения баз данных, которая является приложением к задачам обработки данных таких разделов математики как теории множеств и логика первого порядка. Термин «реляционный» означает, что теория основана на математическом понятии отношение (relation). В качестве неформального синонима термину «отношение» часто встречается слово таблица. Необходимо помнить, что «таблица» есть понятие нестрогое и неформальное и часто означает не «отношение» как абстрактное понятие, а визуальное представление отношения на бумаге или экране. Некорректное и нестрогое использование термина «таблица» вместо термина «отношение» нередко приводит к недопониманию. Наиболее частая ошибка состоит в рассуждениях о том, что РМД имеет дело с «плоскими», или «двумерными» таблицами, тогда как таковыми могут быть только визуальные представления таблиц. Отношения же являются абстракциями, и не могут быть ни «плоскими», ни «неплоскими».

_ORM_ – Object-relational mapping, объектно-реляционное отображение – преобразование данных между ООП и реляционными базами данных.

_SQL_ – Структурированный язык запросов (Structed Query Language) – является информационно-логическим языком, предназначенным для описания, изменения и извлечения данных, хранимых в реляционных базах данных (relation, отношение).

__Пример SQL:__

Create a table to store information about weather observation stations:

-- No duplicate ID fields allowed
```sql
CREATE TABLE STATION
(ID INTEGER PRIMARY KEY,
CITY CHAR(20),
STATE CHAR(2),
LAT_N REAL,
LONG_W REAL);
```
populate the table STATION with a few rows:
```sql
INSERT INTO STATION VALUES (13, 'Phoenix', 'AZ', 33, 112);
INSERT INTO STATION VALUES (44, 'Denver', 'CO', 40, 105);
INSERT INTO STATION VALUES (66, 'Caribou', 'ME', 47, 68);
```
query to look at table STATION in undefined order:
```sql
SELECT * FROM STATION;
```
ID | CITY | STATE | LAT_N | LONG_W
---|------|-------|-------|-------
13 | Phoenix | AZ | 33 | 112
44 | Denver | CO | 40 | 105
66 | Caribou | ME | 47 | 68

query to select Northern stations (Northern latitude > 39.7):

-- selecting only certain rows is called a "restriction".
```sql
SELECT * FROM STATION
WHERE LAT_N > 39.7;
```
ID | CITY | STATE | LAT_N | LONG_W
---|------|-------|-------|-------
44 | Denver | CO | 40 | 105
66 | Caribou | ME | 47 | 68

query to select only ID, CITY, and STATE columns:

-- selecting only certain columns is called a "projection".
```sql
SELECT ID, CITY, STATE FROM STATION;
```
ID | CITY | STATE
---|------|------
13 | Phoenix | AZ
44 | Denver | CO
66 | Caribou | ME

query to both "restrict" and "project":
```sql
SELECT ID, CITY, STATE FROM STATION
WHERE LAT_N > 39.7;
```
ID | CITY | STATE
---|------|------
44 | Denver | CO
66 | Caribou | ME

## Целесообразность использования Core Data
Core Data уменьшает количество кода, написанного для поддержки модели слоя приложения, как правило, на 50% - 70%, измеряемое в строках кода. Core Data имеет зрелый код, качество которого обеспечивается путем юнит-тестов, и используется ежедневно миллионами клиентов в широком спектре приложений. Структура была оптимизирована в течение нескольких версий. Она использует информацию, содержащуюся в модели и выполненяет функции, как правило, не работающие на уровне приложений в коде. Кроме того, в дополнение к отличной безопасности и обработке ошибок, она предлагает лучшую масштабируемость при работе с памятью, относительно любого конкурирующего решения. Другими словами: вы могли бы потратить долгое время тщательно обрабатывая Ваши собственные решения оптимизации для конкретной предметной области, вместо того, чтобы получить преимущество в производительности, которую Core Data предоставляет бесплатно для любого приложения.

__Когда нецелесообразно использовать Core Data:__
* если планируется использовать очень небольшой объем данных. В этом случае проще воспользоваться для хранения Ваших данных объектами коллекций - массивами или словарями и сохранять их в .plist файлы.
* если используется кросс-платформерная архитектура или требуется доступ к строго определенному формату файла с данными (хранилищу), например SQLite.
* использование баз данных клиент-сервер, например MySQL или PostgreSQL.

__SQLite__
* Максимальный объем хранимых данных базы SQLite составляет 2 терабайта.
* Чтение из базы данных может производиться одним и более потоками, например несколько процессов могут одновременно выполнять `SELECT`. Однако запись в базу данных может осуществляться, только, если база в данный момент не занята другим процессом.
* SQLite не накладывает ограничения на типы данных. Любые данные могут быть занесены в любой столбец. Ограничения по типам данных действуют только на `INTEGER PRIMARY KEY`, который может содержать только 64-битное знаковое целое.

SQLite версии 3.0 и выше позволяет хранить BLOB данные в любом поле, даже если оно объявлено как поле другого типа.
Обращение к SQLite базе из двух потоков одновременно неизбежно вызовет краш. Выхода два:

1. Синхронизируйте обращения при помощи директивы `@synchronized`.
2. Если задача закладывается на этапе проектирования, завести менеджер запросов на основе `NSOperationQueue`. Он страхует от ошибок автоматически, а то, что делается автоматически, часто делается без ошибок.

__Пример SQLite__

```objectivec
- (int)createTable:(NSString *)filePath {
    sqlite3 *db = NULL;
    int rc = 0;

    rc = sqlite3_open_v2([filePath cStringUsingEncoding:NSUTF8StringEncoding], &db, SQLITE_OPEN_READWRITE | SQLITE_OPEN_CREATE, NULL);
    if (SQLITE_OK != rc) {
        sqlite3_close(db);
        NSLog(@"Failed to open db connection");
    } else {
        char *query ="CREATE TABLE IF NOT EXISTS students (id INTEGER PRIMARY KEY AUTOINCREMENT, name  TEXT, age INTEGER, marks INTEGER)";
        char *errMsg;
        rc = sqlite3_exec(db, query, NULL, NULL, &errMsg);
        if (SQLITE_OK != rc) {
            NSLog(@"Failed to create table rc:%d, msg=%s",rc,errMsg);
        }
        sqlite3_close(db);
    }
    return rc;
}

- (int)insert:(NSString *)filePath withName:(NSString *)name age:(NSInteger)age marks:(NSInteger)marks {
    sqlite3 *db = NULL;
    int rc = 0;
    rc = sqlite3_open_v2([filePath cStringUsingEncoding:NSUTF8StringEncoding], &db, SQLITE_OPEN_READWRITE, NULL);
    if (SQLITE_OK != rc) {
        sqlite3_close(db);
        NSLog(@"Failed to open db connection");
    } else {
        NSString *query  = [NSString stringWithFormat:@"INSERT INTO students (name, age, marks) VALUES (\"%@\", %ld, %ld)", name, (long)age, (long)marks];
        char *errMsg;
        rc = sqlite3_exec(db, [query UTF8String], NULL, NULL, &errMsg);
        if (SQLITE_OK != rc) {
            NSLog(@"Failed to insert record  rc:%d, msg=%s",rc,errMsg);
        }
        sqlite3_close(db);
    }
    return rc;
}
```

## Какие есть нюансы при использовании Core Data в разных потоках? Как синхронизировать данные между потоками?
1. Create a separate managed object context for each thread and share a single persistent store coordinator. This is the typically-recommended approach.
2. Create a separate managed object context and persistent store coordinator for each thread. This approach provides for greater concurrency at the expense of greater complexity (particularly if you need to communicate changes between different contexts) and increased memory usage.

# Какие типы хранилищ поддерживает CoreData?
Persistent Store

* SQLite
* Binary
* XML

Atomic Store

* custom type

## Что такое ленивая загрузка? Что ее связывает с Core Data? Опишите ситуация когда она может быть полезной? Что такое faulting?
Для загрузки данных из БД в память приложения удобно пользоваться загрузкой не только данных об объекте, но и о сопряжённых с ним объектах. Это делает загрузку данных проще для разработчика: он просто использует объект, который, тем не менее вынужден загружать все данные в явном виде. Но это ведёт к случаям, когда будет загружаться огромное количество сопряжённых объектов, что плохо скажется на производительности в случаях, когда эти данные реально не нужны. Паттерн Lazy Loading (Ленивая Загрузка) подразумевает отказ от загрузки дополнительных данных, когда в этом нет необходимости. Вместо этого ставится маркер о том, что данные не загружены и их надо загрузить в случае, если они понадобятся. Как известно, если Вы ленивы, то вы выигрываете в том случае, если дело, которое вы не делали на самом деле и не надо было делать.
Faulting isn't unique to Core Data. A similar technique is used in many other frameworks, such as Ember and Ruby on Rails. Faulting is a mechanism Core Data employs to reduce your application’s memory usage, only load data when it's needed. A fault is a placeholder object that represents a managed object that has not yet been fully realized, or a collection object that represents a relationship. To make faulting work, Core Data does a bit of magic under the hood by creating custom subclasses at compile time that represent the faults.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/core_data_faulting.png">

## Что такое fetch result controller?
Данные сами по себе может быть и представляют какую-либо ценность, но, обычно их нужно использовать. Одним из элементов представления данных в iOS служат таблицы (объекты класса `UITableView`), которые через объект класса `NSFetchedResultsController` можно привязать к CoreData. После этого при изменении данных в CoreData будет актуализироваться информация в таблице. Так же, с помощью таблицы можно управлять данными в хранилище.
`NSFetchedResultsController` — контроллер результатов выборки. Создается, обычно один экземпляр на `ViewController`, но вполне может работать и без оного, внутрь которого помещается исключительно для того, что бы было проще привязать данные к виду.

# Тестирование
## Unit Tests
Tests the smallest unit of functionality, typically a method/function (e.g. given a class with a particular state, calling x method on the class should cause y to happen). Unit tests should be focussed on one particular feature (e.g., calling the pop method when the stack is empty should throw an InvalidOperationException). Everything it touches should be done in memory; this means that the test code and the code under test shouldn't:

1.	Call out into (non-trivial) collaborators
2.	Access the network
3.	Hit a database
4.	Use the file system
5.	Spin up a thread
etc.
Any kind of dependency that is slow / hard to understand / initialise / manipulate should be stubbed / mocked / whatevered using the appropriate techniques so you can focus on what the unit of code is doing, not what its dependencies do.
In short, unit tests are as simple as possible, easy to debug, reliable (due to reduced external factors), fast to execute and help to prove that the smallest building blocks of your program function as intended before they're put together. The caveat is that, although you can prove they work perfectly in isolation, the units of code may blow up when combined which brings us to ...
## Integration Tests
Integration tests build on unit tests by combining the units of code and testing that the resulting combination functions correctly. This can be either the innards of one system, or combining multiple systems together to do something useful. Also, another thing that differentiates integration tests from unit tests is the environment. Integration tests can and will use threads, access the database or do whatever is required to ensure that all of the code and the different environment changes will work correctly.
If you've built some serialization code and unit tested its innards without touching the disk, how do you know that it'll work when you are loading and saving to disk? Maybe you forgot to flush and dispose filestreams. Maybe your file permissions are incorrect and you've tested the innards using in memory streams. The only way to find out for sure is to test it 'for real' using an environment that is closest to production.
The main advantage is that they will find bugs that unit tests can't such as wiring bugs (e.g. an instance of class A unexpectedly receives a null instance of B) and environment bugs (it runs fine on my single-CPU machine, but my colleague's 4 core machine can't pass the tests). The main disadvantage is that integration tests touch more code, are less reliable, failures are harder to diagnose and the tests are harder to maintain.
Also, integration tests don't necessarily prove that a complete feature works. The user may not care about the internal details of my programs, but I do!
## Functional Tests
Functional tests check a particular feature for correctness by comparing the results for a given input against the specification. Functional tests don't concern themselves with intermediate results or side-effects, just the result (they don't care that after doing x, object y has state z). They are written to test part of the specification such as, "calling function `Square(x)` with the argument of `2` returns `4`".
## Acceptance Tests
Acceptance testing seems to be split into two types:
Standard acceptance testing involves performing tests on the full system (e.g. using your web page via a web browser) to see whether the application's functionality satisfies the specification. E.g. "clicking a zoom icon should enlarge the document view by 25%." There is no real continuum of results, just a pass or fail outcome.
The advantage is that the tests are described in plain English and ensures the software, as a whole, is feature complete. The disadvantage is that you've moved another level up the testing pyramid. Acceptance tests touch mountains of code, so tracking down a failure can be tricky.
Also, in agile software development, user acceptance testing involves creating tests to mirror the user stories created by/for the software's customer during development. If the tests pass, it means the software should meet the customer's requirements and the stories can be considered complete. An acceptance test suite is basically an executable specification written in a domain specific language that describes the tests in the language used by the users of the system.

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

http://albertodebortoli.com/blog/2013/04/21/objective-c-blocks-under-the-hood/

http://albertodebortoli.com/blog/2013/08/03/objective-c-blocks-caveat/

https://www.mikeash.com/pyblog/friday-qa-2009-08-14-practical-blocks.html

http://rypress.com/tutorials/objective-c/blocks

http://clang.llvm.org/docs/Block-ABI-Apple.html#imported-variables

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

##Swift closures and functions
```swift
()->()
```
Closures in Swift are similar to blocks in C and Objective-C.
Closures are first-class objects, so that they can be nested and passed around (as do blocks in Objective-C). In Swift, functions are just a special case of closures.

_Defining a function:_

You define a function with the `func` keyword. Functions can take and return none, one or multiple parameters (tuples).
Return values follow the `->` sign.
```swift
func jediGreet(name: String, ability: String) -> (farewell: String, mayTheForceBeWithYou: String) {
	return ("Good bye, \(name).", " May the \(ability) be with you.")
}
```
_Calling a function:_
```swift
let retValue = jediGreet("old friend", "Force")
println(retValue)
println(retValue.farewell)
println(retValue.mayTheForceBeWithYou)
```
_Function types_

Every function has its own function type, made up of the parameter types and the return type of the function itself.
For example the following function:
```swift
func sum(x: Int, y: Int) -> (result: Int) { return x + y }
```
has a function type of:
```swift
(Int, Int) -> (Int)
```
Function types can thus be used as parameters types or as return types for nesting functions.

_Passing and returning functions_

The following function is returning another function as its result which can be later assigned to a variable and called.
```swift
func jediTrainer() -> ((String, Int) -> String) {
	func train(name: String, times: Int) -> (String) {
		return "\(name) has been trained in the Force \(times) times"
  	}
  	return train
}
let train = jediTrainer()
train("Obi Wan", 3)
```
_Variadic functions_

Variadic functions are functions that have a variable number of arguments (indicated by `...` after the argument's type) that can be accessed into their body as an array.
```swift
func jediBladeColor(colors: String...) -> () {
	for color in colors {
		println("\(color)")
  	}
}
jediBladeColor("red","green")
```

__Closures__
```swift
{()->() in}
```
_Defining a closure:_

Closures are typically enclosed in curly braces `{ }` and are defined by a function type `() -> ()`, where `->` separates the arguments and the return type, followed by the `in` keyword which separates the closure header from its body.
```swift
{ (params) -> returnType in
  statements
}
```
An example could be the map function applied to an Array:
```swift
let padawans = ["Knox", "Avitla", "Mennaus"]
padawans.map({(padawan: String) -> String in
	"\(padawan) has been trained!"
})
```

_Closures with known types:_
When the type of the closure's arguments are known, you can do as follows:
```swift
func applyMutliplication(value: Int, multFunction: Int -> Int) -> Int {
	return multFunction(value)
}

applyMutliplication(2, {value in
	value * 3
})
```

_Closures shorthand argument names:_

Closure arguments can be references by position `($0, $1, ...)` rather than by name
```swift
applyMutliplication(2, {$0 * 3})
```
Furthermore, when a closure is the last argument of a function, parenthesis can be omitted as such:
```swift
applyMutliplication(2) {$0 * 3}
```
##How Do I Declare a Closure in Swift?
_As a variable:_
```swift
var closureName: (parameterTypes) -> (returnType)
```
_As an optional variable:_
```swift
var closureName: ((parameterTypes) -> (returnType))?
```
_As a type alias:_
```swift
typealias closureType = (parameterTypes) -> (returnType)
```
_As a constant:_
```swift
let closureName: closureType = { ... }
```
_As an argument to a function call:_
```swift
func({(parameterTypes) -> (returnType) in statements})
```
_As a function parameter:_
```swift
array.sort({ (item1: Int, item2: Int) -> Bool in return item1 < item2 })
```
_As a function parameter with implied types:_
```swift
array.sort({ (item1, item2) -> Bool in return item1 < item2 })
```
_As a function parameter with implied return type:_
```swift
array.sort({ (item1, item2) in return item1 < item2 })
```
_As the last function parameter:_
```swift
array.sort { (item1, item2) in return item1 < item2 }
```
_As the last parameter, using shorthand argument names:_
```swift
array.sort { return $0 < $1 }
```
_As the last parameter, with an implied return value:_
```swift
array.sort { $0 < $1 }
```
_As the last parameter, as a reference to an existing function:_
```swift
array.sort(<)
```
_As a function parameter with explicit capture semantics:_
```swift
array.sort({ [unowned self] (item1: Int, item2: Int) -> Bool in
	return item1 < item2
})
```
_As a function parameter with explicit capture semantics and inferred parameters / return type:_
```swift
array.sort({ [unowned self] in return item1 < item2 })
```

# Autolayout

_"Use Auto Layout"_ determines whether a storyboard uses the Auto Layout features introduced in iOS 6 to automatically layout your interface using constraints.

_"Use Size Classes"_ enables a new Xcode 6 feature called size classes that lets you use Auto Layout to build one interface for all devices and customize constraint constants, and certain views and constraints for different interface idioms while reusing the general layout. It saves the work and repetitiveness of having to build and maintain both MainiPhone and MainiPad storyboards.

__External Changes__

External changes occur when the size or shape of your superview changes.

__Internal Changes__

Internal changes occur when the size of the views or controls in your user interface change.

There are three main approaches to laying out a user interface.

1. you can programmatically lay out the user interface
2. you can use autoresizing masks to automate some of the responses to external change
3. you can use Auto Layout.

The frame defined the view’s origin, height, and width in the superview’s coordinate system.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/autolayout_frame1.png"><img src="https://github.com/sashakid/ios-guide/blob/master/Images/autolayout_frame2.png">

The layout of your view hierarchy is defined as a series of linear equations. Each constraint represents a single equation. Your goal is to declare a series of equations that has one and only one possible solution.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/autolayout.png">

When calculating solutions, Auto Layout attempts to satisfy all the constraints in priority order from highest to lowest. If it cannot satisfy an optional constraint, that constraint is skipped and it continues on to the next constraint.

Some views have a natural size given their current content. This is referred to as their _intrinsic content size_.

__The content hugging__ pulls the view inward so that it fits snugly around the content.

__The compression resistance__ pushes the view outward so that it does not clip the content.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/intrinsic.png">

```
// Compression Resistance
View.height >= 0.0 * NotAnAttribute + IntrinsicHeight
View.width >= 0.0 * NotAnAttribute + IntrinsicWidth

// Content Hugging
View.height <= 0.0 * NotAnAttribute + IntrinsicHeight
View.width <= 0.0 * NotAnAttribute + IntrinsicWidth
```
These properties only take effect for views which define an intrinsic content size, otherwise there is no content size defined that could resist compression or be hugged.
The top and bottom layout guides represent the upper and lower edge of the visible content area for the currently active view controller.

Auto Layout does not operate on views’ frame, but on their alignment rect. It’s easy to forget the subtle difference, because in many cases they are the same.

Unsatisfiable layouts occur when the system cannot find a valid solution for the current set of constraints. Two or more required constraints conflict, because they cannot all be true at the same time.
When the system detects a unsatisfiable layout at runtime, it performs the following steps:

1. Auto Layout identifies the set of conflicting constraints.
2. It breaks one of the conflicting constraints and checks the layout. The system continues to break constraints until it finds a valid layout.
3. Auto Layout logs information about the conflict and the broken constraints to the console.

As soon as you know about the error, the solution is typically very straightforward. Either remove one of the constraints, or change it to an optional constraint.

Ambiguous layouts occur when the system of constraints has two or more valid solutions. There are two main causes:

1. The layout needs additional constraints to uniquely specify the position and location of every view. After you determine which views are ambiguous, just add constraints to uniquely specify both the view’s position and its size.
2. The layout has conflicting optional constraints with the same priority, and the system does not know which constraint it should break.

Here, you need to tell the system which constraint it should break, by changing the priorities so that they are no longer equal. The system breaks the constraint having the lowest priority first.
When an ambiguous layout occurs at runtime, Auto Layout chooses one of the possible solutions to use. This means the layout may or may not appear as you expect. Furthermore, there are no warnings written to the console, and there is no way to set a breakpoint for ambiguous layouts.
There are a few methods you can call to help identify ambiguous layouts. All of these methods should be used only for debugging. Set a breakpoint somewhere where you can access the view hierarchy, and then call one of the following methods from the console:

`hasAmbiguousLayout` Available for both iOS and OS X. Call this method on a misplaced view. It returns YES if the view’s frame is ambiguous. Otherwise, it returns NO.

`exerciseAmbiguityInLayout` Available for both iOS and OS X. Call this method on a view with ambiguous layout. This will toggle the system between the possible valid solutions.

`constraintsAffectingLayoutForAxis:` Available for iOS. Call this method on a view. It returns an array of all the constraints affecting that view along the specified axis.

`constraintsAffectingLayoutForOrientation` Available for OS X. Call this method on a view. It returns an array of all the con-straints affecting that view along the specified orientation.

`_autolayoutTrace` Available as a private method in iOS. Call this method on a view. It returns a string with diagnostic information about the entire view hierarchy containing that view. Ambiguous views are labeled, and so are views that have translatesAutoresizingMaskIntoConstraints set to YES.

Four of these are the Final size classes:

1. Compact-Compact
2. Compact-Regular
3. Regular-Compact
4. Regular-Regular

Base size classes:

5. Compact-Any
6. Regular-Any
7. Any-Compact
8. Any-Regular
9. Any-Any

It is typically easiest to work from the most general size class to the most specific. Select the default layout for your app, and design this layout in the Any-Any size class. Then modify the other Base or Final size classes as needed.

Compared to working with springs and struts, Auto Layout introduces two additional steps to the process before views can be displayed:

* updating constraints
* laying out views

Each step is dependent on the one before; display depends on layout, and layout depends on updating constraints.

The first step – updating constraints – can be considered a “measurement pass.” It happens bottom-up (from subview to super view) and prepares the information needed for the layout pass to actually set the views’ frame. You can trigger this pass by calling setNeedsUpdateConstraints. Any changes you make to the system of constraints itself will automatically trigger this. However, it is useful to notify Auto Layout about changes in custom views that could affect the layout. Speaking of custom views, you can override `updateConstraints` to add the local constraints needed for your view in this phase.

The second step – layout – happens top-down (from super view to subview). This layout pass actually applies the solution of the constraint system to the views by setting their frames (on OS X) or their center and bounds (on iOS). You can trigger this pass by calling `setNeedsLayout`, which does not actually go ahead and apply the layout immediately, but takes note of your request for later. This way you don’t have to worry about calling it too often, since all the layout requests will be coalesced into one layout pass.
To force the system to update the layout of a view tree immediately, you can call `layoutIfNeeded` / `layoutSubtreeIfNeeded` (on iOS and OS X respectively). This can be helpful if your next steps rely on the views’ frame being up to date. In your custom views you can override `layoutSubviews` / `layout` to gain full control over the layout pass.

Finally, the display pass renders the views to screen and is independent of whether you’re using Autolayout or not. It operates top-down and can be triggered by calling `setNeedsDisplay`, which results in a deferred redraw coalescing all those calls. Overriding the familiar `drawRect:` is how you gain full control over this stage of the display process in your custom views.

Since each step depends on the one before it, the display pass will trigger a layout pass if any layout changes are pending. Similarly, the layout pass will trigger updating the constraints if the constraint system has pending changes.

It’s important to remember that these three steps are not a one-way street. Constraint-based layout is an iterative process. The layout pass can make changes to the constraints based on the previous layout solution, which again triggers updating the constraints following another layout pass. This can be leveraged to create advanced layouts of custom views, but you can also get stuck in an infinite loop if every call of your custom implementation of layoutSubviews results in another layout pass.

# Swift
* Multi-paradigm: protocol-oriented, object-oriented, functional, imperative, block structured
* Designed by	Chris Lattner and Apple Inc.
* First appeared:	June 2, 2014
* Stable release:	3.1.1 / April 21, 2017
* Typing discipline:	Static, strong, inferred
* OS: Darwin, Linux, FreeBSD
* Influenced by C#, CLU, D, Haskell, Objective-C, Python, Ruby, Rust

Swift is a multi-paradigm, compiled programming language created by Apple Inc. for iOS, OS X, watchOS and tvOS development. Swift is designed to work with Apple's Cocoa and Cocoa Touch frameworks and the large body of existing Objective-C code written for Apple products. Swift is in-tended to be more resilient to erroneous code ("safer") than Objective-C and also more concise. It is built with the LLVM compiler framework included in Xcode 6 and later and uses the Objective-C runtime, allowing C, Objective-C, C++ and Swift code to run within a single program.
Swift supports the core concepts that made Objective-C flexible, notably dynamic dispatch, wide-spread late binding, extensible programming, and similar features. These features also have well known performance and safety trade-offs, which Swift was designed to address. For safety, Swift introduced a system that helps address common programming errors like null pointers, as well as introducing syntactic sugar to avoid the pyramid of doom that can result. For performance issues, Apple has invested considerable effort in aggressive optimization that can flatten out method calls and accessors to eliminate this overhead. More fundamentally, Swift has added the concept of protocol extensibility, an extensibility system that can be applied to types, structs and classes, Apple promotes this as a real change in programming paradigms they refer to as "protocol-oriented programming".
Swift was introduced at Apple's 2014 Worldwide Developers Conference (WWDC). It underwent an upgrade to version 1.2 during 2014, and a more major upgrade to Swift 2 at WWDC 2015. Initially a proprietary language, it was announced that Swift 2 would become open source later that year, sup-porting iOS, OS X and Linux.

__History__

Development on Swift began in 2010 by Chris Lattner, with the eventual collaboration of many other programmers at Apple. Swift took language ideas "from Objective-C, Rust, Haskell, Ruby, Python, C#, CLU, and far too many others to list". On June 2, 2014, the Worldwide Developers Conference (WWDC) application became the first publicly released app written in Swift. A beta version of the programming language was released to registered Apple developers at the conference, but the company did not promise that the final version of Swift would be source-compatible with the test version. Apple planned to make source code converters available if needed for the full release.
The Swift Programming Language, a free 500-page manual, was also released at WWDC, and is available on the iBooks Store.

__Features__

Swift is an alternative for the Objective-C language that employs contemporary programming language theory concepts and strives to present a simpler syntax. During its introduction, it was described simply as "Objective-C without the C".
By default, Swift does not expose pointers and other unsafe accessors, contrary to Objective-C, which uses pointers pervasively to refer to object instances. Additionally, Objective-C's use of a Smalltalk-like syntax for making method calls has been replaced with a dot-notation style and namespace system more familiar to programmers from other common object-oriented (OO) languages like Java or C#. Swift introduces true named parameters and retains key Objective-C concepts, including protocols, closures and categories, often replacing former syntax with cleaner versions and allowing these concepts to be applied to other language structures, like enums.

_Generics_

Generic code enables you to write flexible, reusable functions and types that can work with any type, subject to requirements that you define. You can write code that avoids duplication and expresses its intent in a clear, abstracted manner.
Generics are one of the most powerful features of Swift, and much of the Swift standard library is built with generic code. In fact, you’ve been using generics throughout the Language Guide, even if you didn’t realize it. For example, Swift’s Array and Dictionary types are both generic collections. You can create an array that holds Int values, or an array that holds String values, or indeed an array for any other type that can be created in Swift. Similarly, you can create a dictionary to store values of any specified type, and there are no limitations on what that type can be.
```swift
func swapTwoValues<T>(inout a: T, inout _ b: T) {
	let temporaryA = a
	a = b
	b = temporaryA
}
```

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
* что такое volatile? что такое inline функции?
* в чем отличие потока от процесса?
* NSThread vs pthread
* сокет, tcp, udp когда что применять?
* гонка потоков, методы синхронизации, защита критической секции, семафор, мьютекс, барьер, что это и зачем нужно? что такое OSSpinLock?
* как передавать данные между NSOperation? когда операция отправленная в NSOperationQueue начинает выполняться, можно ли отло-жить выполнение?
* как тестировать асинхронные методы?
* как написать синхронную обертку для асинхронного метода?
* что такое стек вызовов и как это работает?
* в чем отличие стека от кучи?
* `int8_t matrix[2048][2024]`, допустимо ли?
* рекурсивные функции и хвостовая рекурсия, любая ли рекурсия может быть хвостовой?
* что происходит со счетчиком ссылок когда объект добавляется в array, dictionary, set? если нужно другое поведение, что использовать? можно ли узнать, какой объект сколько раз был добавлен в set? (bag)
* как использовать свой класс как ключ?
* в чем плюсы использования immutable? в чем минусы? зачем нужен атрибут copy для property и какую проблему решает?
* почему и как работает KVC? key-path, хаки для коллекций
* зачем нужен NSMapTable, какие отличия от NSHashTable
* проблемы при работе с KVO и как это все работает
* как изменятся свойства, если применить поворот на 45º?
* как передвинуть все subviews на 3 pt вверх и влево?
* отличие view от layer?
* responder принцип работы
* как отправить сообщение по responder chain?
* как работают категории? в какой момент происходит влияние на классы? что будет если категории пересекутся? зачем у категории есть имя?
* зачем нужен NSCache? В чем от реализации кэша на NSDictionary?
* поддерживает ли NSURLConnection протокол HTTP/2?
* какая типизация у objc? Сильная/слабая, явная/не явная, статическая/динамическая?
* в чем отличие QoS User-interactive и user-initiated?
* почему синглтон это плохо?
* bridge casting
* swift optonals, objc new modifiers (`nullable`, etc.). что это и как реализовано?
* dynamic method resolution
* swift 1, 2, 3
* dependency injection
* SOLID
* как сделать миграцию БД
* VIPER, MVVM,...?
* можно ли скачать что-нибудь, пока приложение выполняется в фоне?
* debugging in core data, what is fault object?
* Что такое SOLID?
* Как работает NSNotificationCenter? В каком потоке приходит оповещение?
* Как реализовать хеш-таблицу? Как избежать коллизий?
* Можно ли использовать объект Core Data из одного потока в другом? Можно ли скопировать?
* Что такое Optionals в Swift? Как они реализованы?
* Что такое протокол-ориентированное программирование? Как оно связано со Swift? Чем протоколы Swift отличаются от протоколов Objective-C?
* Чем отличается NSOperationQueue от GCD? Можно ли остановить операцию в GCD или в NSOperationQueue?
* Что происходит, если у объекта вызвать несуществующий метод?
* Что такое реактивное программирование? Как работает RAC?
* Что такое функциональное программирование? Какие фичи есть для этого в Swift / Objective-C?


***

# Задачи
## Задача про банерокрутилку
Из заданного списка вывести поочередно, рандомно, а главное, без повторений, все его элементы.
```java
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
```
Теперь кратко и по сути, что здесь происходит. Пока в списке есть элементы, мы берем случайное число в пространстве длины массива, выводим его, потом последний элемент ставим на место только что выведенного, а индекс длины уменьшаем на единицу, пока не останется ничего.

## Задача на регулярное выражение
В системе авторизации есть следующее ограничение на формат логина: он должен начинаться с латинской буквы, может состоять из латинских букв, цифр, точки и минуса и должен закан-чиваться латинской буквой или цифрой. Минимальная длина логина — 1 символ. Максимальная — 20 символов.
```objectivec
BOOL loginTester(NSString* login) {
    NSError *error = NULL;
    NSRegularExpression *regex = [NSRegularExpression regularExpressionWithPattern:@"\\A[a-zA-Z](([a-zA-Z0-9\\.\\-]{0,18}[a-zA-Z0-9])|[a-zA-Z0-9]){0,1}\\z" options:NSRegularExpressionCaseInsensitive error:&error];
    // Здесь надо бы проверить ошибки, но если регулярное выражение оттестированное и
    // не из пользовательского ввода - можно пренебречь.
    NSRange rangeOfFirstMatch = [regex rangeOfFirstMatchInString:login options:0 range:NSMakeRange(0, [login length])];
    return (BOOL)(rangeOfFirstMatch.location!=NSNotFound);
}
```

## Метод, возвращающий N наиболее часто встречающихся слов во входной строке
```objectivec
- (NSArray *)mostFrequentWordsInString:(NSString *)string count:(NSUInteger)count {
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
        NSNumber *countOfFirstSelectedWord = [countsOfSelectedWords count] ? [countsOfSelectedWords objectAtIndex:0] : nil; // в iOS 7 появился firstObject
        if ([selectedWords count] < count || wordCount >= [countOfFirstSelectedWord unsignedLongValue]) {
            NSNumber *wordCountNSNumber = [NSNumber numberWithUnsignedLong:wordCount];
            NSRange range = NSMakeRange(0, [countsOfSelectedWords count]);
            NSUInteger indexToInsert = [countsOfSelectedWords indexOfObject:wordCountNSNumber inSortedRange:range options:NSBinarySearchingInsertionIndex usingComparator:^(NSNumber *n1, NSNumber *n2) {
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
```
Я бы именно такой подход и использовал, если бы мне нужно было решить эту задачу в реальном iOS приложении, при условии, что я понимаю, откуда будут браться входные данные для поиска и предполагаю, что размеры входной строки не будут больше нескольких мегабайт. Вполне разумное допущение для iOS приложения, на мой взгляд. Иначе на входе не было бы строки, а был бы файл. При реально больших входных данных прийдется попотеть над регулярным выражением для перебора слов, чтоб избавиться от одного промежуточного массива. Такое регулярное выражение очень зависит от языка — то что сработает для русского не проканает для китайского. А вот что делать со словами дальше — кроме прямолинейного алгоритма в голову ничего не приходит. Если бы нужно было выбрать одно наиболее часто встречающееся слово — это Fast Majority Voting. Но вся красота этого алгоритма в том, что он работает для выбора одного значения. Модификаций алгоритма для выбора N значений мне не известны. Самому модифицировать не получилось.

## Используя NSURLConnection, напишите метод для асинхронной загрузки текстового документа по HTTP. Приведите пример его использования
```objectivec
- (void)pullTextFromURLString:(NSString *)urlString completion:(void(^)(NSString *text))callBack {
    NSURLRequest *request = [NSURLRequest requestWithURL: [NSURL URLWithString:urlString] cachePolicy:NSURLRequestUseProtocolCachePolicy timeoutInterval:60.0];
    [NSURLConnection sendAsynchronousRequest:request queue:[NSOperationQueue mainQueue] completionHandler:^(NSURLResponse *response, NSData *data, NSError *error) {
        if (error) {
            NSLog(@"Error %@", error.localizedDescription);
        } else {
            // вообще, не мешало бы определить кодировку, чтоб не было неприятностей
            callBack( [[NSString alloc]initWithData:data encoding:NSUTF8StringEncoding] );
        }
    }];
}
```

## Перечислите все проблемы, которые вы видите в приведенном ниже коде. Предложите, как их исправить
```objectivec
NSOperation *operation = [NSBlockOperation blockOperationWithBlock:^{
    for (int i = 0; i < 1000; ++i) {
        if ([operation isCancelled]) return;
        process(data[i]);
    }
}];
[queue addOperation:operation];
```
Лично я вижу проблему в том, что переменная operation, «захваченная» блоком при создании блока, еще не проинициализирована до конца. Какое реально значение этой переменной будет в момент «захвата», зависит от того, используется ли этот код в методе класса или в простой функции. Вполне возможно, что сгенерированный код будет вполне работоспособен и так, но мне этот код не ясен. Как выйти из ситуации? Так:
```objectivec
NSBlockOperation *operation = [[NSBlockOperation alloc] init];
[operation addExecutionBlock:^{
    for (int i = 0; i < 1000; ++i) {
        if ([operation isCancelled]) return;
        process(data[i]);
    }
}];
[queue addOperation:operation];
```
Возможно, достаточно было бы просто добавить модификатор `__block` в объявление переменной operation. Но так, как в коде выше — наверняка. Некоторые даже создают `__weak` копию переменной operation и внутри блока используют ее. Хорошо подумав я решил, что в данном конкретном случае, когда известно время жизни переменной operation и блока — это излишне. Ну и я бы подумал, стоит ли использовать `NSBlockOperation` для таких сложных конструкций. Разумных доводов привести не могу — вопрос личных предпочтений.
Что еще с этим кодом не так? Я не люблю разных магических констант в коде и вместо 1000 использовал бы `define`, `const`, `sizeof` или что-то в этом роде.
В длинных циклах в objective-c нужно помнить об autoreleased переменных и, если такие пере-менные используются в функции или методе process, а сам этот метод или функция об этом не заботится, нужно завернуть этот вызов в `@autoreleasepool {}`. Создание нового пула при каждой итерации цикла может оказаться накладным или излишним. Если не используется ARC, можно создавать новый NSAutoreleasePool каждые, допустим, 10 итераций цикла. Если исполь-зуется ARC, такой возможности нет. Кстати, это, наверное, единственный довод не использо-вать ARC.
По коду не ясно, меняются ли данные в процессе обработки, обращается ли кто-то еще к этим данным во время обработки из других потоков, какие используются структуры данных, заботится ли сам process о монопольном доступе к данным тогда когда это нужно. Может понадобиться позаботиться о блокировках.

Doh. Dear future googlers: of course operation is nil when copied by the block, but it doesn't have to be copied. It can be qualified with `__block` like so:
```objectivec
//THIS MIGHT LEAK! See the update below.
__block NSBlockOperation *operation = [NSBlockOperation blockOperationWithBlock:^{
   while( ! [operation isCancelled]){
      //do something...
   }
}];
```
_UPDATE:_

Upon further meditation, it occurs to me that this will create a retain cycle under ARC. In ARC, I believe `__block` storage is retained. If so, we're in trouble, because NSBlockOperation also keeps a strong references to the passed in block, which now has a strong reference to the operation, which has a strong reference to the passed in block, which…
It's a little less elegant, but using an explicit weak reference should break the cycle:
```objectivec
NSBlockOperation *operation = [[NSBlockOperation alloc] init];
__weak NSBlockOperation *weakOperation = operation;
[operation addExecutionBlock:^{
   while(![weakOperation isCancelled]){
      //do something...
   }
}];
```

## Напишите запрос, возвращающий названия треков, скачанных более 1000 раз
```sql
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
```
Вот такой запрос справляется с задачей замечательно:
```sql
select name from tracks where id in
    (select track_id from
        (select track_id, count(*) as track_download_count from track_downloads
            group by track_id order by track_download_count desc)
				where track_download_count > 1000)
```
