---
title: Algorithm Analysis
description: 
published: true
date: 2021-07-12T00:07:31.277Z
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
* **Average-case** - Average number of steps over all instances of size $n$. Average-case is useful for randomized algorithms.
* **Worst-case** - Maximum number of steps taken in any instance of size $n$. This is typically the most important / useful case to observe.  

Each time complexity defines a numerical function for any given algorithm. These functions are as well defined as any other numberical function. 
### Example - Sorting algorithm
The best case for a sorting algorithm would be an empty array, or an array that is already in order.
The worse case would be an array that is in the opposite preferred sort order.
## Big O Notation
The Big O simplifies analysis of algorithms by ignoring levels of detail that don't impact comparison between algorithms. Things ignored are 
* Difference between multiplicative constants. $f(n)=2 n$ and $g(n)=n$ are identical in Big O analysis.