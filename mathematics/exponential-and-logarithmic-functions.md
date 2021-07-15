---
title: Exponential and Logarithmic Functions
description: 
published: true
date: 2021-07-15T17:28:21.723Z
tags: mathematics
editor: markdown
---

# Exponential Functions
Let $n$ be a positive integer, and let $b$ be a fixed positive real number. The function $f_{b}(n)=b^{n}$ is defined by
$$
f_{b}(n)=b^{n}=b \cdot b \cdot b \cdot \cdots \cdot b
$$

## Theorem 1
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

## Theorem 2
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

## Theorem 3
Let $a$ and $b$ be real numbers greater than 1 , and let $x$ be a positive real number. Then
$$
\log _{a} x=\log _{b} x / \log _{b} a
$$

### Proof
To prove this, it suffices to show that
$$
b^{\log _{a} x \cdot \log _{b} a}=x
$$

By part 2 of Theorem 1, we have
$$
\begin{aligned}
b^{\log _{a} x \cdot \log _{b} a} &=\left(b^{\log _{b} a}\right)^{\log _{a} x} \\
&=a^{\log _{a} x} \\
&=x
\end{aligned}
$$
This completes the proof. $\hspace {32em} \blacksquare$