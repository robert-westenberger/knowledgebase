---
title: Sets
description: 
published: true
date: 2021-04-12T01:23:14.459Z
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
$X \subseteq Y$ indicates that $X$ is a subset of $T$ (every element of $S$ is an element of $T$).

$X \subset Y$ indicates that $X$ is a subset of $Y$, but the two are not equal.

$X \subseteq Y \leftrightarrow (x \in X \longrightarrow x \in Y)$ 
#### Union 
$X \cup Y$ The union of sets $X$ and $Y$ contains all elements appearing in $X$ or $Y$.

$$x \in X \cup Y \leftrightarrow x \in X \medspace \vee \medspace x \in Y$$
$$
X \cup Y=\{x \mid x \in X \text { or } x \in Y\}
$$

![union.png](/union.png)
#### Intersection
$X \cap Y$ The intersection of sets $X$ and $Y$ consists of all elements that appear in both $X$ and $Y$.
$$x \in X \cap Y \leftrightarrow x \in X \medspace \wedge \medspace x \in Y$$
$$
X \cap Y=\{x \mid x \in X \text { and } x \in Y\}
$$
![intersection.png](/intersection.png)
#### Difference
$X-Y$ or $X\backslash Y$ of The difference sets $X$ and $Y$ contain all elements that are in $X$, but not in $Y$.

$$x \in X - Y \leftrightarrow x \in X \medspace \wedge \medspace x \notin Y$$

$$
X-Y=\{x \mid x \in X \text { and } x \notin Y\}
$$

![difference.png](/difference.png)
#### Cartesian Product
$X \times Y$ contains all the ordered pairs in which the first elements are selected from $X$, and the second elements are selected from $Y$.

$$X \times Y=\{(x, y) \mid x \in X \wedge y \in Y\}$$
#### Complement 
Often all the sets being considered are subsets of a known domain of discourse $D$. For any subset $A$ of $D$, we define $\bar{A}$ to be the set of all elements of $D$ *not* in $A$. That is, $\bar{A}::=D-A$. The set $\bar{A}$ is the complement of $A$.

For example, the complement of positive real numbers is the set of negative real numbers together with zero when the domain is all real numbers.
$$
\overline{\mathbb{\LARGE R}^{\large +}}=\mathbb{R}^{-} \cup\{0\}
$$

If $A$ is in a universal set $U$, the complement of $A$ is 
$$\bar{A}=\{x \in U \mid x \notin A\}$$
#### Power Set
The collection of all subsets of a set. If $A$ has $n$ elements, there are $2^n$ sets in $pow(A)$.
$$
B \in \operatorname{pow}(A) \quad \text { IFF } \quad B \subseteq A
$$

If $A$ and $B$ are sets, and $f:A \rarr B$ is a function, and $B$ is equal to $P(A)$, this means that $f$ is simply a function that each element of $A$ to some subset of $A$.

The power set of the empty set $\emptyset$ has $2^0=1$ element.


## Set Builder Notation
Used to describe sets that cannot be listed by elements or taking unions, intersections, etc. 

The idea is to define a set using a **predicate**. The set consists of all values that make the predicate true. 

### Examples

$$
A=\{n \in \mathbb{N} \mid n \text { is a prime and } n=4 k+1 \text { for some integer } k\}
$$
The set $A$ consists of all natural numbers $n$ for which the predicate 
$$
" n \text { is a prime and } n=4 k+1 \text { for some integer } k^{\prime \prime}
$$
is true. The smallest elements of $A$ are:

$$
5,13,17,29,37,41,53,57,61,73, \ldots
$$


$$
B=\left\{x \in \mathbb{R} \mid x^{3}-3 x+1>0\right\}
$$
The set $B$ consists of all real numbers $x$ for which the predicate 
$$
x^{3}-3 x+1>0
$$
is true.
$$
C=\left\{a+b i \in \mathbb{C} \mid a^{2}+2 b^{2} \leq 1\right\}
$$

Set $C$ consists of all complex numbers $a+b i$ such that

$$
a^{2}+2 b^{2} \leq 1
$$

## Proving Set Equalities
Two sets are equal if they have exactly the same elements. $X=Y$ means that $z \in X$ if and only if $z \in Y$, for all elements $z$. Set equalities can be formulated and proved as "iff" theorems.

### Example: Proof of Distribute Law for Sets 
**Theorem:** Let $A$, $B$, and $C$ be sets, then 
$$
A \cap(B \cup C)=(A \cap B) \cup(A \cap C)
$$
Note: above read as "The intersection of set A with the union of set B and set C is equivalent to the union of the intersections of sets A and B and sets A and C"

**Proof:** The equality is equivalent to the assertion that 
$$
x \in A \cap(B \cup C) \iff x \in(A \cap B) \cup(A \cap C)
$$
for all x. We prove the above assertion by using a chain of iff's. 

1. Definition of intersection:
$$
x \in A \cap(B \cup C) \iff (x \in A) \wedge (x \in B \cup C)
$$
2. Definition of union:
$$
(x \in A) \wedge (x \in B \cup C) \iff (x \in A) \wedge (x \in B \vee x \in C)
$$
3. AND distributivity:
$$
(x \in A) \wedge (x \in B \vee x \in C) \iff (x \in A \wedge x \in B) \vee (x \in A \wedge x \in C)
$$
4. Definition of intersection
$$
(x \in A \wedge x \in B) \vee (x \in A \wedge x \in C) \iff (x \in A \cap B) \vee (x \in A \cap C)
$$
5. Definition of union
$$
(x \in A \cap B) \vee (x \in A \cap C) \iff x \in(A \cap B) \cup(A \cap C)
$$
$$\hspace{24em} \blacksquare$$