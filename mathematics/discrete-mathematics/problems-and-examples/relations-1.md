---
title: Relations 1 Exercises
description: 
published: true
date: 2021-06-03T17:21:38.271Z
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
Verify that each of the following relations is a partial order by describing a function, $g$, such that the relation is defined by $g$ according to the following definition: 
A relation, $R$, on a set, $A$, is a partial order providing there is a function, $g$, from $A$ to some collection of sets such that 

$$
a_{1} R a_{2} \quad \text { iff } \quad g\left(a_{1}\right) \subset g\left(a_{2}\right)
$$
for all $a_{1} \neq a_{2} \in A$
For each, is it a total order?
**a)** The relation $\lt$ on $\R$
**b)** The superset relation $\supseteq$ on $\mathcal{P}(B)$ for a set $B$.
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
**b)** $g(a)::=\bar{a}::=B-\{a\}$, and note that for $a_{1} \neq a_{2} \in \mathcal{P}(B)$,

$$
\begin{aligned}
a_{1} \supseteq a_{2} & \text { iff } \quad a_{1} \supset a_{2} & \text{(since} \medspace a_1 \ne a_2 \text{)} \\
& \text { iff } \quad \overline{\huge a_{1}} \subset \overline{\huge a_{2}} & \text{(basic set theory)} \\
& \text { iff } \quad g\left(a_{1}\right) \subset g\left(a_{2}\right) & \text{(def of g)}
\end{aligned}
$$


**c)** 


# Show a property about a relation
## Rosen 7th Edition Sec 9.1 Exercise 51
Show that the relation $R$ on a set $A$ is symmetric iff $R=R^{-1}$, where $R^{-1}$ is the inverse relation.

### Solution
Since this is a bidirectional statement we need to prove that 
1) if a relation is symmetric, then $R=R^{-1}$
and 
2) $R=R^{-1}$ implies that the relation is symmetric.

For 1, we must show that $R \subseteq R^{-1}$ and $R^{-1} \subseteq R$. To do this, let $(a, b) \in R$. Since $R$ is symmetric, this implies that $(b,a) \in R$. Since $R^{-1}$. But since $R^{-1}$ consists of all pairs $(a, b)$ such that $(b, a) \in R$, this means that $(a, b) \in R^{-1}$. Thus we have shown that $R \subseteq R^{-1}$. Next let $(a, b) \in R^{-1}$. By definition this means that $(b, a) \in R$. Since $R$ is symmetric, this implies that $(a,b) \in R$ as well. Thus we have show that $R^{-1} \subseteq R$.
 
For 2, We let $(a,b) \in R$ and try to show that $(b,a)$ is also necessarily an element of $R$. Since $(a,b) \in R$, the definition tells us that $(b, a) \in R^{-1}$. But since we are under the hypothesis that $R=R^{-1}$, this tells us that $(b,a) \in R$, exactly as desired.

## Rosen 7th Edition Sec 9.1 Exercise 55
Let $R$ be a relation that is reflexive and transitive. Prove that $R^{n}=R$ for all positive integers $n .$
### Solution
We prove this by induction on $n$. The case $n=1$ is trivial, since it is the statement $R=R$. Assume the inductive hypothesis that $R^{n}=R .$ We must show that $R^{n+1}=R .$ By definition $R^{n+1}=R^{n} \circ R .$ Thus our task is to show that $R^{n} \circ R \subseteq R$ and $R \subseteq R^{n} \circ R .$ The first uses the transitivity of $R$, as follows. Suppose that $(a, c) \in R^{n} \circ R .$ This means that there is an element $b$ such that $(a, b) \in R$ and $(b, c) \in R^{n} \cdot$ By the inductive hypothesis, the latter statement implies that $(b, c) \in R .$ Thus by the transitivity of $R$, we know that $(a, c) \in R$, as desired

Next assume that $(a, b) \in R$. We must show that $(a, b) \in R^{n} \circ R .$ By the inductive hypothesis, $R^{n}=R$ and therefore $R^{n}$ is reflexive by assumption. Thus $(b, b) \in R^{n} .$ Since we have $(a, b) \in R$ and $(b, b) \in R^{n}$, we have by definition that $(a, b)$ is an element of $R^{n} \circ R$, exactly as desired. 

## Rosen 7th Edition Sec 9.1 Exercise 57
Let $R$ be a reflexive relation on a set $A$. Show that $R^{n}$ is reflexive for all positive integers $n$.

### Solution
We use induction on $n$, the result being trivially true for $n=1 .$ Assume that $R^{n}$ is reflexive; we must show that $R^{n+1}$ is reflexive. Let $a \in A$, where $A$ is the set on which $R$ is defined. By definition $R^{n+1}=R^{n} \circ R .$ By the inductive hypothesis, $R^{n}$ is reflexive, so $(a, a) \in R^{n} .$ Also, since $R$ is reflexive by assumption, $(a, a) \in R$. Therefore by the definition of composition, $(a, a) \in R^{n} \circ R$, as desired.

## Discrete Mathematics Study Center Relations Exercise
Suppose that $R$ is a relation defined on a set $A$ that is not reflexive. Prove or disprove that $R^2$ is not reflexive. 
### Solution
We show that it is possible for $R$ not to be reflexive but $R^{2}$ to be reflexive. Let $A=\{a, b\}$. Let $R=\{(a, b),(b, a)\}$. Given this, $R^{2}=\{(a, a),(b, b)\} . R$ is not reflexive but $R^{2}$ is reflexive

# Prove a property about a relation
## How to Prove It 2nd ed 4.2 Exercise 10
Suppose $R$ is a relation from $A$ to $B$ and $S$ is a relation from $B$ to $C$. Prove that $S \circ R=\varnothing$ iff Ran $(\mathrm{R})$ and $\operatorname{Dom}(S)$ are disjoint.
### Solution
$$
\operatorname{Ran}(R)=\{b \in B \mid \exists a \in A((a, b) \in R)\}
$$

$$\operatorname{Dom}(S)=\{b \in B \mid \exists c \in C((b, c) \in S)\}$$

$\operatorname{Ran}(R)$ and $\operatorname{Dom}(S)$ are disjoint. That is, the set of elements they have in common is $\emptyset$. That is, $\operatorname{Ran}(R) \cap \operatorname{Dom}(S) = \emptyset$.


$$
S \circ R=\{(a, c) \in A \times C \mid \exists b \in B((a, b) \in R \text { and }(b, c) \in S)\}
$$

We must prove a biconditional here. We must prove both directions. That is, we must prove  
1. if $S \circ R=\varnothing$ then  $\operatorname{Ran}(\mathrm{R})$ and $\operatorname{Dom}(S)$ are disjoint
2. if $\operatorname{Ran}(\mathrm{R})$ and $\operatorname{Dom}(S)$ are disjoint then $S \circ R=\varnothing$.

We prove the contrapositives of both directions. 
1. Suppose $S \circ R \neq \varnothing .$ Then we can choose some $(a, c) \in S \circ R$. By definition of $S \circ R$, this means that we can choose some $b \in B$ such that $(a, b) \in R$ and $(b, c) \in S .$ But then $b \in \operatorname{Ran}(R)$ and $b \in \operatorname{Dom}(S)$, so $\operatorname{Ran}(R)$ and $\operatorname{Dom}(S)$ are not disjoint. 
2. Suppose $\operatorname{Ran}(R)$ and $\operatorname{Dom}(S)$ are not disjoint. Then we can choose some $b \in \operatorname{Ran}(R) \cap \operatorname{Dom}(S)$. Since $b \in \operatorname{Ran}(R)$, we can choose some $a \in A$ such that $(a, b) \in R$. Similarly, since $b \in \operatorname{Dom}(S)$, we can choose some $c \in C$ such that $(b, c) \in S .$ But then $(a, c) \in S \circ R$, so $S \circ R \neq \varnothing$

## How to Prove It 2nd ed 4.3 Theorem 4.3.4 Part 2
Suppose $R$ is a relation on a set $A$. $R$ is symmetric iff $R=R^{-1}$.
### Solution
Suppose $R$ is symmetric. Let $(x, y)$ be an arbitrary element of $R$. Then $x R y$, so since $R$ is symmetric, $y R x$. Thus, $(y, x) \in R$, so by the definition of $R^{-1},(x, y) \in R^{-1}$. Since $(x, y)$ was arbitrary, it follows that $R \subseteq R^{-1}$.

Now suppose $(x, y) \in R^{-1}$. Then $(y, x) \in R$, so since $R$ is symmetric, $(x, y) \in R .$ Thus, $R^{-1} \subseteq R$, so $R=R^{-1}$.

Suppose $R=R^{-1}$, and let $x$ and $y$ be arbitrary elements of $A$. Suppose $x R y .$ Then $(x, y) \in R$, so since $R=R^{-1},(x, y) \in R^{-1} .$ By the definition of $R^{-1}$ this means $(y, x) \in R$, so $y R x .$ Thus, $\forall x \in A \forall y \in A(x R y \rightarrow y R x)$, so $R$ is symmetric. $\blacksquare$.

## How to Prove It 2nd ed 4.3 Exercise 7
Suppose $R$ is a relation on a set $A$. Prove $R$ is reflexive iff $i_{A} \subseteq R$, where $i_{A}$ is the identity relation on $A$.
### Solution
Suppose $R$ is reflexive. Let $(x, y)$ be arbitrary element of $i_{A} .$ Then by the definition of $i_{A}, x=y \in A .$ Since $R$ is reflexive, $(x, y)=(x, x) \in R$ Since $(x, y)$ was arbitrary, this shows that $i_{A} \subseteq R$.

Suppose $i_{A} \subseteq R .$ Let $x \in A$ be arbitrary. Then $(x, x) \in i_{A}$, so since $i_{A} \subseteq R,(x, x) \in R .$ Since $x$ was arbitrary, this shows that $R$ is reflexive.

## How to Prove It 2nd ed section 4.3 Exercise 10
Suppose $S$ is a relation on $A .$ Let $D=\operatorname{Dom}(S)$ and $R=\operatorname{Ran}(S) .$ Prove that $i_{D} \subseteq S^{-1} \circ S$ and $i_{R} \subseteq S \circ S^{-1}$.
### Solution
**scratch:**
$S=\{(a_1, a_2) \in A \}$.
$S^{-1}=\{(a_2, a_1) \in A \times A \mid(a_1, a_2) \in S\}$.

$
D = \operatorname{Dom}(S)=\{a \in A \mid \exists b \in B((a, b) \in S)\}
$
$i_D=\{(x, y) \in D \times D \mid x=y\}$.
$
R = \operatorname{Ran}(S)=\{b \in B \mid \exists a \in A((a, b) \in S)\}
$
$i_R=\{(x, y) \in R \times R \mid x=y\}$.
$S^{-1} \circ S=\{(a_1, a_1) \in A \times A \mid \exists a_2 \in A((a_1, a_2) \in S$ and $(a_2, a_1) \in S^{-1})\}$

Proving $i_{D} \subseteq S^{-1} \circ S$ :
We must prove that $(x,y) \in i_D \rarr (x,y) \in S^{-1} \circ S$.

Suppose $(x,y) \in i_D$. This means that $\{(x, y) \in D \times D \mid x=y\}$. So this means that $x$ and $y$ are the same. $i_D$
# Powers of Relations 
## Rosen 7th Edition Sec 9.1 Exercise 39
Let $R$ be the relation on the set of people with doctorates such that $(a, b) \in R$ if and only if $a$ was the thesis advisor of $b$. When is an ordered pair $(a, b)$ in $R^{2} ?$ When is an ordered pair $(a, b)$ in $R^{n}$, when $n$ is a positive integer? (Assume that every person with a doctorate has a thesis advisor.
### Solution
For $(a, b)$ to be in $R^2$, we must find a $c$ such that $(a, c) \in R$ and $(c, b) \in R .$ In our context, this says that $b$ got his / her doctorate under someone who got his / her doctorate under $a .$ Colloquially, $a$ is the academic grandparent of $b$, or $b$ is the academic grandchild of $a .$ Generalizing, $(a, b) \in R^{n}$ precisely when there is a sequence of $n+1$ people, starting with $a$ and ending with $b$, such that each is the advisor of the next person in the sequence.

# Counting number of relations on a set
## Rosen 7th Edition Sec 9.1 Exercise 42 + 43
List the 16 different relations on the set $\{0,1\}$.
How many of the 16 different relations on $\{0,1\}$ contain the pair $(0,1) ?$

### Solution
$$
\begin{array}{l}
\emptyset \\
\{(0,0)\} \\
\{(0,1)\} \\
\{(1,0)\} \\
\{(1,1)\} \\
\{(0,0),(0,1)\} \\
\{(0,0),(1,0)\} \\
\{(0,0),(1,1)\} \\
\{(0,1),(1,0)\} \\
\{(0,1),(1,1)\} \\
\{(1,0),(1,1)\} \\
\{(0,0),(0,1),(1,0)\} \\
\{(0,0),(0,1),(1,1)\} \\
\{(0,0),(1,0),(1,1)\} \\
\{(0,1),(1,0),(1,1)\} \\
\{(0,0),(0,1),(1,0),(1,1)\}
\end{array}
$$

A relation is just a subset. A subset can either contain a specified element or not; half of them do and half of them do not. Therefore 8 of the 16 relations on $\{0,1\}$ contain the pair $(0,1)$. Alternatively, a relation on $\{0,1\}$ containing the pair $(0,1)$ is just a set of the form $\{(0,1)\} \cup X$, where $X \subseteq\{(0,0),(1,0),(1,1)\}$. Since this latter set has 3 elements, it has $2^{3}=8$ subsets.

## Rosen 7th Edition Sec 9.1 Exercise 45
**a)** How many relations are there on the set $\{a, b, c, d\} ?$
**b)** How many relations are there on the set $\{a, b, c, d\}$ that contain the pair $(a, a)$ ?
### Solution
**a)** A relation on a set $S$ with $n$ elements is a subset of $S \times S$. Since $S \times S$ has $n^{2}$ elements, we are asking for the number of subsets of a set with $n^{2}$ elements, which is $2^{n^{2}} .$ In our case $n=4$, so the answer is $2^{16}=65,536$
**b)** In solving part (a), we had 16 binary choices to make-whether to include a pair $(x, y)$ in the relation or not as $x$ and $y$ ranged over the set $\{a, b, c, d\} .$ In this part, one of those choices has been made for us: we must include $(a, a) .$ We are free to make the other 15 choices. So the answer is $2^{15}=32,768 .$ See Exercise 47 for more problems of this type.

# Prove a relation is an equivalence relation and describe its equivalence classes

## Book of Proof Section 11.3 Exercise 7
Define a relation $R$ on $\mathbb{Z}$ as $x R y$ if and only if $3 x-5 y$ is even. Prove $R$ is an equivalence relation. Describe its equivalence classes.

### Solution

We must prove that $R$ is reflexive, symmetric and transitive. The relation $R$ is reflexive for the following reason. If $x \in \mathbb{Z}$, then $3 x-5 x=-2 x$ is even. But then since $3 x-5 x$ is even, we have $x R x .$ Thus $R$ is reflexive.

To see that $R$ is symmetric, suppose $x R y .$ We must show $y R x$. Since $x R y$, we know $3 x-5 y$ is even, so $3 x-5 y=2 a$ for some integer $a$. Now reason as follows:
$$
\begin{aligned}
3 x-5 y &=2 a \\
3 x-5 y+8 y-8 x &=2 a+8 y-8 x \\
3 y-5 x &=2(a+4 y-4 x) .
\end{aligned}
$$

From this it follows that $3 y-5 x$ is even, so $y R x$. We've now shown $x R y$ implies $y R x$, so $R$ is symmetric.

To prove that $R$ is transitive, assume that $x R y$ and $y R z .$ (We will show that this implies $x R z$.) Since $x R y$ and $y R z$, it follows that $3 x-5 y$ and $3 y-5 z$ are both even, so $3 x-5 y=2 a$ and $3 y-5 z=2 b$ for some integers $a$ and $b$. Adding these equations, we get $(3 x-5 y)+(3 y-5 z)=2 a+2 b$, and this simplifies to $3 x-5 z=2(a+b+y)$. Therefore $3 x-5 z$ is even, so $x R z$. We've now shown that if $x R y$ and $y R z$, then $x R z$, so $R$ is transitive.

We've shown $R$ is reflexive, symmetric and transitive, so it's an equivalence relation.

The completes the first part of the problem. Now we move on the second part. To find the equivalence classes, first note that $[0]=\{x \in \mathbb{Z}: x R 0\}=\{x \in \mathbb{Z}: 3 x-5 \cdot 0$ is even $\}=\{x \in \mathbb{Z}: 3 x$ is even $\}=\{x \in \mathbb{Z}: x$ is even $\} .$
Thus the equivalence class [0] consists of all even integers. Next, note that $[1]=\{x \in \mathbb{Z}: x R 1\}=\{x \in \mathbb{Z}: 3 x-5 \cdot 1$ is even $\}=\{x \in \mathbb{Z}: 3 x-5$ is even $\}=\{x \in \mathbb{Z}: x$ is odd $\}$.
Thus the equivalence class [1] consists of all odd integers.
Consequently there are just two equivalence classes $\{\ldots,-4,-2,0,2,4, \ldots\}$ and $\{\ldots,-3,-1,1,3,5, \ldots\}$.

# Interpreting what a statement means about some relations

## How to Prove It 2nd ed 4.2 Exercise 7
Let $E=\{(p, q) \in P \times P \mid$ the person $p$ is an enemy of the person $q\}$, and $F=\{(p, q) \in P \times P \mid$ the person $p$ is a friend of the person $q\}$, where $P$ is the set of all people. What does the saying "an enemy of one's enemy is one's friend" mean about the relations $E$ and $F$ ?

### Solution
Suppose $p$ is the enemy of $q$ and $q$ is the enemy of $r$, then it is given that $p$ is the friend of $r$. Thus we have if $(p, q) \in E$ and $(q, r) \in E$, then $(p, r) \in F$.
Now since $(p, q) \in E$ and $(q, r) \in E$, it follows $(p, r) \in E \circ E$. Thus the given statement says: if $(p, r) \in E \circ E$, then $(p, r) \in F$, or Enemy of an enemy is a
friend. Since $(p, r)$ is arbitrary, it follows that $E \circ E \subseteq F$.