---
title: "Pragmatic Programmer" 
excerpt: "As an engineering team leader, this book gives great advice. Some of it is outdated, but much of the relevant topics are included below"
categories:
  - book notes
  - engineering strategy
tags:
  - engineering strategy
toc: true
toc_sticky: true
date: 2020-4-15
header:
  teaser: https://i.gr-assets.com/images/S/compressed.photo.goodreads.com/books/1401432508l/4099.jpg
---
# Intro
Some of the advice in this book is old and dated while others have been proven timeless. In general, many of the philosophy and approach are timeliness while the tool recommendations and examples are dated. For engineering leaders who have been in the field for a long time, this may be a good thing. If it's been a while since getting your hands dirty, the references to the languages in this book may give a good analogy for what current teams are doing. 

While enumerating what I feel is important, I'll be trying to keep other startup books in mind so I can focus on the commonalities. I'll be using this as a proxy to decide what is truly timeliness. I'll also include suggestions that overlap with what I've seen while leading engineering teams.

# Philosophy
## Mindset
It's important to think beyond the immediate problem by placing it in a larger context. 
Take responsibility for everything that we do, refuse to do, or can't do. No fear of appearing weak; this hurts progress of the team.
## Provide Options
Act constructively <s>if</s> when something happens by offering opinions, not excuses. Don't say something can't be done, explain *what* can be done to salvage a situation.

## Be a Catalyst for Change
Disasters in software can start so small they go unnoticed. Project extensions happen one day at a time. A frog put into boiling water will notice and jump out. But put into water warmed slowly, the frog will not notice until it is too late. Don't be the frog; notice the small details and understand how it affects the big picture.

## Make Quality a Requirement
Knowing went to stop is an art. I've only met a few leaders who can balance this. It turns out it is easier to *want* to make something perfect than to *know* when something has to be "perfect". Great software today is preferable to perfect software tomorrow. Especially, if that perfect software is delayed a day.

## Explicitly Grow

Constantly learn, technology, frameworks, processes are changing. It can be exhausting, but like any investment it pays dividends. 
- Learn at least one new language a year
- Read a technical book each quarter
- Read a book on soft skills 2x a year
- Take classes
- Subscribe to technology newsletters
- Experiment
- Be a part of technical groups

## Communicate
Strive to become better at communicating with your team as much as becoming better technically. Plan what you want to say, know what you want to say.
1. What do you want your audience to learn?
2. What is the interest of the audience in what you've to say?
3. How sophisticated is your audience?
4. How much detail does your audience want?
5. How can you motivate your audience to listen?
5. Choose your moment.
6. Make it look good.
7. Involve your audience in the process.
8. Be a listener.
9. Get back to people.

# Approach

## Duplication is Waste
Duplicating an effort is already spending extra time. Changing code in two places takes twice and long and is more likely to be missed or cause bugs. Maintenance now takes twice as long which slows the velocity of your team when it comes to feature creation. Not including maintenance as part of velocity incentivizes this behaviour. 

## Orthogonal Shy Code
Although the book uses the terms "orthogonal", more currently it would be referred to as decoupled plus more. Increased speed of development, especially during merge operations, as engineers can work on different features independently. Changes to features will have minimum side effects with a better ability to coverage code with test cases. Design has an easier time completing projects where only components have to change.

Temporal Coupling is still a type of coupling
{: .notice--warning}

If your developers are *afraid* to change code. There is a good chance coupled code is part of the reason.

## Use Tracer Bullets
Different than a prototype we aim to explore only a specific aspect of the system but with code that forms part of the skeleton of the final system. A prototype would normally be discarded.

## Prototype
This is also advocated by almost every intro startup book such as *Lean Startup*. The book *Lean UX* has a particularly thorough set of methods to explore.
Prototype everything that carries risk, hasn't been tried before, is critical to the final system, and is unproven. Unproven can have a context of the environment. Something proven on the NASA space-shuttle might be unproven on your phone.

The point of prototyping is to learn. Although, generally lead by the design and product team, there're situations where engineering will need to prototype. Currently, many machine learning models need prototypes in the correct context to decide on an implementation path. The collaboration between engineering and design on what is possible has become so important with the advent of wide-spread machine learning.

## Estimates
Understand what is dependent on giving an estimate. Is a client dependent on it, is an investor, is it for a pitch? Understanding the details gives information on how detailed the estimate needs to be. Project schedules are a function of: requirements, risk, integrations, validations, testing in addition to engineering.

# The Tools
This part of the book is relatively outdated and is known but every engineer in this day and age. The only advice I would give is if your team has a machine learning component. Review the academic papers, they may be dense but will often reference cutting edge tools and techniques that will save time and increase the positive outcomes for the product.


# Outro
Having written this summary I realize that I've only covered about 30% of the book. I'll find another time to cover the rest that I think it's helpful in this field. Some of the topics the book does a good job discussing are:
- Pre-project preparation
- Project structuring
- Coding techniques
- Paranoia

The remaining sections seem to be outdated and not really worth reading in the advent of current lead product and even agile methodologies.