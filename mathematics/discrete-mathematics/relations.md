---
title: Relations
description: 
published: true
date: 2021-05-13T17:48:29.915Z
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

The composition of relations $S$ and $R$ can also be denoted by $S \circ R$ for example.
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
In representing a relation as a graph, elements of $A$ are called the vertices (or node/point/junction) of the graph. They are typically represented by labeled points or small circles.We connect vertex $a$ to vertex $b$ with a narrow, called an edge (or arc, line, branch), going from vertex $a$ to vertex $b$ iff $arb$. This type of graph of a relation $r$ is called a **directed graph** or **digraph**.
## Example
Let $A=\{0,1,2,3\}$ and let $r=\{(0,0),(0,3),(1,2),(2,1),(3,2),(2,0)\}$. 
and its digraph..
![digraph.png](/digraph.png)
or 
![graph_2.png](/graph_2.png)

# Properties of Relations
## Individual Properties
### Reflexive
#### Informal definition
Each element is related to itself.
#### Formal Definition
Let $A$ be a set and let $r$ be a relation on $A$. Then $r$ is **reflexive** iff $ara$ for all $a \in A$.

Or 

if $(a, a) \in R a$ for all $a \in A$
#### Represented Graphically
Each point of the graph has an arrow looping from it and back onto itself.
### Irreflexive
#### Informal definition
No element is related to itself.
#### Formal definition
Let $A$ be a set and let $r$ be a relation on $A$. Then $r$ is **irreflexive** iff $a \not r \medspace a$ for all $a \in A$.

Or 
if $(a, a) \notin R$ for all $a \in A$
### Antisymmetric 
#### Informal definition
There are no pairs of distinct elements that are related to eachother. In other words, the only way for two elements to be related to eachother is for them to be the same element. 
#### Formal Definition
Let $A$ be a set and let $r$ be a relation on $A$. Then $r$ is **antisymmetric** iff whenever $arb$ and $a\ne b$ then $bra$ is false.
Or 
if $[(a, b) \in R \wedge(b, a) \in R] \Rightarrow a=b$ for all $a, b \in A$
#### Represented Graphically
Whenever there is an arrow going from one element to another distinct element, there is not an arrow going back from the second to the first.
### Transitive
#### Informal definition
If any one element is related to a second and that second element is related to a third, then the first element is related to the third.
#### Formal Definition
Let $A$ be a set and let $r$ be a relation on $A$. $r$ is transitive iff whenever $arb$ and $brc$ then $arc$.
Or 
if $[(a, b) \in R \wedge(b, c) \in R] \Rightarrow(a, c) \in R$ for all $a, b, c \in A$
#### Represented Graphically
In each case where there is an arrow going from one point to a second and from the second point to a third, there is an arrow going form the first point to the third. That is, there are no "incomplete directed triangles" in the graph.
## Equivalence Relations
A relation $r$ on a set $A$ is aclled an equivalence relation iff it is reflexive, symmetric, and transitive.
### Symmetric
#### Informal definition
If any one element is related to any other element, then the second element is related to the first. 
#### Formal Definition
Let $r$ be a relation on a set $A$. $r$ is symmetric iff whenever $arb$, it follows that $bra$.
Or 
if $(a, b) \in R \Rightarrow(b, a) \in R$ for all $a, b \in A$
#### Represented Graphically
In each case where there is an arrow goign from one point to a second, there is an arrow going from the second point back to the first.

## Partial Orderings
A relation on a set $A$ that is **reflexive**, **antisymmetric**, and **transitive** is a **partial ordering** on set $A$. A set on which there is a partial ordering relation is called a **partially ordered set** or **poset**.

### Partial Order by Function
We will define partial orders via the subset relation. For any element $a$, we think of a function $g$, such that $g(a)$ is the set of properties that $a$ has. Then we relate different elements according to how their properites compare. All partial orders will arise this way.

For partial orders the symbols $\prec$ and $\preceq$ are used because they resemble the symbols for subset and less-or-equal, which are the most common partial orders. (General orders are usually denoted by a letter like $R$).

#### Formal Definition
Given any total function $g$, from a set $A$, to a collection of sets, define the binary relation $\prec_{g}$ on $A$ by the rule 
$$
a \prec_{g} b \quad \text { iff } \quad g(a) \subset g(b)
$$
for $a, b \in A$. A binary relation, $R$, on a set, $A$, is a partial order iff there is a $g$ such that $R$ agrees with $\prec_{g}$ for every pair of distinct elements. That is, 
$$
a R b \quad \text { iff } \quad a \prec_{g} b
$$
for all $a \ne b \in A$.
# Inverse Relations
Let $R$ be a relation from set $A$ to a set $B$. The **inverse relation** from $B$ to $A$, denoted by $R^{-1}$, is the set of ordered pairs $\{(b, a) \mid(a, b) \in R\}$.

For example, let $A=\{1,2,3\}$ and $B=\{x,y,z\}$. Then the inverse of 
$$R=\{(1,y),(1,z),(3,y)\} \medspace \text {is} \medspace R^{-1}=\{(y,1),(z,1),(y,3)\}$$

If $R$ is any relation, then $(R^{-1})^{-1}=R$.

The domain and range of $R^{-1}$ are equal to the domain and range of $R$. 

If $R$ is a relation on $A$, then $R^{-1}$ is also a relation on $A$.
# Complementary Relations
Let $R$ be a relation from set $A$ to a set $B$. The **complementary relation** $\bar{R}$ is the set of ordered pairs $\{(a, b) \mid(a, b) \notin R\}$.

# Combining Relations
Let $R$ be a relation from a set $A$ to a set $B$ and $S$ a relation from $B$ to a set $C$.The composite of $R$ and $S$ is the relation consisting or ordered pairs $(a, c)$ where $a \in A$, $c \in C$, and for which there exists an element $b \in B$ such that $(a, b) \in R$ and $(b, c) \in S$. We denote the composite of $R$ and $S$ by $S \circ R$.




