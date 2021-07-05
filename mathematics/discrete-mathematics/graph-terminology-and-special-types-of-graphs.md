---
title: Graph Terminology and Special Types of Graphs
description: 
published: true
date: 2021-07-05T01:50:54.059Z
tags: computer-science, mathematics, discrete-mathematics
editor: markdown
---


# Undirected Graph Terminology
Two vertices $u$ and $v$ in an undirected graph $G$ are called **adjacent** (or **neighbors**) in $G$ if $u$ and $v$ are endpoints of an edge $e$ of $G$. Such an edge $e$ is called **incident** with the vertices $u$ and $v$ and $e$ is said to **connect** $u$ and $v$.

The set of all neighbors of a vertex $v$ of $G=(V, E)$, denoted by $N(v)$, is called the **neighborhood** of $v$. If $A$ is a subset of $V$, we denote by $N(A)$ the set of all vertices in $G$ that are adjacent to at least one vertex in $A .$ So, $N(A)=\bigcup_{v \in A} N(v)$.

The **degree of a vertex in an undirected graph** is the number of edges incident with it, except that a loop at a vertex contributes twice to the degree of that vertex. The degree of the vertex $v$ is denoted by $\operatorname{deg}(v)$. 

A vertex of degree zero is **isolated**.
A vertex of degree one is **pendant**.

# Handshaking Theorem
