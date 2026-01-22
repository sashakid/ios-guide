- [Что произойдет если сначала нажать на кнопку 1 а потом на кнопку 2?](#что-произойдет-если-сначала-нажать-на-кнопку-1-а-потом-на-кнопку-2)
- [Что произойдет при исполнении следующего кода?](#что-произойдет-при-исполнении-следующего-кода)
- [Реализуйте следующие методы: retain, release, autorelease](#реализуйте-следующие-методы-retain-release-autorelease)
- [Выведется ли в дебагер Hello world? Почему?](#выведется-ли-в-дебагер-hello-world-почему)
- [Что выведется в консоль?](#что-выведется-в-консоль)
- [Перечислите все проблемы, которые вы видите в приведенном ниже коде. Предложите, как их исправить](#перечислите-все-проблемы-которые-вы-видите-в-приведенном-ниже-коде-предложите-как-их-исправить)
- [Заполнить строку буквами А, чтобы не делать миллионы итераций](#заполнить-строку-буквами-а-чтобы-не-делать-миллионы-итераций)
- [Написать процедуру, инвертирующую массив символов](#написать-процедуру-инвертирующую-массив-символов)
- [Что не так с этим кодом?](#что-не-так-с-этим-кодом)
- [Какой метод вызовется: класса A или класса B?](#какой-метод-вызовется-класса-a-или-класса-b)
- [`int8_t matrix [2048][2024]`, допустимо ли?](#int8_t-matrix-20482024-допустимо-ли)
- [Одинаковую ли память занимают эти структуры и почему так?](#одинаковую-ли-память-занимают-эти-структуры-и-почему-так)
- [Будет ли вызван deinit у A после выхода из test()?](#retain-in-class)
- [Будет ли вызван deinit у ViewModel после выхода из test()? Что не так? Как исправить?](#retain-in-vm)
- [Задача на посещение веб-страниц](#web)
- [Предсказать порядок вывода](#порядок)
- [Задача на QOS](#qos)
- [Задача на диспетчеризацию](#dispatch)
- [Что делать, если при скролле тормозит таблица](#что-делать-если-при-скролле-тормозит-таблица)
- [Debugging в XCode и Instruments](#debugging-в-xcode-и-instruments)

<a name="string-autorelease"></a>

## Что произойдет если сначала нажать на кнопку 1 а потом на кнопку 2?

```objectivec
- (IBAction)btn1DidTouch:(id)sender {
 _string = [[[NSString alloc] initWithFormat:@"v=%i", rand()] autorelease];
}
- (IBAction)btn2DidTouch:(id)sender {
 NSLog(@"_string is equal to ‘%@’", _string);
}
```

Крэш, т.к utoreleasepool создается в начале обработки события и уничтожается в конце. т.е. нажали на первую кнопку — началась обработка события, нажали на вторую — кнопку — закончилась обработка первого события, очистился autoreleasepool а вместе с ним и объект удалился, а ссылка осталась. Затем началась обработка второго события и мы обращаемся к задеалоченному объекту, результат — крэш.

<a name="что-произойдет"></a>

## Что произойдет при исполнении следующего кода?

```objectivec
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];
```

Впоследствии это вызовет крэш. Потому что объект дважды добавляется в пул автоосвобождения, и `release` вызовется дважды.

<a name="retain-release-autorelease"></a>

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

<a name="hello-world"></a>

## Выведется ли в дебагер Hello world? Почему?

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

## Что выведется в консоль?

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

<a name="проблемы-в-коде"></a>

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
  В длинных циклах в objective-c нужно помнить об autoreleased переменных и, если такие переменные используются в функции или методе process, а сам этот метод или функция об этом не заботится, нужно завернуть этот вызов в `@autoreleasepool {}`. Создание нового пула при каждой итерации цикла может оказаться накладным или излишним. Если не используется ARC, можно создавать новый NSAutoreleasePool каждые, допустим, 10 итераций цикла. Если используется ARC, такой возможности нет. Кстати, это, наверное, единственный довод не использовать ARC.
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

<a name="заполнить-строку-буквами-a"></a>

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

<a name="инвертировать-массив-символов"></a>

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

<a name="что-не-так-с-этим-кодом"></a>

## Что не так с этим кодом?

```objectivec
[[[SomeClass alloc] init] init];
```

Пример: есть класс `A`, который имеет поле `NSString *b` и в ините ты делаешь `_b = @"somestring";` Стринг `b` не хранится в памяти выделенной под `A` – в этой памяти хранится лишь ссылка на `b`, а сам объект создается вовне. При повторном ините стринг просто пересоздастся, не стерев старый, и мы получаем утекший стринг. Вообще, такая ситуация есть далеко не везде, и далеко не всегда вызовет проблемы. Но кастомные повторные инициализации реально могут вызывать утечки памяти — зависит от конкретного типа объекта. Двойной инит может вызвать утечку. А может не вызвать. Каждый конкретный класс - отдельный вопрос.

<a name="какой-метод-вызовется"></a>

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

<a name="int8_t-matrix"></a>

## `int8_t matrix [2048][2024]`, допустимо ли?

2048 * 2024 = 4145152 байт, так как int8_t = 1 байт. Значит для хранения массива нужно 4.15 мегабайт памяти в стеке. На iOS размер стека ограничен 1 мегабайтом, следовательно, такая запись недопустима.

<a name="memory-for-structs"></a>

## Одинаковую ли память занимают эти структуры и почему так?

```c
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

```
sizeof(StructA) == 8
sizeof(StructB) == 12
```

Выравнивание необходимо для оптимизации доступа к данным в памяти. Процессоры часто требуют, чтобы данные (например, целочисленные типы) находились в памяти по адресам, которые кратны их размеру. Это позволяет ускорить доступ к этим данным и избегать ошибок при их чтении или записи.

```c
struct StructA {
  int32_t a;  // 4 байта
  char b;     // 1 байт
  char c;     // 1 байт
};

struct StructB {
  char b;     // 1 байт
  int32_t a;  // 4 байта
  char c;     // 1 байт
};
```
- sizeof(StructA) == 8, так как после поля a (4 байта) компилятор вставляет 2 байта паддинга, чтобы выровнять поля структуры по 4 байта.
- sizeof(StructB) == 12, так как после поля b (1 байт) вставляется 3 байта паддинга для выравнивания поля a (4 байта). Далее стоит c (1 байт), и еще 2 байта паддинга.

Таким образом, структуры занимают разное количество памяти из-за порядка расположения полей и выравнивания данных.

Зачем нужно выравнивание?

Выравнивание необходимо для оптимизации работы процессора, поскольку он может быстрее обращаться к данным, если они находятся по адресам, кратным их размеру.

<a name="retain-in-class"></a>

## Будет ли вызван deinit у A после выхода из test()?

```swift
class A {
    var closure: (() -> Void)?
    deinit { print("A deinit") }
}

func test() {
    let a = A()
    a.closure = {
        print("Inside closure")
    }
}
```

Нет, deinit не будет вызван, потому что возникает retain cycle:

•	a содержит closure (сильная ссылка на блок)

•	блок захватывает a (неявно, через self), а замыкания по умолчанию захватывают переменные сильно

```swift
/// Правильное решение:
func test() {
    let a = A()
    a.closure = { [weak a] in
        print("Inside closure")
        // Если нужно, можно: a?.doSomething()
    }
}
```

<a name="retain-in-vm"></a>

## Будет ли вызван deinit у ViewModel после выхода из test()? Что не так? Как исправить?

```swift
class ViewModel {
    var onUpdate: (() -> Void)?

    func fetchData() {
        DispatchQueue.global().async {
            sleep(1)
            self.onUpdate?()
        }
    }

    deinit {
        print("ViewModel deinit")
    }
}

func test() {
    let vm = ViewModel()
    vm.onUpdate = {
        print("UI updated")
    }
    vm.fetchData()
}
```

Нет, deinit НЕ будет вызван после test() — снова из-за retain cycle, но на этот раз он завуалирован:

1.	ViewModel → onUpdate → closure → self (ViewModel)

2.	closure держит self, self держит closure — цикл.

3.	closure будет вызван асинхронно, через DispatchQueue, а значит, объект vm останется в памяти до этого момента.

И даже если бы ты вручную занулял vm.onUpdate, это было бы поздно, потому что self уже была захвачена замыканием.

___

А теперь представь, что ViewModel не просто хранит замыкание, а использует его в Combine: Когда будет вызван deinit у ViewModel, и как избежать утечки?

```swift
class ViewModel {
    var cancellable: AnyCancellable?

    func bind() {
        cancellable = Timer.publish(every: 1, on: .main, in: .common)
            .autoconnect()
            .sink { _ in
                self.doSomething()
            }
    }

    func doSomething() {
        print("tick")
    }

    deinit {
        print("ViewModel deinit")
    }
}
```

self захватывается в sink, а sink живёт в cancellable, который хранится в self. Получаем цикл.

Решение — [weak self] внутри .sink { [weak self] _ in ... }

<a name="web"></a>

## Задача на посещение веб-страниц

Определите пользователей, которые за день посетили ровно две уникальные страницы (неважно, сколько раз они заходили на каждую из них, но важны только два разных PageId).

1.	У нас есть логи с полями:

•	Timestamp (дата и время посещения)

•	PageId (идентификатор страницы)

•	CustomerId (идентификатор пользователя)

2.	Нужно сгруппировать данные по пользователям (CustomerId) и дню (Timestamp).
3.	Проверить, что у каждого пользователя ровно 2 уникальных PageId за день.

```swift
import Foundation

// Структура для хранения записей логов
struct LogEntry {
    let timestamp: Date
    let pageId: Int
    let customerId: Int
}

// Примерные входные данные
let logs: [LogEntry] = [
    LogEntry(timestamp: Date(), pageId: 1, customerId: 100),
    LogEntry(timestamp: Date(), pageId: 2, customerId: 100),
    LogEntry(timestamp: Date(), pageId: 1, customerId: 100), // Повтор страницы 1
    LogEntry(timestamp: Date(), pageId: 3, customerId: 101),
    LogEntry(timestamp: Date(), pageId: 4, customerId: 101),
    LogEntry(timestamp: Date(), pageId: 5, customerId: 102)
]

// Функция для группировки логов по пользователям и дням
func findUsersWithExactlyTwoUniquePages(logs: [LogEntry]) -> Set<Int> {
    var userPages: [Int: [Date: Set<Int>]] = [:] // Словарь: CustomerId -> [Date -> Set<PageId>]

    let calendar = Calendar.current

    for log in logs {
        let day = calendar.startOfDay(for: log.timestamp) // Упрощаем до даты без времени

        // Если пользователь еще не существует в словаре, создаем запись
        if userPages[log.customerId] == nil {
            userPages[log.customerId] = [:]
        }
        
        // Если день еще не существует для этого пользователя, создаем Set для страниц
        if userPages[log.customerId]?[day] == nil {
            userPages[log.customerId]?[day] = Set()
        }

        // Добавляем страницу в Set
        userPages[log.customerId]?[day]?.insert(log.pageId)
    }

    // Фильтруем пользователей с ровно двумя уникальными страницами
    var result = Set<Int>()
    for (customerId, days) in userPages {
        for (_, pages) in days {
            if pages.count == 2 {
                result.insert(customerId)
            }
        }
    }
    
    return result
}

// Запускаем функцию
let users = findUsersWithExactlyTwoUniquePages(logs: logs)
print("Пользователи, посетившие ровно две уникальные страницы: \(users)")
```

•	Время работы: O(N), где N — это количество записей в логах.

•	Это решение сохраняет высокую производительность и эффективно обрабатывает большие объемы данных.

<a name="порядок"></a>

## Предсказать порядок вывода

```swift
import Foundation

let queue1 = DispatchQueue(label: "queue1", attributes: .concurrent)
let queue2 = DispatchQueue(label: "queue2")
let queue3 = DispatchQueue(label: "queue3")
let mainQueue = DispatchQueue.main

print("Start")
queue1.async {
    print("1")
    queue2.sync {
        print("2")
        queue3.async {
            print("3")
            mainQueue.sync {
                print("4")
            }
            print("5")
        }
        print("6")
    }
    print("7")
}
print("End")
```

```
Start
End
1
2
6
7
3
4
5
```

<a name="qos"></a>

## Задача на QOS

```swift
func log(_ message: String) {
    print("\(message) — \(Thread.isMainThread ? "🟢 main" : "🔵 background")")
}

print("🚀 Start")

let queueA = DispatchQueue.global(qos: .background)
let queueB = DispatchQueue.global(qos: .userInitiated)
let queueC = DispatchQueue.global(qos: .utility)
let queueD = DispatchQueue.global(qos: .userInteractive)

queueA.async {
    log("A1 (background)")            // 1

    queueB.async {
        log("B1 (userInitiated)")      // 2

        queueC.async {
            log("C1 (utility)")        // 3

            queueD.async {
                log("D1 (userInteractive)")  // 4
            }

            log("C2 (utility)")        // 5
        }

        log("B2 (userInitiated)")      // 6
    }

    log("A2 (background)")            // 7
}

print("🚀 End")

RunLoop.main.run(until: Date().addingTimeInterval(3))
```

```
🚀 Start
🚀 End
A1 (background)
A2 (background)
B1 (userInitiated)
B2 (userInitiated)
C1 (utility)
C2 (utility)
D1 (userInteractive)
```
Но возможны перестановки между задачами, особенно C1/C2 и D1, в зависимости от загрузки системы. Однако D1 с userInteractive QoS будет выполнен быстрее, даже если был вложен в utility.

•	queueA.async → запускается первой (низкий приоритет), но она и вложенные не блокируют.

•	queueB.async (внутри A) имеет более высокий приоритет, выполняется быстрее.

•	Даже вложенные задачи могут стартовать раньше внешних, если у них выше QoS.

•	Все вложенные async блоки — независимы, они планируются системой по своим приоритетам.

<a name="dispatch"></a>

## Задача на диспетчеризацию

```swift
// MARK: - Протокол с requirement
protocol Speaker {
    func speak() // Это requirement — будет участвовать в PWT
}

// MARK: - Extension к протоколу Speaker
extension Speaker {
    func shout() {
        print("Speaker shouts (extension, не requirement, поэтому не попадает в PWT)")
    }
}

// MARK: - Пустой протокол без requirements
protocol Listener {} // Нет ни одного метода в протоколе

// MARK: - Extension к пустому протоколу Listener
extension Listener {
    func listen() {
        print("Listener listens (extension-only method, не доступен через Listener)")
    }
}

// MARK: - Базовый класс с виртуальными методами
class Animal {
    func speak() {
        print("Animal speaks") // виртуальный метод, попадает в vtable
    }

    func eat() {
        print("Animal eats") // виртуальный метод, может быть переопределён
    }
}

// MARK: - Extension к Animal
extension Animal {
    func sleep() {
        print("Animal sleeps (extension method, не попадает в vtable)")
    }
}

// MARK: - Подкласс с override методов
class Dog: Animal {
    override func speak() {
        print("Dog barks (override — dynamic dispatch через vtable)")
    }

    override func eat() {
        print("Dog eats (override — dynamic dispatch через vtable)")
    }

    func run() {
        print("Dog runs (новый метод, static dispatch)")
    }
}

// MARK: - Подкласс с hiding (метод с тем же именем, но не override)
class DogHiding: Animal {
    func speak() {
        print("DogHiding barks (method hiding — это НЕ override, будет static dispatch)")
    }
}

// MARK: - Класс, реализующий протокол Speaker
class Parrot: Speaker {
    func speak() {
        print("Parrot talks (реализация requirement — участвует в PWT)")
    }
}

// MARK: - Структура, реализующая пустой протокол Listener
struct MyListener: Listener {} // Не реализует listen() явно

// MARK: - Использование

// ==== Dynamic dispatch через vtable ====
let dog = Dog()
dog.speak()    // вызов переопределенного метода → dynamic dispatch (vtable)
dog.eat()      // тоже override → dynamic dispatch (vtable)
dog.sleep()    // метод из extension → static dispatch (не в vtable)
dog.run()      // обычный метод → static dispatch

// ==== Animal-ссылка на Dog ====
let animal: Animal = Dog()
animal.speak() // вызов переопределенного метода → dynamic dispatch (vtable)
animal.eat()   // dynamic dispatch
animal.sleep() // extension method → static dispatch (компилятор подставит напрямую)

// ==== Hiding — НЕ переопределение ====
let hiding = DogHiding()
hiding.speak() // static dispatch — метод вызывается напрямую

let animal2: Animal = DogHiding()
animal2.speak() // вызов родительского метода, НЕ переопределён → dynamic dispatch, но вызовется Animal.speak()

// ==== Protocol witness table ====
let parrot = Parrot()
parrot.speak() // direct call — тип известен компилятору, без PWT

let speaker: Speaker = parrot
speaker.speak() // dynamic dispatch через PWT
speaker.shout() // static dispatch — метод из extension, не requirement

// ==== Extension-only method в пустом протоколе ====
let myListener = MyListener()
myListener.listen() // OK — тип известен, static dispatch

let listener: Listener = MyListener()
// listener.listen() // ❌ Ошибка — метод не является requirement, нет в PWT
```

🧠 Ключевые моменты:

•	✅ Методы, помеченные override, вызываются через vtable (dynamic dispatch).

•	❌ Методы, определённые в extension, не участвуют в vtable или PWT — вызываются только при известном типе (static dispatch).

•	❌ Если протокол не содержит requirement, его методы не видны через протокольную ссылку.

•	❗ method hiding — это НЕ override, поэтому при обращении через родительский тип вызывается базовая версия метода.

## ❗ Почему `method hiding` — плохая идея

| Проблема                         | Описание |
|----------------------------------|----------|
| 🔍 **Трудность отладки**         | При чтении кода кажется, что вызывается метод сабкласса, но на деле — родительский. Это запутывает. |
| ⚠️ **Неожиданное поведение**     | Один и тот же объект (`DogHiding`) вызывает разные методы в зависимости от типа ссылки (`Animal` или `DogHiding`). |
| 🚫 **Не используется полиморфизм** | Полиморфизм работает только с `override`, а не с "method hiding". |
| 🧪 **Тестировать сложнее**       | Нужно следить за типами переменных и знать, где может внезапно вызваться родительский метод. |

## ✅ Когда может быть оправдано

- Когда ты **намеренно хочешь скрыть** метод родителя, потому что сабкласс **полностью меняет логику**, и метод родителя **не должен быть виден**.
- Например: у тебя старый `BaseAPI` с `request()`, а в `NewAPI` ты делаешь свою реализацию `request()` без наследования поведения.

> ⚠️ Но даже тогда лучше **переименовать метод**, а не скрывать родительский.

## 🧠 Вывод

> **Никогда не скрывай методы родителя, если можешь этого избежать.**
>
> Используй `override`, если хочешь переопределить поведение.

## Что делать, если при скролле тормозит таблица

Причины и как решить:

| Причина                                  | Описание                                                                 | Решение                                                                                     |
|------------------------------------------|--------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| Тяжёлые операции в `cellForRowAt`       | Загрузка изображений, форматирование текста, сложные вычисления         | Перенести тяжёлые операции в фоновый поток или кэшировать результаты                        |
| Отсутствие переиспользования ячеек      | Не используется `dequeueReusableCell`                                    | Убедиться, что используется `tableView.dequeueReusableCell(withIdentifier:for:)`           |
| Высокая нагрузка на main thread         | UI-обновления, сетевые запросы и парсинг на главном потоке              | Перенести в фоновый поток (например, через `DispatchQueue.global()`)                       |
| Нерелевантный `reloadData`              | Частые вызовы `reloadData` при скролле или обновлении                    | Использовать `reloadRows(at:)`, `performBatchUpdates` или `diffable data source`           |
| Слишком сложный UI в ячейках            | Много вложенных вью или autolayout constraints                           | Упростить UI, использовать `rasterization`, по возможности использовать `draw(_:)`         |
| Неправильная настройка Auto Layout      | Конфликты или неоптимальные constraints                                  | Использовать `UITableView.automaticDimension` правильно, кэшировать высоту                 |
| Большие изображения без кэширования     | Каждая ячейка грузит изображение с нуля                                  | Использовать библиотеку кэширования (например, SDWebImage, Kingfisher)                      |
| Отсутствие предварительной подготовки   | Ячейки готовятся "впритык" к экрану                                      | Использовать `prefetchDataSource`                                                           |
| Слишком часто вызывается layoutSubviews | Сложные layout-операции при каждом скролле                               | Оптимизировать layout в ячейках, избегать лишних пересозданий UI                            |
| Анимации во время скролла               | Активные анимации мешают плавному скроллу                                | Уменьшить количество/сложность анимаций или временно отключать во время скролла            |
| Отрисовка теней                         | `CALayer.shadow*` вызывает offscreen rendering и тормоза                | Использовать `shadowPath`, избегать прозрачности, по возможности отключить тень            |
| Прозрачности и слои с `alpha < 1.0`     | Вызывает offscreen rendering и GPU-блокировки                            | Избегать прозрачных слоёв в скроллируемых ячейках или объединять их в один непрозрачный    |

✅ Примеры кода для оптимизации теней и прозрачности в ячейках UITableView:

```swift
override func layoutSubviews() {
    super.layoutSubviews()
    
    layer.shadowColor = UIColor.black.cgColor
    layer.shadowOpacity = 0.2
    layer.shadowOffset = CGSize(width: 0, height: 2)
    layer.shadowRadius = 4
    
    // Важно: задать shadowPath — это отключит offscreen rendering
    layer.shadowPath = UIBezierPath(roundedRect: bounds, cornerRadius: layer.cornerRadius).cgPath
    
    // Растеризация слоя — полезно, если тень не меняется
    layer.shouldRasterize = true
    layer.rasterizationScale = UIScreen.main.scale
}
```

✅ Оптимизация прозрачности:

```swift
someView.alpha = 1.0              // по возможности избегайте alpha < 1 в scrollable UI
someView.backgroundColor = .white // сделать фон непрозрачным
someView.isOpaque = true          // поможет GPU быстрее отрисовывать
```

🚫 Что не делать:

```swift
someView.layer.shadowOpacity = 0.5 // без shadowPath — это вызовет offscreen rendering
someView.alpha = 0.5               // может тормозить на слабых устройствах
```

## Debugging в XCode и Instruments

__Debug__

| Инструмент                 | Назначение                                                        | Как использовать                                                                 |
|---------------------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
| Breakpoints               | Остановка кода в нужной точке                                     | Клик по номеру строки слева в редакторе, или через Debug Navigator              |
| LLDB Console (Debugger)   | Ручное управление отладкой, просмотр переменных                   | View > Debug Area > Activate Console (или ⌘⇧Y), команды: `po`, `print`, `bt`    |
| View Debugger             | Отладка UI, иерархия view, прозрачности, constraints              | Debug > View Debugging > Capture View Hierarchy                                 |
| Memory Graph Debugger     | Поиск утечек памяти и retain cycles                               | Запустить приложение → Debug Navigator → Memory Graph (иконка с кубиками)       |
| Instruments               | Глубокая профилизация (время CPU, утечки, FPS и т.д.)             | Product > Profile (⌘I) → выбрать нужный шаблон (Time Profiler, Leaks, и т.д.)   |
| Network Debugging         | Просмотр сетевых запросов                                         | Включить Network Debugging в Instruments или использовать Charles/Proxyman      |
| Console Output            | Логи, print, NSLog, ошибки                                        | View > Debug Area > Show Debug Area (⌘⇧Y)                                       |
| Debug Navigator           | Просмотр стеков вызовов, переменных, потоков                      | Навигация слева → иконка с отладкой (или ⌘7)                                    |
| Performance HUD (SwiftUI) | Живой мониторинг рендеринга SwiftUI                              | Использовать .debugPerformanceHUD() (iOS 17+), или через Instruments             |
| Accessibility Inspector   | Проверка доступности UI элементов                                 | Xcode > Open Developer Tool > Accessibility Inspector                           |

__Instruments__

| Инструмент           | Назначение                                                              | Применение и советы                                                                 |
|----------------------|-------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| **Time Profiler**     | Анализ CPU: что занимает процессорное время                            | Найти медленные функции, "узкие места" (bottlenecks), использовать часто            |
| **Leaks**             | Поиск утечек памяти (memory leaks)                                     | Покажет объекты, которые не освобождаются                                           |
| **Allocations**       | Отслеживание выделений памяти, живых объектов                          | Полезен для анализа роста памяти и поиска retain cycles                             |
| **Instruments > Zombies** | Поиск обращений к деаллокированным объектам (EXC_BAD_ACCESS)       | Включается отдельно — фиксирует попытки обращения к уже освобождённой памяти        |
| **Core Animation**    | Мониторинг производительности GPU, отрисовки, FPS                      | Видно, если есть offscreen rendering, лишние перерисовки                            |
| **Network**           | Анализ сетевых запросов (через URLSession и т.п.)                      | Видно длительность запросов, количество, ошибки                                     |
| **Energy Log**        | Анализ энергопотребления                                               | Важно для приложений с фоновой работой или GPS                                      |
| **Metal/System Trace**| Глубокая GPU/CPU профилизация                                          | Используется при рендере 3D, тяжелых анимациях                                       |
| **File Activity**     | Работа с файловой системой                                             | Когда приложение активно читает/пишет файлы                                         |
| **Disk I/O**          | Мониторинг операций чтения/записи на диск                             | Помогает выявить узкие места при работе с БД, файлами                              |
| **SwiftUI** (в iOS 17+)| Анализ SwiftUI-перерисовок и body-обновлений                          | Можно выявить избыточные рендеры `.body`, плохие `@State` или `@Binding`            |
| **Signpost**          | Кастомные метки производительности в коде                             | Используй `os_signpost` для измерения времени выполнения конкретных блоков кода     |

•	Time Profiler — начни с него, если есть лаги.

•	Leaks + Allocations — идеальны для отслеживания утечек.

•	Core Animation — если тормозит скролл или анимации.

•	Используй Instruments одновременно, можно комбинировать.