---
title: Strong Induction vs Induction vs Well Ordering
description: 
published: true
date: 2021-04-26T00:57:15.944Z
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
**Theorem:** For all natural numbers $n$ and $m$, if $m \gt 0$, then there are natural numbers $q$ and $r$ such that $n=mq+r$ and $r \lt m$ (the numbers $q$ and $r$ are called the quotient and remainder when $n$ is divided by $m$).

**Scratch Work:** We let $m$ be an arbitrary positive integer and then we use strong induction to prove that $\forall n \exists q \exists r(n=m q+r \wedge r<m)$ (for all $n \in \natnums$ there exists a $q$ and $r$ where $n$ is equal to $mq+r$ and $r$ is less than $m$. According to strong induction, this means we should let $n$ be an arbitrary natural number, assume that $\forall k<n \exists q \exists r(k=m q+r \wedge r<m)$ ( $P(n)$ is true for all $n \le k$) and prove that $\exists q \exists r(n=m q+r \wedge r<m)$.

The goal is an existential statement so we need to come up with values of $q$ and $r$ with the required properties. 

If $n \lt m$ we can just let $q=0$ and $r=n$ (multiply a number by 0 and add the number to the product to get...itself). For example $n=-5$, $m=3$, $q=-2$, $r=1$ becomes $n=-5$, $m=3$, $q=0$, $r=-5$.

If $n \ge m$, this won't work, since we must have $m \gt r$, so we must do something different. The inductive hypothesis starts with $\forall k \lt n$, so to apply it we should plug in some nat num smaller than $n$ for $k$, but what should we plug in??
