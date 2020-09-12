---
title: "Bluebird Promises with Mongoose for MongoDB" 
excerpt: "Quick examples of using bluebird with mongoose in node. I just want to show you a couple common use cases to help you recognize how to use promises."
categories:
  - programming
tags:
  - programming
  - Mongoose.js
  - MongoDB
  - databases
  - Bluebird.js
  - Javascript
toc: true
toc_sticky: true
---
We are going to take common Mongoose use cases for finding and creating documents and going to use Bluebird (or more generally, any promise library that follows [Promises/A+](https://promisesaplus.com/implementations)) to migrate from the typical callback method to promises.

There are many sites showing simple examples of promises but sometimes you just: 

* need an example specific to what you are doing to understand it
* need to just get going in it without fully understanding it

I assume you have a basic understanding of Bluebird promises and an intermediate understanding of Mongoose otherwise these examples won't make sense. 
I also assume you are convinced you need/want/should use promises instead of callbacks for Mongoose in Node. I am not here to convince you that you need to use promises.

## Save a document
Create a new document (review) in the database
### Callback Style

```javascript
   Review
   .create(review, function(err, savedReview){
    if (!err && savedReview){
      // we created the savedReview successfully
      res.status(200).send(savedReview);
    } else {
      res.status(500).send(err);
    }
  });
```
### Promise Style

```javascript
  var Promise = require('bluebird');
  Promise.promisifyAll(Review);

  Review
  .createReviewAsync(review)
  .then(function(savedReview){
    res.status(200).send(savedReview);
  })
  .catch(function(err){
    res.status(500).send(err);
  });
```



# Find document using mPromise (Mongoose Promise)
Find a user in the database
### Callback style

```javascript
User
.findOne({username:username})
.exec(function(err, user){
  if (err){
    res.status(500).send(err);
  } else {
    res.status(200).send(user);
  }
});

```

### Promise style
```javascript
  var Promise = require('bluebird');
  Promise.resolve(User.findOne({username:username}).exec())
  .then(function(user){
    res.status(200).send(user);
  })
  .then(undefined, function(err){
    res.status(500).send(err);
  });
```