---
title: Functions
description: 
published: true
date: 2021-03-04T17:41:50.755Z
tags: mathematics, discrete-mathematics
editor: markdown
---

A **function** assigns an element of one set, the **domain**, to elements of another set called the **codomain**.

The notation 
$$
f: A \rightarrow B
$$
indicates that $f$ is a function domain $A$ and codomain $B$.

The notation 
$$
f(a)=b
$$
indicates that $f$ assigns the element $b \in B$ to $a$. Here $b$ would be called the $value$ of $f$ at argument $a$.
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
Given a function $f: A \rightarrow B$, the **image** of a function is the set of all output values it may produce. The **image** of set $A$ is the $range$ of $f$, which is the set of all possible images that $f$ can assume.

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


## Function Composition
Composing functions $f$ and $f$ means that $f$ is applied to some argument, $x$, to produce $f(x)$, and then $g$ is applied to that result to produce $g(f(x))$. 

For functions $f: A \rightarrow B$ and $g: B \rightarrow C$, the **composition** $g \circ f$, of $g$ with $f$ is defined to be the function from $A$ to $C$ defined by the rule: 
$$
(g \circ f)(x)::=g(f(x))
$$
for all $x \in A$.

## Binary Relations
A **binary relation**, $R$, consists of a set, $A$, called the **domain** of $R$, a set, $B$, called the **codomain** of $R$, and a subset of $A \times B$ called the **graph** of $R$. 

A relation whose domain is $A$ and codomain is $B$ is said to be "between $A$ and $B$", or "from $A$ to $B$." 

When the domain and codomain are the same set, $A$, we simply say the relation is "on A." 

It is common to use "$a \medspace R \medspace b$" to mean the pair $(a, b)$ is in the graph of $R$.

## Types Binary Relations
We say a function $f: A \rightarrow B$ is:

### Total and Partial
**Total** if every element of $A$ is assigned to some element of $B$, otherwise $f$ is called a **partial** function.
### Surjective
If every element of $B$ is mapped at least once. Also known as **onto**.

For every element $b \in B$, there exists an element $a \in A$ such that
$$f(a) = b$$
### Injective
If every element of $B$ is mapped to at most once. Also known as **one-to-one**.

$$
f\left(x_{1}\right)=f\left(x_{2}\right) \Rightarrow x_{1}=x_{2}
$$
for all elements $x_{1}, x_{2} \in A$
### Bijective
If $f$ is total, surjective, and injective. In particular, each element of $B$ is mapped to exactly once.