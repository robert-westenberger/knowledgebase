---
title: RAM Model of Computation
description: 
published: true
date: 2021-08-23T19:33:35.766Z
tags: algorithms
editor: markdown
---

Machine-independent algorithm design depends upon a hypothetical computer called the Random Access Machine (RAM). This hypothetical computer has the following attributes:
* Each simple operation (+, *, -, =, if, call) takes exactly one time step.
* Loops and subroutines are a composition of many single-step operations. The time it takes to run through a loop or execute a subprogram depends on the number of loop iterations or the specific nature of the subprogram.
* Each memory access takes one time step. The RAM has unlimited memory.

Run time on the RAM is measured by counting the number of steps an algorithm takes on a given problem instance.