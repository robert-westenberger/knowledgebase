---
title: Graph Terminology and Special Types of Graphs
description: 
published: true
date: 2021-07-05T04:16:16.748Z
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

#### Necessary and Sufficient Conditions For Complete Matchings

#### Hall's Marriage Theorem
The bipartite graph $G=(V, E)$ with bipartition $\left(V_{1}, V_{2}\right)$ has a complete matching from $V_{1}$ to $V_{2}$ if and only if $|N(A)| \geq|A|$ for all subsets $A$ of $V_{1}$

(Recall $N(A)$ is the set of all vertices in $G$ that are adjacent to at least one vertex in $A$. $N(A)=\bigcup_{v \in A} N(v)$)

#### Proof
We first prove the only if part of the theorem. To do so, suppose that there is a complete matching $M$ from $V_{1}$ to $V_{2}$. Then, if $A \subseteq V_{1}$, for every vertex $v \in A$, there is an edge in $M$ connecting $v$ to a vertex in $V_{2}$. Consequently, there are at least as many vertices in $V_{2}$ that are neighbors of vertices in $V_{1}$ as there are vertices in $V_{1}$. It follows that $|N(A)| \geq|A|$.

To prove the if part of the theorem, the more difficult part, we need to show that if $|N(A)| \geq|A|$ for all $A \subseteq V_{1}$, then there is a complete matching $M$ from $V_{1}$ to $V_{2} .$ We will use strong induction on $\left|V_{1}\right|$ to prove this.

**Basis step:** If $\left|V_{1}\right|=1$, then $V_{1}$ contains a single vertex $v_{0} .$ Because $\left|N\left(\left\{v_{0}\right\}\right)\right| \geq\left|\left\{v_{0}\right\}\right|=1$, there is at least one edge connecting $v_{0}$ and a vertex $w_{0} \in V_{2} .$ Any such edge forms a complete matching from $V_{1}$ to $V_{2}$.

**Inductive step:** We first state the inductive hypothesis.
**Inductive hypothesis:** Let $k$ be a positive integer. If $G=(V, E)$ is a bipartite graph with bipartition $\left(V_{1}, V_{2}\right)$, and $\left|V_{1}\right|=j \leq k$, then there is a complete matching $M$ from $V_{1}$ to $V_{2}$ whenever the condition that $|N(A)| \geq|A|$ for all $A \subseteq V_{1}$ is met.

Now suppose that $H=(W, F)$ is a bipartite graph with bipartition $\left(W_{1}, W_{2}\right)$ and $\left|W_{1}\right|=k+ 1$

We will prove that the inductive holds using a proof by cases, using two case. Case $(i)$ applies when for all integers $j$ with $1 \leq j \leq k$, the vertices in every set of $j$ elements from $W_{1}$ are adjacent to at least $j+1$ elements of $W_{2}$. Case (ii) applies when for some $j$ with $1 \leq j \leq k$ there is a subset $W_{1}^{\prime}$ of $j$ vertices such that there are exactly $j$ neighbors of these vertices in $W_{2} .$ Because either Case (i) or Case (ii) holds, we need only consider these cases to complete the inductive step


**Case $(i):$** Suppose that for all integers $j$ with $1 \leq j \leq k$, the vertices in every subset of $j$ elements from $W_{1}$ are adjacent to at least $j+1$ elements of $W_{2}$. Then, we select a vertex $v \in W_{1}$ and an element $w \in N(\{v\})$, which must exist by our assumption that $\mid N(\{v\}|\geq|\{v\} \mid=1 .$ We delete $v$ and $w$ and all edges incident to them from $H$. This produces a bipartite graph $H^{\prime}$ with bipartition $\left(W_{1}-\{v\}, W_{2}-\{w\}\right) .$ Because $\left|W_{1}-\{v\}\right|=k$, the inductive hypothesis tells us there is a complete matching from $W_{1}-\{v\}$ to $W_{2}-\{w\}$. Adding the edge from $v$ to $w$ to this complete matching produces a complete matching from $W_{1}$ to $W_{2}$.

**Case ($ii$):** Suppose that for some $j$ with $1 \leq j \leq k$, there is a subset $W_{1}^{\prime}$ of $j$ vertices such that there are exactly $j$ neighbors of these vertices in $W_{2}$. Let $W_{2}^{\prime}$ be the set of these neighbors. Then, by the inductive hypothesis there is a complete matching from $W_{1}^{\prime}$ to $W_{2}^{\prime} .$ Remove these $2 j$ vertices from $W_{1}$ and $W_{2}$ and all incident edges to produce a bipartite graph $K$ with bipartition $\left(W_{1}-W_{1}^{\prime}, W_{2}-W_{2}^{\prime}\right)$
We will show that the graph $K$ satisfies the condition $|N(A)| \geq|A|$ for all subsets $A$ of $W_{1}-$ $W_{1}^{\prime}$. If not, there would be a subset of $t$ vertices of $W_{1}-W_{1}^{\prime}$ where $1 \leq t \leq k+1-j$ such that the vertices in this subset have fewer than $t$ vertices of $W_{2}-W_{2}^{\prime}$ as neighbors. Then, the set of $j+t$ vertices of $W_{1}$ consisting of these $t$ vertices together with the $j$ vertices we removed from $W_{1}$ has fewer than $j+t$ neighbors in $W_{2}$, contradicting the hypothesis that $|N(A)| \geq|A|$ for all $A \subseteq W_{1}$. Hence, by the inductive hypothesis, the graph $K$ has a complete matching. Combining this complete matching with the complete matching from $W_{1}^{\prime}$ to $W_{2}^{\prime}$, we obtain a complete matching from $W_{1}$ to $W_{2}$.

We have shown that in both cases there is a complete matching from $W_{1}$ to $W_{2}$. This completes the inductive step and completes the proof. 

## Parallel Processing and Parallel Algorithms
**Parallel processing**, which uses computers made up of many separate processors, each with its own memory, helps overcome the limitations of computers with a single processor.

**Parallel algorithms**, which break a problem into a number of subproblems that can be solved concurrently, can then be devised to rapidly solve problems using a computer with multiple processors. In a parallel algorithm, a single instruction stream controls the execution of the algorithm, sending subproblems to different processors, and directs the input and output of these subproblems to the appropriate processors.

## Subgraphs
Sometimes we need only part of a graph to solve a problem. 

A **subgraph of a graph** $G=(V, E)$ is a graph $H=(W, F)$, where $W \subseteq V$ and $F \subseteq E$. A subgraph $H$ of $G$ is a **proper subgraph** of $G$ if $H \neq G$

Let $G=(V, E)$ be a simple graph. The **subgraph induced** by a subset $W$ of the vertex set $V$ is the graph $(W, F)$, where the edge set $F$ contains an edge in $E$ if and only if both endpoints of this edge are in $W$.

### Removing Vertices From a Graph
