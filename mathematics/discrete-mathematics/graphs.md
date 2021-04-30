---
title: Graphs
description: 
published: true
date: 2021-04-30T19:51:35.038Z
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

**Irreflexivity:** Iff No vertices have selfloops.
**Symmetry:** Iff All edges are bidirectional. 
**Antisymmetry:** Iff there are never two edges in opposite directions between distinct vertices.
**Transitivity:** Shortcircuits—for any path through the graph, there is an arrow from the first vertex to the last vertex in the path. 


We can define some new relations based on paths. Let $R$ be a digraph with vertices, $A$. Define relations $R^{\ast}$ and $R^+$ on $A$ by the conditions that 

$$
\begin{array}{ll}
a R^{\ast} b & ::=  \quad \text{there is a path in} \medspace R \medspace \text{from} \medspace a \medspace \text {to} \medspace b \\
a R^{+} b & ::= \quad \text{there is a positive length path in} \medspace R \medspace \text{from} \medspace a \medspace \text {to} \medspace b 
\end{array}
$$

$R^{\ast}$ is called the **path relation** of $R$. It follows from the definition of path that $R^{\ast}$ is transitive. IT is also reflexive because it has $0$ length paths and it contains the graph of $R$ because of the length-one paths. $R^+$ is called the **positive-length path relation**; it also contains graph $(R)$ and is transitive.

## Directed Acylic Graphs
Scheduling problems are a common source of partial orders: there is a set $A$ of tasks and a set of constraints specifying that starting a certain task depends on other tasks being completed beforehand. We represent the task by vertices and a constraint that task $a$ must finish before task $b$ can start by an arrow from $a$ to $b$. 
Below is a directed acylcic graph that describes the order in which to put on clothes.
![directed_acyclic_graph_example.png](/directed_acyclic_graph_example.png)

If we were to add a relation from belt to underwear, that would create a **cyclic dependency** and we would have no way to get dressed.

A **cycle** is a positive length path in a digraph that begins and ends at the same vertex. A **directed acyclic graph** is a graph with no cycles.

We use DAG's as an economic way to represent the dependency relation. Usually a task-graph DAG itself is not a transitive relation because it only includes the edges showing "direct" dependencies. Rather, the **dependency relation** we care about is defined by the positive length path relation, $R^+$, in the task graph. The dependency relation will always be a partial order. 

## Topological Sorting
In a DAG for a partial order, incomparable elements appear as vertices with no path between them in either direction. So in a partial order on clothes in the above example, "left shoe" and "right shoe" are incomparable. If the order is total, then the order can be represented by a DAG that looks like a line. 

$$
\circ \longrightarrow \circ \longrightarrow \cdots \longrightarrow \circ
$$

When we have a partial order of tasks to be performed, it can be useful to have an order in which to perform all the tasks, one at a time, while respecting the dependency constraints. This amounts to finding a total order that is consistent with the partial roder. This task of finding a total ordering that is consistent with a partial order is known as **topological sorting**.

A topological sort of a partial order $\prec$ on a set $A$ is a total ordering $\sqsubset$ on $A$ such that 

$$
a \prec b \text { implies } a \sqsubset b
$$

A topological sort (one of a few possible) for our dressing example above could be 
$$
\text { shirt } \sqsubset \text { sweater } \sqsubset \text { underwear } \sqsubset \text { leftsock } \sqsubset \text { rightsock } \sqsubset \text { pants } \sqsubset \text { leftshoe } \sqsubset \text { rightshoe } \sqsubset \text { belt } \sqsubset \text { jacket }
$$
