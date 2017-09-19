- [iOS](#ios)
	- [IPhone, resolution, pixels vs points](#iphone,-resolution,-pixels-vs-points)
	- [Файловая система iOS](#файловая-система-ios)
	- [Жизненный цикл приложения](#жизненный-цикл-приложения)
	- [Жизненный цикл UIViewController](#жизненный-цикл-uiviewController)
	- [UIView](#uiview)
  - [Фреймворки](#фреймворки)
    - [Core Foundation](#core-foundation)
	  - [UIKit](#uikit)
    - [CFNetwork](#cfnetwork)
    - [QuartzCore](#quartzcore)

<a name="ios"></a>
# iOS
<a name="iphone,-resolution,-pixels-vs-points"></a>
## IPhone, resolution, pixels vs points?
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/resolutions.png">
A pixel on iOS is the full resolution of the device, which means if I have an image that is 100x100 pixels in length, then the phone will render it 100x100 pixels on a standard non-retina device. However, because newer iPhones have a quadrupled pixel density, that same image will render at 100x100 pixels, but look half that size. The iOS engineers solved this a long time ago (way back in OS X with Quartz) when they introduced Core Graphics' point system. A point is a standard length equivalent to 1x1 pixels on a non-retina device, and 2x2 pixels on a retina device. That way, your 100x100 image will render twice the size on a retina device and basically normalize what the user sees.
It also provides a standard system of measurement on iOS devices because no matter how the pixel density chanes, there have always been 320x480 points on an iPhone screen and 768x1024 points on an iPad screen.*
But at the same time, you can basically disregard the documentation considering that retina devices were introduced with iOS 4 at a minimum, and I don't know of too many people still running iOS 3 on a newer iPhone. But if such a case arises, your UIImage would need to be rendered at exactly twice it's dimensions in pixels on a retina iPhone to make up for the pixel density difference.

<a name="файловая-система-ios"></a>
## Файловая система iOS
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/file_system.png">

<a name="жизненный-цикл-приложения"></a>
## Жизненный цикл приложения
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/lifecycle.png">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/app_states.png">

_Возможные состояния программы_

* Not running (не запущенное) — приложение не было запущено или его работа была прекращена
* Inactive (неактивное) — приложение работает, но не принимает события (например, когда пользователь заблокировал телефон при запущенном приложении)
* Active (активное) — нормальное состояние приложения при его работе
* Background (фоновое) — приложение больше не на дисплее, но оно все еще выполняет код
* Suspended (приостановленное) — приложение занимает память, но не выполняет код

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/app_states_2.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/app_states_3.png">

<a name="жизненный-цикл-uiviewController"></a>
## Жизненный цикл UIViewController
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/uiviewcontroller.png">

<a name="uiview"></a>
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

<a name="фреймворки"></a>
# Фреймворки
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

<a name="core-foundation"></a>
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

<a name="uikit"></a>
## UIKit
The UIKit framework provides the classes needed to construct and manage an application’s user interface for iOS. It provides an application object, event handling, drawing model, windows, views, and controls specifically designed for a touch screen interface.
The UIKit framework defines a number of functions, many of them used in graphics and drawing operations.
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/uikit.png">

<a name="cfnetwork"></a>
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

<a name="quartzcore"></a>
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

All three frameworks use OpenGL underneath because all drawing in iOS or OS X goes through OpenGL at some point. OpenGL (Open Graphics Library — открытая графическая библиотека, гра-фический API) — спецификация, определяющая независимый от языка программирования платформонезависимый программный интерфейс для написания приложений, использующих двумерную и трёхмерную компьютерную графику. Включает более 250 функций для рисования сложных трёхмерных сцен из простых примитивов. Используется при создании компьютерных игр, САПР, виртуальной реальности, визуализации в научных исследованиях. На платформе Windows конкурирует с DirectX.
