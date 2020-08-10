---
title: Sequences as Conventional Interfaces
description: 
published: true
date: 2020-08-10T02:03:04.154Z
tags: book-notes, data-structures, design-principles
editor: markdown
---

# Sequences as Conventional Interfaces

It is frequently helpful to conceptualize processes in terms of signals flowing through a cascade of stages, each of which implements part of the program plan. 

Compare the algorithms for summing the squares of the leaves of a  [tree](/computer-science/trees) that are odd (**TOP**) and constructing a list of even fibo numbers *Fib(k)* where *k* is less than or equal to *n* (**BOTTOM**).

![signalflowalgorithm.png](/signalflowalgorithm.png)

* Sum squares of the leaves of a tree that are odd
	* Begin with *enumerator* that generates a **signal** consisting of leaves on given tree.
  * The signal is passed through a **filter**, eliminating all but the odd elements
  * The resulting signal is turn passed through a map, which a **transducer** that applies the square function to each element. 
  * The output of the map is then fed to an **accumulator** which combines the elements using + starting from an initial 0.

##### Sequence Operations
* Focus on the signals that flow from one stage in the process to the next in order to organize programs that clearly reflect the signal flow structure.

* Sum squares of the leaves of a tree that are odd
* 
