---
title: "Transliteration of Promises to Callbacks" 
excerpt: "Promises seem like an amazing way to take advantage of non-blocking io in a very readable way"
categories:
  - JS
tags:
  - Reference
  - Javascript
  - Bluebird.js
  - Node.js
  - Mongoose.js
  - Programming
toc: true
toc_sticky: true
---
Sometimes when you see enough examples, things just click. I have multiple examples that show you an implementation (before) and then an alternate implementation using promises (after). 
*Note:* Keep in mind that different libraries have different implementations but these should all still be relevant;

Here are some before and afters

---
before

```javascript
getUser('washington', function(err, user){
  if (!err) {
    // do something with user
  } else {
    // handle the error
  }
});
```
after

```javascript
getUser('washington').then(function onFulfilled (user){
  // do something with user
}, function onRejected (err){
  // handle the error
});

```
---
before

```javascript
var user = getUser('washington');
var name = user.name;
```
after

```javascript
getUser('washington').then(function(user){
  return user.name
});

```
---
before

```javascript
var user = getUser('washington');
if (!user) {
  throw new Error('no user!');
}
var name = user.name;
```
after

```javascript
getUser('washington').then(function (user){
  if (!user){
    throw new Error('no user!');
  }
  return user.name;
});

```
---
before

```javascript
try {
  deliverTweetTo(tweet, 'washington');
} catch (error) {
  handleError(error);
}
```
after

```javascript
deliverTweetTo(tweet, 'washington')
.then(undefined, handleError);
```
---
before (callbacks)

```javascript
getUser('washington', function(user){
  getNewTweets(user, function (tweets){
    updatePage(tweets);
  });
});
```
after (promises)

```javascript
getUser('washington')
.then(getNewTweets)
.then(updatePage);
```
---
before

```javascript
getUser('washington', function(err, user){
  if (err){
    handleError(err);
  } else {
    getNewTweets(user, function(err, tweets){
      if (err){
        handleError(err);
      } else {
        updatePage(tweets, function(err){
          if (err){
            handleError(err);
          }
        });
      }
    });
  }
});

```
after

```javascript
getUser('washington')
.then(getNewTweets)
.then(updatePage)
.then(undefined, handleError);

```

Another example with Mongoose

```javascript
userSchema.statics.checkAuthentication = function(options, cb) {
  var username = options.username;
  var password = options.password;

  var Promise = require('bluebird');
  // bind to have an object along the chain of promises
  Promise.resolve(User.findOne({username:username}).exec()).bind({})
  .then(function(user){
    this.user = user;
    // call comparePassword with user as the context of this vs global
    return Promise.promisify(user.comparePassword).call(user, password);
  })
  .then(function(match){
    // check password match
    if (match) {
      cb(null, this.user);
    } else {
      throw new Error("invalid username or password");
    }
  })
  .then(undefined, function(err){
    cb(err);
  });
};
```
