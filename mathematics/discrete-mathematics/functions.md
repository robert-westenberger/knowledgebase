---
title: Functions
description: 
published: true
date: 2021-04-29T19:07:09.570Z
tags: mathematics, discrete-mathematics
editor: markdown
---

A **function** assigns an element of one set, the **domain**, to elements of another set called the **codomain**.

The notation 
$$
f: A \rightarrow B
$$
indicates that $f$ is a function with domain $A$ and codomain $B$.

The notation 
$$
f(a)=b
$$
indicates that $f$ assigns the element $b \in B$ to $a$. Here $b$ would be called the $value$ of $f$ at argument $a$.

For example, consider two sets and a function. The first set is students in a discrete math class, $\{ \text{Adams}, \text{Chou}, \text{Smith}, \text{Rodriguez}, \text{Stevens} \}$. The second set are letter grades, $\{ \text{A}, \text{B}, \text{C}, \text{D}, \text{F} \}$.  The function $G$ assigns letter grades to students. Suppose the grades assigned are $A$ for $\text{Adams}$, $C$ for $\text{Chou}$, $B$ for $\text{Smith}$, $A$ for $\text{Rodriguez}$, $F$ for $\text{Stevens}$.

The domain of $G$ in the above example is the set of students. The codomain is the set of letter grades. The range of $G$ is the set $\{A, B, C, F\}$ since nobody is assigned a $D$ grade. 
## Defining Functions
Every function can be described in four ways: algebraically (formula), numerically (a table), graphically, or in words. 

Functions are often defined by formulas, for example $f_{1}(x)::=\frac{1}{x^{2}}$. Notice how this won't assign a value for every element in the domain (value at 0 will be undefined). 

**Support** of the function - The set of domain elements for which a function is defined.

**Total function** - A function that assigns a value to every element of its domain.

A function with a finite domain could be represented with a with a truth table to show the value of the function at each element of the domain. For example, a function $f_{4}(P, Q)$ where $P$ and $Q$ are propositional variables is specified by: 
$$
\begin{array}{|cc|c|}
\hline P & Q & f_{4}(P, Q) \\
\hline \mathbf{T} & \mathbf{T} & \mathbf{T} \\
\hline \mathbf{T} & \mathbf{F} & \mathbf{F} \\
\hline \mathbf{F} & \mathbf{T} & \mathbf{T} \\
\hline \mathbf{F} & \mathbf{F} & \mathbf{T} \\
\hline
\end{array}
$$

## Image and Inverse Image
Given a function $f: A \rightarrow B$, the **image** (or **range**) of a function is the set of all output values it may produce. The **image** of set $A$ is the **range** of $f$, which is the set of all possible images that $f$ can assume.

More formally, given a function $f: A \rightarrow B$, and $C \subseteq A$, the **image of** $c$ **under** $f$ is defined as 
$$
f(C)=\{f(x) \mid x \in C\}
$$
In other words, $f(C)$ is the set of all the images of the elements of $C$.

Things to remember

1. It is about the image of a subset  𝐶  of the domain of  𝐴 . Do not confuse it with the image of an element  𝑥  from  𝐴 
2. Therefore, do not merely say “the image.” Be specific: the image of an element, or the image of a subset.
3. Better yet: include the notation  𝑓(𝑥)  or  𝑓(𝐶)  in the discussion.
4. While  𝑓(𝑥)  is an element in the codomain,  𝑓(𝐶)  is a subset of the codomain.
5. Perhaps, the most important thing to remember is:
If $y \in f(C)$, then $y \in B$, and then there exists an $x \in C$ such that $f(x) = y$.


### Examples
#### Example 1
Let the function $f: \mathbb{R} \rightarrow \mathbb{R}$ be defined by 
$$
f(x)=x^{2}
$$
We find the range of $F$ is $\lbrack 0, \infty)$ We also have, for example, $f(\lbrack 2, \infty))=\lbrack 4, \infty)$. It is clear that $f$ is neither one-to-one nor onto.
#### Example 2
Let the function $g: \mathbb{Z} \rightarrow \mathbb{Z}$ be defined by:

$$g(n)=n+3$$

we find the range of $g$ is $\mathbb Z$, and $g(\mathbb{N})=\{4,5,6, \ldots\}$. The function $g$ is both one-to-one and onto. 

#### Example 3
Consider the function $f:\{1,2,3,4,5,6\} \rightarrow\{a, b, c, d\}$ given by

$$
f=\left(\begin{array}{llllll}
1 & 2 & 3 & 4 & 5 & 6 \\
a & a & b & b & b & c
\end{array}\right)
$$
Find $f(\{1,2,3\}), f^{-1}(\{a, b\})$ and $f^{-1}(d)$

##### Solution
$f(\{1,2,3\})=\{a, b\}$ since $a$ and $b$ are the elements in the codomain to which $f$ sends 1 and 2.
$f^{-1}(\{a, b\})=\{1,2,3,4,5\}$ since these are exactly the elements that $f$ sends to $a$ and $b$.
$f^{-1}(d)=\emptyset$ since $d$ is not in the range of $f$.
## Function Composition
Composing functions $f$ and $f$ means that $f$ is applied to some argument, $x$, to produce $f(x)$, and then $g$ is applied to that result to produce $g(f(x))$. 

For functions $f: A \rightarrow B$ and $g: B \rightarrow C$, the **composition** $g \circ f$, of $g$ with $f$ is defined to be the function from $A$ to $C$ defined by the rule: 
$$
(g \circ f)(x)::=g(f(x))
$$
for all $x \in A$.

## Types of Functions
(Diagrams of two example functions)![diagrams_of_two_functions.png](/diagrams_of_two_functions.png)

(Left is total and surjective, but not injective)
(Right is total and injective but not surjective)
(If $f$ is a function, it means that every point in the domain column, $A$, has at most one arrow out of it. (If more than one arrow comes out of the first column, then it would be a relation not a function). 


We say a function $f: A \rightarrow B$ is:

### Total and Partial
**Total** if every element of $A$ is assigned to some element of $B$, otherwise $f$ is called a **partial** function.

"$f$ is total" means that every point in the domain column of a function graph has at least one arrow out of it, which really means it has exactly one arrow out of it since $f$ is a function. 
### Surjective
If every element of $B$ is mapped at least once. Also known as **onto**.
This is a property of the codomain.
For every element $b \in B$, there exists an element $a \in A$ such that
$$f(a) = b$$


"$f$ is surjective" means that evry point in the codomain column has at least one arrow into it.
If $A$ is a finite set, we let $|A|$ be the number of elements in $A$. If $f : A \rarr B$ is surjective, then $|A| \geq|B|$.
### Injective
If every element of $B$ is mapped to at most once. Also known as **one-to-one**. This is a property of the domain of a function. 

"$f$ is injective" means that every point in the codomain column, $B$, has at most one arrow into it. 

If $A$ is a finite set, we let $|A|$ be the number of elements in $A$. If $f : A \rarr B$ is total and injective, then $|A| \leq|B|$.

$$
f\left(x_{1}\right)=f\left(x_{2}\right) \Rightarrow x_{1}=x_{2}
$$
for all elements $x_{1}, x_{2} \in A$
### Bijective
If $f$ is total, surjective, and injective. In particular, each element of $B$ is mapped to exactly once.

"$f$ is bijective" means that every point in the $A$ column has exactly one arrow out of it, and every point in the $B$ column has exactly one arrow into it.
If $A$ is a finite set, we let $|A|$ be the number of elements in $A$. If $f : A \rarr B$ is bijective, then $|A| =|B|$.

## Increasing and Decreasing
A function $f$ whose domain and codomain are subsets of the set of real numbers is **increasing** if $f(x) \leq f(y)$ and **strictly increasing** if $f(x) \lt f(y)$, wherever $x \lt y$ and $x$ and $y$ are in the domain of $f$. $f$ is **decreasing** if $f(x) \geq f(y)$ and **stricly decreasing** if $f(x) \gt f(y)$


## Equivalence Relations

### Equivalence by Function
Given any total function $f$ with domain $A$, define the binary relation $\equiv_{f}$ on $A$ by the rule 
$$
a \equiv_{f} b \quad \text { iff } \quad f(a)=f(b)
$$
for all $a, b \in A$
A binary relation is an **equivalence relation** iff it equals $\equiv_{f}$ for some $f$.

Abstractly, we assume there is some function that extracts the angles, size, color, or whatever other property of elements we’re interested in. Two elements would be considered equivalent iff the function extracts the same value for each.

For example, if $f_{c}$ is the function mapping a triangle to the lengths of its sides, then $f_{c}$ determines the congruence relation. If $f_{s}$ is the function mapping a triangle to the sizes of its angles, then $f_{s}$ determines the similarity relation.

### Partitions
A partition of a set $A$, is a collection $\mathcal{A}$, of nonempty sets called the blocks of the partition such that 
1. $A=\textstyle\bigcup_{B \in \mathcal A}B$ and
2. if $B_{1} \neq B_{2}$ are blocks of $\mathcal A$, then $B_1$ and $B_2$ are disjoint (they have no elements in common and their intersection is empty).

For example, we can partition the integers into four blocks according to whether their remainder on division by $4$ is $0$, $1$, $2$, or $3$:
$$
\begin{array}{l}
\{0,4,-4,8,-8,12, \ldots\} \\
\{1,-3,5,-7,9,-11, \ldots\} \\
\{2,-2,6,-6,10,-10, \ldots\} \\
\{3,-1,7,-5,11,-9, \ldots\}
\end{array}
$$

We could partition the pixels of an image by their color. So there will be between $2$ and several million blocks depending on whether the image is pure black and white or is true color.

The relation of **being in the same block** is an equivalence relation. We can extract an equivalence relation from any partition, and conversely, we can define a partition determined by any equivalence relation. Partitions and equivalence relations are interchangeable ways of talking about the same thing.

## Properties of Equivalence Relations


### Reflexive
$(a, a) \in R$ for every element $a \in A$.
A relation $R$ on a set $A$ is reflexive iff for every $a \in A$, $aRa$.
In a reflexive relation, an element is always related to itself. For example, let $R$ be the relation on the set of all people consisting of pairs $(x, y)$ where $x$ and $y$ have the same mother and the same father. Then $xRx$ for every person $x$.

### Symmetric
$(b, a) \in R$ whenever $(a,b) \in R$, for all $a,b \in A$. 
A relation $R$ on $A$ is **symmetric** iff for all $a,b \in A$, if $aRb$ then $bRa$.


In other words, a relation is **symmetric** iff $a$ is related to $b$ always implies that $b$ is related to $a$. 

The equality relation is symmetric since $x=y \leftrightarrow y=x$. 


### Antisymmetric
A relation $R$ on a set $A$ such that for all $a,b \in A$, if $(a,b) \in R$ and $(b, a) \in R$, then $a=b$ is called **antisymmetric**.
In other words, a relation is **antisymmetric** iff there are no pairs of distinct elements $a$ and $b$ with $a$ related to $b$ and $b$ related to $a$.That is, the only way to have $a$ related to $b$ and $b$ related to $a$ is for $a$ and $b$ to be the same element. 

The less than or equal to relation is antisymmetric. $a \le b$ and $b \le a$ implies $a=b$.

**Note that symmetric and asymmetric are not opposites.** A relation can have both or lack both.

### Transitive
A relation $R$ on a set $A$ is called transitive if whenever $(a, b) \in R$ and $(b, c) \in R$, then $(a, c) \in R$, for all $a, b, c \in A$

For example, $\boldsymbol{G}: \mathbb{R} \rightarrow \mathbb{R}$ by $x G y \Longleftrightarrow x>y$. Since $a \gt b$ and $b \gt c$ then $a \gt c$ is true for all $a, b, c \in \mathbb{R}$, then $G$ is transitive.

## Partial Orders
A general example of a partial order is the subset relation $\subset$ on sets. For any element, $a$, we think of a function, $g$, such that $g(a)$ is the set of properties that $a$ has. Then we relate different elements according to how their properties compare.

For partial orders the symbols $\prec$ or $\preceq$ are used because they resemble the symbols used for subset and less-or-equal, which are the most common partial orders.



The most familiar examples of partial orders are the "less than relations", for example, the $\lt$ relation on real numbers. To see that $\lt$ is indeed a partial order, just define $h(r)::=\{q \in \mathbb{Q} \mid q<r\}$. Since there is a rational number between any two real numbers, it follows that $\lt$ is simply $\prec_{h}$. Likewise, the relation $\le$ is a partial order because it agrees with $\prec_{h}$ for all pairs of distinct real numbers.

### Definitions

Given any total function, $g$, form a set, $A$, to a collection of sets, define the binary relation $\prec_{g}$ on $A$ by the rule 

$$
a \prec_{g} b \quad \text { iff } \quad g(a) \subset g(b)
$$
for $a, b \in A$. A binary relation, $R$, on a set, $A$, is a partial order if and only if ther eis a $g$ such that $R$ agrees with $\prec_{g}$ for every pair of distinct elements. That is, 
$$
a R b \quad \text { iff } \quad a \prec_{g} b
$$
for all $a \neq b \in A$

A partial order is called **weak** iff it is reflexive. For example, the relation $\le$ on the real numbers and the relation $\subseteq$ on sets, are weak partial orders.

A binary relation, $R$, on a set, $A$, is **irreflexive** iff for all $a \in A$ it is not true that $aRa$. A partial order is **strict** iff it is irreflexive. 

The $\lt$ relation on the reals and the proper subset relation $\subset$ are strict partial orers. In general, a partial order may be neither weak nor strict; this happens when some elements are related to themselves and others are not.

### Properties of Partial Orders
Every partial order is transitive.
## Total Orders
Given any two numbers, one will be bigger than the other. Partial orders with this property are **total orders**.

Let $R$ be a binary relation on a set, $A$, and let $a,b$ be elements of $A$. Then $a$ and $b$ are comparable with respect to $R$ iff ($aRb$ or $bRa$). A partial order under which every two distinct elements are comparable is called a total order. 