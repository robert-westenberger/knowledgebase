---
title: Representing Relations
description: 
published: true
date: 2021-05-12T18:31:29.544Z
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

Another example, $A=\left\{a_{1}, a_{2}, a_{3}\right\}$, $B=\left\{b_{1}, b_{2}, b_{3}, b_{4}, b_{5}\right\}$, and $R=\left\{\left(a_{1}, b_{2}\right),\left(a_{2}, b_{1}\right),\left(a_{2}, b_{3}\right),\left(a_{2}, b_{4}\right),\left(a_{3}, b_{1}\right),\left(a_{3}, b_{3}\right),\left(a_{3}, b_{5}\right)\right\}$

$$
\mathbf{M}_{R}=\left[\begin{array}{lllll}
0 & 1 & 0 & 0 & 0 \\
1 & 0 & 1 & 1 & 0 \\
1 & 0 & 1 & 0 & 1
\end{array}\right]
$$

## Reflexivity
The matrix relationship on a set, which is a square matrix, will have $1$s along the entirety of the main diagonal if the relationship is reflexive.

## Symmetry and Antisymmetry
![symmetry_antisymmetry.png](/symmetry_antisymmetry.png)

# Finding Union and Intersection of Relations Using Matrices
The boolean operations **join** and **meet** can be used to find the matrices representing the union and the intersection of two relations. Suppose $R_1$ and $R_2$ are relations on a set $A$ represented by the matrices $M_{R_1}$ and $M_{R_2}$, respectively. The matrix representing the union of these relations has a $1$ in the positions where either $M_{R_1}$ or $M_{R_2}$ has a $1$. The matrix representing the intersection has a $1$ in positions where both $M_{R_1}$ and $M_{R_2}$ have a $1$. The matrices representing these relations are 

$$
\mathbf{M}_{R_{1} \cup R_{2}}=\mathbf{M}_{R_{1}} \vee \mathbf{M}_{R_{2}} \quad \text { and } \quad \mathbf{M}_{R_{1} \cap R_{2}}=\mathbf{M}_{R_{1}} \wedge \mathbf{M}_{R_{2}}
$$

# Finding Composite of Relations Using Matrices
Can be found using the boolean product of matrices.