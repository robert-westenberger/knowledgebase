---
title: Logarithms
description: 
published: true
date: 2021-07-22T16:30:29.410Z
tags: mathematics, algorithms
editor: markdown
---

A **logarithm** is simply an inverse exponential function. Saying $b^{x}=y$ is equivalent to saying that $x=\log _{b} y .$ Further, this equivalence is the same as saying $b^{\log _{b} y}=y$

Logarithms arise in any process where things are repeatedly halved.

# Logarithms, Trees, and Bits
![tree_fig.png](/tree_fig.png)
A height $h$ tree with $d$ children per node has $d^{h}$ leaves. Here $h=3$ and $d=3$ (left). The number of bit patterns grows exponentially with pattern length (right). These would be described by the root-to-leaf paths of a binary tree of height $h=3$.

There are two bit patterns of length $1(0$ and 1$)$, four of length $2(00,01,10$, and 11), and eight of length 3 (see right of above image). How many bits $w$ do we need to represent any one of $n$ different possibilities, be it one of $n$ items or the integers from 0 to $n-1 ?$

The key observation is that there must be at least $n$ different bit patterns of length $w$. Since the number of different bit patterns doubles as you add each bit, we need at least $w$ bits where $2^{w}=n$. In other words, we need $w=\log _{2} n$ bits.

# Logarithms and Multiplication
Logarithms are useful for multiplication, particularly for exponentiation. 

Recall that $\log _{a}(x y)=\log _{a}(x)+\log _{a}(y) ;$ that is, the log of a product is the sum of the logs. A direct consequence of this is
$$
\log _{a} n^{b}=b \cdot \log _{a} n
$$
How can we compute $a^{b}$ for any $a$ and $b$ using the $\exp (x)$ and $\ln (x)$ functions on your calculator, where $\exp (x)=e^{x}$ and $\ln (x)=\log _{e}(x) ?$ We know
$$
a^{b}=\exp \left(\ln \left(a^{b}\right)\right)=\exp (b \ln (a))
$$
so the problem is reduced to one multiplication plus one call to each of these functions.

# Fast Exponentiation
Logarithms can be used to quickly give an exact computation of the value of $a^n$. 