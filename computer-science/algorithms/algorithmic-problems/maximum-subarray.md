---
title: Maximum Subarray
description: 
published: true
date: 2022-05-15T21:58:12.111Z
tags: algorithms, dynamic-programming, arrays
editor: markdown
---

# Problem
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.


## Constraints
- 1 <= nums.length <= 10^5^
- -10^4^ <= nums[i] <= 10^4^

## Examples
**Input**: nums = [-2,1,-3,4,-1,2,1,-5,4]
**Output**: 6
**Explanation**: [4,-1,2,1] has the largest sum = 6.

**Input**: nums = [1]
**Output**: 1

**Input**: nums = [5,4,-1,7,8]
**Output**: 23

# Approach
## Divide and Conquer
We repeatedly cut the array in half, and search the halves for the max contiguous subarray sum. 

We then return the maximum of the following three: 
- Maximum subarray sum in left half (Make a recursive call)
- Maximum subarray sum in right half (Make a recursive call)
- Maximum subarray sum such that the subarray crosses the midpoint. 
	- This is found by finding the maximum sum starting from mid point and ending at some point on left of mid. Then find the maxumum sum starting from mid + 1 and ending with some point on right of mid + 1. Finally, combine the two and return the max among left, right, and combination of both. 

### Implementation (Javascript)
```
const maxSubArray = function(nums) {
    const findMaxSumInArr = (arr) => {

        // Base Case 1: 1 array item, return it.
        if (arr.length === 1) {
            return arr[0];
        }

        // Base Case 2: 0 array items, return -Infinity for 
        // the purpose of calculations. ( We want a number that 
        // will never be the max )
        if (arr.length === 0) {
            return -Infinity;
        }

        // 0-indexed length and midpoint
        const length = arr.length - 1;
        const mid = Math.floor(length / 2);

        // Recursively divide, finding max sum in left and 
        // right subarrs.

        const leftMaxSumInSubarr = findMaxSumInArr(arr.slice(0, mid));
        const rightMaxSumInSubarr = findMaxSumInArr(arr.slice(mid+1, length+1));

        // Variables to record max contiguous sums for each side
        let leftMaxContiguousSum = 0;
        let rightMaxContiguousSum = 0;

        // For left, find sum of contiguous array and keep an 
        // updated record of the maximum.
        // In order to account for contiguos arrays that 
        // traverse the midpoint, start the search 
        // from midpoint - 1 and traverse leftwards towards index 0.
        // This will guarantee that a contiguous array traversing
        // the midpoint will be able to add the midpoint itself
        // and the right side's contiguous array.
        for (let i = mid - 1, currContiguousSum = 0;i >= 0; i--) {
            currContiguousSum += arr[i];
            leftMaxContiguousSum = Math.max(leftMaxContiguousSum, currContiguousSum);
        }

        // Same as above, but for right side. 
        for (let i = mid + 1, currContiguousSum = 0; i <= length; i++) {
            currContiguousSum += arr[i];
            rightMaxContiguousSum = Math.max(rightMaxContiguousSum, currContiguousSum);
        }

        // Return max sum from current array.. either 
        // from the left side, right side, or a contiguous
        // sub array traversing from left to right through the 
        // midpoint.

        const sumTraversingMidpoint = leftMaxContiguousSum + arr[mid] + rightMaxContiguousSum;
        return Math.max(
            // Max sum traverses the midpoint
            sumTraversingMidpoint,
            // Max sum is on the left
            leftMaxSumInSubarr,
            // Max sum is on the right
            rightMaxSumInSubarr
        );

    }
    return findMaxSumInArr(nums);
};
```
#### Explanation 
Array is `[-2,1,-3,4,-1,2,1,-5,4]`

Array is split into `[-2,1,-3,4]` and `[2, 1, -5, 4]`, (`-1`) is the midpoint).

`[-2,1,-3,4]` is split into `[-2]` and `[-3,4]`.

The max subarray of `[-2]` is just `-2`.

`[-3,4]` is split into `[]` and `[4]`, since the mid point is `[-3]`.

The max sum for `[]` is `-Infinity` and `4` for `[4]`.

The left max contiguous sum for `[-3, 4]` is `0` and the right max contiguous sum is `4`. The sum traversing the midpoint is the midpoint (`-3`) + left max (`0`) + right max (`4`) which is `1`. From this, we return the max between the midpoint sum, left sum and right sum, which is the right max (`4`).

Now we are back to `[-2,1,-3,4]`, and we know now that the max contiguous sum on the left subarray is `-2`, and on the right is `4` (`1` is the midpoint). 

The left max contiguous sum for `[-2,1,-3,4]` is `0` and the right max contiguous sum is `1`. The sum traversing the midpoint is left max contiguous sum (`0`) + midpoint (`1`) + rightmax contiguous sum(`1`) = `2`. We return the max val between the sum traversing the midpoint, the left sum and the right sum, which is the right side (`4`).

Now onto the right side of the original array, `[2, 1, -5, 4]`. 
It's split into `[2]` and `[-5, 4]`. 

The max subarray of `[2]` is just `2`.

`[-5,4]` is split into `[]` and `[4]`, since the mid point is `[-5]`. The sum traversing the midpoint is `-1`.
## Dynamic Programming
### Kadane's Algorithm
TODO