---
title: Algorithms
description: 
published: true
date: 2023-03-18T20:59:52.227Z
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
## Quick Sort
## Shaker Sort
## Insertion Sort

## Selection Sort
## $O\left(n^2\right)$ algorithms
### Inversions
Bubble sort, for example, always swaps consecutive elements in the array. The time complexity of such an algorithm is always at least $O(n^2)$, because in the worst case, $O(n^2)$ swaps are required for sorting the array.

A useful concept when analyzing sorting algorithms is an inversion: a pair of array elements (array $[a]$, array $[b]$ ) such that $a<b$ and array $[a]>$ array $[b]$, i.e., the elements are in the wrong order. For example, the array

$$
\begin{array}{|l|l|l|l|l|l|l|l|}
\hline 1 & 2 & 2 & 6 & 3 & 5 & 9 & 8 \\
\hline
\end{array}
$$

has three inversions: $(6,3),(6,5)$ and $(9,8)$. The number of inversions indicates how much work is needed to sort the array. An array is completely sorted when there are no inversions. On the other hand, if the array elements are in the reverse order, the number of inversions is the largest possible:
$$
1+2+\cdots+(n-1)=\frac{n(n-1)}{2}=O\left(n^2\right)
$$
Swapping a pair of consecutive elements that are in the wrong order removes exactly one inversion from the array. Hence, if a sorting algorithm can only swap consecutive elements, each swap removes at most one inversion, and the time complexity of the algorithm is at least $O\left(n^2\right)$.



### Bubble Sort 

Simple but not very efficient. Bubble sort conists of $n$ rounds. Orders by comparing adjacent elements, interchanging them if they are in the wrong order. 
To carry out the bubble sort, we
perform the basic operation, that is, interchanging a larger element with a smaller one following
it, starting at the beginning of the list, for a full pass.
```
for (int i = 0; i < n; i++) {
  for (int j = 0; j < n-1; j++) {
    if (array[j] > array[j+1]) {
      swap(array[j],array[j+1]);
    }
  }
}
```

## $O(n \log n)$ algorithms
It is possible to sort an array efficiently in $O(n \log n)$ time using algorithms that are not limited to swapping consecutive elements.
### Merge Sort
Based on recursion. 

Merge sort sorts a subarray array $[a \ldots b]$ as follows:
1. If $a=b$, do not do anything, because the subarray is already sorted.
2. Calculate the position of the middle element: $k=\lfloor(a+b) / 2\rfloor$.
3. Recursively sort the subarray array $[a \ldots k]$.
4. Recursively sort the subarray array $[k+1 \ldots b]$.
5. Merge the sorted subarrays array $[a \ldots k]$ and array $[k+1 \ldots b]$ into a sorted subarray array $[a \ldots b]$.

Merge sort is efficient beacuse it halves the size of the subarray at each step. The recursion consists of $O(\log n)$ levels, and processing each level takes $O(n)$ time. Merging the subarrays array $[a \ldots k]$ and array $[k+1 \ldots b]$ is possible in linear time, because they are already sorted.

#### Example
Consider the following array 
$$
\begin{array}{|l|l|l|l|l|l|l|l|}
\hline 1 & 3 & 6 & 2 & 8 & 2 & 5 & 9 \\
\hline
\end{array}
$$

Itll be divided into two subarrays

$$
\begin{aligned}
&\begin{array}{|l|l|l|l|}
\hline 1 & 3 & 6 & 2 \\
\hline
\end{array}\\
&\begin{array}{|l|l|l|l|}
\hline 8 & 2 & 5 & 9 \\
\hline
\end{array}
\end{aligned}
$$

The subarrays will be sorted recursively as follows 

$$
\begin{aligned}
&\begin{array}{|l|l|l|l|}
\hline 1 & 2 & 3 & 6 \\
\hline
\end{array}\\
&\begin{array}{|l|l|l|l|}
\hline 2 & 5 & 8 & 9 \\
\hline
\end{array}
\end{aligned}
$$

Finally, the algorithm merges the sorted subarrays and creates the final sorted array. 

$$
\begin{array}{|l|l|l|l|l|l|l|l|}
\hline 1 & 2 & 2 & 3 & 5 & 6 & 8 & 9 \\
\hline
\end{array}
$$

## $O(n+k)$ algorithms
### Counting Sort
Sorts an array in $O(n)$ time assuming that every element in the array is an integer between $0 \ldots c$ and $c=O(n)$

The algorithm creates a bookkeeping array, whose indices are elements of the original array. The algorithm iterates through the original array and calculates how many times each element appears in the array. 

#### Example
The array 
$$
\begin{array}{|l|l|l|l|l|l|l|l|}
\hline 1 & 3 & 6 & 9 & 9 & 3 & 5 & 9 \\
\hline
\end{array}
$$

corresponds to the following bookkeeping array 

$$
\begin{aligned}
&\begin{array}{lllllllll}
1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9
\end{array}\\
&\begin{array}{|l|l|l|l|l|l|l|l|l|}
\hline 1 & 0 & 2 & 0 & 1 & 1 & 0 & 0 & 3 \\
\hline
\end{array}
\end{aligned}
$$

For example, the value at position 3 in the bookkeeping array is 2 , because the element 3 appears 2 times in the original array.

Construction of the bookkeeping array takes $O(n)$ time. After this, the sorted array can be created in $O(n)$ time because the number of occurrences of each element can be retrieved from the bookkeeping array. Thus, the total time complexity of counting sort is $O(n)$.

Counting sort is a very efficient algorithm but it can only be used when the constant $c$ is small enough, so that the array elements can be used as indices in the bookkeeping array.


# String Matching
Algorithms for finding where, if at all, a string of characters $P$, called the **pattern** occur, within another string $T$, called the **text**.

# Greedy Algorithms
Designed to solve **optimization problems**, the goal of which is to either minimize or maximize the value of some parameter. 

**Greedy Algorithms** are a family of algorithms that choose what seems to be the "best" choice at every step of the algorithm, with no consideration of all sequences of steps that may lead to the true optimal solution.


# The Halting Problem
