---
title: Equivalence Relations
description: 
published: true
date: 2021-06-19T21:25:02.647Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Equivalence Relations
A relation on a set $A$ is called an equivalence relation if it is reflexive, symmetric, and transitive.

Two elements $a$ and $b$ that are related by an equivalence relation are called equivalent. The notation $a \sim b$ is often used to denote that $a$ and $b$ are equivalent elements with respect to a particular equivalence relation.

# Equivalence Classes
Let $R$ be an equivalence relation on a set $A .$ The set of all elements that are related to an element $a$ of $A$ is called the equivalence class of $a$. The equivalence class of $a$ with respect to $R$ is denoted by $[a]_{R}$. When only one relation is under consideration, we can delete the subscript $R$ and write $[a]$ for this equivalence class.

In other words, if $R$ is an equivalence relation on a set $A$, the equivalence class of the element $a$ is
$$
[a]_{R}=\{s \mid(a, s) \in R\}
$$
If $b \in[a]_{R}$, then $b$ is called a representative of this equivalence class. Any element of a class can be used as a representative of this class. That is, there is nothing special about the particular element chosen as the representative of the class.

# Equivalence Classes and Partitions
Cutting up a set into a bunch of different pieces is called **partitioning** the set. 

**Definition 2.3.** A partition of a set, $A$, is a collection, $\mathcal{A}$, of nonempty sets called the blocks of the partition such that
1. $A=\bigcup_{B \in \mathcal{A}} B$, and
2. if $B_{1} \neq B_{2}$ are blocks of $\mathcal{A}$, then $B_{1}$ and $B_{2}$ are disjoint $^{1}$.
## Theorem 1
Shows that the equivalence classes of two elements of $A$ are either identical or disjoint. 

Let $R$ be an equivalence relation on a set $A .$ These statements for elements $a$ and $b$ of $A$ are equivalent:
(i) $a R b$
(ii) $[a]=[b]$
$(i i i)[a] \cap[b] \neq \emptyset$

### Proof of Theorem 1
We first show that $(i)$ implies $(i i) .$ Assume that $a R b$. We will prove that $[a]=[b]$ by showing $[a] \subseteq[b]$ and $[b] \subseteq[a]$. Suppose $c \in[a]$. Then $a R c$. Because $a R b$ and $R$ is symmetric, we know that $b R a$. Furthermore, because $R$ is transitive and $b R a$ and $a R c$, it follows that $b R c$. Hence, $c \in[b]$. This shows that $[a] \subseteq[b]$. The proof that $[b] \subseteq[a]$ is similar; it is left as an exercise for the reader.

Second, we will show that (ii) implies (iii). Assume that $[a]=[b] .$ It follows that $[a] \cap[b] \neq \emptyset$ because $[a]$ is nonempty (because $a \in[a]$ because $R$ is reflexive).

Next, we will show that (iii) implies ( $i$ ). Suppose that $[a] \cap[b] \neq \emptyset$. Then there is an element $c$ with $c \in[a]$ and $c \in[b] .$ In other words, $a R c$ and $b R c .$ By the symmetric property, $c R b$. Then by transitivity, because $a R c$ and $c R b$, we have $a R b$.

Because (i) implies (ii), (ii) implies (iii), and (iii) implies ( $i$ ), the three statements, (i), (ii)., and (iii), are equivalent.

## How An Equivalence Class Partitions a Set

Let $R$ be an equivalence relation on a set $A$. The union of the equivalence classes of $R$ is all of $A$, because an element $a$ of $A$ is in its own equivalence class, namely, $[a]_{R}$. In other words,
$$
\bigcup_{a \in A}[a]_{R}=A .
$$
In addition, from Theorem 1, it follows that these equivalence classes are either equal or disjoint,
So
$$
[a]_{R} \cap[b]_{R}=\emptyset
$$
when $[a]_{R} \neq[b]_{R}$.

These two observations show that the equivalence classes form a partition of $A$, because they split $A$ into disjoint subsets. More precisely, a **partition** of a set $S$ is a collection of disjoint nonempty subsets of $S$ that have $S$ as their union. In other words, the collection of subsets $A_{i}$, $i \in I$ (where $I$ is an index set) forms a partition of $S$ if and only if
$A_{i} \neq \emptyset$ for $i \in I$
$A_{i} \cap A_{j}=\emptyset$ when $i \neq j$,
and
$\bigcup_{i \in I} A_{i}=S$
(Here the notation $\bigcup_{i \in I} A_{i}$ represents the union of the sets $A_{i}$ for all $i \in I$.) 


## Theorem 2
Let $R$ be an equivalence relation on a set $S$. Then the equivalence classes of $R$ form a partition of $S$. Conversely, given a partition $\left\{A_{i} \mid i \in I\right\}$ of the set $S$, there is an equivalence relation $R$ that has the sets $A_{i}, i \in I$, as its equivalence classes.