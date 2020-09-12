---
title: "MongoDB SSH access on remote Meteor deployment" 
excerpt: "Access the MongoDB instance on your MUP (Meteor UP) deployment using a GUI explorer"
categories:
  - programming
tags:
  - Meteor.js
  - Javascript
  - MongoDB
  - databases
  - DevOps
  - programming
toc: true
toc_sticky: true
---
There comes a time when you need to access the MongoDB database associated with your remote MUP (Meteor Up) deployment. According to [their docs](https://github.com/arunoda/meteor-up/tree/v0.11.3#accessing-the-database), the only way you can do this is to SSH in and access it from there. That's fine (and technically accurate) except that leaves you only with a console interface via `meteor mongo` which isn't always great. Here is an alternate method to get access to that database using 3T.

It's not difficult to do and makes sense once you have done it one time. However, there is little documentation on how to implement it.

### 1) Download a MongoDB GUI
Almost any will work as long as they allow you to access a database via an SSH tunnel. Having used RoboMongo, MongoHub, and MongoChef I absolutely recommend 3T [MongoChef](http://3t.io/mongochef/).

### 2) Configure the SSH tunnel settings
Enter in the details for whatever auth scheme you have setup.
![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/Screen_Shot_2015-12-20_at_19_06_56_large.png)


### 2) Configure the server settings
The main thing to remember is you want to configure server settings from the perspective of being connected via SSH. (That means everything, once connected via SSH will look as if it's local).
![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/Screen%20Shot%202015-12-20%20at%2019.26.43_large.png)

That's it! Now you can connect to your remote Meteor Up Mongo database!
![Silvrback blog image](/assets/posts/migrated-codehatcher-blog/giphy_large.gif){: .align-center}
