---
title: "Custom NSNumberFormatter" 
excerpt: "How to create and class a 100% customized NSNumberFormatter in Swift. Useful when frameworks (*cough* 'ios-charts') require a NSNumberFormatter for value formatting."
categories:
  - programming
tags:
  - programming
  - Swift
toc: true
toc_sticky: true
---
When using an API/Framework you may need to provide a `NSNumberFormatter`. 

```swift
iosChart.valueFormatter = MyCustomNSNumberFormatter
```

But what happens if one of the options NSNumberFormatter has doesn't have the options you want and you need something highly customized. And when I say custom, I don't mean deciding if you need a currency style.

```swift
NSNumberFormatter().numberStyle = NSNumberFormatterStyle.CurrencyStyle
```

I mean if you need something highly customized then you need to create a subclass and override the `stringFromNumber` method. Here is an example of how I needed to turn the number of seconds into the format `mm:ss` but using a custom NSNumberFormatter ('ios-charts' required this).

```swift
class FeedDurationFormatter: NSNumberFormatter {
  required init(coder aDecoder: NSCoder) {
    super.init(coder: aDecoder)
  }
  
  override init() {
    super.init()
    self.locale = NSLocale.currentLocale()
  }
  
  override func stringFromNumber(duration: NSNumber) -> String? {
    let duration = duration.floatValue
    let minutes = floor(duration / 60)
    let seconds = duration % 60.0
    
    // time string, we don't want the decimals
    let timeString = String(format: "%01dm %01ds", Int(minutes), Int(seconds))
    
    return timeString
  }
  
  // Swift 1.2 or above
  static let sharedInstance = FeedDurationFormatter()
}

println(FeedDurationFormatter.sharedInstance.stringFromNumber(10))
```

