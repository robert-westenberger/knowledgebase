---
title: Graphs
description: 
published: true
date: 2021-04-30T19:01:15.249Z
tags: discrete-mathematics
editor: markdown
---

# Directed Graph / Digraph
A directed graph is the same as a binary relation on a set $A$, but we picture the digraph geometrically by representing elements of $A$ as points on the plane, with an arrow from the point for $a$ to the point for $b$ exactly when $aRb$. The elements of $A$ are referred to as the vertices of the digraph.

Below, the divisibility relation on $\{1,2, \ldots, 12\}$ is represented by the following digraph:

![digraph_example_1.png](/digraph_example_1.png)

## Paths in Digraphs
A path in a digraph, $R$, is a sequence of vertices $a_{0}, \ldots, a_{k}$, with $k \ge 0$ such that $a_{i} R a_{i+1}$, for every $0 \le i \lt k$. The path is said to start at $a_0$, to end at $a_k$, and the length of the path is defined to be $k$.

Many of the relation properties have geometric descriptions in terms of digraphs. For example: 

**Reflexivity:** All vertices have self loops (a self loop at a vertex is an arrow going from the vertex back to itself)

**Irreflexivity:** No vertices have selfloops.
**Symmetry:** All edges are bidirectional. 
**Transitivity:** Shortcircuits—for any path through the graph, there is an arrow from the first vertex to the last veretx in the path. 


We can define some new relations based on paths. Let $R$ be a digraph with vertices, $A$. Define relations $R^{\ast}$ and $R^+$ on $A$ by the conditions that 

$$
\begin{array}{ll}
a R^{\ast} b & ::=  \quad \text{there is a path in} \medspace R \medspace \text{from} \medspace a \medspace \text {to} \medspace b \\
a R^{+} b & ::= \quad \text{there is a positive length path in} \medspace R \medspace \text{from} \medspace a \medspace \text {to} \medspace b 
\end{array}
$$

$R^{\ast}$ is called the **path relation** of $R$. It follows from the definition of path that $R^{\ast}$ is transitive. IT is also reflexive because it has $0$ length paths and it contains the graph of $R$ because of the length-one paths. $R^+$ is called the positive-length path relation; it also contains graph $(R)$ and is transitive.