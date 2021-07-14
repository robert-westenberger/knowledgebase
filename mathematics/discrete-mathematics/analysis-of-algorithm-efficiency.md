---
title: Analysis of Algorithm Efficiency
description: 
published: true
date: 2021-07-14T17:39:45.387Z
tags: discrete-mathematics, algorithms
editor: markdown
---


# Orders of Power Functions
The functions that are most commonly used for comparing algorithm efficiencies are power functions, such as $n^{1 / 2}, n, n^{2}$, and $n^{3}$, and combinations involving a power function and an exponential or logarithmic function, such as $2^{n}, \log (n), n \log (n)$, and $n^{2} \log (n)$

## Theorem: Transitivity of Order
For any positive rational numbers $r$ and $s$ and any integer $n \ge 1$, 

$$
\text { if } r \leq s, \quad \text { then } \quad n^{r} \leq n^{s}
$$