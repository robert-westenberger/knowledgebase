---
title: Integer Representations
description: 
published: true
date: 2020-09-30T03:12:21.509Z
tags: computer-science, computer
editor: markdown
---

# Integer Representations

#### Integral Data Types
* C integral data types ( char, short, int, long, signed and unsigned) have different minimum and maximum allocatable bytes (dependent on whether its compiled on 32 or 64 bit machines). 

##### Unsigned Encodings

* An integer can be encoded as a bit vector. The below equation (binary to unsigned) maps strings of zeros and ones of length *w* to nonnegative integers..
  $$ B2U_{w}(\overrightarrow{x})\doteq\sum_{i=0}^{w-1}x_12^i $$

For example...

  $B2U_{4}([0101])$ = 0 * 2^3^ + 1 * 2^2^ + 0 * 2^1^ + 1 * 2^0^ =  5
  
* The smallest possible value of *w* bits would be all 0s and the greatest would be all 1s. (denoted as $UMax_w$). Using a 4-bit representation as an example

  $$ UMax_4=B2U_{4}([1111])=2^4-1=15 $$
  
##### Two's-Complement Encodings
* The most common representation of signed numbers. It is defined as interpreting the most significant bit of a particular word to have negative weight. 
* The definition of two's-complement encoding for a particular bit vector 

$$ B2T_w(\overrightarrow{x})\doteq-x_{w-1}2^{w-1}+\sum_{i=0}^{w-2}x_i2^i $$

* The most significant bit $x_{w-1}$ is the *sign bit*. When the sign bit is 1, the represented value is negative, and when it is 0 the represented value is positive. 
* Examples (also using a 4 bit representation)
$B2T_{4}([0101])$ = -0 * 2^3^ + 1 * 2^2^ + 0 * 2^1^ + 1 * 2^0^ =  5
$B2T_{4}([1111])$ = -1 * 2^3^ + 1 * 2^2^ + 1 * 2^1^ + 1 * 2^0^ =  -1
* The range of a 4 bit representation would be -8 to 7.