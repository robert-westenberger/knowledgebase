---
title: Real Valued Functions of a Real Variable and Their Graphs
description: 
published: true
date: 2021-07-15T18:11:56.953Z
tags: 
editor: markdown
---

# Power Functions
Let $a$ be any nonnegative real number. Define $p_{a}$, the **power function with exponent** $\boldsymbol{a}$, as follows:
$p_{a}(x)=x^{a}$ for each nonnegative real number $x$.

# Floor Functions

$$
\begin{aligned}
F(x)&=\lfloor x\rfloor \\
&=\text { the greatest integer that is less than or equal to } x \\
&\text { = the unique integer } n \text { such that } n \leq x<n+1
\end{aligned}
$$

# Graph of a Multiple of a Function
A **multiple** of a function is obtained by multiplying every value of the function by a fixed number. To understand the concept of $O$-notation, it is helpful to understand the relation between the graph of a function and the graph of a multiple of the function.

Let $f$ be a real-valued function of a real variable and let $M$ be any real number. The function $M f$, called the **multiple of** $\boldsymbol{f}$ **by** $\boldsymbol{M}$ or $\boldsymbol{M}$ **times** $\boldsymbol{f}$, is the real-valued function with the same domain as $f$ that is defined by the rule
$$
(M f)(x)=M \cdot(f(x)) \quad \text { for each } x \in \text { domain of } f
$$

# Increasing and Decreasing Functions

Consider the absolute value function, $A$, defined as follows: 
$$
\begin{array}{l}
A(x)=|x|=\left\{\begin{aligned}
x & \text { if } x \geq 0 \\
-x & \text { if } x<0
\end{aligned}\right.\\
\text { for each real number } x
\end{array}
$$

When $x \geq 0$, the graph of $A$ is the same as the graph of $y=x$, the straight line with slope 1 that passes through the origin $(0,0)$. For $x<0$, the graph of $A$ is the same as the graph of $y=-x$, which is the straight line with slope $-1$ that passes through $(0,0) .$ (See below graph of absolute value function)
![graph_of_absolute_value_function.png](/graph_of_absolute_value_function.png)

Note that as you trace from left to right along the graph to the left of the origin, the height of the graph continually decreases. For this reason, the absolute value function is said to be **decreasing** on the set of real numbers less than $0$. On the other hand, as you trace from left to right along the graph to the right of the origin, the height of the graph continually increases. Consequently, the absolute value function is said to be **increasing** on the set of real numbers greater than $0$.

## Definition
Let $f$ be a real-valued function defined on a set of real numbers, and suppose the domain of $f$ contains a set $S$. We say that $f$ is **increasing on the set** $S$ if, and only if,
for all real numbers $x_{1}$ and $x_{2}$ in $S$, if $x_{1}<x_{2}$ then $f\left(x_{1}\right)<f\left(x_{2}\right)$.
We say that $f$ is decreasing on the set $S$ if, and only if,
for all real numbers $x_{1}$ and $x_{2}$ in $S$, if $x_{1}<x_{2}$ then $f\left(x_{1}\right)>f\left(x_{2}\right)$.
We say that $f$ is an increasing (or decreasing) function if, and only if, $f$ is increasing (or decreasing) on its entire domain.