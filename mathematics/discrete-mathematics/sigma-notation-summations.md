---
title: Sigma Notation and Summations
description: 
published: true
date: 2021-07-23T19:28:05.257Z
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
Sometimes its useful to shift the index of summation in a sum.