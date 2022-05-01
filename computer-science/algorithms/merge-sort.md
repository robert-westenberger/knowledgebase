---
title: Merge Sort
description: 
published: true
date: 2021-11-08T20:03:49.130Z
tags: algorithms
editor: markdown
---

# Algorithm
1. Divide the unsorted list into n sublists, each containing one element
2. Repeatedly merge sublists to produce new sorted sublists until there is only one sublist remaining. This will be the sorted list.

# C Implementation
```
static void merge(int *arr, int leftIndex, int middleIndex, int rightIndex) {
	int i, j, k;
	int n1 = middleIndex - leftIndex + 1;
	int n2 = rightIndex - middleIndex;
	int tempLeftArray[n1];
	int tempRightArray[n1];

	for (i = 0; i < n1; i++) {
		tempLeftArray[i] = *(arr + leftIndex + i);
	}
	for (j = 0; j < n2; j++)
	{
		tempRightArray[j] = *(arr + middleIndex + j + 1);
	}
	i=0;
	j=0;
	k=leftIndex;

	while (i < n1 && j < n2)
	{
		if (tempLeftArray[i] <= tempRightArray[j])
		{
			*(arr + k) = tempLeftArray[i];
			i++;
		}
		else
		{
			*(arr + k) = tempRightArray[j];
			j++;
		}
		k++;
	}

	/* Copy the remaining elements of L[], if there
    are any */
	while (i < n1)
	{
		*(arr + k) = tempLeftArray[i];
		i++;
		k++;
	}

	/* Copy the remaining elements of R[], if there
    are any */
	while (j < n2)
	{
		*(arr + k) = tempRightArray[j];
		j++;
		k++;
	}
}
void mergeSort(int *arr, int leftIndex, int rightIndex) {
  if (leftIndex < rightIndex) {
		/* Same as (leftIndex + r)/2, but avoids overflow for large leftIndex and rightIndex */
		int middleIndex = leftIndex + (rightIndex - leftIndex) / 2;

		mergeSort(arr, leftIndex, middleIndex);
		mergeSort(arr, middleIndex + 1, rightIndex);
		merge(arr, leftIndex, middleIndex, rightIndex);
	}
}
```

The above implementation will recursively halve the array until it is n arrays of size 1, where n = the length of the original array.

Once the size becomes 1, 