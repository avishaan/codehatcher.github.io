---
title: "Use 'type' as a Property Name in a Mongoose Doc" 
excerpt: "The syntax is a little different since 'type' already has a meaning in a Mongoose schema."
categories:
  - programming
tags:
  - Reference
  - Mongoose
  - databases
toc: true
toc_sticky: true
---
Jump in!

This will **not** work.

```javascript
var contractSchema = new mongoose.Schema({
  questions: [{
    type: {type: 'string'},
    question: 'string'
  }],
  version: String,
  state: String
});
```

This will work.

```javascript
var contractSchema = new mongoose.Schema({
  questions: [{
    type: 'string'
    question: 'string'
  }],
  version: String,
  state: String
});
```

Glad that's settled :)