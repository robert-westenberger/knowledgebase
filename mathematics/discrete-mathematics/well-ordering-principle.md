---
title: Well Ordering Principle
description: 
published: true
date: 2021-03-05T19:31:49.066Z
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

so any way of expressing the left-hand fraction in lowest terms would also work for $m_{0} / n_{0}$, which implies
$$
\text { the fraction } \frac{m_{0} / p}{n_{0} / p} \text { cannot be in written in lowest terms either. }
$$

So by definition of $C$, the numerator $m_{0} / p$ is in $C$. But $m_{0} / p<m_{0}$m which contradicts the fact that $m_0$ is the smallest element of $C$.

Since the assumption that $C$ is nonempty leads to a contradiction, it follows that $C$ must be empty. That is, there are no numerators of fractions that can't be written in lowest terms, and hence there are no such fractions at all.
# Template Well Ordering Proofs
Standard way to prove that $P(n)$ holds for every nonnegative integer $n$ ( "$P(n)$ is true for all $n \in \natnums$".

* Define the set $C$ of counterexamples to $P$ being true. Specifically, define

$$
C:=\{n \in \mathbb{N} \mid \operatorname{NOT}(P(n)) \text { is true }\}
$$


