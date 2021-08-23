---
title: Big Oh Notation
description: 
published: true
date: 2021-08-23T19:29:23.706Z
tags: mathematics, discrete-mathematics, algorithms
editor: markdown
---

The Big O simplifies analysis of algorithms by ignoring levels of detail that don't impact comparison between algorithms. For example, difference between multiplicative constants. $f(n)=2 n$ and $g(n)=n$ are identical in Big O analysis

It is used extensively to estimate the number of operations an algorithm uses as its input grows. 

# Notation
Let $f$ and $g$ be functions from the set of integers or the set of real numbers to the set of real numbers. We say that $f(x)$ is $O(g(x))$ if there are constants $C$ and $k$ such that
$$
|f(x)| \leq C|g(x)|
$$
whenever $x>k$. (This is read as " $f(x)$ is big-oh of $g(x) . ")$
The constants $C$ and $k$ are called **witnesses** to the relationship of $f(x)$ is $O(g(x))$. To establish $f(x)$ is $O(g(x))$, we need find only one pair of constants $C$ and $k$, the witnesses, such that $|f(x)| \leq C|g(x)|$ whenever $x \gt k$.

Intuitively, the definition that $f(x)$ is $O(g(x))$ says that $f(x)$ grows slower than some fixed multiple of $g(x)$ as $x$ grows without bound.
![asymptotic-notation-graphs.png](/asymptotic-notation-graphs.png)
**(a)** $f(n)=O(g(n))$ means $c \cdot g(n)$ is an **upper bound** on $f(n)$. There exists some constant $c$, such that $f(n) \leq c \cdot g(n)$ for every large enough $n$ (that is, for all $n \ge n_0$, for some constant $n_0$).
**(b)** $f(n)=\Omega(g(n))$ means $c \cdot g(n)$ is a **lower bound** on $f(n)$. Thus, there exists some constant $c$ such that $f(n) \ge c \cdot g(n)$ for all $n \ge n_0$.
**(c)** $f(n)=\Theta(g(n))$ means $c_1 \cdot g(n)$ is an **upper bound** on $f(n)$ and $c_2 \cdot g(n)$ is a **lower bound** on $f(n)$, for all $n \ge n_0$. Thus, there exist constants $c_1$ and $c_{2}$ such that $f(n) \leq c_{1} \cdot g(n)$ and $f(n) \geq c_{2} \cdot g(n)$ for all $n \geq n_{0}$. This means that $g(n)$ provides a nice, tight bound on $f(n)$.

We are not concerned with small values of $n$ (anything to the left of $n_0$ in the graphs).