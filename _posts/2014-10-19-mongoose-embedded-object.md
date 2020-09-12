---
title: "Mongoose v3 Embedded Object without Explicit Subschema Declaration" 
excerpt: "A quick code example of how to embed a subdocument/collection of objects in a Mongoose model without creating a whole other explicit subdoc reference"
categories:
  - programming
tags:
  - reference
  - Mongoose
  - databases
toc: true
toc_sticky: true
---
Jump in!

```javascript
var contractSchema = new mongoose.Schema({
  questions: [{
    type: {type: 'string'},
    question: 'string',
    choices: ['string'],
    cycles: 'string'
  }],
  version: String,
  state: String
});
```

This will allow us to have a document in the following form.

```javascript
var obj = {
      questions: [
        {
          type: 'date',
          question: 'What is the start date?'
        },
        {
          type: 'date',
          question: 'What is the end date?'
        }
      ],
       version: '0.1',
       state: 'CA'
};
```

Alternatively, if you wanted to use subdocuments you could have done this.

```javascript
var contractSchema = new mongoose.Schema({
  questions: [questionSchema],
  version: String,
  state: String
});
```