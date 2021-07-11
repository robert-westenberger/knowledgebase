---
title: Algorithm Analysis
description: 
published: true
date: 2021-07-11T23:48:29.285Z
tags: data-structures, algorithms
editor: markdown
---

# The RAM Model of Computation
Machine-independent algorithm design depends upon a hypothetical computer called the Random Access Machine (RAM). This hypothetical computer has the following attributes:
* Each simple operation (+, *, -, =, if, call) takes exactly one time step.
* Loops and subroutines are a composition of many single-step operations. The time it takes to run through a loop or execute a subprogram depends on the number of loop iterations or the specific nature of the subprogram.
* Each memory access takes one time step. The RAM has unlimited memory.

Run time on the RAM is measured by counting the number of steps an algorithm takes on a given problem instance.

## Best-Case, Worst-Case, and Average-Case Complexity
" "-Case refers to the resources (computations, memory) required for an algorithm to finish.

* **Best-case** - Minimum number of steps taken in any instance of size $n$.
* **Average-case** - Average number of steps over all instances of size $n$.
* **Worst-case** - Maximum number of steps taken in any instance of size $n$. This is typically the most important / useful case to observe.  
