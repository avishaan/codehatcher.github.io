---
title: "Dealing with Complex @IBDesignable" 
excerpt: "When your @IBDesignable is either too complex or requires data not available when previewing in the interface builder, here is how you deal with those errors."
categories:
  - programming
tags:
  - programming
  - iOS
  - Xcode
  - Objective-C
toc: true
toc_sticky: true
---
In situation where our `@IBDesignable` is too complex to complete in under 200ms we need a way to still get it's benefits without the complex errors that it throws. You may argue that "well my code still builds just fine". Sure, but now you have a bunch of errors and when you actually get one, you may have trouble debugging. Here is a easy solution.

In my example I was generating a thumbnail from a video and overlaying that on top of the player as a preview image of the video. In my interface builder, apparently this code was taking too long to execute and giving me the following errors. 

![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/Screen%20Region%202015-09-26%20at%2018.41.24_large.png)

It's important to note that none of those errors stopped me from building the project. But it definitely made it difficult to see when I had new errors popping up. The solution was actually simple. Have certain code run in the app and have different code run in the Interface Builder (IB). Here it is below.

```ObjectiveC
  @IBInspectable var videoTime: Int32 = 0 {
    didSet {
      #if !TARGET_INTERFACE_BUILDER
        // this code will run in the app itself
        thumbnailOfVideo(time: videoTime)
        #else
        // this code will execute only in IB
      #endif

    }
  }
```