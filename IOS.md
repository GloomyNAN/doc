---
title:  UIKit
date: 
tags:
---

## About App Development with UIKit

* `UIDocument` object for organizing the data structures that belong in a disk-based file
* The `Swift Standard Library` provides many of the same types available in the Foundation framework
* `UIKit` defines the `UIView` class
* The `UIApplication` object runs your app’s main event loop and manages your app’s overall life cycle.

## App Structure

### Core App

The execution states of a UIKit app
![The execution states of a UIKit app](IOS/1.png)

> p1:When your app transitions from one state to another, `UIKit` notifies your app delegate object—an object that conforms to the `UIApplicationDelegate` protocol.

### Responding to a location event at launch time

```swift
class AppDelegate: UIResponder, UIApplicationDelegate, 
               CLLocationManagerDelegate {
    
   let locationManager = CLLocationManager()
   func application(_ application: UIApplication,
              didFinishLaunchingWithOptions launchOptions:
              [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
       
      // If launched because of new location data,
      //  start the visits service right away.
      if let keys = launchOptions?.keys {
         if keys.contains(.location) {
            locationManager.delegate = self
            locationManager.startMonitoringVisits()
         }
      }
       
      return true
   }
   // other methods…
}
```

### Getting the location of app-specific directories


```swift
let appSupportURL = FileManager.default.urls(for: 
      .applicationSupportDirectory, in: .userDomainMask)

let cachesURL = FileManager.default.urls(for: 
      .cachesDirectory, in: .userDomainMask)
```

### resourse

[About Info.plist Keys and Values](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009247)
[我是如何学习IOS的-简书](https://www.jianshu.com/p/9a502d58dc1a)

