---
title: Merge Sort
description: 
published: true
date: 2021-11-08T18:06:47.410Z
tags: algorithms
editor: markdown
---

# Algorithm
1. Divide the unsorted list into n sublists, each containing one element
2. Repeatedly merge sublists to produce new sorted sublists until there is only one sublist remaining. This will be the sorted list.

# C Implementation
```
static void merge(int *arr, int leftIndex, int middleIndex, int rightIndex) {
	int n1 = middleIndex - leftIndex + 1;
	int n2 = rightIndex - middleIndex;
	int tempLeftArray[n1];
	int tempRightArray[n1];
}
void mergeSort(int *arr, int leftIndex, int rightIndex) {
  if (leftIndex < rightIndex) {
		/* Same as (leftIndex + r)/2, but avoids overflow for large leftIndex and rightIndex */
		int middleIndex = leftIndex + (rightIndex - 1) / 2;

		mergeSort(arr, leftIndex, middleIndex);
		mergeSort(arr, middleIndex + 1, rightIndex);
		merge(arr, leftIndex, middleIndex, rightIndex);
	}
}
```