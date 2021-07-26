---
title: Sigma Notation and Summations
description: 
published: true
date: 2021-07-26T18:37:41.900Z
tags: mathematics, discrete-mathematics
editor: markdown
---

$$
a_{m}, a_{m+1}, \ldots, a_{n}
$$

from the sequence $\left\{a_{n}\right\}$. We use the notation
$$
\sum_{j=m}^{n} a_{j}, \quad \sum_{j=m}^{n} a_{j}, \quad \text { or } \quad \sum_{m \leq j \leq n} a_{j}
$$
(read as the sum from $j=m$ to $j=n$ of $a_{j}$ ) to represent
$$
a_{m}+a_{m+1}+\cdots+a_{n}
$$

Above, the variable $j$ is called the **index of summation**. The choice of $j$ is arbitrary, we could have used any letter, such as $i$ or $k$.. 

$$
\sum_{j=m}^{n} a_{j}=\sum_{i=m}^{n} a_{i}=\sum_{k=m}^{n} a_{k}
$$

Here, the index of summation runs through all integers with its **lower limit** $m$ and ending with its **upper limit** $n$.

# Shifting the Index of Summation
Sometimes its useful to shift the index of summation in a sum. This is often done when two sums need to be added but their indices of summation do not match. When shifting an index of summation, it is important to make the appropriate changes in the corresponding summand. 

## Example
Suppose we have the sum 
$$\sum_{j=1}^{5} j^{2}$$
but want the index of summation to run between $0$ and $4$ rather than $1$ to $5$. To do this, we let $k=j-1$. Then the new summation index runs from 0 (because $k=1-0=0$ when $j=1$ ) to 4 (because $k=5-1=4$ when $j=5$ ), and the term $j^{2}$ becomes $(k+1)^{2}$. Hence,
$$
\sum_{j=1}^{5} j^{2}=\sum_{k=0}^{4}(k+1)^{2}
$$

# Formula for the Sum of Terms of a Geometric Progression
Recall that sums of geometric progressions are called **geometric series**. 
If $a$ and $r$ are real numbers and $r \neq 0$, then
$$
\sum_{j=0}^{n} a r^{j}=\left\{\begin{array}{ll}
\frac{a r^{n+1}-a}{r-1} & \text { if } r \neq 1 \\
(n+1) a & \text { if } r=1
\end{array}\right.
$$

## Proof
Let 
$$S_{n}=\sum_{j=0}^{n} a r^{j}$$

To compute $S$, first multiply both sides of the equality by $r$ and then manipulate the resulting sum as follows:

1. Substitute Summation formula for $S$
$$r S_{n}=r \sum_{j=0}^{n} a r^{j}$$

2. by the distributive property
$$
=\sum_{j=0}^{n} a r^{j+1}
$$
3. Shifting the index of summation, with $k=k+1$
$$
=\sum_{k=1}^{n+1} a r^{k}
$$
4. Removing $k=n+1$ term and adding $k=0$ term
$$
=\left(\sum_{k=0}^{n} a r^{k}\right)+\left(a r^{n+1}-a\right)
$$
5. Substituting $S$ for summation formula
$$
=S_{n}+\left(a r^{n+1}-a\right)
$$

From these equalities, we see that
$$
r S_{n}=S_{n}+\left(a r^{n+1}-a\right)
$$
Solving for $S_{n}$ shows that if $r \neq 1$, then
$$
S_{n}=\frac{a r^{n+1}-a}{r-1}
$$
If $r=1$, then the $S_{n}=\sum_{j=0}^{n} a r^{j}=\sum_{j=0}^{n} a=(n+1) a$
$$\hspace {32em} \blacksquare$$

# Double Summations
Arise in many contexts, such as the analysis of ensted loops in computer programs.