---
title: Graphs
description: 
published: true
date: 2021-04-30T18:31:17.325Z
tags: discrete-mathematics
editor: markdown
---

# Directed Graph / Digraph
A directed graph is the same as a binary relation on a set $A$, but we picture the digraph geometrically by representing elements of $A$ as points on the plane, with an arrow from the point for $a$ to the point for $b$ exactly when $aRb$. The elements of $A$ are referred to as the vertices of the digraph.

Below, the divisibility relation on $\{1,2, \ldots, 12\}$ is represented by the following digraph:

![digraph_example_1.png](/digraph_example_1.png)

## Paths in Digraphs
A path in a digraph, $R$, is a sequence of vertices $a_{0}, \ldots, a_{k}$, with $k \ge 0$ such that $a_{i} R a_{i+1}$, for every $0 \le i \lt k$. The path is said to start at $a_0$, to end at $a_k$, and the length of the path is defined to be $k$.

Many of the relation properties have geometric descriptions in terms of digraphs.