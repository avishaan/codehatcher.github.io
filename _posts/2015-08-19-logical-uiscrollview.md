---
title: "Faster Logical UIScrollView in Swift" 
excerpt: "UIScrollView is something that can be very confusing because it uses constraints in a way that they aren't normally used. Because of this there is so much confusion."
categories:
  - programming
tags:
  - Swift
  - programming
toc: true
toc_sticky: true
---
Implementing a UIScrollView is actually really easy when you know/do three fundamental things. There is a video I uploaded that walks you through this process [UIScrollView Video](https://youtu.be/dtcrlRBYTWU)  but incase you forget you can use the following as a reference.

1. Use a View (let's call it, ContentView) in your ScrollView to keep the layout of your buttons easier. But putting all your controls in your ContentView which is inside your ScrollView, you will make everything much easier.

![Silvrback blog image](https://silvrback.s3.amazonaws.com/uploads/bef75bfc-50ce-4cc4-8c58-c10f05440d72/Screen%20Region%202015-08-19%20at%2018.41.14_large.png)

2. Your ContentView needs to have constraints to your ScrollView. These constraints will not change the size of your ContentView but will be used by the ScrollView to calculate the boundaries of your ContentView. Apple has purposely repurposed this constraint so that you can do this in the Storyboard. 

![Silvrback blog image](https://silvrback.s3.amazonaws.com/uploads/50c5e582-0a24-4d29-acea-37086b439fd3/Screen%20Region%202015-08-19%20at%2018.40.07_large.png)

3. Your ContentView can't depend on the ScrollView for the size (partially because of point #2). But it could use constraints on the highest level View or but using it's own content.