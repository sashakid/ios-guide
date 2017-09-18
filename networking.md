- [Networking](#networking)
	- [Преимущества и недостатки синхронного и асинхронного соединения?](#преимущества-и-недостатки-синхронного-и-асинхронного-соединения?)
	- [Протоколы передачи данных](#протоколы-передачи-данных)
	- [Какие различия между HEAD, GET, POST, PUT?](#какие-различия-между-head,-get,-post,-put? )
	- [Что такое REST архитектура?](#что-такое-rest-архитектура?)
	- [Как загрузить что-то из интернета? NSURL, NSURLSession, NSURLConnection, NSURLRequest](#как-загрузить-что-то-из-интернета? nsurl, nsurlsession, nsurlconnection, nsurlrequest)
	- [Парсинг JSON, HTML, XML](#парсинг json, html, xml)

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
