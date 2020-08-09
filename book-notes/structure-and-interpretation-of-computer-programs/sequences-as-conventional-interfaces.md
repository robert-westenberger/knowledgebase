---
title: Sequences as Conventional Interfaces
description: 
published: true
date: 2020-08-09T03:55:56.973Z
tags: book-notes, data-structures, design-principles
editor: markdown
---

# Sequences as Conventional Interfaces

It is frequently helpful to conceptualize processes in terms of signals flowing through a cascade of stages, each of which implements part of the program plan. 

Compare the algorithms for summing the squares of the leaves of a  [tree](/computer-science/trees) that are odd (**TOP**) and constructing a list of even fibo numbers *Fib(k)* where *k* is less than or equal to *n* (**BOTTOM**).

![signalflowalgorithm.png](/signalflowalgorithm.png)

* Sum squares of the leaves of a tree that are odd
	* Begin with *enumerator* that generates a **signal** consisting of leaves on given tree.
* Construct list of even fibo numbers where k is less than or equal to n