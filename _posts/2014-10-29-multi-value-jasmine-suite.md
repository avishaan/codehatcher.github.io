---
title: "Multi Valued Single Jasmine Automated Test Suite" 
excerpt: "An alternative to npm libraries like 'jasmine-where' and full blown data provider pattern. Anything that gives us a boost for our TDD & CI/CD pipeline is worth considering"
categories:
  - engineering execution
tags:
  - engineering execution
  - TDD
  - CI/CD
toc: true
toc_sticky: true
---
## Reminder
I can't stress enough how important TDD and CI/CD is when it comes to having an efficient engineering team. We scoff at hand ledgers in the era of Excel yet we (business included) still **over**use manual QA.
Forget about nonsense like this to compare two Mongoose Ids

## Jump-in
Often, we want to reuse the test suites and encompassing assertions when writing out test cases but want to input different values. Currently, Jasmine doesn't provide any kind of pattern for doing so. If you don't want to use another 3rd party library, such as 'jasmine-where', there is a relatively easy way to do so below. In both examples, it will go through the array of objects expecting the answer from the calculation to equal the answer in the array of values.

The first way is if we are doing things synchronously.

```javascript
describe("A calculator", function() {
  it("should square correctly", function() {
    [
      { number: 2, answer: 4},
      { number: 3, answer: 9},
      { number: 4, answer: 16}
    ].forEach(function(problem, index, array){
      // we will pretend to calculate with our fnc here
      var calcAnswer = problem.number*problem.number;
      expect(calcAnswer).toEqual(problem.answer);
    });
  });
});
```

The second way is if we are doing things asynchronously which I have just pretended with the good ole' setTimeout function.

```javascript
describe("A calculator", function() {
  it("should square correctly", function(done) {
    [
      { number: 2, answer: 4},
      { number: 3, answer: 9},
      { number: 4, answer: 16}
    ].forEach(function(problem, index, array){
      // we will pretend to calculate with our fnc here
      setTimeout(function(){
        var calcAnswer = problem.number*problem.number;
        expect(calcAnswer).toEqual(problem.answer);
        // once we have finished checking the values, we can call done
        if (index === (array.length-1)){
          done();
        }
      },100);
    });
  });
});
```

## Code-Examples
The gists are here in case you are interested. 
### Synchronous
<script src="https://gist.github.com/codeHatcher/cdd87ef1ce1863929be1.js"></script>

### Asynchronous
<script src="https://gist.github.com/codeHatcher/fe2e7cf732542a7ac9fe.js"></script>

[Sync Example on Github](https://gist.github.com/codeHatcher/cdd87ef1ce1863929be1)

[Async Example on Github](https://gist.github.com/codeHatcher/fe2e7cf732542a7ac9fe)