- [Networking](#networking)
  - [Протоколы передачи данных](#протоколы-передачи-данных)
  - [Какие различия между HEAD, GET, POST, PUT?](#какие-различия-между-head-get-post-put)
  - [Что такое REST архитектура?](#что-такое-rest-архитектура)
  - [Как загрузить что-то из интернета? NSURL, NSURLSession, NSURLConnection, NSURLRequest](#как-загрузить-что-то-из-интернета-nsurl-nsurlsession-nsurlconnection-nsurlrequest)
  - [Парсинг JSON, HTML, XML](#парсинг-json-html-xml)
  - [Сокет, TCP, UDP, NSStream - когда что применять?](#сокет-tcp-udp-nsstream---когда-что-применять)
  - [Как написать синхронную обертку для асинхронного метода?](#как-написать-синхронную-обертку-для-асинхронного-метода)
  - [В чем разница между HTTP и HTTPS?](#в-чем-разница-между-http-и-https)

<a name="networking"></a>

# Networking

<a name="протоколы-передачи-данных"></a>

## Протоколы передачи данных

Протокол передачи данных — набор соглашений интерфейса логического уровня, которые определяют обмен данными между различными программами. Эти соглашения задают единообразный способ передачи сообщений и обработки ошибок при взаимодействии программного обеспечения разнесённой в пространстве аппаратуры, соединённой тем или иным интерфейсом.

__IP__

Internet Protocol, межсетевой протокол - маршрутизируемый протокол сетевого уровня стека TCP/IP. Именно IP стал тем протоколом, который объединил отдельные компьютерные сети во всемирную сеть Интернет. Неотъемлемой частью протокола является адресация сети.

__TCP__

Transmission Control Protocol, протокол управления передачей — один из основных протоколов передачи данных Интернета, предназначенный для управления передачей данных в сетях и подсетях TCP/IP.

__UDP__

User Datagram Protocol, протокол пользовательских датаграмм. С UDP компьютерные приложения могут посылать сообщения (в данном случае называемые датаграммами) другим хостам по IP-сети без необходимости предварительного сообщения для установки специальных каналов передачи или путей данных. Природа UDP как протокола без сохранения состояния также полезна для серверов, отвечающих на небольшие запросы от огромного числа клиентов, например DNS и потоковые мультимедийные приложения вроде IPTV, Voice over IP, протоколы туннелирования IP и многие онлайн-игры.

__HTTP__

HyperText Transfer Protocol, протокол передачи гипертекста — протокол прикладного уровня передачи данных (изначально — в виде гипертекстовых документов). Основой HTTP является технология «клиент-сервер», то есть предполагается существование потребителей (клиентов), которые инициируют соединение и посылают запрос, и поставщиков (серверов), которые ожидают соединения для получения запроса, производят необходимые действия и возвращают обратно сообщение с результатом. Этот протокол описывает взаимодействие между двумя компьютерами (клиентом и сервером), построенное на базе сообщений, называемых запрос (Request) и ответ (Response). Каждое сообщение состоит из трех частей: стартовая строка, заголовки и тело. При этом обязательной является только стартовая строка.

__FTP__

File Transfer Protocol — это протокол передачи файлов со специального файлового сервера на компьютер пользователя. FTP дает возможность абоненту обмениваться двоичными и текстовыми файлами с любым компьютером сети. Установив связь с удаленным компьютером, пользователь может скопировать файл с удаленного компьютера на свой или скопировать файл со своего компьютера на удаленный.

__SIP__

Session Initiation Protocol, протокол установления сеанса — протокол передачи данных, описывающий способ установления и завершения пользовательского интернет-сеанса, включающего обмен мультимедийным содержимым (IP-телефония, видео- и аудиоконференции, мгновенные сообщения, онлайн-игры). Протокол описывает, каким образом клиентское приложение может запросить начало соединения у другого, возможно, физически удалённого клиента, находящегося в той же сети, используя его уникальное имя. Протокол определяет способ согласования между клиентами об открытии каналов обмена на основе других протоколов, которые могут использоваться для непосредственной передачи информации (например, RTP). Допускается добавление или удаление таких каналов в течение установленного сеанса, а также подключение и отключение дополнительных клиентов (то есть допускается участие в обмене более двух сторон — конференц-связь). Протокол также определяет порядок завершения сеанса.

<a name="head-get-post-put"></a>

## Какие различия между HEAD, GET, POST, PUT?

`GET`

Используется для запроса содержимого указанного ресурса. С помощью метода `GET` можно также начать какой-либо процесс. В этом случае в тело ответного сообщения следует включить информацию о ходе выполнения процесса. Клиент может передавать параметры выполнения запроса в URI целевого ресурса после символа `?`:

```
GET /path/resource?param1=value1&param2=value2 HTTP/1.1
```

`HEAD`

Аналогичен методу `GET`, за исключением того, что в ответе сервера отсутствует тело. Запрос `HEAD` обычно применяется для извлечения метаданных, проверки наличия ресурса (валидация URL) и чтобы узнать, не изменился ли он с момента последнего обращения. Заголовки ответа могут кэшироваться. При несовпадении метаданных ресурса с соответствующей информацией в кэше копия ресурса помечается как устаревшая.

`POST`

Применяется для передачи пользовательских данных заданному ресурсу. Например, в блогах посетители обычно могут вводить свои комментарии к записям в HTML-форму, после чего они передаются серверу методом `POST` и он помещает их на страницу. При этом передаваемые данные (в примере с блогами — текст комментария) включаются в тело запроса. Аналогично с помощью метода `POST` обычно загружаются файлы на сервер. В отличие от метода `GET`, метод `POST` не считается идемпотентным, то есть многократное повторение одних и тех же запросов `POST` может возвращать разные результаты (например, после каждой отправки комментария будет появляться одна копия этого комментария).

```swift
var request = URLRequest(url: URL(string: "http://www.thisismylink.com/postName.php")!)
request.httpMethod = "POST"
let postString = "id=13&name=Jack"
request.httpBody = postString.data(using: .utf8)
let task = URLSession.shared.dataTask(with: request) { data, response, error in
  guard let data = data, error == nil else {                                                 
  // check for fundamental networking error
    print("error=\(error)")
    return
  }
  if let httpStatus = response as? HTTPURLResponse, httpStatus.statusCode != 200 {           
  // check for http errors
    print("statusCode should be 200, but is \(httpStatus.statusCode)")
    print("response = \(response)")
  }
  let responseString = String(data: data, encoding: .utf8)
  print("responseString = \(responseString)")
}
task.resume()
```

`PUT`

Применяется для загрузки содержимого запроса на указанный в запросе URI. Если по заданному URI не существовало ресурса, то сервер создаёт его и возвращает статус `201` (Created). Если же был изменён ресурс, то сервер возвращает `200` (Ok) или `204` (No Content). Сервер не должен игнорировать некорректные заголовки `Content-*`, передаваемые клиентом вместе с сообщением. Если какой-то из этих заголовков не может быть распознан или не допустим при текущих условиях, то необходимо вернуть код ошибки `501` (Not Implemented). Фундаментальное различие методов `POST` и `PUT` заключается в понимании предназначений URI ресурсов. Метод `POST` предполагает, что по указанному URI будет производиться обработка передаваемого клиентом содержимого. Используя `PUT`, клиент предполагает, что загружаемое содержимое соответствует находящемуся по данному URI ресурсу.

__URI__

Uniform Resource Identifier — унифицированный (единообразный) идентификатор ресурса. URI — это символьная строка, позволяющая идентифицировать какой-либо ресурс: документ, изображение, файл, службу, ящик электронной почты и т. д. Прежде всего, речь идёт, конечно, о ресурсах сети Интернет.

__URL__

Uniform Resource Locator — единообразный локатор (определитель местонахождения) ресурса. URL — это стандартизированный способ записи адреса ресурса в сети Интернет. URL это частный случай URI. Понятие URI включает в себя, помимо URL, например, ссылки на адреса электронной почты и т.п. URL указывает на Веб-ресурс, вроде сайта, страницы или конкретного файла, расположенных на интернет-серверах.

<a name="rest-архитектура"></a>

## Что такое REST архитектура?

REST (Representational state transfer) – это стиль архитектуры программного обеспечения для распределенных систем, таких как World Wide Web, который, как правило, используется для построения веб-служб. Системы, поддерживающие REST, называются RESTful-системами. В общем случае REST является очень простым интерфейсом управления информацией без использования каких-то дополнительных внутренних прослоек. Каждая единица информации однозначно определяется глобальным идентификатором, таким как URL. Каждый URL в свою очередь имеет строго заданный формат. Вызов удаленной процедуры представляет собой обычный HTTP-запрос (обычно GET или POST; такой запрос называют REST-запрос), а необходимые данные передаются в качестве параметров запроса. Этот способ является альтернативой более сложным методам, таким как SOAP, CORBA и RPC.

```
GET /book/ — получить список всех книг
GET /book/3/ — получить книгу номер 3
PUT /book/ — добавить книгу (данные в теле запроса)
POST /book/3 — изменить книгу (данные в теле запроса)
DELETE /book/3 — удалить книгу
```

каждый запрос (REST-запрос) клиента к серверу содержит в себе исчерпывающую информацию о желаемом ответе сервера (желаемом репрезентативном состоянии), и сервер не обязан сохранять информацию о состоянии клиента («клиентской сессии»).

__Архитектура REST__

Необходимые условия для построения распределенных REST-приложений:

1. Клиент-серверная архитектура.
2. Сервер не обязан сохранять информацию о состоянии клиента.
3. В каждом запросе клиента должно явно содержаться указание о возможности кэширования ответа и получения ответа из существующего кэша
4. Клиент может взаимодействовать не напрямую с сервером, а с произвольным количеством промежуточных узлов. При этом клиент может не знать о существовании промежуточных узлов, за исключением случаев передачи конфиденциальной информации.
5. Унифицированный программный интерфейс сервера. Филдинг приводил URI в качестве примера формата запросов к серверу, а в качестве примера ответа сервера форматы HTML, XML и JSON, различаемые с использованием идентификаторов MIME.

Преимущества:

- надёжность (за счет отсутствия необходимости сохранять информацию о состоянии клиента, которая может быть утеряна);
- производительность (за счет использования кэша);
- масштабируемость;
- прозрачность системы взаимодействия, особенно необходимую для приложений обслуживания сети;
- простоту интерфейсов;
- портативность компонентов;
- легкость внесения изменений;
- способность эволюционировать, приспосабливаясь к новым требованиям (на примере Всемирной паутины).

<a name="загрузить-из-интернета"></a>

## Как загрузить что-то из интернета? NSURL, NSURLSession, NSURLConnection, NSURLRequest

__NSURLConnection__

Is a much older API, introduced in OS X 10.2. It's an abstraction on top of the Core Foundation / CFNetwork APIs. If we have an open connection with NSURLConnection and the system interrupt our App, when our App goes to background mode, everything we have received or sent were lost.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/nsurlconnection.png">

__NSURLSession__

Is designed around the assumption that you'll have a lot of requests that need similar configuration (standard sets of headers, etc.), and makes life much easier if you do. `NSURLSession` also provides support for background downloads, which make it possible to continue downloading resources while your app isn't running (or when it is in the background on iOS). `NSURLSession` also provides grouping of related requests, making it easy to cancel all of the requests associated with a particular work unit, such as canceling all loads associated with loading a web page when the user closes the window or tab. `NSURLSession` also provides nicer interfaces for requesting data using blocks, in that it allows you to combine them with delegate methods for doing custom authentication handling, redirect handling. The most immediate improvement `NSURLSession` provides over `NSURLConnection` is the ability to configure per-session cache, protocol, cookie, and credential policies, rather than sharing them across the app. This allows the networking infrastructure of frameworks and parts of the app to operate independently, without interfering with one another. Each `NSURLSession` object is initialized with an `NSURLSessionConfiguration`, which specifies these policies, as well a number of new options specifically added to improve performance on mobile devices. The other big part of `NSURLSession` is session tasks, which handle the loading of data, as well as uploading and downloading files and data between the client and server. `NSURLSessionTask` is most analogous to `NSURLConnection` in that it is responsible for loading data, with the main difference being that tasks share the common delegate of their parent NSURLSession. Solves background mode problem and also give us out of process downloads. It manage the connection process even when we don't have access. You will need to use `application:handleEventsForBackgroundURLSession:completionHandler` in your AppDelegate

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/nsurlsession.png">

```objectivec
NSURL *URL = [NSURL URLWithString:@"http://example.com"];
NSURLRequest *request = [NSURLRequest requestWithURL:URL];
NSURLSession *session = [NSURLSession sharedSession];
NSURLSessionDataTask *task = [session dataTaskWithRequest:request completionHandler: ^(NSData *data, NSURLResponse *response, NSError *error) {
 // ...
}];
[task resume];
```

## Парсинг JSON, HTML, XML

Парсинг – обработка данных, разбор входной последовательности с целью получения токенов.

Токен – лексема, минимальная единица языка, имеющая самостоятельный смысл (имя, знак операции, ключевое слово)

Регулярные выражения – формальный язык поиска и осуществления манипуляций с подстроками в тексте, основанный на использовании метасимволов. По сути, это строка-образец (pattern), состоящая из символов и метасимволов и задающая правило поиска. The `NSRegularExpression` class is used to represent and apply regular expressions to Unicode strings. An instance of this class is an immutable representation of a compiled regular expression pattern and various option flags.

Example use the regular expression `\\b(a|b)(c|d)\\b`. This snippet creates a regular expression to match two-letter words, in which the first letter is “a” or “b” and the second letter is “c” or “d”. Specifying `NSRegularExpressionCaseInsensitive` means that matches will be case-insensitive, so this will match “BC”, “aD”, and so forth, as well as their lower-case equivalents.

```objectivec
NSError *error = NULL;
NSRegularExpression *regex = [NSRegularExpression regularExpressionWithPattern:@"\\b(a|b)(c|d)\\b" options:NSRegularExpressionCaseInsensitive error:&error];
```

__HTML__

HyperText Markup Language - is a markup language, that tells browsers how to layout a web page. By its very nature, this content is in a hierarchy that defines where within the page a piece of information is to be displayed.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/html_parsing.png">

__XML__

eXtensible Markup Language - расширяемый язык разметки. XML разрабатывался как язык с простым формальным синтаксисом, удобный для создания и обработки документов программами и одновременно удобный для чтения и создания документов человеком, с подчёркиванием нацеленности на использование в Интернете.

Pro:

- Generalized markup; it is possible to create "dialects" for any kind of purpose
XML Schema for datatype, structure validation. Makes it also possible to create new datatypes
- XSLT for transformation into different output formats
- XPath/XQuery for extracting information in deeply nested structures
- built in support for namespaces

Con:

- Relatively wordy compared to JSON (results in more data for the same amount of information).

__JSON__

JavaScript Object Notation - is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language, Standard ECMA-262 3rd Edition - December 1999. JSON is a text format that is completely language independent but uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python, and many others. These properties make JSON an ideal data-interchange language.

Pro:

- Simple syntax, which results in less "markup" overhead compared to XML.
- Easy to use with JavaScript as the markup is a subset of JS object literal notation and has the same basic data types as JavaScript.
- JSON Schema for description and datatype and structure validation
- JsonPath for extracting information in deeply nested structures

Con:

- Simple syntax, only a handful of different data types are supported.

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

<a name="socket-tcp-udp-nsstream"></a>

## Сокет, TCP, UDP, NSStream - когда что применять?

__Socket__

Название программного интерфейса для обеспечения обмена данными между процессами,  абстрактный объект, представляющий конечную точку соединения. Для взаимодействия между машинами с помощью стека протоколов TCP/IP используются адреса и порты. Первое на текущий момент представляет собой 32-битный адрес, наиболее часто его представляют в символьной форме mmm.nnn.ppp.qqq. Второе — это номер порта в диапазоне от 0 до 65535. Эта пара и есть сокет. В процессе обмена, как правило, используется два сокета — сокет отправителя и сокет получателя. Каждый процесс может создать «слушающий» сокет (серверный сокет) и привязать его к какому-нибудь порту операционной системы. Слушающий процесс обычно находится в цикле ожидания, то есть просыпается при появлении нового соединения. При этом сохраняется возможность проверить наличие соединений на данный момент, установить тайм-аут для операции и т. д.

__WebSocket__

Протокол полнодуплексной связи (может передавать и принимать одновременно) поверх TCP-соединения, предназначенный для обмена сообщениями между браузером и веб-сервером в режиме реального времени. WebSocket разработан для воплощения в web-браузерах и web-серверах, но он может быть использован для любого клиентского или серверного приложения. Протокол WebSocket — это независимый протокол, основанный на протоколе TCP. Unlike traditional TCP sockets, WebSockets do at least maintain a relationship with HTTP and can be useful to achieve the same real-time communication goals as traditional sockets, all from the comfort and safety of the browser.

__TCP Stream Socket__

Is much more commonly used, as it provides the framework for a complete, structured "conversation" to occur between the two endpoints. TCP connections provide a means to ensure the message was received, and guarantees that packets are received in order. TCP is used by protocols including HTTP, FTP, and others where data must be reliably sent and received in order. To keep track of the ordering of packets, TCP employs a sequence number, which identifies the sequence of each packet. This not only keeps your conversation in order, but also adds a basic level of protection against some forms of spoofing (data forgery by a malicious party).

- Dedicated & point-to-point channel between server and client.
- Reliable and Lossless.
- Data sent/received in the similar order.
- Long time for recovering lost/mistaken data
- Web, SSH, FTP, TELNET, SMTP, IMAP/POP

__UDP Datagram Socket__

Is used for sending short messages called datagrams to the recipient. Datagrams are single packets of data that are sent and received without any "return postage." There is no guarantee that the recipient will receive a particular packet, and multiple packets may be received out of order. Datagrams are generally thought of as unreliable, in the same way that a carrier pigeon can be unreliable. This form of communication is used for sending short query/response-type messages that do not require authentication, such as DNS (name resolution) lookups, as well as by some protocols where lost packets are irrelevant; such as live video streams and online multiplayer games, where an interruption can be ignored.

- No dedicated & point-to-point channel between server and client.
- Not 100% reliable and may lose data.
- Data sent/received order might not be the same
- Don't care or rapid recovering lost/mistaken data
- Tunneling/VPN (lost packets are ok - the tunneled protocol takes care of it)
- Media streaming
- Games that don't care if you get every update
- Local broadcast mechanisms (same application running on different machines "discovering" each other)

***

```c
CFSocketRef CFSocketCreate (
    CFAllocatorRef allocator,
    SInt32 protocolFamily,
    SInt32 socketType,
    SInt32 protocol,
    CFOptionFlags callBackTypes,
    CFSocketCallBack callout,
    const CFSocketContext *context
);
```

***

__CFStream__

Socket streams provide an easy interface for reading and writing data to or from a socket. Each socket can be bound to a read and write stream, allowing for synchronous or asynchronous communication. Streams encapsulate most of the work needed for reading and writing byte streams, and replace the traditional `send()` and `recv()` functions used in C. Two different stream objects are used with sockets: `CFReadStream` and `CFWriteStream`

__NSStream__

`NSStream` is an abstract class that defines the fundamental interface and properties for all stream objects. `NSInputStream` and `NSOutputStream` are subclasses of `NSStream` and implement default input-stream and output-stream behavior. `NSStream` is built on the `CFStream` layer of Core Foundation. This close relationship means that the concrete subclasses of `NSStream`, `NSOutputStream` and `NSInputStream`, are toll-free bridged with their Core Foundation counterparts `CFWriteStream` and `CFReadStream`. Although there are strong similarities between the Cocoa and Core Foundation stream APIs, their implementations are not exactly coincident. The Cocoa stream classes use the delegation model for asynchronous behavior (assuming run-loop scheduling) while Core Foundation uses client callbacks. Despite their strong similarities, __`NSStream` does give you a major advantage over `CFStream`. Because of its Objective-C underpinnings, it is extensible.__ You can subclass `NSStream`, `NSInputStream`, or `NSOutputStream` to customize stream attributes and behavior. For example, you could create an input stream that maintains statistics on the bytes it reads; or you could make a `NSStream` subclass whose instances can seek through their stream, putting back bytes that have been read. `NSStream` has its own set of required overrides, as do `NSInputStream` and `NSOutputStream`.

<a name="async-inside-sync"></a>

## Как написать синхронную обертку для асинхронного метода?

```objectivec
//Original asynchronous method
- (void)executeInBackgroundWithCompletion:(void(^)(void))completion {
  NSOperationQueue* callbackQueue = [NSOperationQueue currentQueue];
  [[[NSOperationQueue alloc] init] addOperationWithBlock:^{
    //do something that takes a long time
    [callbackQueue addOperationWithBlock:^{
      if (completion) {
        completion();
      }
    }];
  }];
}

//Synchronous version
- (void)executeInBackgroundAndWait {
  dispatch_semaphore_t semaphore = dispatch_semaphore_create(0);
  [self executeInBackgroundWithCompletion:^{
    dispatch_semaphore_signal(semaphore);
  }];
  while (dispatch_semaphore_wait(semaphore, DISPATCH_TIME_NOW)) {
    [[NSRunLoop currentRunLoop] runMode:NSDefaultRunLoopMode beforeDate:[NSDate dateWithTimeIntervalSinceNow:0]];
  };
}
```

<a name="http-https"></a>

## В чем разница между HTTP и HTTPS?

И то, и другое является протоколами, с помощью которых происходит взаимодействие пользователей с сайтами в интернете. Сама аббревиатура `HTTP` обозначает `Hyper Text Transfer Protocol` то есть протокол передачи гипертекста. Та самая буква, которая отличает термины между собой – S – означает `Security`.

**HTTP** 

При отправлении и получении пакетов данных по сети интернет через `HTTP` используется протокол управления передачей (`TCP`). Соединение при этом происходит через порт `80`. Клиент отправляет запрос на HTTP-сервер, где располагается сайт, после чего сервер посылает ответ. Этот ответ содержит информацию о состоянии завершения. Выглядит это примерно так: `HTTP/1.1 200 OK`. За прошедшие годы протокол `TCP` был некоторым образом усовершенствован, но по большей части остается таким же, каким был в 1974 году. `HTTP` также применяет `UDP` (протокол пользовательских дейтаграмм), который был разработан Дэвидом Ридом ещё в 1980-м. Это менее надёжный протокол, однако его активно применяются в видеоконференциях, играх и потоковой передаче. Благодаря этому можно отбрасывать и принимать отдельные пакеты в произвольном порядке для увеличения производительности.

**HTTPS**

`HTTPS` означает безопасный протокол передачи гипертекста (или `HTTP` через `TLS` или `SSL`). Когда вы вводите `https://` в адресную строку перед доменом, вы передаёте браузеру информацию о подключении через `HTTPS`. Сайты, работающие по протоколу `HTTPS`, обычно имеют перенаправление, то есть даже при вводе обычного `http://` происходит переадресация для доставки по защищенному соединению. `HTTPS` также использует `TCP` (протокол управления передачей) для отправки и получения пакетов данных. Это делается через порт `443` соединением, зашифрованным `TSL`. `HTTPS` шифрует данные открытым ключом, а затем получатель расшифровывает его. Открытый ключ лежит на сервере и входит в SSL-сертификат. Сертификаты, в свою очередь, криптографически подписываются центром сертификации (ЦС). Каждый браузер имеет список доверенных ЦС. Любой подписанный центром сертификации сертификат, входящий в список доверенных, получает в адресной строке значок в виде зеленого замка.

**В чем разница между HTTP и HTTPS**

- По-разному записывается URL-адрес. Для `HTTP` — `http://`, а для `HTTPS` — `https://`.
- `HTTP` является не защищенным, а `HTTPS` защищенным.
- `HTTP` посылает данные через порт `80`, а `HTTPS` использует порт `443`.
- `HTTP` работает на уровне приложений, а `HTTPS` — на транспортном уровне.
- Для `HTTP` не нужны SSL-сертификаты; для `HTTPS` нужен SSL-сертификат, подписанный центром сертификации.
- `HTTP` не требует проверки домена, тогда как `HTTPS` требует хотя бы проверки домена, а для некоторых сертификатов даже проверки юридического документа.
- В `HTTP` нет шифрования, `HTTPS` шифрует данные перед отправкой.

**Как работает TLS**

`TLS` – гибридная криптографическая система. Это означает, что она использует несколько криптографических подходов:

1. Асиметричное шифрование (криптосистема с открытым ключом) для генерации общего секретного ключа и аутентификации (то есть удостоверения в том, что вы – тот за кого себя выдаете).
2. Симметричное шифрование, использующее секретный ключ для дальнейшего шифрования запросов и ответов.

**Криптосистема с открытым ключом** – это разновидность криптографической системы, когда у каждой стороны есть и открытый, и закрытый ключ, математически связанные между собой. Открытый ключ используется для шифрования текста сообщения в “тарабарщину”, в то время как закрытый ключ используется для дешифрования и получения исходного текста. С тех пор как сообщение было зашифровано с помощью открытого ключа, оно может быть расшифровано только соответствующим ему закрытым ключом. Ни один из ключей не может выполнять обе функции. Открытый ключ публикуется в открытом доступе без риска подвергнуть систему угрозам, но закрытый ключ не должен попасть к кому-либо, не имеющему прав на дешифровку данных. Итак, мы имеем ключи – открытый и закрытый. Одним из наиболее впечатляющих достоинств ассиметричного шифрования является то, что две стороны, ранее совершенно не знающие друг друга, могут установить защищенное соединение, изначально обмениваясь данными по открытому, незащищенному соединению.
Клиент и сервер используют свои собственные закрытые ключи (каждый – свой) и опубликованный открытый ключ для создания общего секретного ключа на сессию. Это означает, что если кто-нибудь находится между клиентом и сервером и наблюдает за соединением – он все равно не сможет узнать ни закрытый ключ клиента, ни закрытый ключ сервера, ни секретный ключ сессии. Как это возможно? Математика!

Одним из наиболее распространенных подходов является **алгоритм обмена ключами Ди́ффи — Хе́ллмана (DH)**. Этот алгоритм позволяет клиенту и серверу договориться по поводу общего секретного ключа, без необходимости передачи секретного ключа по соединению. Таким образом, злоумышленники, прослушивающие канал, не смогу определить секретный ключ, даже если они будут перехватывать все пакеты данных без исключения. Как только произошел обмен ключами по DH-алгоритму, полученный секретный ключ может использоваться для шифрования дальнейшего соединения в рамках данной сессии, используя намного более простое симметричное шифрование.

Математические функции, лежащие в основе этого алгоритма, имею важную отличительную особенность — они относительно просто вычисляются в прямом направлении, но практически не вычисляются в обратном. Это именно та область, где в игру вступают очень большие простые числа. Пусть Алиса и Боб – две стороны, осуществляющие обмен ключами по DH-алгоритму. Сперва они договариваются о некотором основании root (обычно маленьком числе, таком как 2,3 или 5) и об очень большом простом числе prime (больше чем 300 цифр). Оба значения пересылаются в открытом виде по каналу связи, без угрозы компрометировать соединение. Напомним, что и у Алисы, и у Боба есть собственные закрытые ключи (из более чем 100 цифр), которые никогда не передаются по каналам связи.  По каналу связи же передается смесь mixture, полученная из закрытых ключей, а также значений prime и root. Таким образом:
```
Alice’s mixture = (root ^ Alice’s Secret) % prime
Bob’s mixture = (root ^ Bob’s Secret) % prime
где % — остаток от деления
```
Таким образом, Алиса создает свою смесь mixture на основе утвержденных значений констант (root и prime), Боб делает то же самое. Как только они получили значения mixture друг друга, они производят дополнительные математические операции для получения закрытого ключа сессии. А именно:
```
Вычисления Алисы
(Bob’s mixture ^ Alice’s Secret) % prime

Вычисления Боба
(Alice’s mixture ^ Bob’s Secret) % prime
```
Результатом этих операций является одно и то же число, как для Алисы, так и для Боба, и это число и становится закрытым ключом на данную сессию. Обратите внимание, что ни одна из сторон не должна была пересылать свой закрытый ключ по каналу связи, и полученный секретный ключ так же не передавался по открытому соединению. Данный процесс на примере смешивания цветов:

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tls.jpg">

Обратите внимание как начальный цвет (желтый) в итоге превращается в один и тот же “смешанный” цвет и у Боба, и у Алисы. Единственное, что передается по открытому каналу связи так это наполовину смешанные цвета, на самом деле бессмысленные для любого прослушивающего канал связи.

Обмен ключами происходит всего один раз за сессию, во время установления соединения. Когда же стороны уже договорились о секретном ключе, клиент-серверное взаимодействие происходит с помощью **симметричного шифрования**, которое намного эффективнее для передачи информации, поскольку не требуется дополнительные издержки на подтверждения. Используя секретный ключ, полученный ранее, а также договорившись по поводу режима шифрования, клиент и сервер могут безопасно обмениваться данными, шифруя и дешифруя сообщения, полученные друг от друга с использованием секретного ключа. Злоумышленник, подключившийся каналу, будет видеть лишь “мусор”, гуляющий по сети взад-вперед.

Алгоритм Диффи-Хеллмана позволяет двум сторонам получить закрытый секретный ключ. Но откуда обе стороны могут уверены, что разговаривают действительно друг с другом? Мы еще не говорили об **аутентификации**. Что если я позвоню своему приятелю, мы осуществим DH-обмен ключами, но вдруг окажется, что мой звонок был перехвачен и на самом деле я общался с кем-то другим?! Я по прежнему смогу безопасно общаться с этим человеком – никто больше не сможет нас прослушать – но это будет совсем не тот, с кем я думаю, что общаюсь. Это не слишком безопасно! Для решения проблемы аутентификации, нам нужна Инфраструктура открытых ключей, позволяющая быть уверенным, что субъекты являются теми за кого себя выдают. Эта инфраструктура создана для создания, управления, распространения и отзыва цифровых сертификатов. Сертификаты – это те раздражающие штуки, за которые нужно платить, чтобы сайт работал по HTTPS.

В самом грубом приближении, **цифровой сертификат** – это файл, использующий электронной-цифровую подпись и связывающий открытый (публичный) ключ компьютера с его принадлежностью. Цифровая подпись на сертификате означает, что некто удостоверяет тот факт, что данный открытый ключ принадлежит определенному лицу или организации.  По сути, сертификаты связывают доменные имена с определенным публичным ключом. Это предотвращает возможность того, что злоумышленник предоставит свой публичный ключ, выдавая себя за сервер, к которому обращается клиент. В примере с телефоном, приведенном выше, хакер может попытаться предъявить мне свой публичный ключ, выдавая себя за моего друга – но подпись на его сертификате не будет принадлежать тому, кому я доверяю. Чтобы сертификату доверял любой веб-браузер, он должен быть подписан аккредитованным удостоверяющим центром (центром сертификации, Certificate Authority, CA). CA – это компании, выполняющие ручную проверку, того что лицо, пытающееся получить сертификат, удовлетворяет следующим двум условиям:

1. является реально существующим;
2. имеет доступ к домену, сертификат для которого оно пытается получить.

Как только CA удостоверяется в том, что заявитель – реальный и он реально контролирует домен, CA подписывает сертификат для этого сайта, по сути, устанавливая штамп подтверждения на том факте, что публичный ключ сайта действительно принадлежит ему и ему можно доверять. В ваш браузер уже изначально предзагружен список аккредитованных CA. Если сервер возвращает сертификат, не подписанный аккредитованным CA, то появится большое красное предупреждение. В противном случае, каждый мог бы подписывать фиктивные сертификаты. Так что даже если хакер взял открытый ключ своего сервера и сгенерировал цифровой сертификат, подтверждающий что этот публичный ключ, ассоциирован с сайтом facebook.com, браузер не поверит в это, поскольку сертификат не подписан аккредитованным CA.