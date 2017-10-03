- [Networking](#networking)
	- [Протоколы передачи данных](#протоколы-передачи-данных)
	- [Какие различия между HEAD, GET, POST, PUT?](#head-get-post-put)
	- [Что такое REST архитектура?](#rest-архитектура)
	- [Как загрузить что-то из интернета? NSURL, NSURLSession, NSURLConnection, NSURLRequest](#загрузить-из-интернета)
	- [Парсинг JSON, HTML, XML](#парсинг)
	- [Сокет, TCP, UDP, NSStream - когда что применять?](#socket-tcp-udp-nsstream)
	- [Как написать синхронную обертку для асинхронного метода?](#async-inside-sync)

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

* надёжность (за счет отсутствия необходимости сохранять информацию о состоянии клиента, которая может быть утеряна);
* производительность (за счет использования кэша);
* масштабируемость;
* прозрачность системы взаимодействия, особенно необходимую для приложений обслуживания сети;
* простоту интерфейсов;
* портативность компонентов;
* легкость внесения изменений;
* способность эволюционировать, приспосабливаясь к новым требованиям (на примере Всемирной паутины).

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

* Generalized markup; it is possible to create "dialects" for any kind of purpose
XML Schema for datatype, structure validation. Makes it also possible to create new datatypes
* XSLT for transformation into different output formats
* XPath/XQuery for extracting information in deeply nested structures
* built in support for namespaces

Con:

* Relatively wordy compared to JSON (results in more data for the same amount of information).

__JSON__

JavaScript Object Notation - is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language, Standard ECMA-262 3rd Edition - December 1999. JSON is a text format that is completely language independent but uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python, and many others. These properties make JSON an ideal data-interchange language.

Pro:

* Simple syntax, which results in less "markup" overhead compared to XML.
* Easy to use with JavaScript as the markup is a subset of JS object literal notation and has the same basic data types as JavaScript.
* JSON Schema for description and datatype and structure validation
* JsonPath for extracting information in deeply nested structures

Con:

* Simple syntax, only a handful of different data types are supported.

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
# Сокет, TCP, UDP, NSStream - когда что применять?

__Socket__

Название программного интерфейса для обеспечения обмена данными между процессами,  абстрактный объект, представляющий конечную точку соединения. Для взаимодействия между машинами с помощью стека протоколов TCP/IP используются адреса и порты. Первое на текущий момент представляет собой 32-битный адрес, наиболее часто его представляют в символьной форме mmm.nnn.ppp.qqq. Второе — это номер порта в диапазоне от 0 до 65535. Эта пара и есть сокет. В процессе обмена, как правило, используется два сокета — сокет отправителя и сокет получателя. Каждый процесс может создать «слушающий» сокет (серверный сокет) и привязать его к какому-нибудь порту операционной системы. Слушающий процесс обычно находится в цикле ожидания, то есть просыпается при появлении нового соединения. При этом сохраняется возможность проверить наличие соединений на данный момент, установить тайм-аут для операции и т. д.

__WebSocket__

Протокол полнодуплексной связи (может передавать и принимать одновременно) поверх TCP-соединения, предназначенный для обмена сообщениями между браузером и веб-сервером в режиме реального времени. WebSocket разработан для воплощения в web-браузерах и web-серверах, но он может быть использован для любого клиентского или серверного приложения. Протокол WebSocket — это независимый протокол, основанный на протоколе TCP. Unlike traditional TCP sockets, WebSockets do at least maintain a relationship with HTTP and can be useful to achieve the same real-time communication goals as traditional sockets, all from the comfort and safety of the browser.

__TCP Stream Socket__

Is much more commonly used, as it provides the framework for a complete, structured "conversation" to occur between the two endpoints. TCP connections provide a means to ensure the message was received, and guarantees that packets are received in order. TCP is used by protocols including HTTP, FTP, and others where data must be reliably sent and received in order. To keep track of the ordering of packets, TCP employs a sequence number, which identifies the sequence of each packet. This not only keeps your conversation in order, but also adds a basic level of protection against some forms of spoofing (data forgery by a malicious party).

* Dedicated & point-to-point channel between server and client.
* Reliable and Lossless.
* Data sent/received in the similar order.
* Long time for recovering lost/mistaken data
* Web, SSH, FTP, TELNET, SMTP, IMAP/POP

__UDP Datagram Socket__

Is used for sending short messages called datagrams to the recipient. Datagrams are single packets of data that are sent and received without any "return postage." There is no guarantee that the recipient will receive a particular packet, and multiple packets may be received out of order. Datagrams are generally thought of as unreliable, in the same way that a carrier pigeon can be unreliable. This form of communication is used for sending short query/response-type messages that do not require authentication, such as DNS (name resolution) lookups, as well as by some protocols where lost packets are irrelevant; such as live video streams and online multiplayer games, where an interruption can be ignored.

* No dedicated & point-to-point channel between server and client.
* Not 100% reliable and may lose data.
* Data sent/received order might not be the same
* Don't care or rapid recovering lost/mistaken data
* Tunneling/VPN (lost packets are ok - the tunneled protocol takes care of it)
* Media streaming
* Games that don't care if you get every update
* Local broadcast mechanisms (same application running on different machines "discovering" each other)
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
