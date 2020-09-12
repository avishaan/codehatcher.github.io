---
title: "Vim Mnemonic Devices" 
excerpt: "An easier way to remember what each vim command does"
categories:
  - vim
tags:
  - reference
  - vim
toc: true
toc_sticky: true
date: 2015-12-18
---

#### Introduction
A pneumonic device helps us remember something seemingly abstract by giving it a familiar context. For instance in order to remember the planets in order from closest to furthest from the sun you could use the handy "My Very Educated Mother Just Served Us Nectarines".

When I first learned Vim I just spent a couple hours to remember them, but that prevented me from utilizing the slightly more abstract and less often used commands. Realizing that 'i' means 'insert mode' I started to look for a other keys based on commands. Then I realized that it doesn't really matter how logical it is, if you remember it then that is good enough. It reminds a little bit of the book, **Moonwalking with Einstein**

**NOTE**: This won't teach you Vim at all, just how to remember some of the keys.

#### List of Vim Commands

- i - enter **i**nsert mode
- v - enter **v**isual mode (duh)
- a - **a**ppend
- d - **d**elete a character.
- D -  **D**ELETE whole line!
- p - **p**aste
- c - small **c**hange
- C - enter **C**HANGE mode to
- u - **u**ndo
- t - **t**o
- f - **f**orward
- ; - keep going to the next (yes this is weak but a reference of how a semicolon is like a period but without the hassle of the capitalization of the next complete thought)
- y - **y**ank from last register
- dit - **d**elete **i**nner **t**ag block `<html>test</html>` --> `<html></html>`
- dst - **d**elete **s**urrounding **t**ag block `<html>test</html>`-->`test`
- cit - **c**hange **i**nner **t**ag block: same as dit but put your cursor in insert mode
- r - **r**eplace a single character
- R - enter **R**EPLACE mode to overwrite characters continuously
- z - fold**z** for day**z** (yes, it's weak)
- zf - **f**old**z**
- gq - (with jdaddy.vim) *g*orgeous json *q*uickly on the visual selection without much work (yes, very w
- 0 -  the **start of the line**  you start with nothing and you have to build up to be rich
- $ - when you are rich, you have money, and you are at the **end of the line** and of your goal
- J - **j**oin the visually selected lin