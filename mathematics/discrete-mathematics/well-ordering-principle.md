---
title: Well Ordering Principle
description: 
published: true
date: 2021-03-05T19:13:13.429Z
tags: mathematics, discrete-mathematics
editor: markdown
---

The Well Ordering Principle is
$$
\text { Every nonempty set of nonnegative integers has a smallest element. }
$$

or 
$$
\text { Every nonempty subset of } \mathbb{N} \text { has a smallest element. }
$$
note how it only applies to sets with nonnegative integers.


## Using WOP to prove $\sqrt 2$ is irrational
By the WOP, we can assume that for any positive integers $m$ and $n$,  the fraction $m/n$ can be written in lowest terms.. in the form $m^{\prime} / n^{\prime}$ where $m^{\prime}$ and $n^{\prime}$ are positive integers with no common prime factors. How do we know this is possible?

Suppose to the contrary that there are positive integers $m$ and $n$ such that the fraction $m/n$ cannot be written in lowest terms. 

Let $C = \{ \text{positive integers that are numerators of such fractions} \}$.

Then $m \in C$ so $C$ is nonempty.

By WOP, there must be a smallest integer $m_0 \in C$.

By definition of $C$, there is an integer $n_0 \gt 0$ such that 
$$
\text { the fraction } \frac{m_{0}}{n_{0}} \text { cannot be written in lowest terms. }
$$

This means that $m_0$ and $n_0$ must have a common prime factor, $p \gt 1$, but

$$
\frac{m_{0} / p}{n_{0} / p}=\frac{m_{0}}{n_{0}}
$$
# Well Ordering Proofs
