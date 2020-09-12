---
title: "Method Chaining in JS Style Opinion" 
excerpt: "A more definitive answer to the indent style of chaining multiple methods in Javascript for easier readability."
categories:
  - programming
tags:
  - Javascript
  - opinion
toc: true
toc_sticky: true
---

There are primarily three ways to chain Javascript methods.

### Method 1: Almost Unbearable
```javascript
superagent.post(domain + "/challenges/" + challenge1._id + "/submissions").type('form').attach("image", "./tests/specs/images/onepixel.png").field("owner", user2._id).end(function(err, res){
  done();
});
```

We all know Method 1 is not acceptable in this situation. But what about the following?

### Method 2: Much Better
```javascript
superagent
  .post(domain + "/challenges/" + challenge1._id + "/submissions")
  .type('form')
  .attach("image", "./tests/specs/images/onepixel.png")
  .field("owner", user2._id)
  .end(function(err, res){
    done();
  });
```

### Method 3: Arguably, The Best
```javascript
superagent
.post(domain + "/challenges/" + challenge1._id + "/submissions")
.type('form')
.attach("image", "./tests/specs/images/onepixel.png")
.field("owner", user2._id)
.end(function(err, res){
  done();
});
```

Both #2 & #3 above are huge improvements over #1. Now if you don't already have an opinion on which one is better and you flip flop around between #2 and #3. Allow me to persuade you to choose #3. You see in some contexts #3 is better as it's alignment in another function allows you to quickly skim a document and see where something has gone awry. Something that #2 doesn't make easy. Look at these.

### Method 2: Seems worse now
```javascript
function(cb){
  //have nerdy submit into the challenge
  describe("A Submission", function(){
    it("can be submitted by a user", function(done){
      superagent
        .post(domain + "/challenges/" + challenge1._id + "/submissions")
        .type('form')
        .attach("image", "./tests/specs/images/onepixel.png")
        .field("owner", user2._id)
        .end(function(err, res){
          cb(null);
          done();
        });
    });
  });
},
```
### Method 3: Seems better now
```javascript
function(cb){
  //have nerdy submit into the challenge
  describe("A Submission", function(){
    it("can be submitted by a user", function(done){
      superagent
      .post(domain + "/challenges/" + challenge1._id + "/submissions")
      .type('form')
      .attach("image", "./tests/specs/images/onepixel.png")
      .field("owner", user2._id)
      .end(function(err, res){
        cb(null);
        done();
      });
    });
  });
},
```

Anyone familiar with the callback hell and nested functions that can be Javascript, the benefit of using method #3 becomes clear. Scanning that code in #2 some brains may need an extra second to process which could cause something to be looked over.

So if you already don't have an opinion on which style to use. Definitely consider #3