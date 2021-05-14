---
title: Closures of Relations
description: 
published: true
date: 2021-05-14T17:52:54.754Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Types of Closures

If $R$ is a relation on a set $A$, it may or may not have some property $\textbf P$, such as reflexivity, symmetry, or transitivity. When $R$ does not enjoy propety $\textbf P$, we would like to find the smallest relation $S$ on $A$ with property $\textbf P$ that contains $R$.

If $R$ is a relation on a set $A$, then the **closure** of $R$ with respect to $P$, if it exists, is the relation $S$ on $A$ with property $P$ that ocntains $R$ and is a subset of every subset $A \times A$ containing $R$ with property $P$.

## Reflexive Closure

The relation $R=\{(1,1),(1,2),(2,1),(3,2)\}$ on set $A=\{1,2,3\}$ is not reflexive. By adding $(2,2)$ and $(3,3)$ to $R$, $R$ is now reflexive. This new relation contains $R$. Any reflexive relation that contains $R$ must also contain $(2,2)$ and $(3,3)$. Because this relation contains $R$, is reflexive, and is contained within every reflexive relation that contains $R$, it is called the **reflexive closure** of $R$.

As the above example illustrates, given a relation $R$ on a set $A$, the reflexive closure of $R$ can be formed by adding to $R$ all pairs of the form $(a, a)$ with $a \in A$, not already in $R$. The addition of these pairs produces a new relation that is reflexive, contains $R$, and is contained within any reflexive relation containing $R$. We see that the reflexive closure of $R$ equals $R \cup \Delta$, where $\Delta=\{(a, a) \mid a \in A\}$ is the **diagonal relation** on $A$.

### Example
What is the reflexive closure of the relation $R=\{(a, b) \mid a<b\}$ on the set of integers?

The reflexive closure of $R$ is 
$$
R \cup \Delta=\{(a, b) \mid a<b\} \cup\{(a, a) \mid a \in \mathbf{Z}\}=\{(a, b) \mid a \leq b\}
$$

