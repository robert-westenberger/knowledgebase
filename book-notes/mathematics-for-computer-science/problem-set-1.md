---
title: Problem Set 1
description: 
published: true
date: 2021-02-22T19:04:59.023Z
tags: computer-science, mathematics, book-notes, discrete-mathematics
editor: markdown
---

# Problem Set 1 (MIT OCW 6.042J Fall '05): Mathematics for Computer Science

## Problem 1
A real number r is called sensible if there exist positive integers $a$ and $b$ such
that $\sqrt{a/b} = r$. For example, setting $a = 2$ and $b = 1$ shows that $\sqrt 2$ is sensible. Prove that $\sqrt[3]2$ is not sensible. (Consider only positive real roots in this problem).

### Solution
We use proof by contradiction. Suppose that $\sqrt[3]2 = \frac ab$ where a and b are two positive integers.

We cube both sides to get $2 = \frac{a^3}{b^3}$.

We divide both sides to get $2b^3 = a^3$. This implies a is an even integer. If $a^3$ is an even integer, that means that $a$ is an even integer as well.

We can rewrite $a$ as $a=2n$ for some unknown integer $n$. Therefore,
$$(2n)^3 = 2b^3$$
$$8n^3 = 2b^3$$
$$4n^3 = b^3$$

We see that b is also even (its a multiple of 4). Since a and b are both even, they are not coprime numbers, which is a contradiction.

Since we have a contradiction, we must assume that $\sqrt[3] 2$ is irrational. $\blacksquare$
## Problem 2
Translate the following sentence into a predicate formula:

"There is a student who has e-mailed exactly two other people in the class, besides possibly herself."
