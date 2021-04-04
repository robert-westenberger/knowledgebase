---
title: Discrete Mathematics 7th Edition Section 1.7 Exercises
description: 
published: true
date: 2021-04-04T02:32:14.955Z
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

We see $m+p$ written as $2$ times an integer ($a+b+n$), we conclude $m+p$ is even $\blacksquare$


## Exercise 7
Use a direct proof to show that every odd integer is the difference of two squares.
### Solution (Work in progress)
Consider the difference of two consecutive squares $a$ and $b$.
$$
\begin{aligned}
a^2 - b^2 &= 2k+1 \\
(k+1)^2 - k^2 &= 2k+1 \\
(k+1)(k+1)-k^2 &= 2k+1 \\
k^2  + k + k + 1 - k^2 &= 2k + 1 \\
2k + 1 &= 2k + 1
\end{aligned}
$$
a
