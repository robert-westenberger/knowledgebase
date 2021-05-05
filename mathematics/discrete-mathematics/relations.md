---
title: Relations
description: 
published: true
date: 2021-05-05T18:53:17.436Z
tags: discrete-mathematics
editor: markdown
---

# Relations
> This page contains a lot of duplications from the [functions](/mathematics/discrete-mathematics/functions) page..
{.is-warning}

Let $s$ be a relation from set $A$ into a set $B$. Then the fact that $(x,y) \in s$ is frequently written as $xsy$.
# Relations between two sets
Let $A$ and $B$ be sets. A relation from $A$ into $B$ is any subset of $A \times B$.

## Examples of relations between two sets
### Example
Let $A=\{1,2,3\}$ and $B=\{4,5\}$. Then  $\{(1,4),(2,4),(3,5)\}$ is a relation from $A$ into $B$. There would be $64$ possible relations for these two sets.

A graph of this simple relation:
![simple_relation_graph.png](/simple_relation_graph.png)
### Divisibility Example
Let $A=\{2,3,5,6\}$ and define a relation $r$ from $A$ into $A$ by $(a,b) \in r$ iff $a \mid b$. The set of pairs that qualify for membership is $r=\{(2,2),(3,3),(5,5),(6,6),(2,6),(3,6)\}$

# Relations on a set
A relation from a set $A$ into itself is called a relation on $A$.

The "divides" relation, for example on the set of integers is: Let $a, b \in \Z$, $a \ne 0$. We say that $a$ divides $b$, denoted by $a \mid b$, iff there exists an integer $k$ such that $ak=b$.

# Composition of Relations
Let $r$ be a relation from a set $A$ into a set $B$, and let $s$ be a relation from $B$ into a set $C$. The composition of $r$ with $s$, written $rs$, is the set of pairs of the form $(a, c) \in A \times C$, where $(a, c) \in r s$ iff there exists $b \in B$ such that $(a,b) \in r$ and $(b,c) \in s$.

## Example
Take for example three sets
$A=\{2,3,5,8\}$
$B=\{4,6,16\}$
$C=\{1,4,5,7\}$
and two relations on those sets
$r = \text{divides from A into B}$
$s= \le \text{from B into C}$
so $r=\{(2,4),(2,6),(2,16),(3,6),(8,16)\}$ and $s=\{(4,4),(4,5),(4,7),(6,7)\}$.

Viewed graphically: 
![composition_relation_graph.png](/composition_relation_graph.png)

Note how certain elements in $A$ go through elements in $B$ to results in $C$. That is, 
$$
\begin{array}{l}
2 \mid 4 \text { and } 4 \leq 4 \\
2 \mid 4 \text { and } 4 \leq 5 \\
2 \mid 4 \text { and } 4 \leq 7 \\
2 \mid 6 \text { and } 6 \leq 7 \\
3 \mid 6 \text { and } 6 \leq 7
\end{array}
$$

Based on this, a new relation $rs$, from $A$ into $C$ can be defined. In order for $(a,c)$ to be in $rs$, it must be possible to travel along a path from $a$ to $c$. In other words, $(a,c) \in rs$ iff $(\exists b)_{B}(a r b$ and $b s c)$.

# Graphs of Relations on a Set