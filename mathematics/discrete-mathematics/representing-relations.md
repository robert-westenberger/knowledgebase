---
title: Representing Relations
description: 
published: true
date: 2021-05-13T18:40:12.298Z
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

## Boolean product of matrices
Let $\mathbf{A}=\left[a_{i j}\right]$ be an $m \times k$ boolean matrix and $\mathbf{B}=\left[b_{i j}\right]$ be a $k \times n$ boolean matrix. The **boolean product** of $A$ and $B$, denoted by  $\mathbf{A} \odot \mathbf{B}$, is the matrix $m \times n$ with $(i, j)$th entry $c_{ij}$ where 

$$
c_{i j}=\left(a_{i 1} \wedge b_{1 j}\right) \vee\left(a_{i 2} \wedge b_{2 j}\right) \vee \cdots \vee\left(a_{i k} \wedge b_{k j}\right)
$$

### Example
The boolean product of $\textbf {A}$ and $\textbf {B}$

$$
\mathbf{A}=\left[\begin{array}{ll}
1 & 0 \\
0 & 1 \\
1 & 0
\end{array}\right], \quad \mathbf{B}=\left[\begin{array}{lll}
1 & 1 & 0 \\
0 & 1 & 1
\end{array}\right]
$$



$$
\begin {aligned}
\mathbf{A} \odot \mathbf{B}&=\left[\begin{array}{lll}
(1 \wedge 1) \vee(0 \wedge 0) & (1 \wedge 1) \vee(0 \wedge 1) & (1 \wedge 0) \vee(0 \wedge 1) \\
(0 \wedge 1) \vee(1 \wedge 0) & (0 \wedge 1) \vee(1 \wedge 1) & (0 \wedge 0) \vee(1 \wedge 1) \\
(1 \wedge 1) \vee(0 \wedge 0) & (1 \wedge 1) \vee(0 \wedge 1) & (1 \wedge 0) \vee(0 \wedge 1)
\end{array}\right] \\
&=\left[\begin{array}{lll}
1 \vee 0 & 1 \vee 0 & 0 \vee 0 \\
0 \vee 0 & 0 \vee 1 & 0 \vee 1 \\
1 \vee 0 & 1 \vee 0 & 0 \vee 0
\end{array}\right] \\
& =\left[\begin{array}{lll}
1 & 1 & 0 \\
0 & 1 & 1 \\
1 & 1 & 0
\end{array}\right]
\end {aligned}
$$


## Matrix for composite relations
Suppose $R$ is a relation from $A$ to $B$ and $S$ is a relation from $B$ to $C$. Suppose $A$ $B$ and $C$ have $m$, $n$ and $p$ elements, respectively. Let the boolean matrices for $S \circ R$, $R$, and $S$ be $\mathbf{M}_{S \circ R}=\left[t_{i j}\right]$, $\mathbf{M}_{R}=\left[r_{i j}\right]$, and $\mathbf{M}_{S}=\left[s_{i j}\right]$, respectively. These matrices have sizes $m \times p$, $m \times n$, and $n \times p$, respectively. The ordered pair $\left(a_{i}, c_{j}\right)$ belongs to $S \circ R$ iff there is an element $b_k$ such that $\left(a_{i}, b_{k}\right)$ belongs to $R$ and $\left(b_{k}, c_{j}\right)$ belongs to $S$. It follows that $t_{ij}=1$ iff $r_{i k}=s_{k j}=1$ for some $k$.

From the definition of boolean product this means that 
$$
\mathbf{M}_{S \circ R}=\mathbf{M}_{R} \odot \mathbf{M}_{S}
$$


### Example

$\mathbf{M}_{R}=\left[\begin{array}{lll}1 & 0 & 1 \\ 1 & 1 & 0 \\ 0 & 0 & 0\end{array}\right]$ and $\mathbf{M}_{S}=\left[\begin{array}{lll}0 & 1 & 0 \\ 0 & 0 & 1 \\ 1 & 0 & 1\end{array}\right]$

$$
\mathbf{M}_{S \circ R}=\mathbf{M}_{R} \odot \mathbf{M}_{S}=\left[\begin{array}{ccc}
1 & 1 & 1 \\
0 & 1 & 1 \\
0 & 0 & 0
\end{array}\right]
$$

## Boolean Powers of a Square Zero-One Matrix
Let $\textbf A$ be a square zero-one matrix and let $r$ be a positive integer. The $r$th **boolean power** of $\textbf A$ is the boolean product of $r$ factors of $\textbf A$. The $rth$ boolean product of $\textbf A$ is denoted by $\textbf A^{[r]}$, Hence

$$
\mathbf{A}^{[r]}=\underbrace{\mathbf{A} \odot \mathbf{A} \odot \mathbf{A} \odot \cdots \odot \mathbf{A}}_{r \text { times }} .
$$
We also define $\mathbf{A}^{[0]}$ to be $\mathbf{I}_{n}$.

(Remember that $\textbf I_n$ is the **identity matrix of order** $\textbf n$, which is the $\textbf n \times \textbf n$ matrix $\mathbf{I}_{n}=\left[\delta_{i j}\right]$ (The Kronecker delta) where $\delta_{i j}=1$ if $i=j$ and $\delta_{i j}=0$ if $i \ne j$. Hence,

$$
\mathbf{I}_{n}=\left[\begin{array}{llll}
1 & 0 & \ldots & 0 \\
0 & 1 & \ldots & 0 \\
. & . & & . \\
. & . & & . \\
. & . & & . \\
0 & 0 & \ldots & 1
\end{array}\right]
$$

## Using Matrices Representing the Composite of Two Relations to find the Powers of a relation

The matrix representing the composite of two relations can be used to find the matrix for $\mathbf{M}_{R^{n}}$. In particular, 
$$
\mathbf{M}_{R^{n}}=\mathbf{M}_{R}^{[n]}
$$

### Example
Find the matrix representing $R^2$, where the matrix for $R$ is 
$$\mathbf{M}_{R}=\left[\begin{array}{lll}0 & 1 & 0 \\ 0 & 1 & 1 \\ 1 & 0 & 0\end{array}\right]$$

$$
\mathbf{M}_{R^{2}}=\mathbf{M}_{R}^{[2]}=\left[\begin{array}{lll}
0 & 1 & 1 \\
1 & 1 & 1 \\
0 & 1 & 0
\end{array}\right]
$$

# Representing Relations Using Digraphs