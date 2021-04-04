---
title: Discrete Mathematics 7th Edition Section 1.7 Exercises
description: 
published: true
date: 2021-04-04T02:10:40.920Z
tags: discrete-mathematics
editor: markdown
---

# Section 1.7 Introduction to Proofs

## Exercise 5
Prove that if $m + n$ and $n + p$ are even integers, where $m$, $n$, and $p$ are integers, then $m + p$ is even. What kind of proof did you use?
### Solution
Assume for integers $m$, $n$, and $p$, $m+n$ and $n+p$ are even integers. That means that there are some integers a and b where $m+n$ = 2a and $n+p=2b$.

Adding those two together, we get 
$$
\begin{aligned}
m+n+n+p&=2a+2b \\
m + 2n + p &= 2a+2b \\
m + p &= 2a + 2b -2n \\ 
m+p &= 2(a+b+n)
\end{aligned}
$$

We see $m+p$ written as $2$ times an integer ($a+b+n$)