---
title: Representing Relations
description: 
published: true
date: 2021-05-12T18:09:18.930Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Representing Relations Using Matrices
A relation between finite sets can be represented using a zero-one matrix.

Support $R$ is ar elation from $A=\left\{a_{1}, a_{2}, \ldots, a_{m}\right\}$ to $B=\left\{b_{1}, b_{2}, \ldots, b_{n}\right\}$. The relation $R$ can be represented by the matrix $\mathbf{M}_{R}=\left[m_{i j}\right]$, where 

$$
m_{i j}=\left\{\begin{array}{l}
1 \text { if }\left(a_{i}, b_{j}\right) \in R, \\
0 \text { if }\left(a_{i}, b_{j}\right) \notin R
\end{array}\right.
$$

Below is an example of a matrix of a set $A=\{1,2,3\}$, $B=\{1,2\}$, and a relation $R=\{(2,1),(3,1),(3,2)\}$:

$$
\mathbf{M}_{R}=\left[\begin{array}{ll}
0 & 0 \\
1 & 0 \\
1 & 1
\end{array}\right]
$$
