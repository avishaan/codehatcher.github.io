---
title: "Engineering Team Principles" 
excerpt: "The rules that should govern the actions of an engineering team"
categories:
  - Management
tags:
  - Engineering Management
toc: true
toc_sticky: true
---
## Introduction
While leading multiple engineering teams there are many patterns that emerge. I can see the reason for some of these even based in my own background as an engineer. On the engineering side, we don't always consider the larger ramifications for the decisions that are made. Nor do we always have the full perspective on why we create what we do. Engineering team principles give a starting point for what the team should focus on to make sure the team is ultimately successful and fulfilled.

The below is just a baseline, it should always be combined with the experience gained from other engineering teams and adjusted. This is also a balance; adjusting too much means you lose the principles and not adjusting at all means you lose the context.

This article will only contain the guiding principals. Other articles will contain the values and sometimes step by step instructions.

## Principles
### TDD
Reduces regressions, bugs, and broken demos while ensuring business alignment and increasing the release speed of working software.
Writing a test case is the first code written.
### Bugs
More than an engineering cost - it affects sales, business, customers, and engineering.
The cost of a bug is clear on the engineering side, time to fix. The cost outside is poorly understood and often underestimated.
### Features
Without test cases or with bugs are considered incomplete features - working code serves the customer by having PM/VPE to correctly describe test cases.
A feature that took 1 hour to release with bugs that took 1 hour to fix produces only 1 hour of value. Focus on writing test cases first.
### Linters
Always used and allows current and new engineers to adopt similar code style making it easier to onboard new engineers as well as allowing engineers who didn’t write the code to maintain the code of other engineers.
The config and grammar agreed upon by the team can be adopted from Google or AirBnB to get started.
Informal exceptions are understood by the team and used sparingly. Reference *The Zen of Python* to inform your decision of whether an exception is valuable.
### Estimations
Bugs and chores are not estimated.
These are considered part of normal software product overhead—they emerge over time, and are continual overhead, an ongoing cost of doing business. This lets you focus your planning on business value, risk, and priorities. Therefore, bugs and chores in Tracker are not *normally* estimated although should be paid attention to.
### Code coverage
As a team, decide on appropriate code coverage and commit to reaching that level of coverage. This can be revisited monthly.
### Continuous Integration
Smaller faster merges shorter feedback loop and fewer bugs.
No more release day conflicts into the main branch.
Faster feedback for engineers regarding bugs in code that allow fixes while still familiar with the context of the code. Don’t need to wait for a multi-day QA loop to find an issue.
### Continuous Delivery
Automated release process with continuous delivery deployed at the click of a button or with a single unified process.
Release schedule agreed upon by the engineering team but at least weekly
### Continuous Deployment
No more frantic fire-filled “release day”. Builds go live to customers as soon as the code is pushed
It's important to remember business release != engineering release - we release constantly into staging via CI/CD, business releases based on features manually at a set time


## Outro
It may not be reasonable to implement everything at once, especially if you already have a product live with customers. If that's the case a few of these principles should be implemented first. Using impact to the customer as a proxy will give good intuition on what to implement first.