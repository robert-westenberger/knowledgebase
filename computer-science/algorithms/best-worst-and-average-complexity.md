---
title: Best, Worst, and Average Complexity
description: 
published: true
date: 2021-08-23T19:42:50.584Z
tags: computer-science, algorithms, analysis-of-algorithms
editor: markdown
---

* **Best-case** - Minimum number of steps taken in any instance of size $n$.
* **Average-case** - Average number of steps over all instances of size $n$. Average-case is useful for randomized algorithms.
* **Worst-case** - Maximum number of steps taken in any instance of size $n$. This is typically the most important / useful case to observe.  

We can use [big oh notation](/computer-science/algorithms-and-data-structures/big-oh-notation) to describe running times for algorithms in the best, average, and worst case. 

* **Best-case** = Big $\Omega$ describes an asymptotic lower bound
* **Average-case** = Big $\Theta$ describes an asymptotic upper and lower bound
* **Worst-case** = Big $O$, describes an asymptotic upper bound. Usually the most important.