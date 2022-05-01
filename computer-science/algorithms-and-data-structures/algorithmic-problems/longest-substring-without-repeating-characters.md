---
title: Longest Substring Without Repeating Characters
description: 
published: true
date: 2022-05-01T21:06:40.690Z
tags: algorithms, sliding-window-technique
editor: markdown
---

# Problem
Given a string `s`, find the length of the longest substring without repeating characters.

## Constraints
$0 \le \text{s.length} \le 5 \cdot 10^4$
$s$ consists of English letters, digits, symbols and spaces.
## Examples
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

## Approach
### Sliding Window Technique
- Run a loop from the beginning of the string to the end of the string.
- Inside this loop, do two things: 
	- Create an object that will keep track of letters visited.
  - Run another loop inside this loop, starting at the current outer loop's position and running to the end of the string.
- Inside the inner loop, if we encounter a character we have seen before, we break, incrementing the outer loop. This will reset the visited characters, and we restart the process over again.
- Otherwise, we mark the character as visited. We also record the result, if its greater than the current result.

The outer loop represents the left side of the sliding window. The inner loop represents the right side of the sliding window. 

So starting from the beginning of the string, we increase the size of the window one character at a time. Every time the window size is increased, we check to see if the character that is added to the window is unique. If it is, we can expand the size of the window yet again. If it's not, we move the left bound of the window a position to the right, reset our "visited" object and shrink the window back to 1 character again. Then we repeat the process. 

The result is whenever the window was at it's largest. 

#### Implementation (Javascript)
```
const lengthOfLongestSubstring = (s) => {
    let result = 0;
    
    for (let i = 0; i < s.length; i++) {
      const visited = {};
      for (let j = i; j < s.length; j++) {
        if (visited[s[j]]) {
          break;
        } else {
          result = Math.max(result, j - i + 1);
          visited[s[j]] = true;
        }
      }
    }
    return result;
};
```
##### Example 
So for the string "abcabcbb", the window is shown in **bold**.

**a**bcabcbb
**ab**cabcbb
**abc**abcbb
a**b**cabcbb
a**bc**abcbb
a**bca**bcbb
ab**c**abcbb
ab**ca**bcbb
ab**cab**cbb
abc**a**bcbb
abc**ab**cbb
abc**abc**bb
abca**b**cbb
abca**bc**bb
abcab**c**bb
abcab**cb**b
abcabc**b**b
abcabcb**b**

### Optimized Sliding Window Technique
- Initialize an object to keep track of characters encountered.
- Initialize result, left, and right variables to `0`.
- Slide the right index from the beginning of the string to the end of the string. 

