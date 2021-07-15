---
title: Exponential and Logarithmic Functions
description: 
published: true
date: 2021-07-15T17:24:03.327Z
tags: mathematics
editor: markdown
---

# Exponential Functions
Let $n$ be a positive integer, and let $b$ be a fixed positive real number. The function $f_{b}(n)=b^{n}$ is defined by
$$
f_{b}(n)=b^{n}=b \cdot b \cdot b \cdot \cdots \cdot b
$$

## Theorem
Let $b$ be a positive real number and $x$ and $y$ real numbers. Then
1. $b^{x+y}=b^{x} b^{y}$, and
2. $\left(b^{x}\right)^{y}=b^{x y}$.

# Logarithmic Functions
If $b$ is a real number greater than 1 and $x$ is a positive real number, then
$$
b^{\log _{b} x}=x
$$

It follows that 
$$\log _{b} b^{x}=x$$

## Theorem 1
Let $b$ be a real number greater than 1 . Then
1. $\log _{b}(x y)=\log _{b} x+\log _{b} y$ whenever $x$ and $y$ are positive real numbers, and
2. $\log _{b}\left(x^{y}\right)=y \log _{b} x$ whenever $x$ is a positive real number and $y$ is a real number.

### Proof
Because $\log _{b}(x y)$ is the unique real number with $b^{\log _{b}(x y)}=x y$, to prove part 1 it suffices to show that $b^{\log _{b} x+\log _{b} y}=x y$. By part 1 of Theorem 1 , we have
$$
\begin{aligned}
b^{\log _{b} x+\log _{b} y} &=b^{\log _{b} x} b^{\log _{b} y} \\
&=x y
\end{aligned}
$$
To prove part 2 , it suffices to show that $b^{y \log _{b} x}=x^{y} .$ By part 2 of Theorem 1 , we have
$$
\begin{aligned}
b^{y \log _{b} x} &=\left(b^{\log _{b} x}\right)^{y} \\
&=x^{y}
\end{aligned}
$$
$$ 
\hspace {32em} \blacksquare
$$
