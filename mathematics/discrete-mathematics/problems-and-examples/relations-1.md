---
title: Relations 1 Exercises
description: 
published: true
date: 2021-05-05T17:26:09.237Z
tags: discrete-mathematics
editor: markdown
---

# Determine if relations on a set are reflexive, symmetric, antisymmetric, or transitive

## Rosen 7th Edition Sec 9.1 Exercise 3
For each of these relations on the set $\{1,2,3,4\}$, decide
whether it is reflexive, whether it is symmetric, whether
it is antisymmetric, and whether it is transitive.
**a)** $\{(2,2),(2,3),(2,4),(3,2),(3,3),(3,4)\}$
**b)** $\{(1,1),(1,2),(2,1),(2,2),(3,3),(4,4)\}$
**c)** $\{(2,4),(4,2)\}$
**d)** $\{(1,2),(2,3),(3,4)\}$
**e)** $\{(1,1),(2,2),(3,3),(4,4)\}$
**f)** $\{(1,3),(1,4),(2,3),(2,4),(3,1),(3,4)\}$.

### Soln
**a)** Transitive.
**b)** This is reflexive since it contains $(a, a) \in R$ for every $a \in A$. It is also symmetric since $(2,1)$ is in $R$ when $(1, 2)$ is. It is not antisymmetric since $(1,2)$ and $(2,1)$ are in the relation. It is transitive since $(1,2)$ and $(2, 1)$ are in the relation then $(1,1)$ and $(2,2)$ are in the relation as well.
**c)** Not reflexive, but it is symmetric. Not antisymmetric because $(2,4)$ and $(4,2)$ are in the relation. IT isn't transitive because $(2,4)$ and $(4,2)$ are in the relation but $(2,2)$ is not.
**d)** Not reflexive or symmetrical. It is antisymmetric since there are no cases of $(a,b)$ being in the relation when $(b, a)$ is. It is not transitive since although $(1,2)$ and $(2,3)$ are in the relation, $(1,3)$ is not.
**e)** Reflexive, symmetric, antisymmetric, and transitive (the only tyime the hypothesis ($(a, b) \in R \wedge(b, c) \in R$) is met is when $a=b=c$.
**f)** Not reflexive or symmetric or antisymmetric. It is not transitive, since $(2,3)$ and $(3,1)$ are in the relation, but $(2,1)$ is not.

## Rosen 7th Edition Sec 9.1 Exercise 5
Determine whether the relation $R$ on the set of all Web pages is reflexive, symmetric, antisymmetric, and/or transitive, where $(a, b) \in R$ if and only if

**a)** everyone who has visited Web page $a$ has also visitedWeb page $b$.
**b)** there are no common links found on both Webpage $a$ and Web page $b$.
**c)** there is at least one common link onWeb page $a$ andWeb page $b$.
**d)** there is a Web page that includes links to both Webpage $a$ and Web page $b$.

### Soln
**a)** It's reflexive (if you visited website $a$ you have also visited website $a$..) It is not symmetric since there must exist a website $a$ and $b$ such that the set of people who visited $a$ are a proper subset of $b$. If there exists two different web pages that have the same exact set of visitors, then $R$ is not antisymmetric. $R$ is transitive (if everyone who visited $a$ visited $b$, and everyone who visited $b$ visited $c$, then everyone who visited $a$ has also visited $c$.
**b)** Not reflexive, any page $a$ that has links on it, $(a, a) \notin R$. $R$ is symmetric in its very definition. $R$ is not antisymmetric because there are surely two different webpages $a$ and $b$ that have no common links in them. Lastly, $R$ is not transitive since for webpages with no links in common, if they have links at all, give an example of a failure of the definition $(a, b) \in R$ and $(b,a) \in R$, but $(a, a) \notin R$.
**c)**
**d)**
# Determine whether a relation is an equivalence relation (reflexive, symmetric, and transitive)
## 2000 Solved Problems in Discrete Mathematics 2.180
Let $R$ be the relation ont he set $N$ of positive integers defined by $R=\{(a,b): a + b \medspace \text {is even}\}$. Is $R$ an equivalence relation?
### Soln
It is reflexive ($a+a$ is even).
It is symmetric (if $a+b$ is even then $b+a$ is even).
It is transitive (if $a+b$ is even and $b+c$ is even then $a+c$ is also even)

It is reflexive, symmetric, and transitive, so it is an equivalence relation.
## 2000 Solved Problems in Discrete Mathematics 2.181
Let $S$ be the relation "is a blood relative of" on the set $X$ of people. Is $S$ an equivalence relation?

It is not reflexive (a person can't be a blood relative of themselves, that doesnt make sense. The book says this is reflexive, so they are considering a person a relative of themselves...). 
It is symmetric (if a person $a$ has a blood relative $b$, then person $b$ is a blood relative of $a$).
It is not transitive (a person may have a cousin $a$ through his mothers family and another cousin $b$ through their fathers family, but $a$ and $c$ may not be blood relatives).
## 2000 Solved Problems in Discrete Mathematics 2.182 
Let $R = \{(1,1),(1,3),(3,1),(3,3)\}$. Is $R$ an equivalence relation on $A=\{1,2,3\}$? on $B=\{1,3\}$?
### Solution
For $A$, its not reflexive since its missing $(2,2)$, so its not an equivalence relation.
For $B$, it is symmetric, reflexive, and transitive so it is an equivalence relation.

# Determine whether a relation is an equivalence relation (reflexive, symmetric, and transitive) and if applicable, how many and what equivalence classes are there

## MIT OCW 6.042J Fall 2005 In-Class Problems Week 4 Problem 1
In each case, say whether or not $R$ is an equivalence relation on $A$. If it is an equivalence relation, what are the equivalence classes and how many equivalence classes are there?

**a)** $R::=\{(x, y) \in W \times W \mid$ the words $x$ and $y$ start with the same letter $\}$ where $W$ is the set of all words in the 2001 edition of the Oxford English dictionary.
**b)** $R::=\{(x, y) \in W \times W \mid$ the words $x$ and $y$ have at least one letter in common $\}$
**c)** $R=\{(x, y) \in W \times W$ and the word $x$ comes before the word $y$ alphabetically $\}$
**d)** $R=\{(x, y) \in \mathbb{R} \times \mathbb{R}$ and $|x| \leq|y|\}$
**e)** $R=\{(x, y) \in B \times B$, where $\mathrm{B} \medspace \text {is the set of all bit strings and} \medspace \mathrm{x} \medspace \text {and} \medspace \mathrm{y} \medspace \text { have the same number of 1s\} }$.

### Solution
**a)** This is an equivalence relation, being symmetric reflexive and transitive. The equivalence class is $\lbrack x \rbrack _R$ is the set of words $y$ such that $y$ has the same first letter as $x$. There are $26$ equivalence classes, one for each letter of the alphabet. 
**b)** Not an equivalence relation, since its not transitive. There can exist a word $a$ that has letters in common with another word $b$, and word $b$ can have letters in common with a word $c$, but $a$ may have no letters in common with $c$.
**c)** Not an equivalence relation. A word can't come before itself alphabetically. 
**d)** Its not symmetric, no equiv relation.
**e)** This is an equivalence relation. There is an equivalence relation for all positive integers with that number of ones.
# Show that a relation is an equivalence relation ( reflexive, symmetric, and transitive)
## Rosen 7th Edition Sec 9.1 Exercise 9
Show that the relation $R=\emptyset$ on the empty set $S=\emptyset$ is reflexive, symmetric, and transitive.
### Soln
Each of the properties reflexive, symmetric, and transitive are universally quantified statements. Because the domain is empty, each of them is vacuously true.

# Determine which relations are irreflexive
## Rosen 7th Edition Sec 9.1 Exercise 11
A relation $R$ on the set $A$ is irreflexive if for every $a \in A$, $(a, a) \notin R$. That is, $R$ is irreflexive if no element in $A$ is related to itself. 

Which relations from exercise 3 are irreflexive?
### Soln
c, d, f are irreflexive.

# Answer about the nature of reflexivity / irreflexivity
## Rosen 7th Edition Sec 9.1 Exercise 15
Can a relation on a set be neither reflexive nor irreflexive?

### Soln
Yes, a relation $R$ may contain some pairs of $(a, a)$ but not all of them.
## Rosen 7th Edition Sec 9.1 Exercise 17
Give an example of an irreflexive relation on the set of all people.
### Soln
$(a,b) \in R$ iff $a$ weighs more than $b$. A person can't weigh more than themselves, so this is irreflexive.

# Use quantifiers to express a statement about a relation
## Rosen 7th Edition Sec 9.1 Exercise 23
Use quantifiers to express what it means for a relation to be asymmetric.

### Soln
$$
\forall a \forall b \neg((a, b) \in R \wedge(b, a) \in R)
$$
or 
$$
\forall a \forall b((a, b) \in R \rightarrow(b, a) \notin R)
$$

# Verify a relation is a partial order and possibly a total order
## MIT OCW 6.042J Fall 2005 In-Class Problems Week 4 Problem 3
Verify that each of the following relations is a partial order by describing a function, $g$, such that the relation is defined by $g$ according to the following defintion: 
A relation, $R$, on a set, $A$, is a partial order providing there is a function, $g$, from $A$ to some collection of sets such that 

$$
a_{1} R a_{2} \quad \text { iff } \quad g\left(a_{1}\right) \subset g\left(a_{2}\right)
$$
for all $a_{1} \neq a_{2} \in A$
. For each, is it a total order?
**a)** The relation $\lt$ on $\R$
**b)** The superset relation $\subseteq$ on $\mathcal{P}(B)$ for a set $B$.
**c)** The divides relation on $\natnums$.

### Soln
**a)** $g(r)::=\{t \in \mathbb{R} \mid t<r\}$. It follows that 
$$
r_{1}<r_{2} \quad \text { iff } \quad g\left(r_{1}\right) \subset g\left(r_{2}\right)
$$
so $\lt$ satisfies the condition $a_{1} R a_{2}$ iff $g\left(a_{1}\right) \subset g\left(a_{2}\right)$ on $R$ that defines partial orders. Likewise the relation $\le$ is a partial order because 
$$
r_{1} \leq r_{2} \quad \text { iff } \quad r_{1}<r_{2}
$$
for all reals $r_1 \ne r_2$. $\blacksquare$.
**b)** 
**c)** 