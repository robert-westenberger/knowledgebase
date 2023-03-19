---
title: Algorithmic Problems
description: 
published: true
date: 2023-03-19T23:36:52.855Z
tags: algorithms
editor: markdown
---

# Dynamic Programming
Dynamic Programming is simplifying a complicated problem by breaking it down into simpler sub-problems in a recursive manner.
## Examples
[Coin Change Problem](/computer-science/algorithms/algorithmic-problems/coin-change-problem) - Calculate how many ways you can make change for an amount of money, given a set of coins. This is a variation of the knapsack problem.


[Max Path Sum in a Pyramid of Numbers](/computer-science/algorithms/algorithmic-problems/max-path-sum-in-a-pyramid-of-numbers) - Calculate the maximum sum, from the top to the bottom of a pyramid, when you're only allowed to move to adjacent numbers at each level.

[Minimum Cost Path](/computer-science/algorithms/algorithmic-problems/minimum-cost-path) - Given a 2D matrix where each cell has a cost to travel, find a path from the left-top corner to the bottom-right corner with minimum travel cost. You can only move right or down. 

[House Robber](/computer-science/algorithms/algorithmic-problems/house-robber) - Given an integer array, return the maximum sum when picking no two adjacent integers. 
## Kadane's Algorithm
### Examples
[Best Time to Buy and Sell Stock](/computer-science/algorithms/algorithmic-problems/best-time-to-buy-and-sell-stock) - Given an array prices where prices[i] is the price of a given stock on the i^th^ day, return the maximum profit you can achieve by buy choosing a single day to buy the stock and a single day in the future to sell it. 

[Maximum Subarray](/computer-science/algorithms/algorithmic-problems/maximum-subarray) - Find the contiguous subarray that has the largest sum. 

# [Binary Search](/computer-science/algorithms/binary-search)
## Find First Position of Element in Array sorted in non-increasing order ($O(\log n)$)
Use iterative binary search. 
Initialize low = 0 
high = arr.length - 1.

1. While $\mathrm{low} \le \mathrm{high}$ :
2. If arr[mid] is negative and arr[mid-1] is nonnegative, return mid.
3. If mid is 0 and arr[mid] is negative, return mid.
4. If arr[mid] is positive, set low = mid + 1 and continue the while loop.
5. Otherwise, high = mid - 1.

```
function findIndexOfFirstNegative(arr) {
  let low = 0;
  let high = arr.length - 1;

  while (low <= high) {
    const mid = low + Math.floor((high - low) / 2);

    if (0 > arr[mid] && 0 < arr[mid - 1]) {
      return mid;
    }

    if (mid === 0 && arr[mid] < 0) {
      return mid;
    }

    if (0 < arr[mid]) {
      low = mid + 1;

      continue;
    }
    high = mid - 1;
  }
  return -1;
}
```
## Count Negative Numbers in a Sorted Matrix
Given a m x n matrix grid which is sorted in non-increasing order both row-wise and column-wise, return the number of negative numbers in grid.
### First attempt 
Once we find the first occurence of a negative number within a row, know that all numbers to the right in the same row and below it in the same column are negative. 

The approach is, starting from the first row, to use binary search to scan for the first negative. Once the first negative is found, subsequent rows are searched with the upper limit as the index of the first negative number in the current row. In other words, once a negative number is found, that entire column for subsequent rows is never searched.
```
function findIndexOfFirstNegative(arr: number[], arrHigh: number) {
  let low = 0;
  let high = arrHigh;

  while (low <= high) {
    const mid = low + Math.floor((high - low) / 2);

    if (0 > arr[mid] && 0 <= arr[mid - 1]) {
      return mid;
    }

    if (mid === 0 && arr[mid] < 0) {
      return mid;
    }

    if (0 <= arr[mid]) {
      low = mid + 1;

      continue;
    }
    high = mid - 1;
  }
  return -1;
}

function countNegatives(grid: number[][]): number{
  let count = 0;
  const rowLastIndex = grid[0].length - 1;
  let high = rowLastIndex;
  grid.forEach((row) => {
    const indexOfFirstNeg = findIndexOfFirstNegative(row, high);
    if (indexOfFirstNeg < 0) {
      high = rowLastIndex;
      return;
    }
    high = indexOfFirstNeg;
    count = count + grid[0].length - indexOfFirstNeg;
  });
  return count;
}
```
## Find Target Indices After Sorting Array 
You are given a 0-indexed integer array nums and a target element target.

A target index is an index i such that nums[i] == target.

Return a list of the target indices of nums after sorting nums in non-decreasing order. If there are no target indices, return an empty list. The returned list must be sorted in increasing order.

### First attempt
```
function targetIndices(nums: number[], target: number): number[] {
    const ans: number[] = [];
    const sorted = nums.sort((a, b) => {
        return a-b;
    });
    let a = 0; 
    let b = sorted.length - 1;
    while (a <= b) {
        const k = Math.floor((a+b) / 2);
        
        if (sorted[k] === target) {
            let c = k - 1;
            let d = k + 1
            ans.push(k);
            while (0 <= c) {
                if (sorted[c] === target) {
            
                    ans.unshift(c);
                
                } else {
                    break;
                }
                c = c-1;
            }
            while (d < sorted.length) {
               if (sorted[d] === target) {
                    ans.push(d);
                } else {
                    break;
                }
                d = d + 1;
            }
       break;
        }
        if (sorted[k] > target) {
            b = k-1;
        } else {
            a = k+1;
        }
    }
    return ans;
};
```
### $O(n)$ algorithm
Don't need to sort the array.
Maintain a `count` and a `lessThan` variable, both initialized to 0. 

- For each number in the array
	- If num === target, increment count
  - If num < target, increment lessThan
  
- For the number of found items (IE, count) 
  - Push the current value of lessThan to the results array
  - Increment lessThan

# Depth First Search
## Examples
### [Find Connected Cells in a Matrix](/computer-science/algorithms/algorithmic-problems/find-connected-cells-in-matrix)
# Divide and Conquer
Divide and Conquer works by dividing the problem into sub-problems, conquer each sub-problem recursively and combine these solutions.
## Examples
[Maximum Subarray](/computer-science/algorithms/algorithmic-problems/maximum-subarray) - Find the contiguous subarray that has the largest sum. 
# Two Pointer Algorithms 
Algorithms that take advantage of the structure of data, using pointers, to calculate something.

## Examples
[Detect Loop in Linked List (Floyd's Cycle Detection Algorithm)](/computer-science/algorithms/algorithmic-problems/detect-loop-in-linked-list) - Uses two pointers, moving through a linked list at different speeds, to detect a loop.
[Squares of a sorted array](/computer-science/algorithms/algorithmic-problems/squares-of-a-sorted-array) - Given a sorted array of numbers, return the squares of those numbers, maintaining sorted order.
# Backtracking
See [Backtracking](/computer-science/algorithms/backtracking)
Backtracking is a general algorithm for finding solutions to some computational problems, notably constrant satisfaction problems, that incrementally builds candidates to the solutions, and abandons a candidate ("backtracks") as soon as it determines that the candidate cannot possibly be completed to a valid solution.
## Examples
[Generate Valid Parentheses](/computer-science/algorithms/algorithmic-problems/generate-valid-parentheses) - For a number `n`, generate all combinations of well-formed parentheses.

[Find Permutations](/computer-science/algorithms/algorithmic-problems/find-permutations) - Given an array nums of distinct integers, return all the possible permutations.

[Find Combinations](/computer-science/algorithms/algorithmic-problems/combinations)
# Sliding Window Technique
A computational technique which aims to reduce the use of a nested loop and replace it with a single loop (thereby reducing time complexity).

## When to use it
For finding subarrays in an array that satisfies given conditions. 


## Examples
### Find the longest substring of a string containing distinct characters
[Longest Substring Without Repeating Characters](/computer-science/algorithms/algorithmic-problems/longest-substring-without-repeating-characters)
Given a string and a positive number `k`, find the longest substring of the string containing `k` distinct characters. If `k` is more than the total number of distinct characters in the string, return the whole string.
### Find all substrings of a string that are a permutation of another string.
Find all substrings of a string that contains all characters of another string. In other words, find all substrings of the first string that are anagrams of the second string.
### Find maximum length sequence of continuous ones (Using Sliding Window)
Given a binary array, find the index of 0 to be replaced with 1 to get a maximum length sequence of continuous ones.
### Count distinct absolute values in a sorted array
Given an array of sorted integers that may contain several duplicate elements, count the total number of distinct absolute values in it.

# Linked Lists
## Merge
### Example
[Merge Two Sorted Linked Lists](/computer-science/algorithms/algorithmic-problems/merge-two-sorted-linked-lists)
# Trees
## Balancing
### Examples
#### Balance a Binary Search Tree
## Insertions
### Examples
#### Build a "Maximum Binary Tree"
[Maximum Binary Tree](/computer-science/algorithms/algorithmic-problems/maximum-binary-tree)
#### Construct Binary Search Tree from Preorder Traversal
[Construct Binary Search Tree from Preorder Traversal](/computer-science/algorithms/algorithmic-problems/construct-binary-tree-from-given-preorder-traversal)
## Traversals
### Examples
#### Maximum Difference Between Node and Ancestor
[Maximum Difference Between Node and Ancestor](/computer-science/algorithms/algorithmic-problems/maximum-difference-between-node-and-ancestor)
#### Find a Corresponding Node of a Binary Tree in a Clone of That Tree
[Find a Corresponding Node of a Binary Tree in a Clone of That Tree](/computer-science/algorithms/algorithmic-problems/find-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree)
#### Sum of Nodes With Even Valued Grandparent
[Sum of Nodes With Even Valued Grandparent](/computer-science/algorithms/algorithmic-problems/sum-of-nodes-with-even-valued-grandparent)
#### Sum Numbers In A Range In A Binary Search Tree
[Range Sum of Binary Search Tree](/computer-science/algorithms/algorithmic-problems/range-sum-of-bst)
## Miscellaneous
### Examples
[Populating Next Right Pointers in Each Node](/computer-science/algorithms/algorithmic-problems/populating-next-right-pointers-in-each-node)
# Stack
## Examples
### Building Lowest Number by Removing k digits from a given number
[Remove k digits](/computer-science/algorithms/algorithmic-problems/remove-k-digits)

# Graphs
## Breadth First Search
### Examples
[0 1 Matrix](/computer-science/algorithms/algorithmic-problems/0-1-matrix) - Given an m x n binary matrix mat, return the distance of the nearest 0 for each cell.

# Arrays
## Examples
[Find Minimum In Rotated Array](/computer-science/algorithms/algorithmic-problems/find-minimum-in-rotated-array) - Given the sorted rotated array nums of unique elements, return the minimum element of this array in O(log n) time.
[Search in Rotated Sorted Array](/computer-science/algorithms/algorithmic-problems/search-in-sorted-rotated-array) - Given the sorted rotated array nums of unique elements, return the index of a target number, and -1 if it doesn't exist in the array.