---
title: Algorithms
description: 
published: true
date: 2023-03-18T20:21:06.642Z
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

# Sorting Algorithms
Many efficient algorithms use sorting as a subroutine, because it is often easier to process data if the elements are in a sorted order. 
## Tim Sort
## Merge Sort
## Quick Sort
## Shaker Sort
## Insertion Sort

## Selection Sort
## Bubble Sort
Simple but not very efficient. Orders by comparing adjacent elements, interchanging them if they are in the wrong order. 
To carry out the bubble sort, we
perform the basic operation, that is, interchanging a larger element with a smaller one following
it, starting at the beginning of the list, for a full pass.
# String Matching
Algorithms for finding where, if at all, a string of characters $P$, called the **pattern** occur, within another string $T$, called the **text**.

# Greedy Algorithms
Designed to solve **optimization problems**, the goal of which is to either minimize or maximize the value of some parameter. 

**Greedy Algorithms** are a family of algorithms that choose what seems to be the "best" choice at every step of the algorithm, with no consideration of all sequences of steps that may lead to the true optimal solution.


# The Halting Problem
