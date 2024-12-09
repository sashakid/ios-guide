- [iOS](#ios)
  - [UIApplication](#uiapplication)
  - [AppDelegate](#appdelegate)
  - [UIWindow](#uiwindow)
  - [UIViewController](#uiviewcontroller)
  - [UIView](#uiview)
  - [Жизненный цикл приложения](#жизненный-цикл-приложения)
  - [Жизненный цикл UIViewController](#жизненный-цикл-uiviewcontroller)
  - [Как работает UIScrollView?](#как-работает-uiscrollview)
  - [Как работает UITableView?](#как-работает-uitableview)
  - [UIView](#uiview-1)
  - [IPhone, resolution, pixels vs points?](#iphone-resolution-pixels-vs-points)
  - [Файловая система iOS](#файловая-система-ios)
  - [Какой контент лучше хранить в Documents, а какой в Cache?](#какой-контент-лучше-хранить-в-documents-а-какой-в-cache)

<a name="ios"></a>
# iOS

## UIApplication

UIApplication — центральная точка контроля

The centralized point of control and coordination for apps running in iOS.
Every iOS app has exactly one instance of `UIApplication` (or, very rarely, a subclass of `UIApplication`). When an app launches, the system calls the `UIApplicationMain(_:_:_:_:)` function. Among its other tasks, this function creates a singleton `UIApplication` object that you access using shared. Your app’s application object handles the initial routing of incoming user events. It dispatches action messages forwarded to it by control objects (instances of the `UIControl` class) to appropriate target objects. The application object maintains a list of open windows (`UIWindow` objects), which it can use to retrieve any of the app’s `UIView` objects. The `UIApplication` class defines a delegate that conforms to the `UIApplicationDelegate` protocol and must implement some of the protocol’s methods. The application object informs the delegate of significant runtime events—for example, app launch, low-memory warnings, and app termination—giving it an opportunity to respond appropriately. Apps can cooperatively handle a resource, such as an email or an image file, through the `open(_:options:completionHandler:)` method. For example, an app that calls this method with an email `URL` causes the Mail app to launch and display the message.
The APIs in this class allow you to manage device-specific behavior. 

Use your `UIApplication` object to do the following:

- Temporarily suspend incoming touch events (`beginIgnoringInteractionEvents()`)
- Register for remote notifications (`registerForRemoteNotifications()`)
- Trigger the undo-redo UI (`applicationSupportsShakeToEdit`)
- Determine whether there is an installed app registered to handle a `URL` scheme (`canOpenURL(_:)`)
- Extend the execution of the app so that it can finish a task in the background (`beginBackgroundTask(expirationHandler:)` and `beginBackgroundTask(withName:expirationHandler:)`)
- Schedule and cancel local notifications (`scheduleLocalNotification(_:)` and `cancelLocalNotification(_:)`)
- Coordinate the reception of remote-control events (`beginReceivingRemoteControlEvents()` and `endReceivingRemoteControlEvents()`)
- Perform app-level state restoration tasks (methods in the Managing state restoration task group)

## AppDelegate

AppDelegate — шарит состояния приложения и взаимодействия с системой

A set of methods to manage shared behaviors for your app. Your app delegate object manages your app’s shared behaviors. The app delegate is effectively the root object of your app, and it works in conjunction with `UIApplication` to manage some interactions with the system. Like the `UIApplication` object, `UIKit` creates your app delegate object early in your app’s launch cycle so it’s always present.

Use your app delegate object to handle the following tasks:

- Initializing your app’s central data structures
- Configuring your app’s scenes
- Responding to notifications originating from outside the app, such as low-memory warnings, download completion notifications, and more
- Responding to events that target the app itself, and aren’t specific to your app’s scenes, views, or view controllers
- Registering for any required services at launch time, such as Apple Push Notification service

When your app’s state changes, UIKit notifies you by calling methods of the appropriate delegate object:

- In iOS 13 and later, use UISceneDelegate objects to respond to life-cycle events in a scene-based app.
- In iOS 12 and earlier, use the UIApplicationDelegate object to respond to life-cycle events.

## UIWindow

UIWindow — отвечает за UI

The backdrop for your app’s user interface and the object that dispatches events to your views. Windows work with your view controllers to handle events and to perform many other tasks that are fundamental to your app’s operation. `UIKit` handles most window-related interactions, working with other objects as needed to implement many app behaviours.

You use windows only when you need to do the following:

- Provide a main window to display your app’s content.
- Create additional windows (as needed) to display additional content.

Normally, Xcode provides your app’s main window. New iOS projects use storyboards to define the app’s views. Storyboards require the presence of a window property on the app delegate object, which the Xcode templates automatically provide. If your app doesn’t use storyboards, you must create this window yourself. Most apps need only one window, which displays the app’s content on the device’s main screen. Although you can create additional windows on the device’s main screen, extra windows are commonly used to display content on an external screen, as described in Presenting content on a connected display.

You also use UIWindow objects for a handful of other tasks:

- Setting the z-axis level of your window, which affects the visibility of the window relative to other windows.
- Showing windows and making them the target of keyboard events.
- Converting coordinate values to and from the window’s coordinate system.
- Changing the root view controller of a window.
- Changing the screen on which the window is displayed.

Windows don’t have any visual appearance of their own. Instead, a window hosts one or more views, which are managed by the window’s root view controller. You configure the root view controller in your storyboards, adding whatever views are appropriate for your interface.
You should rarely need to subclass UIWindow. The kinds of behaviors you might implement in a window can usually be implemented in a higher-level view controller more easily. One of the few times you might want to subclass is to override the `becomeKey()` or `resignKey()` methods to implement custom behaviors when a window’s key status changes. For information about how to display a window on a specific screen, see `UIScreen`.

## UIViewController

A `UIViewController` is the cornerstone of an iOS app's architecture, managing a screen's content and the interactions within it. It acts as a bridge between the app's data and the `UIViews`, handling tasks such as view hierarchy management, user interaction responses, and navigation between different screens.

## UIView

A `UIView` is the fundamental building block for creating and managing the visual content within an iOS application. It represents a rectangular area on the screen and is responsible for drawing content, handling user interactions, and managing the layout of subviews. In essence, every visual element you see in an iOS app, from buttons to labels to custom graphics, is a subclass of UIView.

- Initialization: The UIView is initialized via `init(frame:)` or `init(coder:)` if loaded from a storyboard.
- Adding to a Superview: Once created, the view can be added to a superview using `addSubview(_:)`.
- Layout: The view’s layout is determined, typically involving methods like `layoutSubviews()` where the view can adjust the frames of its subviews.
- Drawing: The `draw(_:)` method is called when the view needs to render its content, like custom graphics.
- Event Handling: The view handles user interactions such as touches using methods like `touchesBegan(_:with:)`.
- Removing from Superview: The view can be removed from its superview using `removeFromSuperview()`.
- Deinitialization: Finally, when the view is no longer needed, it’s deallocated from memory.

<a name="жизненный-цикл-приложения"></a>
## Жизненный цикл приложения
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/lifecycle.png">

| Состояние | Видимо | Принимает события | Выполняет код | 
| Not running (Приложение не запущено или завершило работу) — приложение не было запущено или его работа была прекращена | Нет | Нет | Нет |
| Inactive (Приложение в памяти, но временно не принимает пользовательские события. Это может быть подготовка к активному состоянию или переход к фоновому.) | Преимущественно | Нет | Да | 
| Active (Приложение активно работает, пользователь может с ним взаимодействовать) | Да | Да | Да | 
| Background (Приложение находится в фоновом режиме. Может выполнять фоновые задачи, такие как загрузка данных) | Нет | Нет | Да | 
| Suspended (Приложение в фоновом режиме, но не выполняет никаких задач. Система может выгрузить его для освобождения памяти) | Нет | Нет | Нет | 

| Метод делегата	| Состояние | Описание состояния |
| application(_:didFinishLaunchingWithOptions:)	| Not Running → Inactive	| Приложение запускается, но еще не готово принимать пользовательские события. Используется для инициализации. | 
| applicationWillResignActive(_:)	| Active → Inactive	| Приложение временно становится неактивным (например, из-за входящего звонка). Приостановка работы. | 
| applicationDidBecomeActive(_:)	| Inactive → Active	| Приложение становится активным и готовым к взаимодействию с пользователем. | 
| applicationDidEnterBackground(_:)	Active → Background	| Приложение уходит в фоновый режим. Выполняет фоновые задачи и освобождает ресурсы. | 
| applicationWillEnterForeground(_:)	Background → Inactive	| Приложение возвращается из фонового режима, готовясь снова стать активным. | 
| applicationWillTerminate(_:)	| Background → Not Running	| Приложение завершает работу. Система завершает его процесс, и данные должны быть сохранены. | 

<a name="жизненный-цикл-uiviewController"></a>
## Жизненный цикл UIViewController

- Initialization: The view controller is instantiated, either programmatically or from a storyboard.
- View Loading: The `loadView()` method is called, creating the view hierarchy for the view controller.
- View Did Load: The `viewDidLoad()` method is called, where you typically initialize data and setup UI elements.
- View Will Appear: The `viewWillAppear(_:)` method is called just before the view becomes visible, useful for tasks like updating the UI based on new data.
- View Did Appear: The `viewDidAppear(_:)` method is called after the view has appeared on the screen, often used for starting animations or tracking analytics.
- View Will Disappear: The `viewWillDisappear(_:)` method is invoked just before the view is hidden, useful for saving state or stopping tasks.
- View Did Disappear: The `viewDidDisappear(_:)` method is called after the view is no longer visible, allowing you to clean up resources or stop processes.
- Deinitialization: The view controller is deallocated when it’s no longer needed, cleaning up any remaining resources.
- `viewWillLayoutSubviews` gets called anytime your view controller's view has its bounds changed. This happens when the view is loaded, when a rotation event occurs, or when a child view controller has its size changed by its parent. (There are probably some other situations, too). If there is anything you need to update before that view lays itself out (and before your constraints are re-applied) you should do it here. you should generally not update constraints here, because updating constraints can cause another layout pass.
- `viewDidLayoutSubviews` is called once all of your subviews have been laid out. If you need to fine-tune that layout by manually adjusting frames, for instance, this would be the place to do it.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/uiviewcontroller.png">

<a name="uiscrollview"></a>
## Как работает UIScrollView?

`UIScrollView` is the superclass of several `UIKit` classes, including `UITableView` and `UITextView`. A scroll view is a view with an origin that’s adjustable over the content view. It clips the content to its frame, which generally (but not necessarily) coincides with that of the application’s main window. A scroll view tracks the movements of fingers, and adjusts the origin accordingly. The view that shows its content through the scroll view draws that portion of itself according to the new origin, which is pinned to an offset in the content view. The scroll view itself does no drawing except for displaying vertical and horizontal scroll indicators. The scroll view must know the size of the content view so it knows when to stop scrolling. By default, it bounces back when scrolling exceeds the bounds of the content. The object that manages the drawing of content that displays in a scroll view needs to tile the content’s subviews so that no view exceeds the size of the screen. As users scroll in the scroll view, this object adds and removes subviews as necessary. Because a scroll view has no scroll bars, it must know whether a touch signals an intent to scroll versus an intent to track a subview in the content. To make this determination, it temporarily intercepts a touch-down event by starting a timer and, before the timer fires, seeing if the touching finger makes any movement. If the timer fires without a significant change in position, the scroll view sends tracking events to the touched subview of the content view. If the user then drags their finger far enough before the timer elapses, the scroll view cancels any tracking in the subview and performs the scrolling itself. Subclasses can override the `touchesShouldBegin(_:with:in:)`, `isPagingEnabled`, and `touchesShouldCancel(in:)` methods (which the scroll view calls) to affect how the scroll view handles scrolling gestures. A scroll view also handles zooming and panning of content. As the user makes a pinch-in or pinch-out gesture, the scroll view adjusts the offset and the scale of the content. When the gesture ends, the object managing the content view updates subviews of the content as necessary. (Note that the gesture can end and a finger might still be down.) While the gesture is in progress, the scroll view doesn’t send any tracking calls to the subview. The `UIScrollView` class can have a delegate that must adopt the `UIScrollViewDelegate` protocol. For zooming and panning to work, the delegate must implement both `viewForZooming(in:)` and `scrollViewDidEndZooming(_:with:atScale:)`. In addition, the `maximumZoomScale` and `minimumZoomScale` zoom scales must be different. If you assign a value to this view’s restorationIdentifier property, it attempts to preserve its scrolling-related information between app launches. Specifically, the values of the `zoomScale`, `contentInset`, and `contentOffset` properties are preserved. During restoration, the scroll view restores these values so that the content appears scrolled to the same position as before.

`UIScrollView` has 3 main properties, known as `contentSize`, `contentOffset`, and `contentInset`.

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/content-size.jpeg">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/content-offset.jpeg">

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/content-inset.png">

<a name="как-работает-uitableview"></a>
## Как работает UITableView?
```
UITableView : UIScrollView <NSCoding> : UIView <NSCoding>

UITableViewController : UIViewController <UITableViewDelegate, UITableViewDataSource> : UIResponder <NSCoding, UIAppearanceContainer> : NSObject
```

<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tableview1.png">
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/tableview2.png">

Ячейки table view, которые больше не отображаются на экране, не выкидываются. Их можно адаптировать под повторное использование, указав идентификатор в процессе инициализации. Когда ячейка table view, отмеченная для повторного использования, пропадает с экрана, table view помещает ее в очередь для повторного использования в дальнейшем. Когда объект table view dataSource запрашивает у table view новую ячейку и указывает идентификатор, table view сначала проверяет очередь ячеек для повторного использования на предмет наличия необходимой ячейки. Если ячейка table view не была обнаружена, то table view создает новую, передавая ее затем объекту dataSource.
```objectivec
UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:CellIdentifier forIndexPath:indexPath];
```

<a name="uiview"></a>
## UIView
The UIView (UIResponder : NSObject) Объект, рисующий контент в прямоугольной области экрана и управляющий событиями, вызванными касаниями экрана пользователем. Представление также может содержать другие представления, называемые субпредставлениями. При добавлении субпредставления к представлению контейнер называется родительским представлением, а его субпредставление называется дочерним представлением. Сочетание родительского представления, его дочерних представлений (а так же их дочерних представлений, если таковые имеются) образует иерархию представлений.
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

<a name="iphone,-resolution,-pixels-vs-points"></a>
## IPhone, resolution, pixels vs points?
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/resolutions.png">
A pixel on iOS is the full resolution of the device, which means if I have an image that is 100x100 pixels in length, then the phone will render it 100x100 pixels on a standard non-retina device. However, because newer iPhones have a quadrupled pixel density, that same image will render at 100x100 pixels, but look half that size. The iOS engineers solved this a long time ago (way back in OS X with Quartz) when they introduced Core Graphics' point system. A point is a standard length equivalent to 1x1 pixels on a non-retina device, and 2x2 pixels on a retina device. That way, your 100x100 image will render twice the size on a retina device and basically normalize what the user sees.
It also provides a standard system of measurement on iOS devices because no matter how the pixel density chanes, there have always been 320x480 points on an iPhone screen and 768x1024 points on an iPad screen.*
But at the same time, you can basically disregard the documentation considering that retina devices were introduced with iOS 4 at a minimum, and I don't know of too many people still running iOS 3 on a newer iPhone. But if such a case arises, your UIImage would need to be rendered at exactly twice it's dimensions in pixels on a retina iPhone to make up for the pixel density difference.

<a name="файловая-система-ios"></a>
## Файловая система iOS
<img src="https://github.com/sashakid/ios-guide/blob/master/Images/file_system.png">

<a name="как-лучше-хранить"></a>
## Какой контент лучше хранить в Documents, а какой в Cache?

Кеш - это специальный буфер (контейнер), содержащий информацию. Эта информация может быть запрошена с наибольшей вероятностью. Соответственно, доступ к этому буферу должен быть очень быстрым, он должен быть быстрее чем доступ к сети или к данным на жестком диске. В операционной системе iOS присутствует функция кэширования, но прямого доступа к данным в кэше нету. Для получения доступа следует использовать класс `NSCache`.
- Only documents and other data that is user-generated, or that cannot otherwise be recreated by your application, should be stored in the `<Application_Home>/Documents` directory and will be automatically backed up by iCloud.
- Data that can be downloaded again or regenerated should be stored in the `<Application_Home>/Library/Caches` directory. Examples of files you should put in the Caches directory include database cache files and downloadable content, such as that used by magazine, newspaper, and map applications.
- Data that is used only temporarily should be stored in the `<Application_Home>/tmp` directory. Although these files are not backed up to iCloud, remember to delete those files when you are done with them so that they do not continue to consume space on the user’s device.
- Use the "do not back up" attribute for specifying files that should remain on device, even in low storage situations. Use this attribute with data that can be recreated but needs to persist even in low storage situations for proper functioning of your app or because customers expect it to be available during offline use. This attribute works on marked files regardless of what directory they are in, including the Documents directory. These files will not be purged and will not be included in the user's iCloud or iTunes backup. Because these files do use on-device storage space, your app is responsible for monitoring and purging these files periodically.
