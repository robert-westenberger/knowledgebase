---
title: Strong Induction vs Induction vs Well Ordering
description: 
published: true
date: 2021-04-26T00:20:25.022Z
tags: discrete-mathematics
editor: markdown
---

# When To Use Incomplete Induction
Use mathematical induction when it is straightforward to prove that $P(k) \rarr P(k+1)$ is true for all positive integers $k$. 

# When To Use Strong Induction
When you see how to prove $P(k+1)$ is true from the assumption that $P(j)$ is true for all positive integers $j$ not exceeding $k$, but yo ucannot see how to prove that $P(k+1)$ follows from just $P(k)$.

# Examples of Strong Induction (and why the use of Strong Induction was required)

## Proof of the fundamental theorem of arithmetic
Show that if $n$ is an integer greater than $1$, then $n$ can be written as the product of primes.


Let $P(n)$ be the proposition that $n$ can be written as the product of primes. 

**Basis Step:** $P(2)$ is true because $2$ can be written as the product of one prime, itself.

**Inductive Step:** The inductive hypothesis is assumption that $P(j)$ is true for all integers $j$ with $2 \le j \le k$. That is, $j$ can be written as the product of primes whenver $j$ is a positive integer at least $2$ and not exceeding $k$. 

To complete the inductive step, it must be shown that $P(k+1)$ is true under this assumption, that is, that $k+1$ is the product of primes. 

There are two cases to consider, when $k+1$ is prime and when $k+1$ is composite. If $k+1$ is prime, we immediately see that $P(k+1)$ is true. Otherwise, $k+1$ is composite and can be written as the product of two positive integers $a$ and $b$ with $2 \leq a \leq b<k+1$. Because both $a$ and $b$ are integers at least $2$ and not exceeding $k$, we can use the inductive hypothesis to write both $a$ and $b$ as the product of primes. Thus, if $k+1$ is composite, it can be written as the product of primes, namely, those primes in the factorization of $a$ and thoser in the factorization of $b$. 


## Proof of division algorithm
For all natural numbers $n$ and $m$, if $m \gt 0$, then there are natural numbers $q$ and $r$ such that $n=mq+r$ and $r \lt m$ (the numbers $q$ and $r$ are called the quotient and remainder when $n$ is divided by $m$).

