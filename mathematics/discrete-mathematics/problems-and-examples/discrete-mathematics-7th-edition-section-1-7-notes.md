---
title: Discrete Mathematics 7th Edition Section 1.7 Exercises
description: 
published: true
date: 2021-04-07T17:24:02.847Z
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
## Exercise 13
Prove that if $x$ is irrational, then $1/x$ is irrational.
### Solution
We prove the contrapositive. We prove "If $1/x$ is rational, then $x$ is rational".
We know that $x \ne 0$ since a fraction cannot be divisible by $0$. If $1/x$ is rational then there are some integers $p$ and $q$ with $q \ne 0$. Since $1/x$ can't be $0$ (if it were, we'd have the contradiction $1 = x \cdot 0$ by multiplying both sides by $x$, we know that $p \ne 0$. Now 
$$x = \frac{1}{\frac{1}{x}}=\frac{1}{\frac{p}{q}}=\frac qp$$
We see $x$ can be written as the quotient of two integers with the denominator nonzero. Thus by definition, $x$ is rational.
## Exercise 23
Show that at least ten of any $64$ days chosen must fall on the same day of the week.
### Solution
Proof by contradiction. Suppose we pick $64$ days and no more than $9$ fall on the same day. This means that we have chosen at most $7 \times 9=63$ days, which is a contradiction. 

## Exercise 25
Use a proof by contradiction to show that there is no rational number $r$ for which $r^3+r+1=0$. (Hint: Assume that $r = a/b$ is a root, where $a$ and $b$ are integers and $a/b$ is in lowest terms. Obtain an equation involving integers by multiplying by $b^3$. Then look at whether $a$ and $b$ are each odd or even.)
### Solution
Proof by contradiction. Suppose $r$ is a rational number that is a root of $r^3+r+1=0$. That means $r$ can be expressed as the ratio of two integers $a$ and $b$ and the ratio is in lowest terms. Plugging this root into the equation we get $a^{3} / b^{3}+a / b+1=0$. Multiplying by $b^3$ we get $a^{3}+a b^{2}+b^{3}=0$. Since $a$ and $b$ are in lowest terms, they both can't be even. No matter which the different possible variations of $a$ and $b$s parity, the lefthand side of the equation must be odd, and so it can't equal 0. This is a contradiction and shows no such root exists.

## Exercise 27
Prove that if $n$ is a positive integer, then $n$ is odd if and only if $5n + 6$ is odd.
### Solution
**Scratch:** Need to show $p \rarr q$ and $q \rarr p$ are true. 
For the domain of positive integers..

$$p= \text{n is odd}$$
$$q= \text{5n+6}$$

Need to prove "If $n$ is odd then $5n +6$ is odd" and "If $5n + 6$ is odd then $n$ is odd".

If $n$ is odd then there is some $c$ where $n=2c + 1$. Plugging that value in to $5n+6$ we get $5(2c+1) + 6$ or $10c + 5 + 6$ or $10c + 11$ or $2(5c+5) +1$. Since $5c+5$ is an integer, we see that $5n+6$ is in the form of an odd number.

To prove that "If $5n+6$ is odd then $n$ is odd" we prove the contrapositive, which is "If $n$ is even then $5n+6$ is even". Suppose $n$ is even so there is some $c$ where $2c=n$. So we plug that in and we get $5(2c) + 6$ or $10c + 6$. That can be written in the form of an even number $2(5c +3)$. 

## Exercise 39

