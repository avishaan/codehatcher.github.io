---
title: "MPAndroidChart to ios-charts syntax conversion" 
excerpt: "It turns out that there is enough difference in the properties each framework uses that it can be frustrating to learn how to use the ios-charts library. Here is a quick reference."
categories:
  - Programming
tags:
  - Java
  - Swift
  - iOS
  - Android
toc: true
toc_sticky: true
---
### ValueFormatter interface

**Android: Simple Formatter**

```java
// usage on axis, could also use on data object or dataset
yAxis.setValueFormatter(new MyValueFormatter());
```
**iOS: Simple Formatter**

```swift
var myValueFormatter = NSNumberFormatter()
// normal value formatter configuration
myValueFormatter.numberStyle = .PercentStyle
yAxis.valueFormatter = myValueFormatter
// usage on axis, could also use on data object or dataset
var leftAxis = chart.getAxis(ChartYAxis.AxisDependency.Left)
```
**Android: Custom Formatter**

```java
public class MyValueFormatter implements ValueFormatter {

    private DecimalFormat mFormat;

    public MyValueFormatter() {
        mFormat = new DecimalFormat("###,###,##0.0"); // use one decimal
    }

    @Override
    public String getFormattedValue(float value) {
        return mFormat.format(value) + " $"; // append a dollar-sign
    }
}
```
**iOS: Custom Formatter** (not directly equivalent to Android version above) 

```swift
  class MyValueFormatter: NSNumberFormatter {
    required init(coder aDecoder: NSCoder) {
      super.init(coder: aDecoder)
    }
    
    override init() {
      super.init()
      self.locale = NSLocale.currentLocale()
    }
    
    override func stringFromNumber(duration: NSNumber) -> String? {
      return String(format: "%01d$", duration.floatValue)
    }
    
    // Swift 1.2 or above
    static let sharedInstance = FeedDurationFormatter()
  }

```

### Y axis

**Android:**

```java
YAxis leftAxis = chart.getAxisLeft();
```
**iOS:**

```swift
var leftAxis = chart.getAxis(ChartYAxis.AxisDependency.Left)
```

####Axis properties:

**Android:**

```java
axis.setEnabled(false)
```
**iOS:**

```swift
axis.enabled = false
```

####Legend Properties:

**Android:**

```java
chart.getLegend().setEnabled(true)
```
**iOS:**

```swift
chart.legend.enabled = false
```

### Label Text Color

**Android:**

```java
XLabels label = chart.getXLabels();
label.setTextColor(getResources().getColor(android.R.color.white));
```
**iOS:**

```swift
var xAxis = chartView.xAxis
xAxis.labelTextColor = UIColor.whiteColor()
```