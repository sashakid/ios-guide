- [Что произойдет если сначала нажать на кнопку 1 а потом на кнопку 2?](#что-произойдет-если-сначала-нажать-на-кнопку-1-а-потом-на-кнопку-2)
- [Что произойдет при исполнении следующего кода?](#что-произойдет-при-исполнении-следующего-кода)
- [Реализуйте следующие методы: retain, release, autorelease](#реализуйте-следующие-методы-retain-release-autorelease)
- [Выведется ли в дебагер Hello world? Почему?](#выведется-ли-в-дебагер-hello-world-почему)
- [Что выведется в консоль?](#что-выведется-в-консоль)
- [Задача про банерокрутилку](#задача-про-банерокрутилку)
- [Задача на регулярное выражение](#задача-на-регулярное-выражение)
- [Метод, возвращающий N наиболее часто встречающихся слов во входной строке](#метод-возвращающий-n-наиболее-часто-встречающихся-слов-во-входной-строке)
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

<a name="задача-про-банерокрутилку"></a>

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

<a name="задача-на-регулярное-выражение"></a>

## Задача на регулярное выражение

В системе авторизации есть следующее ограничение на формат логина: он должен начинаться с латинской буквы, может состоять из латинских букв, цифр, точки и минуса и должен заканчиваться латинской буквой или цифрой. Минимальная длина логина — 1 символ. Максимальная — 20 символов.

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

<a name="наиболее-часто-встречающиеся-слова"></a>

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
•	sizeof(StructA) == 8, так как после поля a (4 байта) компилятор вставляет 2 байта паддинга, чтобы выровнять поля структуры по 4 байта.

•	sizeof(StructB) == 12, так как после поля b (1 байт) вставляется 3 байта паддинга для выравнивания поля a (4 байта). Далее стоит c (1 байт), и еще 2 байта паддинга.

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
class Animal {
    func speak() {
        print("Animal speaks")
    }
}

// ✅ Dog переопределяет метод speak
class DogOverriding: Animal {
    override func speak() {
        print("DogOverriding barks")
    }
}

// 🚫 Dog НЕ переопределяет, а просто объявляет метод с таким же именем
class DogHiding: Animal {
    func speak() {
        print("DogHiding barks")
    }
}

print("== Переопределение (override) ==")
let dog1 = DogOverriding()
dog1.speak()                          // DogOverriding barks

let animal1: Animal = DogOverriding()
animal1.speak()                       // DogOverriding barks (динамическая диспетчеризация)

print("== Сокрытие (method hiding) ==")
let dog2 = DogHiding()
dog2.speak()                          // DogHiding barks

let animal2: Animal = DogHiding()
animal2.speak()                       // Animal speaks (статическая диспетчеризация)
```

```
== Переопределение (override) ==
DogOverriding barks
DogOverriding barks
== Сокрытие (method hiding) ==
DogHiding barks
Animal speaks
```

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