---
title: "Comparing Mongoose Object Ids" 
excerpt: "Forget about finding a deeply nested id property that you have to call the .toString() method on in order to compare."
categories:
  - programming
tags:
  - reference
  - Mongoose.js
  - databases
toc: true
toc_sticky: true
---
Forget about nonsense like this in order to compare two Mongoose Ids

```javascript
if (val.user.toString() === submissionDoc.owner._id.toString()){
	//do stuff
}
```

Use a built in Mongoose function instead!

```javascript
if (val.user.equals(submissionDoc.owner._id)){
	//do stuff
}
```

Or don't, be convoluted, but before you decide on that check the **Zen of Python** and see if you can be swayed ;)