---
title: Sigma Notation and Summations
description: 
published: true
date: 2021-07-23T19:44:39.114Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Sigma Notation 

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

## Shifting the Index of Summation
Sometimes its useful to shift the index of summation in a sum. This is often done when two sums need to be added but their indices of summation do not match. When shifting an index of summation, it is important to make the appropriate changes in the corresponding summand. 

### Example
Suppose we have the sum 
$$\sum_{j=1}^{5} j^{2}$$
but want the index of summation to run between $0$ and $4$ rather than $1$ to $5$. To do this, we let $k=j-1$. Then the new summation index runs from 0 (because $k=1-0=0$ when $j=1$ ) to 4 (because $k=5-1=4$ when $j=5$ ), and the term $j^{2}$ becomes $(k+1)^{2}$. Hence,
$$
\sum_{j=1}^{5} j^{2}=\sum_{k=0}^{4}(k+1)^{2}
$$

