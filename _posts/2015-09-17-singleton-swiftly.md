---
title: "Singleton Swiftly" 
excerpt: "Two design patterns which can be used to implement Singletons in Swift."
categories:
  - Programming
tags:
  - Reference
  - Swift
  - Programming
  - iOS
toc: true
toc_sticky: true
---
The Singleton pattern makes sure only one instance of a given class exists. Usually, that single instance is lazily loaded when it is needed. There are a bunch of examples of this built into iOS such as:

```swift
NSUserDefaults.standardUserDefaults()
UIApplication.sharedApplication()
```

I'm not going to tell you when you might need this pattern, there is a bunch of information out there on this. But I want to show you how to do it in Swift and avoid the ugly Obj-C dispatch_once version you see everywhere.

### Singleton for Swift v1.2+
This is an example for Swift greater than v1.2

```swift
class MyClass {
  static let sharedInstance = MyClass()
  init() {
    println("We did it!")
  }
}
```

### Singleton for Swift < v1.2
This is an example for Swift less than v1.2. I have to be honest, if you are not using at least Swift v1.2 by the time this comes around, you need to switch over. You are missing out on a lot of good stuff.

```swift
class MyClass {
  
  class var sharedInstance: MyClass {
    struct Static {
      static let instance: MyClass = MyClass()
    }
    return Static.instance
  }
  
}
```