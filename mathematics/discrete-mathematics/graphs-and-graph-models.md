---
title: Graphs and Graph Models
description: 
published: true
date: 2021-07-02T19:10:47.462Z
tags: computer-science, mathematics, discrete-mathematics
editor: markdown
---

# Graphs and Graph Models

A **graph** $G=(V, E)$ consists of $V$, a nonempty set of **vertices** (or **nodes**) and $E$, a set of **edges**. Each edge has either one or two vertices associated with it, called its **endpoints**. An edge is said to **connect** its endpoints.

A graph can either be **finite** or **infinite**. They have finite vertex set or infinite vertex set respectively.

A **simple graph** is one in which each edge connects two different vertices and where no two edges connect the same pair of vertices. In this kind of graph, each edge is associated to an unordered pair of vertices, and no other edge is associated to this same edge. 
When there is an edge of a simple graph associated to $\{u, v\}$, we can also say, without possible confusion, that $\{u, v\}$ is an edge of the graph.


A **multigraph** has multiple edges connecting the same vertices. When there are $m$ different edges associated to the same unordered pair of vertices $\{u, v\}$, we also say that $\{u, v\}$ is an edge of multiplicity $m .$ That is, we can think of this set of edges as $m$ different copies of an edge $\{u, v\}$.

A **loop** is an edge that connects a vertex to itself.

A **psuedograph** is a graph that may include loops, and possibly multiple edges connecting to the same pair of vertices or a vertex to itself. 

A **directed graph** (or **digraph**) $(V, E)$ consists of a nonempty set of vertices $V$ and a set of **directed edges** (or **arcs**) $E$. Each directed edge is associated with an ordered pair of vertices. The directed edge associated with the ordered pair $(u, v)$ is said to start at $u$ and end at $v$.