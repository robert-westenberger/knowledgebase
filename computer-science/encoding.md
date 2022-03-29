---
title: Encoding
description: 
published: true
date: 2022-03-29T16:13:52.625Z
tags: computer-science
editor: markdown
---

# What is encoding?
It's a technique in which the data is transformed from one format into another, so that it can be understood and consumed by different systems. 

# Why is encoding necessary?
One particularly important form of encoding  is binary-to-text encoding. It enables the encoding of binary data to plain text. 

One form of binary-to-text encoding is Base64 encoding. It's designed to carry data stored in binary formatas across channels that only reliably support text content. 

## Base64 encoding example
Here is an example of encoding the ASCII text "abc" into Base64.
### Step 1: Convert to decimal
In decimal, `a=97`, `b=98`, `c=99`. 

### Step 2: Convert decimal to 8-bit binary form
`a=0110 0001`, `b=0110 0010`, `c=0110 0011`.

`abc=0110 0001 0110 0010 0110 0011`.

### Step 3: Separate into groups of 6-bit each:

`011000 — 010110 — 001001 — 100011`

### Step 4: 