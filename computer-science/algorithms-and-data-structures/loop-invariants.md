---
title: Loop Invariants
description: 
published: true
date: 2021-08-22T01:25:50.451Z
tags: computer-science, mathematics, discrete-mathematics, algorithms
editor: markdown
---

A **loop invariant** is a logical assertion that is true before and after each iteration of a loop. 

# Three Necessary Parts of a Loop Invariant
## Initialization
It must be true prior to the first iteration of the loop
## Maintenance
If its true before an iteration, it remains true before the next iteration
## Termination
When the loop terminates, the invariant gives us a useful property
that helps show that the algorithm is correct.