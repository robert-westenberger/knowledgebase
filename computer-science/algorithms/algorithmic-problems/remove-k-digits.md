---
title: Remove K Digits
description: Given string num representing a non-negative integer num, and an integer k, return the smallest possible integer after removing k digits from num.
published: true
date: 2022-05-07T21:21:28.091Z
tags: algorithms, stack
editor: markdown
---

# Problem
Given string num representing a non-negative integer `num`, and an integer `k`, return the smallest possible integer after removing `k` digits from `num`.
## Constraints
- $1 \le k \le \text{num.length} \le 10^5$
- `num` constits of only digits
- `num` does not have any leading zeros except for the zero itself.

## Examples
**Input**: num = "1432219", k = 3
**Output**: "1219"
**Explanation**: Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.

**Input**: num = "10200", k = 1
**Output**: "200"
**Explanation**: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.

**Input**: num = "10200", k = 1
**Output**: "200"
**Explanation**: Remove the leading 1 and the number is 200. Note that the output must not contain leading zeroes.

# Approach
## Using Stack
The length of the given string will be `n`, so the result string will contain the length of `n-k`.

We ensure that the output string contains minimum values at their high weightage positions by using a stack.

1. Return $0$ if $k \ge n$, return `num` if $k=0$.

2. Create a stack and iterate through `num` string and push the value at that position if it is greater than the top element of the stack.

3. Iterate through the num string and if the integer value at that position is less than the top of the stack we will pop the stack and decrement k until we reach the condition where the top of the stack is less than the value we are looking at(while $k>0$) (by this we are making sure that most significant positions of the result are filled with minimum values).

4. If the $k$ is still greater than $0$ we will pop stack until $k$ becomes $0$.
5. Append the elements in the stack to the result string.

### Implementation (Javascript)
```
const removeKdigits = function(num, k) {
    const numLength = num.length;
    const stack = [];
    let l = k;
    let position = 0;
    if (k >= numLength) {
        return "0";
    }
    if (k === 0) {
        return num;
    }
    while (position < numLength) {
        while (stack.length > 0 && l > 0 && stack[stack.length - 1] > num[position]) {
            stack.pop();
            l--;
        }
        if (stack.length > 0 || num[position] != "0") {
            stack.push(num[position]);
        }
        position++;
    }
    while (stack.length > 0 && l) {
        l--;
        stack.pop();
    }
    if (!stack.length){
        return "0";
    }
    return stack.join("");
};

```
#### Example
"1432219", 3

**Position**: **1**432219
**Stack**: []
**k**: 3

Stack is empty, push 1 onto stack.

**Position**: 1**4**32219
**Stack**: [1]
**k**: 3

4 greater than 1, push 4 onto stack.

**Position**: 14**3**2219
**Stack**: [1. 4]
**k**: 3

3 less than 4, remove 4 from stack. Decrement k.
3 is greater than 1, push 3 onto the stack.

**Position**: 143**2**219
**Stack**: [1, 3]
**k**: 2

2 is less than 3, remove 3 from the stack. Decrement k.
2 is greater than 1, push 2 onto the stack.

**Position**: 1432**2**19
**Stack**: [1, 2]
**k**: 1
2 is not less than 2, push 2 onto the stack.

**Position**: 14322**1**9
**Stack**: [1, 2, 2]
**k**: 1

1 is less than 2, remove 2 from the stack. Decrement k.
k is now 0, push 1 onto the stack.

**Position**: 143221**9**
**Stack**: [1, 2, 1]
**k**: 0
k is 0, push 9 onto the stack.
**Position**: (end of string)
**Stack**: [1, 2, 1, 9]
**k**: 0


The answer hidden in the string is **1**43**2**2**19**