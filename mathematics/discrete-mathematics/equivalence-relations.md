---
title: Equivalence Relations
description: 
published: true
date: 2021-05-17T19:00:09.123Z
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
## Theorem 1
Shows that the equivalence classes of two elements of $A$ are either identical or disjoint. 

Let $R$ be an equivalence relation on a set $A .$ These statements for elements $a$ and $b$ of $A$ are equivalent:
(i) $a R b$
(ii) $[a]=[b]$
$(i i i)[a] \cap[b] \neq \emptyset$
