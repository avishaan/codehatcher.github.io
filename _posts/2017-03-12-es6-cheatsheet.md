---
title: "ECMAScript 6 Cheatsheet" 
excerpt: "Quick little cheatsheet to get you through ES6"
categories:
  - cheatsheet
tags:
  - Reference
  - ECMAScript 6
  - Javascript
toc: true
toc_sticky: true
---
This won't be close to exhaustive, it's more geared toward items I want to focus on. In general, I won't include items that would be picked up by a linter. You have a linter and it will tell you not to do this, so I am not going to tell you as well.

### var vs let
- var is function scoped, ONLY
- let is blocked scoped
- var is partially accessible before being defined (temporal dead zone)
- accessing let before being defined causes reference error

```js
var age = 10;
if ( age > 12 ) {
  let dogYears = age * 7;
  var dogEars = 2;
}
console.log(dogYears); // will work
console.log(dogEars); // will NOT work

console.log(pizza); // 'uncaught referenceError: pizza not defined'
console.log(hamburger); // logs: 'undefined'
let pizza = "Supreme";
var hamburger = "Big Mac";
```

### const
- doesn't change
- the entire object can't change
- properties of an object can change

```js
const person = {
  name: 'Avi',
  age: 30,
}
person = { name: 'Shaan' }; // NO can do
person.name = 'Shaan'; // can do
```

### block scope real world
Instead of using IIFE you can just block scope with let

```js
(function(){
  var test = 'test';
})();
console.log(test); // test not in global scope, will NOT log
{
  let test = 'test';
}
console.log(test); // test also not in global scope, will NOT log
```
### fat arrow

```js
  const fullNames = names.map(function(name){
    return (name + 'bos');
  });

  // fat arrow equivalent
  const fullNames2 = names.map((name) => {
    return (name + ' bos');
  });

  // if only one arg, don't need parens
  const fullNames3 = names.map(name => {
    return (name + ' bos');
  });

  // implicit return single liner
  const fullNames4 = names.map(name => (name + ' bos'));
```

### this scope with arrow functions

- this with arrow 'inherits' this from the parent scope
- this with 'normal' function uses window as scope

#### wrong
```js
    box.addEventListener('click',() => {
      console.log(this); // output: window
      this.classList.toggle('opening'); // won't work since this is window from parent context
      setTimeout(function() {
      console.log(this); // output: window
        this.classList.toggle('open'); // won't work since this is window since no context was set
      }, 500);
    });
```

#### right
```js
    box.addEventListener('click', function() {
      console.log(this); // output: div
      this.classList.toggle('opening');
      setTimeout(() => {
      console.log(this); // output: div
        this.classList.toggle('open');
      }, 500);
    });
```

### default value for function arguments/parameters

```js
    function calculateBill(total, tax = 0.13, tip = 0.15) {
      return total + (total * tax) + (total * tip);
    }
```


