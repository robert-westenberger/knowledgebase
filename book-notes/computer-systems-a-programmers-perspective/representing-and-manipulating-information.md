---
title: Chapter 2: Representing and Manipulating Information
description: 
published: true
date: 2020-09-16T03:45:49.706Z
tags: book-notes
editor: markdown
---

# Chapter 2: Representing and Manipulating Information
* Bit patterns are written in hexadecimal (base-16) notation. 
* Every computer has a word size, indicating the nominal size of pointer data. Most computers now have a 64 bit word size. A 64 bit machine has a massive virtual address space compared to 32 bit machines. 
* The amount of bytes allocated for different data types in C is dependent on how it is compiled (32 bit vs 64 bit). 
* There are two common conventions to order contiguous bytes in memory for program objects that span multiple bytes: little endianness and big endianness. The convention where the least significant bit comes first, is  little endianness. The convention where the most significant bit comes first, is big endianness. 
    * This only really comes up when binary data is communicated over a network between different machines. Just important to remember, in networking applications, to convert internal byte representations to whatever the network stand ard is. 
    * It comes up again when inspecting machine-level programs. The natural way to write a byte sequence (in a lower-endian representation) is to have the lowest-numbered byte on the left and the highest on the right, but this is contrary to the normal way of writing numbers with the most significant digit on the left and the least on the right. 
    * When programs are written to circumvent the normal type system and allowing an object to be referenced according to a different data type than from which it was created.  This is sometimes necessary for systems level programming.
    
    
C Program representing byte representations of different data values. 

```
#include <stdio.h>

typedef unsigned char *byte_pointer;

void show_bytes(byte_pointer start, size_t len) {
    int i;
    for (i = 0; i < len; i++)
        printf(" %.2x", start[i]);
    printf("\n");
}

void show_int(int x) {
    show_bytes((byte_pointer) &x, sizeof(int));
}

void show_float(float x) {
    show_bytes((byte_pointer) &x, sizeof(float));
}

void show_pointer(void *x) {
    show_bytes((byte_pointer) &x, sizeof(void *));
}

void test_show_bytes(int val) {
    int ival = val;
    float fval = (float) ival;
    int *pval = &ival;
    show_int(ival);
    show_float(fval);
    show_pointer(pval);
}
int main() {
    test_show_bytes(12345);
    return 0;
}
```

Program output... (64 bit linux) . its little endian. Note the 8-byte / 64 bit memory address. 
```
 39 30 00 00
 00 e4 40 46
 f8 a4 03 ed fe 7f 00 00
 ```
 
 
 