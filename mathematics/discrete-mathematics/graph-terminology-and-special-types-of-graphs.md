---
title: Graph Terminology and Special Types of Graphs
description: 
published: true
date: 2021-07-05T01:58:28.184Z
tags: computer-science, mathematics, discrete-mathematics
editor: markdown
---


# Undirected Graph Terminology
Two vertices $u$ and $v$ in an undirected graph $G$ are called **adjacent** (or **neighbors**) in $G$ if $u$ and $v$ are endpoints of an edge $e$ of $G$. Such an edge $e$ is called **incident** with the vertices $u$ and $v$ and $e$ is said to **connect** $u$ and $v$.

The set of all neighbors of a vertex $v$ of $G=(V, E)$, denoted by $N(v)$, is called the **neighborhood** of $v$. If $A$ is a subset of $V$, we denote by $N(A)$ the set of all vertices in $G$ that are adjacent to at least one vertex in $A .$ So, $N(A)=\bigcup_{v \in A} N(v)$.

The **degree of a vertex in an undirected graph** is the number of edges incident with it, except that a loop at a vertex contributes twice to the degree of that vertex. The degree of the vertex $v$ is denoted by $\operatorname{deg}(v)$. 

A vertex of degree zero is **isolated**.
A vertex of degree one is **pendant**.

## Handshaking Theorem
Let $G=(V, E)$ be an undirected graph with $m$ edges. Then
$$
2 m=\sum_{v \in V} \operatorname{deg}(v)
$$
(In other words, the sum of the degrees of the vertices in a graph equals twice the number of edges)
(Note that this applies even if multiple edges and loops are present.)

## Vertices and Degrees of Undirected Graphsd
**An undirected graph has an even number of vertices of odd degree.**
**Proof:** Let $V_{1}$ and $V_{2}$ be the set of vertices of even degree and the set of vertices of odd degree, respectively, in an undirected graph $G=(V, E)$ with $m$ edges. Then
$$
2 m=\sum_{v \in V} \operatorname{deg}(v)=\sum_{v \in V_{1}} \operatorname{deg}(v)+\sum_{v \in V_{2}} \operatorname{deg}(v)
$$
Because $\operatorname{deg}(v)$ is even for $v \in V_{1}$, the first term in the right-hand side of the last equality is even. Furthermore, the sum of the two terms on the right-hand side of the last equality is even, because this sum is $2 m$. Hence, the second term in the sum is also even. Because all the terms in this sum are odd, there must be an even number of such terms. Thus, there are an even number of vertices of odd degree.

# Directed Graph Terminology