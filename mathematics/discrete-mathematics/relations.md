---
title: Relations
description: 
published: true
date: 2021-05-05T18:36:42.750Z
tags: discrete-mathematics
editor: markdown
---

# Relations
> This page contains a lot of duplications from the [functions](/mathematics/discrete-mathematics/functions) page..
{.is-warning}


# Relations between two sets
Let $A$ and $B$ be sets. A relation from $A$ into $B$ is any subset of $A \times B$.

## Examples of relations between two sets
### Example
Let $A=\{1,2,3\}$ and $B=\{4,5\}$. Then  $\{(1,4),(2,4),(3,5)\}$ is a relation from $A$ into $B$. There would be $64$ possible relations for these two sets.

A graph of this simple relation:
![simple_relation_graph.png](/simple_relation_graph.png)
### Divisibility Exmaple
Let $A=\{2,3,5,6\}$ and define a relation $r$ from $A$ into $A$ by $(a,b) \in r$ iff $a \mid b$. The set of pairs that qualify for membership is $r=\{(2,2),(3,3),(5,5),(6,6),(2,6),(3,6)\}$

# Relations on a set
A relation from a set $A$ into itself is called a relation on $A$.

The "divides" relation, for example on the set of integers is: Let $a, b \in \Z$, $a \ne 0$. We say that $a$ divides $b$, denoted by $a \mid b$, iff there exists an integer $k$ such that $ak=b$.