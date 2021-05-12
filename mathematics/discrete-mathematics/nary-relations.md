---
title: n-ary Relations
description: 
published: true
date: 2021-05-12T17:49:35.530Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# n-ary Relations
Let $A_{1}, A_{2}, \ldots, A_{n}$ be sets. An **n-ary relation** on these sets is a subset of $A_{1} \times A_{2} \times \cdots \times A_{n}$. The sets $A_{1}, A_{2}, \ldots, A_{n}$ are called the **domains** of the relation, and $n$ is called its **degree**.

For example, let $R_1$ bbe the relation $\mathbf{N} \times \mathbf{N} \times \mathbf{N}$ consisting of triples $(a,b,c)$, where $a$, $b$, and $c$ are integers with $a \lt b \lt c$. Then $(1,2,3) \in R$, but $(2,4,3) \notin R$. The degree of the relation is $3$. Its domains are all equal to the set of natural numbers.

# Databases and Relations
The **relational data model** is based on the concept of a relation. 

A database consists of **records**, which are **n-tuples**, made up of fields. The fields are the entries of the n-tuples. The relational data model represents a database of records as an n-ary relation. 
For instance, a database of student records may be made up of fields containing the name, student number, major, and gpa of the student. Student records are represented as 4-tuples of the form (Student_name, ID_number, Major, GPA). 

Relations used to represent databases are called **tables**. Each column of the table corresponds to an attribute of the database. A table of student records discussed above is shown below..

$$
\begin{array}{|l|c|l|l|}
\hline \text { Student\_name } & \text { ID\_number } & \text {Major} & \text { GPA } \\
\hline \text { Ackermann } & 231455 & \text { Computer Science } & 3.88 \\
\text { Adams } & 888323 & \text { Physics } & 3.45 \\
\text { Chou } & 102147 & \text { Computer Science } & 3.49 \\
\text { Goodfriend } & 453876 & \text { Mathematics } & 3.45 \\
\text { Rao } & 678543 & \text { Mathematics } & 3.90 \\
\text { Stevens } & 786576 & \text { Psychology } & 2.99 \\
\hline
\end{array}
$$

A domain of an n-ary relation is called a **primary key** when the value of the n-tuple from this domain determines the n-tuple. That is, a domain is a primary key when no two n-tuples in the relation have the same value for this domain.

The current collection of n-tuples in a relation is called the **extension** of the relation.  The more permanent part of a database, including the name and attributes of the database, is called its **intension**.

## Selecting a primary key in a relational database
When selecting a primary key, the goal should be to select a key that can serve as a primary key for all possible extensions of the database. To do this, it is necessary to examine the intension of the database to understand the set of possible n-tuples that can occur in an extension.

Combinations of domains can also uniquely identify n-tuples in an n-ary relation. When the values of a set of domains determine an n-tuple in a relation, the Cartesian product of these domains is called a **composite key**.

## Operations on n-ary Relations
### Selection operator
Let $R$ be an n-ary relation and $C$ a condition that elements in $R$ must satisfy. Then the **selection operator** $s_{C}$ maps the n-ary relation $R$ to the n-ary relation of all n-tuples from $R$ that satisfy the condition $C$. 

Using our student records table above, we could use the operator $s_{C_1}$ where $C_1$ is the condition Major="Computer Science". The result is the two 4 tuples containing data on the students Ackermann and Chou.

### Projections
The **projection** $P_{i_{1} i_{2}, \ldots, i_{m}}$ where $i_{1}<i_{2}<\cdots<i_{m}$, maps the n-tuple $\left(a_{1}, a_{2}, \ldots, a_{n}\right)$ to the m-tuple $\left(a_{i_{1}}, a_{i_{2}}, \ldots, a_{i_{m}}\right)$, where $m \le n$.

In other words, the projection $P_{i_{1} i_{2}, \ldots, i_{m}}$ deletes $n-m$ of the components of an n-tuple, leaving the $i_{1}$th, $i_{2}$th, $\cdots$, and $i_{m}$th components.

For example, taking the projection $P_{1,3}$ on the 4-tuples $(2, 3, 0, 4)$ and (Jane Doe, 234111001, Geography, 3.14) results in $(2,0)$ and (Jane Doe, Geography) respectively. 

### Join Operation
Used to combine two tables into one when these tables share some identical fields. For instance, a table containing fields for airline, flight number, and gate, and another table containing fields for flight number, gate, and departure time can be combined into a table containing fields for airline, flight number, gate, and departure time.

Let $R$ be a relation of degree $m$ and $S$ a relation of degree $n$. The **join** $J_{p}(R, S)$ where $p \le m$ and $p \le n$, is a relation of degree $m+n-p$ that consists of all $(m+n-p)$-tuples $\left(a_{1}, a_{2}, \ldots, a_{m-p}, c_{1}, c_{2}, \ldots, c_{p}, b_{1}, b_{2}, \ldots, b_{n-p}\right)$, where the $m$-tuple $\left(a_{1}, a_{2}, \ldots, a_{m-p}, c_{1}, c_{2}, \ldots, c_{p}\right)$ belongs to $R$ and the n-tuple $\left(c_{1}, c_{2}, \ldots, c_{p}, b_{1}, b_{2}, \ldots\right.\left.b_{n-p}\right)$ belongs to $S$.

In other words, the join operator produces a new relation from two relations by combining all m-tuples of the first relation with all n-tuples of the second relation, where the last $p$ components of the $m-tuples$ agree with the first $p$ components of the n-tuples.


# Association Rules from Data Mining
We will use supermarket transactions as an example domain for discussing concepts in data mining. We will use records from a database to address the question: How likely is it that a customer buys a product given that they also buy a collection of one or more specified products?

A **transaction** is a set of items bought by a customer during a visit to the store, such as \{ milk, eggs, bread \} or \{orange juice, bananas, yogurt, cream\}. 

Each product in the store is an **item**. A collection of items is an **itemset** (or **basket** or **transaction** in this context). A **k-itemset** is an itemset that contains exactly $k$ items. When a store has $n$ items for sale $a_{1}, a_{2}, \ldots, a_{n}$, each transaction can be represented by an n-tuple $b_{1}, b_{2}, \ldots, b_{n}$, where $b_1$ is a binary variable that tells us whether $a_1$ occurs in this transaction. We can represent a transaction by an $(n+1)$-tuple of the form (transaction number, $\left.b_{1}, b_{2}, \ldots, b_{n}\right)$. The collection of these $(n+1)$-tuples forms a database of transactions. 

The **count** of an itemset $I$, denoted by $\sigma(I)$, in a set of transactions $T=\left\{t_{1}, t_{2}, \ldots, t_{k}\right\}$, where $k$ is a positive integer, is the number of transactions that contain this itemset. That is, 
$$
\sigma(I)=\left|\left\{t_{i} \in T \mid I \subseteq t_{i}\right\}\right|
$$
The **support** of an itemset $I$ is the probabilty that $I$ is included ina randomly selected transaction from $T$. That is, 
$$
\operatorname{support}(I)=\frac{\sigma(I)}{|T|}
$$

The support threshhold $s$ is specified for a particular application. **Frequent itemset mining** is the process of finding itemsets $I$ with support greater than or equal to $s$. Such itemsets are said to be **frequent**.

If $S$ is a set of items and $T$ is a set of transactions, an **association rule** is an implication of the form $I \rarr J$, where $I$ and $J$ are disjoint subsets of $S$. Note that the statement $I \rarr J$ is not the statement that whenever $I$ is a subset of a transaction, then $J$ must also be one. Instead, the strength of an association rule is measured in terms of its **support**, the frequency of transactions that contain both $I$ and $J$, and its **confidence**, the frequency of transactions that contain $J$ when they also contain $I$.
