---
title: Without Loss of Generality
description: 
published: true
date: 2021-04-08T17:52:36.102Z
tags: discrete-mathematics
editor: markdown
---

# Without Loss of Generality
When the phrase "without loss of generality" is used in a proof, we are asserting that by proving one case of a theorem, no additional argument is required to prove other specified cases.

## Examples

### Example 1
Show that if $x$ and $y$ are integers and both $xy$ and $x+y$ are even, then both $x$ and $y$ are even. 
#### Solution
We will prove using contraposition, the notion of WLOG, and proof by cases. Suppose that $x$ and $y$ are not both even. That is, assume $x$ is odd or $y$ is odd or both. WLOG, we assume $x$ is odd, so that $x = 2m+1$ for some integer $m$.

To complete the proof, we need to show that $xy$ is odd or $x+y$ is odd. Consider two cases: ($i$) $y$ is even, and ($ii$) $y$ is odd. In ($i$), $y=2n$ for some integer $n$, so that $x+y=(2 m+1)+2 n=2(m+n)+1$ is odd. In ($ii$), $y=2n+1$ for some integer $n$, so that $xy=(2m+1)(2n+1)=4m+2m+2n+1=2(2nm+m+n)+1$ is odd.