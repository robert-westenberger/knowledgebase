---
title: Integer Representations
description: 
published: true
date: 2020-09-29T02:03:01.585Z
tags: computer-science, computer
editor: markdown
---

# Integer Representations

#### Integral Data Types
* C integral data types ( char, short, int, long, signed and unsigned) have different minimum and maximum allocatable bytes (dependent on whether its compiled on 32 or 64 bit machines). 

#### Unsigned Encodings
* Unsigned encodings
	* An integer can be encoded as a bit vector. The below equation (binary to unsigned) maps strings of zeros and ones of length *w* to nonnegative integers..
  $$B2U_{w}(\overrightarrow{x})\doteq\sum_{i=0}^{w-1}x_12^i$$

For example...

  $$B2U_{4}([0101])$$ = 
  
  