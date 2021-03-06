---
title: Sequences as Conventional Interfaces
description: 
published: true
date: 2020-08-17T03:34:25.839Z
tags: book-notes, data-structures, design-principles
editor: markdown
---

# Sequences as Conventional Interfaces

It is frequently helpful to conceptualize processes in terms of signals flowing through a cascade of stages, each of which implements part of the program plan. 

Expressing programs as a sequence of operations helps us make programs that are modular. Modular design can be encouraged by providing a library of standard components together with a conventional interface for connecting 

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
`const sumOddSquares = (tree) => accumulate(plus, 0, map(square, filter(is_odd, enumerate_tree(tree))));`
* Constructing a list of even fibo numbers *Fib(k)* where *k* is less than or equal to *n* 
`const evenFibs = (n) => accumulate(pair, null, filter(is_even, map(fib, enumerate_interval(0, n))));`

These pieces (accumulate, map, filter) can be rearranged to perform many other tasks.

##### Sequence Operations for Conventional Data Processing
* A sequence of personnel records can be processed to find, for example, the salary of the highest-paid programmer.
* When we uniformly represent structures as sequences, we have localized
the data-structure dependencies in our pograms to a small number of sequence operations.
`const salary_of_highest_paid_programmer = records =>`
`accumulate(math_max,`
    `	0,`
    `map(salary,`
      `  filter(is_programmer, records)));`

##### Nested Mappings
* Sequences can be mapped and those mappings mapped themselves 

`const prime_sum_pairs = n => {`
    `	const sequenceOfOrderedPairsToN = flatmap(i => map(j => list(i, j),`
        `		enumerate_interval(1, i - 1)),`
        `		enumerate_interval(1, n));`
    `	const pairSumsThatArePrime = filter(is_prime_sum, sequenceOfOrderedPairsToN);`
    `	return map(make_pair_sum, pairSumsThatArePrime);`
`}`
Above, a way to find all ordered pairs of distinct integers *i* and *j* where 1 <= *j* < i <= *n*, such that i + j is prime. Integers are enumerated from 1 to n, and for each of those integers *i* 