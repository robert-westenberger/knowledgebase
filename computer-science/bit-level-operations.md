---
title: Bit Level Operations
description: 
published: true
date: 2022-04-30T22:10:49.376Z
tags: 
editor: markdown
---

# Bit Level Operations
## Bitwise Operators

* NOT(~) - Unary operation. Bits that are 0 become 1, those that are 1 become 0.
* AND(&) - Binary operation, taking two equal-length binary representations and performs logical AND. If both bits compared are 1, then return 1. Otherwise return 0. 
* Or (|) - Binary operation, taking two equal-length bit patterns and performs inclusive OR. Returns 0 iff both bits are 0, else return 1.
* XOR (^) - Binary operation, taking two equal-length bit patterns and performs logical exclusive OR. If both bits compared are 0 or 1, it will return 1. Any other combination returns 0.
## Bit masking
* Above operations can be used to implement masking operations. 
* A mask is a bit pattern that indicates a selected set of bits within a word.
* For example, the bit-level operation x & 0xFF yields a value consisting of the least significant byte of x, but with all other bytes set to 0. 

## Bit vectors / arrays / maps
* Strings of bits of fixed length w.  

## Bit vector implementation of set operations
* Sets are represented with a single integer in which bit~i~ x is 1 iff x is in the set. Bit vector a=[01101001] encodes the set {0, 3, 5, 6}. (Remember Bits written a~w-1~ on the left and a~0~ on the right ([a~w-1~, a~w-2~, ..., a~0~]))
* With above representation, intersection of two sets is written with binary AND(&).
* Union of two sets is binary OR(|)
* Set difference is a binary AND NOT (x & ~y)
* Symmetric set difference is binary XOR

## Bit Shifting
A bit shift moves each digit in a number's binary representation left or right. There are three main types of shifts:
### Left Shifts
When shifting left, the most-significant bit is lost, and the $0$ bit is inserted on the other end. 
#### In Javascript
The `<<` operator is the left-shift operator.
The operation `a << b` will take a decimal number `a`, and shift it's binary representation `b` bits to the left. `b` $0$ bits will be added to the right. 