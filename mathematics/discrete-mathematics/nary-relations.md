---
title: n-ary Relations
description: 
published: true
date: 2021-05-11T19:01:51.677Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# n-ary Relations
Let $A_{1}, A_{2}, \ldots, A_{n}$ be sets. An **n-ary relation** on these sets is a subset of $A_{1} \times A_{2} \times \cdots \times A_{n}$. The sets $A_{1}, A_{2}, \ldots, A_{n}$ are called the **domains** of the relation, and $n$ is called its **degree**.

For example, let $R_1$ bbe the relation $\mathbf{N} \times \mathbf{N} \times \mathbf{N}$ consisting of triples $(a,b,c)$, where $a$, $b$, and $c$ are integers with $a \lt b \lt c$. Then $(1,2,3) \in R$, but $(2,4,3) \notin R$. The degree of the relation is $3$. Its domains are all equal to the set of natural numbers.

# Databases and Relations
The **relational data model** is based on the concept of a relation. 

A database consists of **records**, which are **n-tuples**, made up of fields. The fields are the entries of the n-tuples. The relational data model represents a database of records as an n-ary relation. For instance, a database of student records may be made up of fields containing the name, student number, major, and gpa of the student. Student records are represented as 4-tuples of the form (Student_name, ID_number, Major, GPA). 

Relations used to represent databases are called **tables**. Each column of the table corresponds to an attribute of the database. 

A domain of an n-ary relation is called a **primary key** when the value of the n-tuple from this domain determines the n-tuple. That is, a domain is a primary key when no two n-tuples in the relation have the same value for this domain.

The current collection of n-tuples in a relation is called the **extension** of the relation.  The more permanent part of a database, including the name and attributes of the database, is called its **intension**.

## Selecting a primary key
When selecting a primary key, the goal should be to select a key that can serve as a primary key for all possible extensions of the database. To do this, it is necessary to examine the intension of the database to understand the set of possible n-tuples that can occur in an extension.