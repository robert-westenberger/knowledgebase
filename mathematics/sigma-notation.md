---
title: Sigma Notation
description: 
published: true
date: 2021-07-23T17:40:17.996Z
tags: mathematics
editor: markdown
---

# Sigma Notation 


$$
\sum_{i=m}^{n} a_{i}=a_{m}+a_{m+1}+a_{m+2}+\cdots+a_{n-1}+a_{n}
$$

* $i$ is the **index of summation**
* $a_i$ is an index variable representing each term of the sum.
* $m$ is the **lower bound of summation**
* $n$ is the **upper bound of summation**
* The $i=m$ under the summation symbol means that the index $i$ starts out equal to $m$.
* The index, $i$, is incremented by one for each successive term, stopping whne $i=n$.

The above summation is read, "sum to $a_i$, from $i=m$ to $n$".

Depending on the context, the upper and lower bounds may be excluded. This applies particularly when the index runs from $1$ to $n$.

$$
\sum a_{i}^{2}=\sum_{i=1}^{n} a_{i}^{2}
$$


Both below are equal (both sum integers from 1 to n)

$$
\sum_{i=1}^{n} i \quad \text { or } \quad \sum_{1 \leq i \leq n} i
$$

