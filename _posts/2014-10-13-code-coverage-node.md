---
title: "Continuous Integration with Code Coverage in Node.js" 
excerpt: "Continuous integration and test driven development are important strategies for any engineering team that wants to be efficient."
categories:
  - engineering execution
tags:
  - Node.js
  - CI/CD
  - TDD
toc: true
toc_sticky: true
---
## Intro

It can be difficult to get an engineering team in sync and aligned for CI, code coverage, and TDD. Without a leader who has experienced the pitfalls of not implementing those methodologies the benefits to a team may not be clear.

### Example Implementation

I am going to talk about one very specific item in this article since it barely exists anywhere on the internet. How to run **both** your integration tests and unit tests in such a way that you can actually see the whole code coverage.
I am **not** going to tell you to download another plugin, I want you to see how this will actually work.
I am **not** going to tell you how to install jasmine-node, nor how to make jasmine assertions, nor how to install mocha, nor convince you that you need unit tests, nor convince you that you need grunt, nor anything else.

#### Prerequisites
* Have [jasmine-node](https://github.com/mhevery/jasmine-node) installed either globally or locally. If locally you need to run it in this manner `./node_modules/jasmine-node/bin`
* Have [istanbul](https://www.npmjs.org/package/istanbul) installed either globally or locally.
* Have your [integration tests](http://en.wikipedia.org/wiki/Integration_testing) written in [jasmine](http://jasmine.github.io/).
* Have your [unit tests](http://en.wikipedia.org/wiki/Unit_testing) written in jasmine.
* Be able to run your jasmine unit and integration tests successfully on their own without istanbul in the picture. Running something like  `./node_modules/jasmine-node/bin/jasmine-node tests/runner_spec.js --captureExceptions --verbose` 
You should get output like this:![Jasmine Test Example] (https://silvrback.s3.amazonaws.com/uploads/c5ebfeed-aab2-4900-a571-649b59e1f1c8/jasminetestexample_large.png)


#### The Goodies
1. Start your node app using istanbul cover. For example if you usually do `node app.js` you will now do `./node_modules/istanbul/lib/cli.js cover --report none app.js` This will check the coverage of the integration tests on your node app and not write the reports right away (`--report none`)
2. Run your tests using istanbul. If you normally run your jasmine tests by doing the following, `./node_modules/jasmine-node/bin/jasmine-node ./tests/runner_spec.js --verbose --captureExceptions` you will instead run it like this `./node_modules/istanbul/lib/cli.js cover --report none --dir coverage/unit ./node_modules/jasmine-node/bin/jasmine-node -- ./tests/runner_spec.js --verbose --captureExceptions`
Notice how I have picked an alternate directory for my unit tests with the '--dir' option. I want them to go into the `./coverage/unit` folder. Also, any options that you want to pass to jasmine-node you will need to place after `--`. 
3. End those processes, you should see some coverage information as you do so.
![Code Coverage Process End](/assets/posts/migrated-codehatcher-blog/codecoverageunittests_large.png)
4. Once all your tests have run, type the following `./node_modules/istanbul/lib/cli.js report`
5. Go to your `./coverage/lcov-report/index.html` and check out your coverage levels. Not bad!!! 

![Code Coverage Full](/assets/posts/migrated-codehatcher-blog/codecoveragefullinfo_large.png)