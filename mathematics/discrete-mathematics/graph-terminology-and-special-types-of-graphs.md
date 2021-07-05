---
title: Graph Terminology and Special Types of Graphs
description: 
published: true
date: 2021-07-05T03:48:52.272Z
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
When $(u, v)$ is an edge of the graph $G$ with directed edges, $u$ is said to be **adjacent** to $v$ and $v$ is said to be **adjacent from** $u$. The vertex $u$ is called the **initial vertex** of $(u, v)$, and $v$ is called the **terminal** or **end vertex** of $(u, v) .$ The initial vertex and terminal vertex of a loop are the same.

In a graph with directed edges the **in-degree of a vertex** $v$, denoted by $\operatorname{deg}^{-}(v)$, is the number of edges with $v$ as their terminal vertex. The **out-degree** of $v$, denoted by $\operatorname{deg}^{+}(v)$, is the number of edges with $v$ as their initial vertex. (Note that a loop at a vertex contributes 1 to both the in-degree and the out-degree of this vertex.)

The undirected graph that results from ignoring directions of edges is called the **underlying directed graph**.
## Sum of in-degrees and out-degrees
The sum of the in-degrees and the sum of the out-degrees of all vertices in a graph with directed edges are the same because each edge has an initial vertex and a terminal vertex. Both of these sums are the number of edges in the graph. 

Written in sigma notation..
Let $G=(V, E)$ be a graph with directed edges. Then
$$
\sum_{v \in V} \operatorname{deg}^{-}(v)=\sum_{v \in V} \operatorname{deg}^{+}(v)=|E|
$$


# Special Simple Graphs
## Complete Graph
A **complete graph on $n$ vertices**, denoted by $K_n$, is a simple graph that contains exactly one edge between each pair of distinct vertices.  A simple graph for which there is at least one pair of distinct vertex not connected by an edge is called **noncomplete**.

## Cycle

## Wheel

## n-Cubes

# Bipartite Graphs
A simple graph $G$ is called **bipartite** if its vertex set $V$ can be partitioned into two disjoint sets $V_{1}$ and $V_{2}$ such that every edge in the graph connects a vertex in $V_{1}$ and a vertex in $V_{2}$ (so that no edge in $G$ connects either two vertices in $V_{1}$ or two vertices in $V_{2}$ ). When this condition holds, we call the pair $\left(V_{1}, V_{2}\right)$ a **bipartition** of the vertex set $V$ of $G$.

A bipartite graph can be colored with only two colors, such that no two adjacent vertices are assigned the same color. 

A bipartite graph iff it is not possible to start a vertex and return to this vertex by traversing an odd number of distinct edges. 
## 2-Coloring and Bipartancy
### Theorem 
A simple graph is bipartite if and only if it is possible to assign one of two different colors to each vertex of the graph so that no two adjacent vertices are assigned the same color.

### Proof
First, suppose that $G=(V, E)$ is a bipartite simple graph. Then $V=V_{1} \cup V_{2}$, where $V_{1}$ and $V_{2}$ are disjoint sets and every edge in $E$ connects a vertex in $V_{1}$ and a vertex in $V_{2}$. If we assign one color to each vertex in $V_{1}$ and a second color to each vertex in $V_{2}$, then no two adjacent vertices are assigned the same color.

Now suppose that it is possible to assign colors to the vertices of the graph using just two colors so that no two adjacent vertices are assigned the same color. Let $V_{1}$ be the set of vertices assigned one color and $V_{2}$ be the set of vertices assigned the other color. Then, $V_{1}$ and $V_{2}$ are disjoint and $V=V_{1} \cup V_{2}$. Furthermore, every edge connects a vertex in $V_{1}$ and a vertex in $V_{2}$ because no two adjacent vertices are either both in $V_{1}$ or both in $V_{2}$. Consequently, $G$ is bipartite.

### Usage
![undirected_graphs.png](/undirected_graphs.png)
We first consider the graph $G$. We will try to assign one of two colors, say red and blue, to each vertex in $G$ so that no edge in $G$ connects a red vertex and a blue vertex. Without loss of generality we begin by arbitrarily assigning red to $a$. Then, we must assign blue to $c, e$, $f$, and $g$, because each of these vertices is adjacent to $a$. To avoid having an edge with two blue endpoints, we must assign red to all the vertices adjacent to either $c, e, f$, or $g$. This means that we must assign red to both $b$ and $d$ (and means that $a$ must be assigned red, which it already has been). We have now assigned colors to all vertices, with $a, b$, and $d$ red and $c, e, f$, and $g$ blue. Checking all edges, we see that every edge connects a red vertex and a blue vertex. Hence, by Theorem 4 the graph $G$ is bipartite.

Next, we will try to assign either red or blue to each vertex in $H$ so that no edge in $H$ connects a red vertex and a blue vertex. Without loss of generality we arbitrarily assign red to $a$. Then, we must assign blue to $b, e$, and $f$, because each is adjacent to $a$. But this is not possible because $e$ and $f$ are adjacent, so both cannot be assigned blue. This argument shows that we cannot assign one of two colors to each of the vertices of $H$ so that no adjacent vertices are assigned the same color. It follows by Theorem 4 that $H$ is not bipartite.


### Bipartite Graphs and Matchings
Bipartite graphs can be used to model types of applications that involve matching the elements of one set to elements of another.

#### Job Assignments
A task like finding an assignment of jobs to employees with the requisite ability can be thought of as finding a **matching** in the graph model. A matching $M$ in a simple graph $G=(V, E)$ is a subset of the set $E$ of edges of the graph such that no two edges are incident with the same vertex. 

In other words, a matching is a subset of edges such that if $\{s, t\}$ and $\{u, v\}$ are distinct edges of the matching, then $s, t, u$, and $v$ are distinct. 

A vertex that is the endpoint of an edge of a matching $M$ is said to be **matched** in $M$; otherwise it is said to be **unmatched**. 

A **maximum matching** is a matching with the largest number of edges. We say that a matching $M$ in a bipartite graph $G=(V, E)$ with bipartition $\left(V_{1}, V_{2}\right)$ is a **complete matching from $V_{1}$ to $V_{2}$** if every vertex in $V_{1}$ is the endpoint of an edge in the matching, or equivalently, if $|M|=\left|V_{1}\right|$. 

For example, to assign jobs to employees so that the largest number of jobs are assigned employees, we seek a maximum matching in the graph that models employee capabilities. To assign employees to all jobs we seek a complete matching from the set of jobs to the set of employees.