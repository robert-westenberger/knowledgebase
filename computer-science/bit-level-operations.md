---
title: Bit Level Operations
description: 
published: true
date: 2020-09-18T03:29:39.113Z
tags: 
editor: markdown
---

# Bit Level Operations


#### Bitwise Operators

* NOT - Unary operation. Bits that are 0 become 1, those that are 1 become 0.
* AND - Binary operation, taking two equal-length binary representations and performs logical AND. If both bits compared are 1, then return 1. Otherwise return 0. 
* Or - Binary operation, taking two equal-length bit patterns and performs inclusive OR. Returns 0 iff both bits are 0, else return 1.
* XOR - Binary operation, taking two equal-length bit patterns and performs logical exclusive OR. If both bits compared are 0 or 1, it will return 1. Any other combination returns 0.
#### Bit masking
* Above operations can be used to implement masking operations. A mask is a bit pattern that indicates a selected set of bits within a word.
