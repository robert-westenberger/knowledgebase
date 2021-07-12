---
title: Algorithms
description: 
published: true
date: 2021-07-12T02:17:13.726Z
tags: computer-science, discrete-mathematics, algorithms
editor: markdown
---

# Properties of Algorithms
▶ **Input**. An algorithm has input values from a specified set.
▶ **Output**. From each set of input values an algorithm produces output values from a specified
set. The output values are the solution to the problem.
▶ **Definiteness**. The steps of an algorithm must be defined precisely.
▶ **Correctness**. An algorithm should produce the correct output values for each set of input
values.
▶ **Finiteness**. An algorithm should produce the desired output after a finite (but perhaps
large) number of steps for any input in the set.
▶ **Effectiveness**. It must be possible to perform each step of an algorithm exactly and in a
finite amount of time.
▶ **Generality**. The procedure should be applicable for all problems of the desired form, not
just for a particular set of input values.

# Searching Algorithms
## Linear / Sequential Search
For each item in a list, check to see if item in the list is the value we are looking for. If it is, return it or the location. If not, check the next item in the list. If we reach the end of the list, the item is not in the list.
## Binary Search
For use when the list is sorted and the list has items ordered by increasing size. It compares the target item to the item in the middle of the list. The list is then split into two smaller sublists of the same size, or where one of the sublists is one item fewer than the other. The search continues by restricting the search to the appropriate sublist based on the comparison of the element to be located and the middle term.