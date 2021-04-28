---
title: Relations
description: 
published: true
date: 2021-04-28T17:16:14.209Z
tags: discrete-mathematics
editor: markdown
---

# Binary Relations
A **binary relation**, $R$, consists of a set, $A$, called the **domain** of $R$, a set, $B$, called the **codomain** of $R$, and a subset of $A \times B$ called the **graph** of $R$. The graph of a function has the property that every element of $A$ is the first element of exactly one ordered pair of the graph.

A relation whose domain is $A$ and codomain is $B$ is said to be "**between** $A$ **and** $B$", or "**from** $A$ **to** $B$." 

When the domain and codomain are the same set, $A$, we simply say the relation is **on A**.

It is common to use "$a \medspace R \medspace b$" to mean the pair $(a, b)$ is in the graph of $R$.

We use the notation $aRb$ to denote that $(a, b) \in R$ and $a \not{R} b$ to denote that $(a, b) \notin R$

When $(a, b)$ belongs to $R$, $a$ is said to be **related to** $b$ by $R$.
Relationships between elements of more than two sets arise in many contexts. These relationships can be represented by $n$-ary relations, which are collections of $n$-tuples. Such relations are the basis of the relational data model, the most common way to store information in computer databases.

## Properties of Relations


### Reflexive
$(a, a) \in R$ for every element $a \in A$.

In a reflexive relation, an element is always related to itself. For example, let $R$ be the relation on the set of all people consisting of pairs $(x, y)$ where $x$ and $y$ have the same mother and the same father. Then $xRx$ for every person $x$.

### Symmetric
$(b, a) \in R$ whenever $(a,b) \in R$, for all $a,b \in A$. 
A relation $R$ on $A$ is **symmetric** iff for all $a,b \in A$, if $aRb$ then $bRa$.
A relation $R$ on a set $A$ such that for all $a,b \in A$, if $(a,b) \in R$ and $(b, a) \in R$, then $a=b$ is called **antisymmetric**.

In other words, a relation is symmetric iff $a$ is related to $b$ always implies that $b$ is related to $a$.

The relation $=$ is symmetric since $x=y \rightarrow y=x$. 

Divides is not symmetric since $5 \mid 10$ but $10 \not \mid 5$