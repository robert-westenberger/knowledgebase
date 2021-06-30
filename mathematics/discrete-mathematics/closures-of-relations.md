---
title: Closures of Relations
description: 
published: true
date: 2021-06-30T18:26:06.498Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Types of Closures

If $R$ is a relation on a set $A$, it may or may not have some property $\textbf P$, such as reflexivity, symmetry, or transitivity. When $R$ does not enjoy propety $\textbf P$, we would like to find the smallest relation $S$ on $A$ with property $\textbf P$ that contains $R$.

If $R$ is a relation on a set $A$, then the **closure** of $R$ with respect to $P$, if it exists, is the relation $S$ on $A$ with property $P$ that ocntains $R$ and is a subset of every subset $A \times A$ containing $R$ with property $P$.

## Reflexive Closure

The relation $R=\{(1,1),(1,2),(2,1),(3,2)\}$ on set $A=\{1,2,3\}$ is not reflexive. By adding $(2,2)$ and $(3,3)$ to $R$, $R$ is now reflexive. This new relation contains $R$. Any reflexive relation that contains $R$ must also contain $(2,2)$ and $(3,3)$. Because this relation contains $R$, is reflexive, and is contained within every reflexive relation that contains $R$, it is called the **reflexive closure** of $R$.

As the above example illustrates, given a relation $R$ on a set $A$, the reflexive closure of $R$ can be formed by adding to $R$ all pairs of the form $(a, a)$ with $a \in A$, not already in $R$. The addition of these pairs produces a new relation that is reflexive, contains $R$, and is contained within any reflexive relation containing $R$. 

We see that the reflexive closure of $R$ equals $R \cup \Delta$, where $\Delta=\{(a, a) \mid a \in A\}$ is the **diagonal relation** on $A$.

### Example
What is the reflexive closure of the relation $R=\{(a, b) \mid a<b\}$ on the set of integers?

The reflexive closure of $R$ is 
$$
R \cup \Delta=\{(a, b) \mid a<b\} \cup\{(a, a) \mid a \in \mathbf{Z}\}=\{(a, b) \mid a \leq b\}
$$

## Symmetric Closure
The relation $R=\{(1,1),(1,2),(2,2),(2,3),(3,1),(3,2)\}$ on a set $A=\{1,2,3\}$ can be made symmetric by adding $(2,1)$ and $(1,3)$, the only pairs of the form $(b,a)$ with $(a,b) \in R$ that are not in $R$. This new relation is the **symmetric closure** of $R$.

The symmetric closure of a relation can be constructed by taking the union of a relation with its inverse, this is, $R \cup R^{-1}$ is the symmetric closure of $R$, where $R^{-1}=\{(b, a) \mid(a, b) \in R\}$.

### Example 
What is the symmetric closure of the relation $R=\{(a, b) \mid a>b\}$ on the set of positive integers?

$$
R \cup R^{-1}=\{(a, b) \mid a>b\} \cup\{(b, a) \mid a>b\}=\{(a, b) \mid a \neq b\}
$$

## Transitive Closures
These are a little more complicated. Take for example a relation $R=\{(1,3),(1,4),(2,1),(3,2)\}$ on a set $A=\{1,2,3,4\}$. The relation isn't transitive because it does not contain all pairs of the form $(a,c)$ where $(a,b)$ and $(b,c)$ are in $R$. The pairs of this form not in $R$ are $(1,2)$, $(2,3)$, $(2,4)$, and $(3,1)$. Adding these pairs doesn't produce a transitive relation because the resulting relation contains $(3,1)$ and $(1,4)$ but does not contain $(3,4)$.

# Paths in Directed Graphs
A **path** from $a$ to $b$ in the directed graph $G$ is a sequence of edges $\left(x_{0}, x_{1}\right),\left(x_{1}, x_{2}\right)$, $\left(x_{2}, x_{3}\right), \ldots,\left(x_{n-1}, x_{n}\right)$ in $G$, where $n$ is a nonnegative integer, and $x_{0}=a$ and $x_{n}=b$, that is, a sequence of edges where the terminal vertex of an edge is the same as the initial vertex in the next edge in the path. This path is denoted by $x_{0}, x_{1}, x_{2}, \ldots, x_{n-1}, x_{n}$ and has **length** $n$. We view the empty set of edges as a path of length zero from $a$ to $a$. A path of length $n \geq 1$ that begins and ends at the same vertex is called a **circuit** or **cycle**.

The term **path** also applies to relations. Carrying over the definition from directed graphs to relations, there is a path from $a$ to $b$ in $R$ if there is a sequence of elements $a, x_{1}, x_{2}, \ldots, x_{n-1}, b$ with $\left(a, x_{1}\right) \in R,\left(x_{1}, x_{2}\right) \in R, \ldots$, and $\left(x_{n-1}, b\right) \in R .$ Theorem 1 can be obtained from the definition of a path in a relation.


## Theorem 1
Let $R$ be a relation on a set $A$. There is a path of length $n$, where $n$ is a positive integer, from $a$ to $b$ if and only if $(a, b) \in R^{n}$.

### Proof of Theorem 1
**Proof:** We will use mathematical induction. By definition, there is a path from $a$ to $b$ of length one if and only if $(a, b) \in R$, so the theorem is true when $n=1$.

Assume that the theorem is true for the positive integer $n$. This is the inductive hypothesis. There is a path of length $n+1$ from $a$ to $b$ if and only if there is an element $c \in A$ such that there is a path of length one from $a$ to $c$, so $(a, c) \in R$, and a path of length $n$ from $c$ to $b$, that is, $(c, b) \in R^{n} .$ Consequently, by the inductive hypothesis, there is a path of length $n+1$ from $a$ to $b$ if and only if there is an element $c$ with $(a, c) \in R$ and $(c, b) \in R^{n} .$ But there is such an element if and only if $(a, b) \in R^{n+1}$. Therefore, there is a path of length $n+1$ from $a$ to $b$ if and only if $(a, b) \in R^{n+1}$. This completes the proof. $\blacksquare$


## Transitive Closures and Connectivity Relation
Transitive closures of a relation are equivalent to determining which pairs of vertices in the associated digraph are connected by a path. With this in mind, we define a new relation.

Let $R$ be a relation on a set $A .$ The **connectivity relation** $R^{*}$ consists of the pairs $(a, b)$ such that there is a path of length at least one from $a$ to $b$ in $R$.

Because $R^{n}$ consists of the pairs $(a, b)$ such that there is a path of length $n$ from $a$ to $b$, it follows that $R^{*}$ is the union of all the sets $R^{n} .$ In other words,
$$
R^{*}=\bigcup_{n=1}^{\infty} R^{n}
$$

### Example
Let $R$ be the relation on the set of all people in the world that contains $(a, b)$ if $a$ has met $b$. What is $R^{n}$, where $n$ is a positive integer greater than one? What is $R^{*}$ ?
#### Solution
The relation $R^{2}$ contains $(a, b)$ if there is a person $c$ such that $(a, c) \in R$ and $(c, b) \in R$ that is, if there is a person $c$ such that $a$ has met $c$ and $c$ has met $b$. Similarly, $R^{n}$ consists of those pairs $(a, b)$ such that there are people $x_{1}, x_{2}, \ldots, x_{n-1}$ such that $a$ has met $x_{1}, x_{1}$ has met $x_{2}, \ldots$, and $x_{n-1}$ has met $b$.

The relation $R^{*}$ contains $(a, b)$ if there is a sequence of people, starting with $a$ and ending with $b$, such that each person in the sequence has met the next person in the sequence. 

### Example
Let $R$ be the relation on the set of all subway stops in New York City that contains $(a, b)$ if it is possible to travel from stop $a$ to stop $b$ without changing trains. What is $R^{n}$ when $n$ is a positive integer? What is $R^{*}$ ?
#### Solution
The relation $R^{n}$ contains $(a, b)$ if it is possible to travel from stop $a$ to stop $b$ by making at most $n-1$ changes of trains. The relation $R^{*}$ consists of the ordered pairs $(a, b)$ where it is possible to travel from stop $a$ to stop $b$ making as many changes of trains as necessary.

## Theorem 2
The transitive closure of a relation $R$ equals the connectivity relation $R^{*}$.
### Proof of Theorem 2
Note that $R^{*}$ contains $R$ by definition. To show that $R^{*}$ is the transitive closure of $R$ we must also show that $R^{*}$ is transitive and that $R^{*} \subseteq S$ whenever $S$ is a transitive relation that contains $R$.

First, we show that $R^{*}$ is transitive. If $(a, b) \in R^{*}$ and $(b, c) \in R^{*}$, then there are paths from $a$ to $b$ and from $b$ to $c$ in $R$. We obtain a path from $a$ to $c$ by starting with the path from $a$ to $b$ and following it with the path from $b$ to $c$. Hence, $(a, c) \in R^{*}$. It follows that $R^{*}$ is transitive. Now suppose that $S$ is a transitive relation containing $R$. Because $S$ is transitive, $S^{n}$ also is transitive and $S^{n} \subseteq S$. Furthermore, because
$$
S^{*}=\bigcup_{k=1}^{\infty} S^{k}
$$
and $S^{k} \subseteq S$, it follows that $S^{*} \subseteq S .$ Now note that if $R \subseteq S$, then $R^{*} \subseteq S^{*}$, because any path in $R$ is also a path in $S .$ Consequently, $R^{*} \subseteq S^{*} \subseteq S .$ Thus, any transitive relation that contains $R$ must also contain $R^*$. Therefore, $R^*$ is the transitive closure of $R$.

## Lemma 1
This lemma shows it is sufficient to examine paths containing no more than $n$ edges, where $n$ is the number of elements in the set. 

Let $A$ be a set with $n$ elements, and let $R$ be a relation on $A$. If there is a path of length at least one in $R$ from $a$ to $b$, then there is such a path with length not exceeding $n$. Moreover, when $a \neq b$, if there is a path of length at least one in $R$ from $a$ to $b$, then there is such a path with length not exceeding $n-1$.

### Proof of Lemma 1
Proof: Suppose there is a path from $a$ to $b$ in $R$. Let $m$ be the length of the shortest such path. Suppose that $x_{0}, x_{1}, x_{2}, \ldots, x_{m-1}, x_{m}$, where $x_{0}=a$ and $x_{m}=b$, is such a path.

Suppose that $a=b$ and that $m>n$, so that $m \geq n+1 .$ By the pigeonhole principle, because there are $n$ vertices in $A$, among the $m$ vertices $x_{0}, x_{1}, \ldots, x_{m-1}$, at least two are equal (see below digraph)

![producing_a_path_with_length_not_exceeding_n.png](/producing_a_path_with_length_not_exceeding_n.png)

Suppose that $x_{i}=x_{j}$ with $0 \leq i<j \leq m-1$. Then the path contains a circuit from $x_{i}$ to itself. This circuit can be deleted from the path from $a$ to $b$, leaving a path, namely, $x_{0}, x_{1}, \ldots, x_{i}, x_{j+1}, \ldots, x_{m-1}, x_{m}$, from $a$ to $b$ of shorter length. Hence, the path of shortest length must have length less than or equal to $n$.

## Theorem 3
Let $\mathbf{M}_{R}$ be the zero-one matrix of the relation $R$ on a set with $n$ elements. Then the zero-one matrix of the transitive closure $R^{*}$ is
$$
\mathbf{M}_{R^{*}}=\mathbf{M}_{R} \vee \mathbf{M}_{R}^{[2]} \vee \mathbf{M}_{R}^{[3]} \vee \cdots \vee \mathbf{M}_{R}^{[n]}
$$

### Example
Find the zero-one matrix of the transitive closure of the relation $R$ where
$$
\mathbf{M}_{R}=\left[\begin{array}{lll}
1 & 0 & 1 \\
0 & 1 & 0 \\
1 & 1 & 0
\end{array}\right]
$$
#### Solution
Solution: By Theorem 3, it follows that the zero-one matrix of $R^{*}$ is
$$
\mathbf{M}_{R^{*}}=\mathbf{M}_{R} \vee \mathbf{M}_{R}^{[2]} \vee \mathbf{M}_{R}^{[3]}
$$
Because
$$
\mathbf{M}_{R}^{[2]}=\left[\begin{array}{lll}
1 & 1 & 1 \\
0 & 1 & 0 \\
1 & 1 & 1
\end{array}\right] \quad \text { and } \quad \mathbf{M}_{R}^{[3]}=\left[\begin{array}{ccc}
1 & 1 & 1 \\
0 & 1 & 0 \\
1 & 1 & 1
\end{array}\right]
$$
it follows that
$$
\mathbf{M}_{R^{*}}=\left[\begin{array}{lll}
1 & 0 & 1 \\
0 & 1 & 0 \\
1 & 1 & 0
\end{array}\right] \vee\left[\begin{array}{lll}
1 & 1 & 1 \\
0 & 1 & 0 \\
1 & 1 & 1
\end{array}\right] \vee\left[\begin{array}{lll}
1 & 1 & 1 \\
0 & 1 & 0 \\
1 & 1 & 1
\end{array}\right]=\left[\begin{array}{lll}
1 & 1 & 1 \\
0 & 1 & 0 \\
1 & 1 & 1
\end{array}\right]
$$