---
title: Closures of Relations
description: 
published: true
date: 2021-05-14T18:41:23.468Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Types of Closures

If $R$ is a relation on a set $A$, it may or may not have some property $\textbf P$, such as reflexivity, symmetry, or transitivity. When $R$ does not enjoy propety $\textbf P$, we would like to find the smallest relation $S$ on $A$ with property $\textbf P$ that contains $R$.

If $R$ is a relation on a set $A$, then the **closure** of $R$ with respect to $P$, if it exists, is the relation $S$ on $A$ with property $P$ that ocntains $R$ and is a subset of every subset $A \times A$ containing $R$ with property $P$.

## Reflexive Closure

The relation $R=\{(1,1),(1,2),(2,1),(3,2)\}$ on set $A=\{1,2,3\}$ is not reflexive. By adding $(2,2)$ and $(3,3)$ to $R$, $R$ is now reflexive. This new relation contains $R$. Any reflexive relation that contains $R$ must also contain $(2,2)$ and $(3,3)$. Because this relation contains $R$, is reflexive, and is contained within every reflexive relation that contains $R$, it is called the **reflexive closure** of $R$.

As the above example illustrates, given a relation $R$ on a set $A$, the reflexive closure of $R$ can be formed by adding to $R$ all pairs of the form $(a, a)$ with $a \in A$, not already in $R$. The addition of these pairs produces a new relation that is reflexive, contains $R$, and is contained within any reflexive relation containing $R$. We see that the reflexive closure of $R$ equals $R \.
3+\Delta$, where $\Delta=\{(a, a) \mid a \in A\}$ is the **diagonal relation** on $A$.

### Example
What is the reflexive closure of the relation $R=\{(a, b) \mid a<b\}$ on the set of integers?

The reflexive closure of $R$ is 
$$
R \cup \Delta=\{(a, b) \mid a<b\} \cup\{(a, a) \mid a \in \mathbf{Z}\}=\{(a, b) \mid a \leq b\}
$$

## Symmetric Closure
The relation $R=\{(1,1),(1,2),(2,2),(2,3),(3,1),(3,2)\}$ on a set $A=\{1,2,3\}$ can be made symmetric by adding $(2,1)$ and $(1,3)$, the only pairs of the form $(b,a)$ with $(a,b) \in R$ that are not in $R$. This new relation is the **symmetric closure** of $R$.

The symmetric closure of a relation can be constructed by taking the union of a relation with its inverse, this is, $R \cup R^{-1}$ is the symmetric closure of $R$, where $R^{-1}=\{(b, a) \mid(a, b) \in R\}$.

### Example 
What is the symmetric closure of the relation $R=\{(a, b) \mid a>b\}$ on the set of positive integers?

$$
R \cup R^{-1}=\{(a, b) \mid a>b\} \cup\{(b, a) \mid a>b\}=\{(a, b) \mid a \neq b\}
$$
## Transitive Closures
These are a little more complicated. Take for example a relation $R=\{(1,3),(1,4),(2,1),(3,2)\}$ on a set $A=\{1,2,3,4\}$. The relation isn't transitive because it does not contain all pairs of the form $(a,c)$ where $(a,b)$ and $(b,c)$ are in $R$. The pairs of this form not in $R$ are $(1,2)$, $(2,3)$, $(2,4)$, and $(3,1)$. Adding these pairs doesn't produce a transitive relation because the resulting relation contains $(3,1)$ and $(1,4)$ but does not contain $(3,4)$.
# Paths in Directed Graphs
A **path** from $a$ to $b$ in the directed graph $G$ is a sequence of edges $\left(x_{0}, x_{1}\right),\left(x_{1}, x_{2}\right)$, $\left(x_{2}, x_{3}\right), \ldots,\left(x_{n-1}, x_{n}\right)$ in $G$, where $n$ is a nonnegative integer, and $x_{0}=a$ and $x_{n}=b$, that is, a sequence of edges where the terminal vertex of an edge is the same as the initial vertex in the next edge in the path. This path is denoted by $x_{0}, x_{1}, x_{2}, \ldots, x_{n-1}, x_{n}$ and has **length** $n$. We view the empty set of edges as a path of length zero from $a$ to $a$. A path of length $n \geq 1$ that begins and ends at the same vertex is called a **circuit** or **cycle**.

The term **path** also applies to relations. Carrying over the definition from directed graphs to relations, there is a path from $a$ to $b$ in $R$ if there is a sequence of elements $a, x_{1}, x_{2}, \ldots, x_{n-1}, b$ with $\left(a, x_{1}\right) \in R,\left(x_{1}, x_{2}\right) \in R, \ldots$, and $\left(x_{n-1}, b\right) \in R .$ Theorem 1 can be obtained from the definition of a path in a relation.


## Theorem 1
Let $R$ be a relation on a set $A$. There is a path of length $n$, where $n$ is a positive integer, from $a$ to $b$ if and only if $(a, b) \in R^{n}$.

### Proof of Theorem 1
**Proof:** We will use mathematical induction. By definition, there is a path from $a$ to $b$ of length one if and only if $(a, b) \in R$, so the theorem is true when $n=1$.

Assume that the theorem is true for the positive integer $n$. This is the inductive hypothesis. There is a path of length $n+1$ from $a$ to $b$ if and only if there is an element $c \in A$ such that there is a path of length one from $a$ to $c$, so $(a, c) \in R$, and a path of length $n$ from $c$ to $b$, that is, $(c, b) \in R^{n} .$ Consequently, by the inductive hypothesis, there is a path of length $n+1$ from $a$ to $b$ if and only if there is an element $c$ with $(a, c) \in R$ and $(c, b) \in R^{n} .$ But there is such an element if and only if $(a, b) \in R^{n+1}$. Therefore, there is a path of length $n+1$ from $a$ to $b$ if and only if $(a, b) \in R^{n+1}$. This completes the proof. $\blacksquare$.