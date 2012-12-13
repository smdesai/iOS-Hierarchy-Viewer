iOS-Hierarchy-Viewer (with new Core Data viewer)
====================

iOS Hierarchy Viewer allows developers to debug their user interfaces. If there are problems with layout calculations, it will catch them by giving a real time preview of the UIViews hierarchy.

**iOS Hierarchy Viewer (since 1.4.6 version) gives preview of data if you use Core Data API in your project. See 'Instruction' section to start with it.**

![](http://github.com/smdesai/OS-Hierarchy-Viewer/Images/view.png)

Features
====================

+ the client is implemented in HTML/JS/CSS. Additional software is not required
+ preview of device/simulator screen. Can be scaled and/or rotated on demand
+ debug frames shows the exact UIViews frames
+ property list shows obj-c properties and their values for selected UIView

Installation
====================

+ download the statiic library and header file from here: [Lib]
+ add these files to your project (drag&drop into into your Xcode project)
+ make sure that you have added “-ObjC -all_load” to “other linker flags” (click at project root element, select “Build settings” tab, search for “other linker flags”)
+ if you already have JSONKit.m in your project, please remove it to avoid linker conflicts
+ launch Hierarchy Viewer in your code by calling [iOSHierarchyViewer start];. The best place for it is AppDelegate::applicationDidBecomeActive callback
+ find or get from the logs device/simulator IP address and go to ‘http://[ip_address]:9449′ address. Simulator IP address is 127.0.0.1

```objc
- (void)applicationDidBecomeActive:(UIApplication *)application
{
    // your stuff
    [iOSHierarchyViewer start];    
}
```

+ if you would like to see data from Core Data API go to 'http://[ip_address]:9449/core.html' and add NSManagedContext object to iOSHierarchyViewer library

```objc
- (void)applicationDidBecomeActive:(UIApplication *)application
{
    // your stuff
    
    setup persistent store coordinator for _managedObjectContext
    
    [iOSHierarchyViewer addContext:_managedObjectContext name:@"Root managed context"];    
}
```

You can always look at sample project, there is only 1 line of code needed for iOSHierarchyViewer to work.

Changelog:
====================

Version 1.3:
+ fixed crashes at UITextView:
+ some properties can be read only from UI thread
+ some properties ( like 'autocapitalizationType' ) are not KVC compliant.

Version 1.4:
+ Accesibility labels are used when set, making it easier to read hierarchy
+ All scaning now takes place on main thread.

Roadmap:
====================
Version 1.5:
- Coloring non-opaque and misaligned view's similar to CoreAnimation instruments
- Selected views from HTML side highlight in tree navigator

Version 1.6:
- Support for cocos2d nodes visualisation and debugging

Contributing:
====================
Did you find a bug ? Do you have feature request ? Do you want to merge a feature ?
Send us a pull request or add an issue in the tracker!

[LIB]: https://github.com/smdesai/iOS-Hierarchy-Viewer/Lib