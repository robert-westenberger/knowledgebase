---
title: Chapter 2: Representing and Manipulating Information
description: 
published: true
date: 2020-09-06T03:19:17.907Z
tags: book-notes
editor: markdown
---

# Chapter 2: Representing and Manipulating Information
* Bit patterns are written in hexadecimal (base-16) notation. 
* Every computer has a word size, indicating the nominal size of pointer data. Most computers now have a 64 bit word size. A 64 bit machine has a massive virtual address space compared to 32 bit machines. 
* The amount of bytes allocated for different data types in C is dependent on how it is compiled (32 bit vs 64 bit). 
* There are two common conventions to order contiguous bytes in memory for program objects that span multiple bytes: little endianness and big endianness. The convention where the least significant bit comes first, is  little endianness. The convention where the most significant bit comes first, is big endianness. This only really comes up when binary data is communicated over a network between different machines. Just important to remember, in networking applications, to convert internal byte representations to whatever the network stand ard is. 