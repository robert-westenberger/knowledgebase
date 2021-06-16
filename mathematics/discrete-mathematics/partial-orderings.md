---
title: Partial Orderings
description: 
published: true
date: 2021-06-16T19:43:53.680Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# Partial Orderings

A relation $R$ on a set $S$ is called a partial ordering or partial order if it is **reflexive**, **antisymmetric**, and **transitive**. A set $S$ together with a partial ordering $R$ is called a partially ordered set, or poset, and is denoted by $(S, R)$. Members of $S$ are called elements of the poset.

## Antisymmetry
Let $R$ be a relation on a set $A . R$ is antisymmetric if, and only if, for every $a$ and $b$ in $A,$ if $a R b$ and $b R a$ then $a=b$.

In terms of an arrow diagram of a relation, saying that a relation is antisymmetric is the same as saying that whenever there is an arrow goign from one element to another distinct element, there is not an arrow going back from the second to the first.

### Example: Testing for Antisymmetry of "Divides" Relations
Let $R_1$ be the "divides" relation on the set of all positive integers, and $R_2$ be the "divides" relation on the set of all integers. Prove or give a counterexample of $R_1$ and $R_2$ being antisymmetric.

$R_1$ is antisymmetric. 
**Proof:** Suppose $a$ and $b$ are positive integers such that $a R_{1} b$ and $b R_{1} a$. [We must show that $a=b .]$ By definition of $R_{1}, a \mid b$ and $b \mid a$. Thus, by definition of divides, there are integers $k_{1}$ and $k_{2}$ with $b=k_{1} a$ and $a=k_{2} b$. It follows that 
$$ 
b=k_{1} a=k_{1}\left(k_{2} b\right)=\left(k_{1} k_{2}\right) b .
$$
Dividing both sides by $b$ gives 
$$ k_{1} k_{2}=1 $$

Now since $a$ and $b$ are both integers, $k_{1}$ and $k_{2}$ are both positive integers also. And the only product of two positive integers that equals 1 is $1 \cdot 1$. Thus 
$$ k_{1}=k_{2}=1 $$ 
and so 
$$ a=k_{2} b=1 \cdot b=b $$
[as was to be shown].

$R_2$ is not antisymmetric. Let $a=2$ and $b=-2$. Then $a \mid b$ since $-2=(-1) \cdot 2]$ and $b \mid a$ [since $2=(-1)(-2)]$. Hence $a R_{2} b$ and $b R_{2} a$ but $a \neq b$.

### Example: Show that the greater than or equal to relation is a partial ordering on the set of integers
Because $a \geq a$ for every integer $a, \geq$ is reflexive. If $a \geq b$ and $b \geq a$, then $a=b$. Hence, $\geq$ is antisymmetric. Finally, $\geq$ is transitive because $a \geq b$ and $b \geq c$ imply that $a \geq c$. It follows that $\geq$ is a partial ordering on the set of integers and $(\mathbf{Z}, \geq)$ is a poset.

### Example: Show that the inclusion relation $\subseteq$ is a partial ordering on the power set of a set $S$.
Because $A \subseteq A$ whenever $A$ is a subset of $S \subseteq$ is reflexive. It is antisymmetric because $A \subseteq \mid B$ and $B \subseteq A$ imply that $A=B$. Finally, $\subseteq$ is transitive, because $A \subseteq B$ and $B \subseteq C$ imply that $A \subseteq C$. Hence, $\subseteq$ is a partial ordering on $P(S)$, and $(P(S) \subseteq)$ is a poset.

## Comparability and Totally Ordered sets
Suppose $\preceq$ is a partial order relation on a set $A$. Elements $a$ and $b$ of $A$ are said to be **comparable** if, and only if, either $a \preceq b$ or $b \preceq a$. Otherwise, $a$ and $b$ are called **noncomparable**.

Given any two real numbers $x$ and $y$, either $x \leq y$ or $y \leq x$. The elements  $x$ and $y$ in this case are **comparable**.

Given two subsets $A$ and $B$ of $\{a,b,c\}$, it may be the case that neither $A \subseteq B$ nor $B \subseteq A$. For instance, let $A=\{a, b\}$ and $B=\{b, c\} .$ Then $A \nsubseteq B$ and $B \nsubseteq A .$ In such a case, $A$ and $B$ are said to be **noncomparable**.

When every two elements in the set are comparable, the relation is called a **total ordering**.

If $(S, \preccurlyeq)$ is a poset and every two elements of $S$ are comparable, $S$ is called a **totally ordered** or **linearly ordered** set, and $\preccurlyeq$ is called a total order or a linear order. A totally ordered set is also called a **chain**. The **length of a chain** is one less than the number of elements in the chain.

A set that is partially ordered but not totally ordered may have totally ordered subsets. Such subsets are **chains**.
### Chain Length Subsets Example
The set $\mathscr{P}(\{a, b, c\})$ is partially ordered with respect to the subset relation. Find a chain of length 3 in $\mathscr{P}(\{a, b, c\})$

**Solution** Since $\varnothing \subseteq\{a\} \subseteq\{a, b\} \subseteq\{a, b, c\}$, the set
$$
S=\{\varnothing,\{a\},\{a, b\},\{a, b, c\}\}
$$
is a chain of length 3 in $\mathscr{P}(\{a, b, c\})$

## Maximal and Minimal Elements
Maximal and minimal elements are easy to spot using a Hasse diagram. They are the "top" and "bottom" elements in the diagram.
### Maximal
An element of a poset is called maximal if it is not less than any element of the poset. That is, a is maximal in the poset $(S, \preccurlyeq)$ if there is no $b \in S$ such that $a \prec b$. 

An element $a$ in $A$ is called a maximal element of $A$ if, and only if, for each $b$ in $A$, either $b \preceq a$ or $b$ and $a$ are not comparable.

### Greatest
An element $a$ in $A \mid$ is called a greatest element of $A$ if, and only if, for each $b$ in $A, b \preceq a$

### Minimal
Similarly, an element of a poset is called minimal if it is not greater than any element of the poset. That is, $a$ is minimal if there is no element $b \in S$ such that $b \prec a$. 

An element $a$ in $A$ is called a minimal element of $A$ if, and only if, for each $b$ in $A$, either $a \preceq b$ or $b$ and $a$ are not comparable.

### Least
An element $a$ in $A$ is called a least element of $A$ if, and only if, for each $b$ in $A$, $a \preceq b$.

#### Example - Identifying minimal and maximal elements of a set
(a) What are the maximal and minimal elements, if any, of the set, $\mathbb{N}$, of all natural numbers under divisibility? Is there a minimum or maximum element?
(b) What are the minimal and maximal elements, if any, of the set of integers $\geq 2$ under divisibility?
##### Solution
**(a)** The minimum (and therefore unique minimal) element is 1 since 1 divides all natural numbers. The maximum (and therefore unique maximal) element is 0 since all numbers divide $0 .$
**(b)** All prime numbers are minimal elements, since no numbers divide them. Since there is more than one minimal element, there can't be a minimum element. There is no maximal element, because for any $n \geq 2$, there is a "larger" number under the divisibility partial order, namely, $m n$, for any $m>1$.
## Well Ordered Set
$(S, \preccurlyeq)$ is a **well-ordered set** if it is a poset such that $\preccurlyeq$ is a total ordering and every nonempty subset of $S$ has a least element.


## Lexicographic Order
Let $A$ be a set with a partial order relation $R$, and let $S$ be a set of strings over $A$ Define a relation $\prec$ on $S$ as follows:

Let $s$ and $t$ be any strings in $S$ of lengths $m$ and $n$, respectively, where $m$ and $n$ are positive integers, and let $s_{m}$ and $t_{m}$ be the characters in the $m$ th position for $s$ and $t$, respectively.
1. If $m \leq n$ and the first $m$ characters of $s$ and $t$ are the same, then $s \preceq t$.
2. If the first $m-1$ characters in $s$ and $t$ are the same, $s_{m} R t_{m}$, and $s_{m} \neq t_{m}$, then $s \preceq t$.
3. If $\lambda$ is the null string then $\lambda \preceq s$.
If no strings are related by $\preceq$ other than by these three conditions, then $\preceq$ is a partial order relation on $S$.

### Example - Testing Strings for Lexicographic Order
Let $A=\{x, y\}$ and let $R$ be the following partial order relation on $A$ :
$$
R=\{(x, x),(x, y),(y, y)\}
$$
Let $S$ be the set of all strings over $A$, and denote by the lexicographic order for $S$ that corresponds to $R$.
**a.** Is $x \preceq x ? \quad$ Is $x \preceq x x ? \quad$ Is $y x \preceq y x y$ ?
**b.** Is $x x x y y y \preceq x y$ ?
**c.** Is $x \preceq y$ ?
**d.** Is $\lambda \preceq x y$ ?
**e.** Is $x y y \preceq x y x$ ?
#### Solution - Testing Strings for Lexicographic Order
**a.** Yes in all three cases, by property (1) of the definition of $\preceq$
**b.** Yes in all cases, by property (2) of the definition of $\preceq$.
**c.** Yes in all cases, by property (2) of the definition of $\preceq$. In this case $m-1=0$, and the statement that the first zero characters of $x$ and $y$ are the same is true by default.
**d.** Yes by property (3) of the definition of $\preceq$
**e.** No because $y$ is not related to $x$ by $R$.


# Hasse Diagrams
A Hasse diagram is a digraph for a finite poset that has mandatory edges removed. 

1. Digraph for the partial ordering $\{(a, b) \mid a \leq b\}$ on the set $\{1,2,3,4\}$. 
![hasse_a.png](/hasse_a.png)

2. Remove the mandatory reflexive relation self loops on vertices.
![hasse_b.png](/hasse_b.png)

3. Remove transitive edges, because they must be present, and remove direction because we assume all edges are pointed "upwards". 
![hasse_c.png](/hasse_c.png)

## Representing a finite poset using a Hasse Diagram

1. Start with the directed graph for the relation.
2. Remove reflexive loops.
3. Remove all edges that must be in the partial ordering because of the presence of other edges and transitivity. That is, remove all edges $(x,y)$ for which there is an element $z \in S$ such that $z \in S$ such that $x \prec z$ and $z \prec x$. 
4. Arrange each edge so that its initial vertex is below its terminal vertex. 
5. Remove all arrows on the directed edges, because all edges point "upward" toward their terminal vertex. 

## Covering Relation
Let $(S, \preccurlyeq)$ be a poset. We say that an element $y \in S$ **covers** an element $x \in S$ if $x<$ $y$ and there is no element $z \in S$ such that $x \prec z<y .$ The set of pairs $(x, y)$ such that $y$ covers $x$ is called the **covering relation** of $(S, \preccurlyeq)$. From the description of the Hasse diagram of a poset, we see that the edges in the Hasse diagram of $(S, \preccurlyeq)$ are upwardly pointing edges corresponding to the pairs in the covering relation of $(S, \preccurlyeq)$. Furthermore, we can recover a poset from its covering relation, because it is the reflexive transitive closure of its covering relation. This tells us that we can construct a partial ordering from its Hasse diagram.

## Recovering a directed graph from the Hasse Diagram
1. Reinsert the direction markers on the arrows making all arrows point upward.
2. Add loops at each vertex.
3. For each sequence of arrows from one point to a second and from that second point to a third, add an arrow from the first point to the third.

# Topological Sorting
Suppose a project is made up of 20 different tasks that can be completed only after others have been finished. How can an order be found for these tasks? 

To model this problem we set up a partial order on the set of tasks so that $a \prec b$ iff $a$ and $b$ are tasks where $b$ cannot be started until $a$ has been completed. To produce a schedule for the project, we need to produce an order for all $20$ tasks that is compatible with this partial order.

## Definition
A **total ordering** $\preccurlyeq$ is said to be compatible with the partial ordering $R$ if $a \preccurlyeq b$ whenever $a R b .$ Constructing a compatible total ordering from a partial ordering is called topological sorting.

**Lemma:**  Every finite nonempty poset $(S, \preccurlyeq)$ has at least one minimal element.

**Proof:** Choose an element $a_{0}$ of $S$. If $a_{0}$ is not minimal, then there is an element $a_{1}$ with $a_{1} \prec a_{0}$. If $a_{1}$ is not minimal, there is an element $a_{2}$ with $a_{2} \prec a_{1}$. Continue this process, so that if $a_{n}$ is not minimal, there is an element $a_{n+1}$ with $a_{n+1} \prec a_{n} .$ Because there are only a finite number of elements in the poset, this process must end with a minimal element $a_{n} \blacksquare$.

## Algorithm

Let $\preceq$ be a partial order relation on a nonempty finite set $A .$ To construct a topological sorting:
1. Pick any minimal element $x$ in $A .$ [Such an element exists since $A$ is nonempty.]
2. Set $A^{\prime}:=A-\{x\}$.
3. Repeat steps $a-c$ while $A^{\prime} \neq \varnothing$
a. Pick any minimal element $y$ in $A^{\prime}$.
b. Define $x \preceq^{\prime} y$.
c. $\operatorname{Set} A^{\prime}:=A^{\prime}-\{y\}$ and $x:=y$.
[Completion of steps $1-3$ of this algorithm gives enough information to construct the Hasse diagram for the total ordering $\preceq$. We have already shown how to use the Hasse diagram to obtain a complete directed graph for a relation. $]$