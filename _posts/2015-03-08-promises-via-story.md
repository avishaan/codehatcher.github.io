---
title: "Learning Programming Promises via a Story" 
excerpt: "Learn the basic idea of promises in Javascript by listening to this story. The code examples may be JS but the story is language agnostic"
categories:
  - programming
tags:
  - reference
  - When.js
  - Javascript
toc: true
toc_sticky: true
---
### What is this about?
Any language/concept/idea is easier to learn when you come up with a relatable real life situation or metaphor. Programming is no different. I'll use the next few minutes to build up a simple promise example that you can run and play with while telling a memorable and relatable story.
My purpose here is to get you familiar enough with a concept via a memorable story while also giving you a runnable example that you can tinker with. This will help you understand the practical aspect of the subject. I am not talking about corner cases, details, why you should use it, performance issues nor the nitty gritty. Once you know the concept and the basics you will be able to do research in order to learn the details on your own.
I assume you understand the concepts of synchronous code, asynchronous code, and callbacks. I also assume you have decided you want to learn promises but are having trouble getting started because you are not able to conceptualize it in such a way where you can write code describing a story.
Enough talk, let's jump in. (if you want to run some of the code below you may need to install [when.js](https://github.com/cujojs/when) from npm via `npm install when`)

### Synchronous Story

Let's say you go to your neighbor's house to borrow money to buy your wife flowers for her birthday. You walk over to Mark's house and ask if you can borrow $50. Mark tells you, "sure no problem but I have to go look for it", at which point he disappears into his house. You sit there waiting at his door and he emerges 20 minutes later with the money. Grateful, you tell him thanks and walk away meanwhile thinking to yourself that you could have started picking out the flowers if you didn't have to wait at Mark's door. "Oh well", you think and walk home to select a flower arrangement online before going to the store.
The problem here is obvious, you had to wait for those 20 minutes and do nothing while Mark looked for the money. Few programmers would say that synchronous code in Javascript is a good idea during a blocking event.

### Callback Story

Next year you need to borrow money from Mark again to buy your wife flowers for her birthday. You walk over to Mark's house and ask if you can borrow $50. Before he disappears into his house to look you say, "hey can you give me a ring and call me back to your house when you find the money?". Mark is fine with that. You go home to start selecting the flowers you want to get your wife. About 20 minutes later you get a phone call from Mark saying that he found the money and that you can come over to grab it. 
You think to yourself how happy you are to have gotten most of your shopping done while he was looking for the money. Too bad you have to waste time and resources walking over to grab the money.
If the above was in code form, it may have looked something like this.

```javascript
var Mark = {
  findMoney: function(cb) {
    // mark looks around for money
    setTimeout(function(){
      // once mark finds it, he gives it to you
      cb("$50");
    }, 20);
  }
};
var You = {
  askMoney: function() {
    // you ask mark to find money
    Mark.findMoney(function(money){
      // with the money you go to the store and buy flowers
      console.log("Mark lends you:", money);
    });
  },
};

You.askMoney();
// you search for flowers after asking for money but before getting money
console.log("You search for flowers");
```

### Promises Story

A year later, you again need to borrow money from Mark to buy your wife flowers for her birthday (good thing he is a great friend). You walk over to Mark's house and ask if you can borrow $50. Always happy to help, he says that he will PayPal you. You think he is annoyed with you so you tell him it's ok if he doesn't have the money. Mark tells you, "It's no problem and I promise the money will be in your account within the next few minutes".
You run home and pick the flowers you want to get. While finishing adding the flowers to your online cart you see an email alert, "$50 received from Mark into your PayPal account", at which point you quickly checkout online. You think to yourself, that was amazing and I didn't  to have Mark call me back this time nor did I have to walk back over.
If the above was in code form it may have looked something like this.

```javascript
var when = require('when');

var Mark = {
  findMoneyPromise: function() {
    var deferred = when.defer();
    // mark looks around for money
    setTimeout(function(){
      var found = true;
      // in this case mark always finds it
      if (found){
        console.log("Mark PayPals you the money");
        deferred.resolve("$50");
      } else {
        console.log("Mark cloudn't find it, send you his apologies");
        deferred.reject("sorry");
      }
    }, 20);
    // return promise
    return deferred.promise;
  }
};
var You = {
  askMoney: function() {
    // you ask mark to find money
    Mark.findMoneyPromise().then(
      function onFulfilled (money){
        console.log("You buy", money, "worth of flowers");
      },
      function onRejected (message){
        console.log("Mark apologized:", message);
      });
  }
};

You.askMoney();
// you search for flowers after asking for money but before getting money
console.log("You search for flowers");

```
You can see how it reacts in the case that Mark can't find the money by setting 
`var found = false;` In that case you can see you will reject the promise and then run onRejected.

### Next Steps
I hope you have a better idea of how to mentally conceptualize promises. You can do other awesome things like resolving promises with another promise. For instance using the same story example, imagine if Mark couldn't find the money and instead asked Bob to give you the money directly. That's resolving a promise with a promise but I think story time is over for now.

[Check out the actual spec.](https://promisesaplus.com/)

[Check out an alternate promise library.](https://github.com/petkaantonov/bluebird)

[Build your own very simple promise library.](http://modernjavascript.blogspot.com/2013/08/promisesa-understanding-by-doing.html)