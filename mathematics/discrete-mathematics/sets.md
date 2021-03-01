---
title: Sets
description: 
published: true
date: 2021-03-01T03:35:45.568Z
tags: mathematics, discrete-mathematics
editor: markdown
---

A set is a bunch of objects, which are called **elements** of the set. 


$$
\begin{aligned}
\mathbb{N} &=\{0,1,2,3, \ldots\} & & \text {the natural numbers } \\
C &=\{\text { red, blue, yellow }\} & & \text {primary colors } \\
D &=\{\text { Teddy, Sheba, Bella }\} & & \text {dead pets } \\ 
P &=\{\{a, b\},\{a, c\},\{b, c\}\} & & \text {a set of sets}
\end{aligned}
$$

The order of elements in a set don't matter. 

Any object only appears in a set once (it's either in the set or not).

The expression $e \in S$ asserts that $e$ is an element of set $S$.

### Popular Sets

$$
\begin{array}{lll}
\textbf { symbol } & \textbf { set } & \textbf { elements } \\
\emptyset & \text { the empty set } & \text { none } \\
\mathbb{N} & \text { nonnegative integers } & \{0,1,2,3, \ldots\} \\
\mathbb{Z} & \text { integers } & \{\ldots,-3,-2,-1,0,1,2,3, \ldots\} \\
\mathbb{Q} & \text { rational numbers } & \frac{1}{2},-\frac{5}{3}, 16, \text { etc. } \\
\mathbb{R} & \text { real numbers } & \pi, e,-9, \sqrt{2}, \text { etc. } \\
\mathbb{C} & \text { complex numbers } & i, \frac{19}{2}, \sqrt{2}-2 i, \text { etc. }
\end{array}
$$

A superscript + or - restricts a set to positive or negative elements.

### Comparing and Combining Sets

#### Subset 
$S \subseteq T$ indicates that S is a subset of T (every element of S is an element of T).

$S \subset T$ indicates that S is a subset of T, but the two are not equal.

#### Union 
$X \cup Y$ The union of sets $X$ and $Y$ contains all elements appearing in $X$ or $Y$.
#### Intersection
$X \cap Y$ The intersection of sets $X$ and $Y$ consists of all elements that appear in both $X$ and $Y$.
#### Difference
$X-Y$ of The difference sets $X$ and $Y$ contain all elements that are in $X$, but not in $Y$.
#### Complement 
Often all the sets being considered are subsets of a known domain of discourse $D$. For any subset $A$ of $D$, we define $\bar{A}$ to be the set of all elements of $D$ *not* in $A$. That is, $\bar{A}::=D-A$. The set $\bar{A}$ is the complement of $A$.

For example, the complement of positive real numbers is the set of negative real numbers together with zero when the domain is all real numbers.
$$
\overline{\mathbb{R}^{+}}=\mathbb{R}^{-} \cup\{0\}
$$
