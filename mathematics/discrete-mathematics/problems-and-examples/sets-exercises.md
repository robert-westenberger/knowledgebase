---
title: Sets Exercises
description: 
published: true
date: 2021-04-12T02:58:39.402Z
tags: discrete-mathematics
editor: markdown
---

# Rosen Discrete Mathematics 7th Edition Section 2.1
## List members of sets

### 1 
List the members of these sets.
**a)** $\left\{x \mid x\right.$ is a real number such that $\left.x^{2}=1\right\}$
**b)** $\{x \mid x$ is a positive integer less than 12$\}$
**c)** $\{x \mid x$ is the square of an integer and $x<100\}$
**d)** $\left\{x \mid x\right.$ is an integer such that $\left.x^{2}=2\right\}$

#### Solution

**a)** $\{-1, 1 \}$
**b)** $\{0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12 \}$
**c)** $\{0, 1, 4, 9, 16, 25, 36, 49, 64, 81 \}$
**d)** $\emptyset$

## Determine set subset relations

### 3 
For each of these pairs of sets, determine whether the first
is a subset of the second, the second is a subset of the first,
or neither is a subset of the other.
**a)** the set of airline flights from New York to New Delhi,
the set of nonstop airline flights from New York to
New Delhi
**b)** the set of people who speak English, the set of people
who speak Chinese
**c)** the set of flying squirrels, the set of living creatures
that can fly
#### Solution
**a)** Every element in the second set is in the first set, so the second set is a subset of the first set. (the set of airline flights from new york to new delhi contains all nonstop flights + flights with layovers). 
**b)** neither
**c)** the first is a subset of the second, and not vice versa.

## Determine set equality
### 5
Determine whether each of these pairs of sets are equal.
**a)** $\{1,3,3,3,5,5,5,5,5\},\{5,3,1\}$
**b)** $\{\{1\}\},\{1,\{1\}\}$
**c)** $\emptyset,\{\emptyset\}$.
#### Solution
**a)** equal (duplicates and order dont matter)
**b)** not equal - first set has 1 element second has 2
**c)** not equal

## Show that a set is a subset of another
### 17
Suppose that $A$, $B$, and $C$ are sets such that $A \subseteq B$ and $B \subseteq C$. Show that $A \subseteq C$.

#### Solution
Need to show that every element of $A$ is also an element of $C$. Let $x \in A$. Since $A \subseteq B$, we can conclude that $x \in B$. Since $B \subseteq C$, the fact that $x \in B$ implies $x \in C$, which is what we want to show. 
### 21
Find the power set of each of these sets, where $a$ and $b$
are distinct elements.

**a)** $\{a\}$ 
**b)** $\{a, b\}$ 
**c)** $\{\emptyset,\{\emptyset\}\}$

#### Solution
**a)** $\{\{a\}, \emptyset\}$
**b)** $\{\emptyset,\{a\},\{b\},\{a, b\}\}$
**c)** $\{\emptyset,\{\emptyset\},\{\{\emptyset\}\},\{\emptyset,\{\emptyset\}\}\}$

## Set Proofs
### 25
Prove that $\mathcal{P}(A) \subseteq \mathcal{P}(B)$ if and only if $A \subseteq B$

#### Solution
We are proving an IFF so we have to show that $p \rarr q$ and $q \rarr p$.
We must prove $(\mathcal{P}(A) \subseteq \mathcal{P}(B) \rarr A \subseteq B) \wedge (A \subseteq B \rarr \mathcal{P}(A) \subseteq \mathcal{P}(B))$.

To prove that one set is a subset of another, we need to prove that an element being a member of one set implies membership of another set. 


**First Part: Prove** $(\mathcal{P}(A) \subseteq \mathcal{P}(B) \rarr A \subseteq B)$

Suppose $\mathcal{P}(A) \subseteq \mathcal{P}(B)$. $A \subseteq A$, so $A \in \mathcal P(A) \subseteq \mathcal P(B)$, so $A \in \mathcal P(B)$, and hence $A \subseteq B$. 

**Second Part: Prove** $(A \subseteq B \rarr \mathcal{P}(A) \subseteq \mathcal{P}(B))$
Suppose $A \subseteq B$. Then for any $x \in \mathcal P(A)$ we have $x \subseteq A \subseteq B$, so $x \subseteq B$, therefore $x \in \mathcal P(B)$. Thus $\mathcal{P}(A) \subseteq \mathcal{P}(B))$


### 31
Let $A$ be a set. Show that $\emptyset \times A = A \times \emptyset = \emptyset$.

#### Solution
By definition, $\emptyset \times A$ consists of all pairs $(x, a)$ such that $x \in \emptyset$ and $a \in A$. Since there are no elements $x \in \emptyset$, there are no such pairs, so $\emptyset \times A = \emptyset$. Similar reasoning shows that $A \times \emptyset = \emptyset$.