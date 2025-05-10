- [Data](#data)
  - [Общие понятия](#общие-понятия)
  - [Что такое Core Data? Опишите стек core data](#что-такое-core-data-опишите-стек-core-data)
  - [Целесообразность использования Core Data](#целесообразность-использования-core-data)
  - [Какие есть нюансы при использовании Core Data в разных потоках? Как синхронизировать данные между потоками?](#какие-есть-нюансы-при-использовании-core-data-в-разных-потоках-как-синхронизировать-данные-между-потоками)
  - [Что такое ленивая загрузка? Что ее связывает с Core Data? Опишите ситуация когда она может быть полезной? Что такое faulting?](#что-такое-ленивая-загрузка-что-ее-связывает-с-core-data-опишите-ситуация-когда-она-может-быть-полезной-что-такое-faulting)
  - [Что такое fetch result controller?](#что-такое-fetch-result-controller)
  - [Как сделать миграцию БД?](#как-сделать-миграцию-бд)
  - [Какие плюсы и минусы у Realm? Чем отличается от Core Data?](#какие-плюсы-и-минусы-у-realm-чем-отличается-от-core-data)
  - [Минусы realm](#минусы-realm)
  - [Что такое @AppStorage в SwiftUI?](#appstorage)
  - [Что такое SwiftData в SwiftUI?](#swiftdata)

# Data

<a name="общие-понятия"></a>

## Общие понятия

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

<a name="core-data"></a>

## Что такое Core Data? Опишите стек core data

Apple предоставляет гибкий фреймворк для работы с хранимыми на устройстве данными — Core Data. Большинство деталей по работе с хранилищем данных Core Data скрывает, позволяя вам сконцентрироваться на том, что действительно делает ваше приложение веселым, уникальным и удобным в использовании. Не смотря на то, что Core Data может хранить данные в реляционной базе данных вроде SQLite, Core Data не является СУБД (системой управления БД). По-правде, Core Data в качестве хранилища может вообще не использовать реляционные базы данных. Core Data скорее является оболочкой для работы с данными, которая позволяет работать с сущностями и их связями (отношениями к другим объектами), атрибутами, в том виде, который напоминает работы с объектным графом в обычном объектно-ориентированном программировании.

A Core Data stack is composed of the following objects: one or more managed object contexts connected to a single persistent store coordinator which is in turn connected to one or more persistent stores. A stack contains all the Core Data components you need to fetch, create, and manipulate managed objects. Minimally it contains:

1. An external persistent store that contains saved records.
2. A persistent object store that maps between records in the store and objects in your application.
3. A persistent store coordinator that aggregates all the stores.
4. A managed object model that describes the entities in the stores.
5. A managed object context that provides a scratch pad for managed objects.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/core_data_stack.jpg">

1. Persistent store

A persistent store is a repository in which managed objects may be stored. You can think of a persistent store as a database data file where individual records each hold the last-saved values of a managed object. Core Data offers three native file types for a persistent store: binary, XML, and SQLite. You can implement your own store type if you want Core Data to interoperate with a custom file format or server. Core Data also provides an in-memory store that lasts no longer than the lifetime of a process. The entities in a store are defined by the managed object model used to create it.

2. Persistent object store

A persistent object store maps between objects in your application and records in a persistent store. There are different classes of persistent object store for the different file types that Core Data supports. You can also implement your own if you want to support a custom file type. You don’t create a persistent object store directly. Instead, Core Data creates a store of the appropriate type for you when you send an `addPersistentStoreWithType:configuration:URL:options:error:` message to a persistent store coordinator.

3. Persistent store coordinator

A persistent store coordinator associates persistent object stores and a managed object model, and presents a facade to managed object contexts such that a group of persistent stores appears as a single aggregate store. A persistent store coordinator is an instance of `NSPersistentStoreCoordinator`. It has a reference to a managed object model that describes the entities in the store or stores it manages. The coordinator is the central object in a Core Data stack. In many applications you just have a single store, but in complex applications there may be several, each potentially containing different entities. The persistent store coordinator’s role is __to manage these stores and present to its managed object contexts the facade of a single unified store__. When you fetch records, Core Data retrieves results from all of them, unless you specify which store you’re interested in.

4. Managed object model

A managed object model is a set of objects that together form a blueprint describing the managed objects you use in your application. A model allows Core Data to map from records in a persistent store to managed objects that you use in your application. It is a collection of entity description objects (instances of `NSEntityDescription`). An entity description describes an entity (which you can think of as a table in a database) in terms of its name, the name of the class used to represent the entity in your application, and what properties (attributes and relationships) it has. During the creation of the Core Data stack, the `NSManagedObjectModel` (often referred to as the “mom”) is loaded into memory as the first step in the creation of the stack. Once the `NSManagedObjectModel` object is initialized, the `NSPersistentStoreCoordinator` object is constructed.

5. Managed object context

A managed object context represents a single object space, or scratch pad, in a Core Data application. A managed object context is an instance of `NSManagedObjectContext`. Its primary responsibility is to manage a collection of managed objects. These managed objects represent an internally consistent view of one or more persistent stores. The context is a powerful object with a central role in the life-cycle of managed objects, with responsibilities from life-cycle management (including faulting) to validation, inverse relationship handling, and undo/redo. From your perspective, the context is the central object in the Core Data stack. It’s the object you use to create and fetch managed objects, and to manage undo and redo operations. Within a given context, there is at most one managed object to represent any given record in a persistent store. __When you fetch objects, the context asks its parent object store to return those objects that match the fetch request__. Changes that you make to managed objects are not committed to the parent store until you save the context.

<a name="целесообразность-использования-core-data"></a>

## Целесообразность использования Core Data

Core Data уменьшает количество кода, написанного для поддержки модели слоя приложения, как правило, на 50% - 70%, измеряемое в строках кода. Core Data имеет зрелый код, качество которого обеспечивается путем юнит-тестов, и используется ежедневно миллионами клиентов в широком спектре приложений. Структура была оптимизирована в течение нескольких версий. Она использует информацию, содержащуюся в модели и выполненяет функции, как правило, не работающие на уровне приложений в коде. Кроме того, в дополнение к отличной безопасности и обработке ошибок, она предлагает лучшую масштабируемость при работе с памятью, относительно любого конкурирующего решения. Другими словами: вы могли бы потратить долгое время тщательно обрабатывая Ваши собственные решения оптимизации для конкретной предметной области, вместо того, чтобы получить преимущество в производительности, которую Core Data предоставляет бесплатно для любого приложения.

__Когда нецелесообразно использовать Core Data:__
- если планируется использовать очень небольшой объем данных. В этом случае проще воспользоваться для хранения Ваших данных объектами коллекций - массивами или словарями и сохранять их в .plist файлы.
- если используется кросс-платформерная архитектура или требуется доступ к строго определенному формату файла с данными (хранилищу), например SQLite.
- использование баз данных клиент-сервер, например MySQL или PostgreSQL.

__SQLite__
- Максимальный объем хранимых данных базы SQLite составляет 2 терабайта.
- Чтение из базы данных может производиться одним и более потоками, например несколько процессов могут одновременно выполнять `SELECT`. Однако запись в базу данных может осуществляться, только, если база в данный момент не занята другим процессом.
- SQLite не накладывает ограничения на типы данных. Любые данные могут быть занесены в любой столбец. Ограничения по типам данных действуют только на `INTEGER PRIMARY KEY`, который может содержать только 64-битное знаковое целое.

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

<a name="core-data-в-разных-потоках"></a>

## Какие есть нюансы при использовании Core Data в разных потоках? Как синхронизировать данные между потоками?

In Core Data, the managed object context can be used with two concurrency patterns, defined by `NSMainQueueConcurrencyType` and `NSPrivateQueueConcurrencyType`.

- `NSMainQueueConcurrencyType` is specifically for use with your application interface and can only be used on the main queue of an application.

- The `NSPrivateQueueConcurrencyType` configuration creates its own queue upon initialization and can be used only on that queue. Because the queue is private and internal to the `NSManagedObjectContext` instance, it can only be accessed through the `performBlock:` and the `performBlockAndWait:` methods.

`NSManagedObject` instances are not intended to be passed between queues. Doing so can result in corruption of the data and termination of the application. When it is necessary to hand off a managed object reference from one queue to another, it must be done through `NSManagedObjectID` instances. You retrieve the managed object ID of a managed object by calling the `objectID` method on the `NSManagedObject` instance.

<a name="ленивая-загрузка-core-data"></a>

## Что такое ленивая загрузка? Что ее связывает с Core Data? Опишите ситуация когда она может быть полезной? Что такое faulting?

Для загрузки данных из БД в память приложения удобно пользоваться загрузкой не только данных об объекте, но и о сопряжённых с ним объектах. Это делает загрузку данных проще для разработчика: он просто использует объект, который, тем не менее вынужден загружать все данные в явном виде. Но это ведёт к случаям, когда будет загружаться огромное количество сопряжённых объектов, что плохо скажется на производительности в случаях, когда эти данные реально не нужны. Паттерн Lazy Loading (Ленивая Загрузка) подразумевает отказ от загрузки дополнительных данных, когда в этом нет необходимости. Вместо этого ставится маркер о том, что данные не загружены и их надо загрузить в случае, если они понадобятся. Как известно, если Вы ленивы, то вы выигрываете в том случае, если дело, которое вы не делали на самом деле и не надо было делать.
Faulting isn't unique to Core Data. A similar technique is used in many other frameworks, such as Ember and Ruby on Rails. Faulting is a mechanism Core Data employs to reduce your application’s memory usage, only load data when it's needed. A fault is a placeholder object that represents a managed object that has not yet been fully realized, or a collection object that represents a relationship. To make faulting work, Core Data does a bit of magic under the hood by creating custom subclasses at compile time that represent the faults.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/core_data_faulting.png">

<a name="fetch-result-controller"></a>

## Что такое fetch result controller?

Данные сами по себе может быть и представляют какую-либо ценность, но, обычно их нужно использовать. Одним из элементов представления данных в iOS служат таблицы (объекты класса `UITableView`), которые через объект класса `NSFetchedResultsController` можно привязать к CoreData. После этого при изменении данных в CoreData будет актуализироваться информация в таблице. Так же, с помощью таблицы можно управлять данными в хранилище.
`NSFetchedResultsController` — контроллер результатов выборки. Создается, обычно один экземпляр на `ViewController`, но вполне может работать и без оного, внутрь которого помещается исключительно для того, что бы было проще привязать данные к виду.

<a name="db-migration"></a>

## Как сделать миграцию БД?

You can only open a Core Data store using the managed object model used to create it. Changing a model will therefore make it incompatible with (and so unable to open) the stores it previously created. If you change your model, you therefore need to change the data in existing stores to new version—changing the store format is known as migration. To migrate a store, you need both the version of the model used to create it, and the current version of the model you want to migrate to. You can create a versioned model that contains more than one version of a managed object model. Within the versioned model you mark one version as being the current version. Core Data can then use this model to open persistent stores created using any of the model versions, and migrate the stores to the current version. To help Core Data perform the migration, though, you may have to provide information about how to map from one version of the model to another. This information may be in the form of hints within the versioned model itself, or in a separate mapping model file that you create.

The migration process itself is in three stages. It uses a copy of the source and destination models in which the validation rules are disabled and the class of all entities is changed to `NSManagedObject`.

To perform the migration, Core Data sets up two stacks, one for the source store and one for the destination store. Core Data then processes each entity mapping in the mapping model in turn. It fetches objects of the current entity into the source stack, creates the corresponding objects in the destination stack, then recreates relationships between destination objects in a second stage, before finally applying validation constraints in the final stage.

Before a cycle starts, the entity migration policy responsible for the current entity is sent a `beginEntityMapping:manager:error:` message. You can override this method to perform any initialization the policy requires. The process then proceeds as follows:

1. Create destination instances based on source instances.

At the beginning of this phase, the entity migration policy is sent a `createDestinationInstancesForSourceInstance:entityMapping:manager:error:` message; at the end it is sent a `endInstanceCreationForEntityMapping:manager:error:` message. In this stage, only attributes (not relationships) are set in the destination objects. Instances of the source entity are fetched. For each instance, appropriate instances of the destination entity are created (typically there is only one) and their attributes populated (for trivial cases, `name = $source.name`). A record is kept of the instances per entity mapping since this may be useful in the second stage.

2. Recreate relationships.

At the beginning of this phase, the entity migration policy is sent a `createRelationshipsForDestinationInstance:entityMapping:manager:error:` message; at the end it is sent a `endRelationshipCreationForEntityMapping:manager:error:` message. For each entity mapping (in order), for each destination instance created in the first step any relationships are recreated.

3. Validate and save.

In this phase, the entity migration policy is sent a `performCustomValidationForEntityMapping:manager:error:` message. Validation rules in the destination model are applied to ensure data integrity and consistency, and then the store is saved.

At the end of the cycle, the entity migration policy is sent an endEntityMapping:manager:error: message. You can override this method to perform any clean-up the policy needs to do. Note that Core Data cannot simply fetch objects into the source stack and insert them into the destination stack, the objects must be re-created in the new stack. Core Data maintains “association tables” which tell it which object in the destination store is the migrated version of which object in the source store, and vice-versa. Moreover, because it doesn't have a means to flush the contexts it is working with, you may accumulate many objects in the migration manager as the migration progresses. If this presents a significant memory overhead and hence gives rise to performance problems, you can customize the process as described in Multiple Passes—Dealing With Large Datasets.

__Lightweight Migration__

If you just make simple changes to your model (such as adding a new attribute to an entity), Core Data can perform automatic data migration, referred to as lightweight migration. Lightweight migration is fundamentally the same as ordinary migration, except that instead of you providing a mapping model (as described in Mapping Overview), Core Data infers one from differences between the source and destination managed object models.

Lightweight migration is especially convenient during early stages of application development, when you may be changing your managed object model frequently, but you don’t want to have to keep regenerating test data. You can migrate existing data without having to create a custom mapping model for every model version used to create a store that would need to be migrated.

A further advantage of using lightweight migration—beyond the fact that you don’t need to create the mapping model yourself—is that if you use an inferred model and you use the SQLite store, then Core Data can perform the migration in situ (solely by issuing SQL statements). This can represent a significant performance benefit as Core Data doesn’t have to load any of your data. Because of this, you are encouraged to use inferred migration where possible, even if the mapping model you might create yourself would be trivial.

<a name="realm-vs-coredata"></a>

## Какие плюсы и минусы у Realm? Чем отличается от Core Data?

Realm - это no-sql база данных для Android (Java, Kotlin), iOS (Objective-C, Swift), Xamarin (C#) и JavaScript (React Native, Node.js). Так же есть backend, который позволяет синхронизировать данные из всех источников. Из ключевых особенностей стоит отметить zero copy, MVCC и ACID. Встроенного механизма устаревания и очистки данных нет.

There currently isn't a clear winner. Much depends on the needs of your project. Realm is still young, but it evolves at an astounding pace. If your project requires encryption or speed, then Realm is an obvious choice. If your project has a complex data model that changes frequently, then Core Data might be a better choice.

__Set Up__

CoreData: `NSPersistentContainer` simplifies the creation and management of the Core Data stack by handling the creation of the managed object model (`NSManagedObjectModel`), persistent store coordinator (`NSPersistentStoreCoordinator`), and the managed object context (`NSManagedObjectContext`).
Realm: No set up needed

__Threads__

An important advantage Realm has over Core Data is consistency across threads. An important downside of Core Data is that managed object contexts can get out of sync. This isn't true for Realm and that is a key advantage it has over Core Data.

__Syntax__

The recent introduction of the `NSFetchedResultsType` protocol makes working with Core Data elegant and concise. Creating a managed object for an entity no longer requires multiple lines of code.

```swift
let note = Note(context: managedObjectContext)
```

__Migrations__

Realm is still very young while Core Data has been around for more than a decade. The result is that Core Data has a few bells and whistles Realm lacks. Xcode's data model editor, for example, is a feature that is often overlooked. For complex applications, it is an incredibly useful tool to have. Another powerful feature of Core Data is data model versioning and the framework's support for migrations. Versioning the data model is easy and lightweight migrations are handled by the framework. Even though Realm also supports migrations, the developer needs to do the heavy lifting. I am sure this will improve over time.

__Speed__

Core Data is incredibly fast if you consider what it does under the hood to do its magic. But Realm is faster, much faster.

__Cross-Platform Support__

Realm is available on multiple platforms and this can be a compelling reason for choosing Realm over Core Data. I agree that it is nice to use the same persistence solution on multiple platforms. But keep in mind that you still need to write an implementation for each platform. You cannot share code between platforms, unless you use Xamarin, which is another discussion. Another compelling feature is the recently announced Realm Mobile Platform. Not only does it look amazing, it offers a valid alternative to, for example, iCloud and Firebase.

__Evolution__

Realm is a third party solution while Core Data isn't. This has pros and cons. Realm can evolve at a rapid pace. Developers can take advantage of new features by upgrading the version of Realm they ship with their application. This isn't true for Core Data. As a developer, you can't decide which version of the framework your application uses. This means that adopting new features of the framework isn't trivial. Apple is in charge.

__App volume__

Realm takes ~13MB of app

## Минусы realm

- Хранит только сырые данные. Enum надо перекладывать в String или Int, Optional в RealmOptional, массивы в List, обратные ссылки в LinkedList. Чтобы превращать это в нормальные объекты надо писать какие-то конвертеры.
- По всему коду размазано обращение к Realm: он импортируется в файл, передается в качестве параметра, из базы тянутся объекты. Мы активно заворачивали всё в репозитории, чтобы скрыть работу с базой, а интерфейсом выходил доменный объект. Но это дополнительный код и слой в архитектуру.
- Работа с базой превратилась в целый слой, который надо поддерживать: писать маперы, обертки. Добавить новую сущность — это слишком много ручной работы: создать Entity, переложить из DTO в нее, потом из Entity в доменную модель. Это всё ещё и протестировать надо, а мы даже на UI выводить ничего не начали.
- Realm-объект должен быть классом. Все его свойства надо пометить как динамичные, при этом нельзя их сделать немутабельными, а конструктор Entity не имеет смысла, он всегда пустой. В итоге легко добавить свойство, но забыть поставить его из всех нужных мест.
- Realm — большая и очень тяжелая зависимость

<a name="appstorage"></a>

## Что такое @AppStorage в SwiftUI?

`@AppStorage` — это property wrapper в SwiftUI, который позволяет привязывать переменную напрямую к UserDefaults. Это даёт удобный способ хранить и синхронизировать простые значения (строки, числа, булевы и т. д.) между интерфейсом и хранилищем данных.

Зачем нужен @AppStorage?

Обычно, чтобы сохранить данные между запусками приложения, используется UserDefaults. @AppStorage упрощает эту работу и автоматически обновляет представление SwiftUI при изменении значения.

```swift
struct SettingsView: View {
    @AppStorage("isDarkMode") private var isDarkMode = false

    var body: some View {
        Toggle("Темная тема", isOn: $isDarkMode)
    }
}
```

Если пользователь изменит значение переключателя, оно сохранится в UserDefaults под ключом "isDarkMode" и будет применяться при следующем запуске.

```swift
struct ProfileView: View {
    @AppStorage("username") private var username = ""

    var body: some View {
        VStack {
            TextField("Введите имя", text: $username)
            Text("Привет, \(username)")
        }
        .padding()
    }
}
```
Имя пользователя сохраняется автоматически и отображается даже после перезапуска приложения.
___
Особенности и ограничения

•	Работает только с типами, совместимыми с UserDefaults (String, Int, Double, Bool, Data, URL и RawRepresentable).

•	Значения сохраняются немедленно, но если вы используете один и тот же ключ в нескольких местах, изменения будут мгновенно синхронизироваться.

•	Использовать @AppStorage стоит для простых пользовательских настроек. Для сложных данных лучше применять @StateObject, @ObservedObject и собственные модели хранения.

@AppStorage — это простой и эффективный способ реализовать сохранение настроек пользователя без лишнего кода. Он идеально подходит для параметров вроде темы, имени, языка, или статуса авторизации.

<a name="swiftdata"></a>

## Что такое SwiftData в SwiftUI?

SwiftData — это нативный фреймворк Apple, представленный в iOS 17, macOS 14 и других новых системах. Он позволяет создавать, сохранять и управлять локальными моделями данных с помощью простых декларативных моделей на основе @Model, интегрированных в SwiftUI.

Это замена или альтернатива Core Data, но в более «свифтовом» стиле: меньше шаблонного кода, больше декларативности и удобной работы с UI.

Как это устроено внутри:

•	SwiftData использует Core Data как хранилище — то есть под капотом по-прежнему работают NSPersistentContainer, NSManagedObjectContext, NSFetchRequest и прочие компоненты.

•	Но вам не нужно взаимодействовать с этими API напрямую — SwiftData предоставляет декларативный синтаксис, более привычный разработчикам SwiftUI.

•	Вместо создания .xcdatamodeld используется аннотация @Model, которая генерирует модель Core Data во время компиляции.

•	SwiftData автоматически создаёт представление схемы, управляет миграциями, запросами и связями.

```swift
import SwiftData

@Model
class Note {
    var title: String
    var content: String
    var date: Date

    init(title: String, content: String, date: Date = .now) {
        self.title = title
        self.content = content
        self.date = date
    }
}
```
Аннотация @Model делает класс Note автоматически совместимым с хранилищем данных.

```swift
struct NotesView: View {
    @Query var notes: [Note]
    @Environment(\.modelContext) private var context

    var body: some View {
        List {
            ForEach(notes) { note in
                Text(note.title)
            }
        }
        .toolbar {
            Button("Добавить") {
                let newNote = Note(title: "Новая заметка", content: "Текст")
                context.insert(newNote)
            }
        }
    }
}
````

•	@Query автоматически извлекает все объекты Note.

•	context.insert() сохраняет новую заметку.

Удаление объекта

.context.delete(note)

Удаление тоже выполняется через modelContext.

__Особенности__

•	Похож на Core Data, но декларативный

•	Глубокая интеграция с SwiftUI (@Query, @Model, @Environment(\.modelContext))

•	Нет нужды в описании схем или создании .xcdatamodeld

•	Работает с iOS 17+ и macOS 14+

__Когда использовать SwiftData?__

•	Когда нужно хранение локальных данных (заметки, задачи, избранное)

•	Когда нужен автоматический доступ к данным в SwiftUI

•	Когда Core Data кажется сложным или избыточным

SwiftData — это простой, декларативный способ работы с локальной базой данных в SwiftUI-приложениях. Он объединяет удобство SwiftUI и мощь Core Data, но без всей лишней сложности.
