---
title: Closures of Relations
description: 
published: true
date: 2021-05-14T17:45:57.517Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Types of Closures

If $R$ is a relation on a set $A$, it may or may not have some property $\textbf P$, such as reflexivity, symmetry, or transitivity. When $R$ does not enjoy propety $\textbf P$, we would like to find the smallest relation $S$ on $A$ with property $\textbf P$ that contains $R$.

If $R$ is a relation on a set $A$, then the **closure** of $R$ with respect to $P$, if it exists, is the relation $S$ on $A$ with property $P$ that ocntains $R$ and is a subset of every subset $A \times A$ containing $R$ with property $P$.

## Example
The relation $R=\{(1,1),(1,2),(2,1),(3,2)\}$ on set $A=\{1,2,3\}$ is not reflexive. By adding $(2,2)$ and $(3,3)$ to $R$, $R$ is now reflexive. This new relation contains $R$. Any reflexive relation that contains $R$ must also contain $(2,2)$ and $(3,3)$. Because this relation contains $R$, is reflexive, and is contained within every reflexive relation that contains $R$, it is called the r**eflexive closure** of $R$.