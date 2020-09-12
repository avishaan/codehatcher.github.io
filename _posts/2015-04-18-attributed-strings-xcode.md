---
title: "Attributed Strings in Xcode with Custom Font" 
excerpt: "Attributed strings build in the storyboard editor which use a custom font does not render correctly. Here are the steps to get around it"
categories:
  - programming
tags:
  - programming
  - Xcode
  - Objective-C
toc: true
toc_sticky: true
---
When setting attributed text in Xcode storyboard editor you will find that any custom font selected will show up in the storyboard, but not when run in the simulator.

### Problem
![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/simulatorvsxcode_large.jpg)

Online people talk about making sure you add your custom fonts to the plist or to make sure you aren't picking a font style that the font doesn't actually support. These may be the cause of your problem but another fix is as follows.

```swift

// make label's set attr string to a mutable so we can add attributes on
var attrString = NSMutableAttributedString(attributedString: rangeChartLabel.attributedText)
    
// add font attribute
attrString.addAttribute(NSFontAttributeName, value: UIFont(name:kOmnesFontSemiBold, size: 15)!, range: NSMakeRange(0, attrString.length))

// update label    
rangeChartLabel.attributedText = attrString

```

### Outcome

With this your simulator will have the custom updated font.
