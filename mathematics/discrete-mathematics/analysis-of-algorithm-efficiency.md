---
title: Analysis of Algorithm Efficiency
description: 
published: true
date: 2021-07-14T18:05:07.742Z
tags: discrete-mathematics, algorithms
editor: markdown
---

# Orders of Power Functions
The functions that are most commonly used for comparing algorithm efficiencies are power functions, such as $n^{1 / 2}, n, n^{2}$, and $n^{3}$, and combinations involving a power function and an exponential or logarithmic function, such as $2^{n}, \log (n), n \log (n)$, and $n^{2} \log (n)$

## Theorem: Transitivity of Order
For any positive rational numbers $r$ and $s$ and any integer $n \ge 1$, 

$$
\text { if } r \leq s, \quad \text { then } \quad n^{r} \leq n^{s}
$$

### Examples
$1 \leq n \leq n^{2} \leq n^{3}$.

# Orders of Polynomial Functions
## Example with some negative coefficients
Show that $n^{4}-5 n-8$ is $O\left(n^{4}\right)$

Observe for every integer $n \ge 1$,

$$
\begin{aligned}
n^{4}-5 n-8 & \leq n^{4}+5 n+8 & \text{because when}\medspace n \ge 1, 5n+8 \medspace \text {is positive}\\
& \leq n^{4}+5 n^{4}+8 n^{4} & \text{by transitivity of order theorem, since} \medspace n \ge 1 \medspace  \\ 
& & \text{then} \medspace n \le n^4 \medspace \text{and} \medspace 1 \le n^4 \medspace \text{and so} \medspace 5n \le 5n^4 \medspace \text{and} \medspace 8 \le 8n^4\\
&=14 n^{4}
\end{aligned}
$$

Thus by transitivity of order and equality,
$$
n^{4}-5 n-8 \leq 14 n^{4} \text { for every integer } n \geq 1
$$