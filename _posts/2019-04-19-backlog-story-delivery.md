---
title: "Efficient Development and Delivery by the Engineering Team" 
excerpt: "Process of developing and delivering backlog stories as a cohesive and efficient engineering team"
categories:
  - engineering execution
tags:
  - engineering execution
toc: true
toc_sticky: true
date: 2018-11-19
---
## Introduction
The below backlog story development and delivery process outlines how the head of engineering or even CTO can use it to create alignment with product and business. The process optimizes for an efficient and bugless(ish) delivery.

Although written specifically for Tracker, I've personally used similar techniques with everything from customized instances of Redmine, to lightweight GH issues, to heavyweight JIRA.

## Process
Engineering follows the below steps when popping a story off the backlog.
### 1. Starting Stories
Feature stories with points are assigned in the “Iteration/Backlog” category, no blockers, no “needs” (such as missing files) can be started. Bugs and chores do not require points but still require everything else to be in order.
### 2. Priority Order
Stories should be started in order from highest priority to lowest at all times, which means the highest story that meets the above criteria should always be started no matter what.
### 3. Assign
Start a story either assigned to you or not assigned to anyone by clicking on the “start" button.
### 4. Single Tasking
Start only one story at a time; there should not be multiple started stories by a person. Multiple started stories blocks others from taking on a task.

1. One of the few exceptions for the above is a long asynchronous task like collecting logs for a day.
2. If you realize that something is missing from the story (such as a design):

If something is missing from the story:
1. stop the story
2. tag with appropriate “needs PM” tag
3. start another story 
4. let the PM decide the proper course of action

### 5. Add Tasks
Add tasks into the story under the tasks section as the first step after starting a story so that the rest of the team can see progress as you go through and update it.
### 6. Connect Branch
A new branch in the codebase needs to be created following the Tracker format here: For example, creating a branch with the name 123123-super-cool-feature will attach it to the story with id 123123.
### 7. Test Cases
A first commit onto branch should be applicable test cases as specified in the story.
### 8. Finish Story
Stories are only marked as finished once the code has been:

1. updated into GitHub
2. linked to the GitHub commit in pivotal
3. merged into the proper branch
4. build created
5. build deployed into staging
6. able to be downloaded/tested by Head of Engineering, Head of Product, PM, and QA.
## Exceptions
### LOE Adjustment
As an engineer, if you start a story and you realize that the LOE is not what you expected or that you need to take a substantially different implementation path than what you had allowed for during the IPM, you should let the PM know. This is especially important if it looks like it will take considerably longer than originally pointed. This is because there may be other more important priorities.
### Restart Implementation
As an engineer, if you start down an implementation path and then you realize you need to “restart from the beginning of your branch,” it is best to revert commits to the start of the branch and then resume instead of just removing the branch and starting over. This process gives the lead engineer a chance to work with the PM to decide if we should proceed down the new path from a technical standpoint given the original implementation didn’t work or even get another engineer to help with the initial implementation in case there was something small that needed to be changed

## Outro
The above process is meant to be a starting point potentially requiring some adjustments to your current workflow. Keep in mind, some of the processes are purposefully not flexible and require discipline or focus. It may take time to enable that in a team but will be worth the investment.
There are many many opportunities to make exceptions and that is a difficult balancing act. Think through the consequences. Sometimes it can be better to have consistency and discipline over the long term vs the most efficient path but inconsistency.