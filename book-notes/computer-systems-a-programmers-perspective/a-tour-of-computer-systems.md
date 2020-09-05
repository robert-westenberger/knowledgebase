---
title: Chapter 1: A Tour of Computer Systems
description: 
published: true
date: 2020-09-05T03:18:17.278Z
tags: book-notes
editor: markdown
---

# Chapter 1: A Tour of Computer Systems


### Information is bits + context
All information in a system is represented as a bunch of bits. A source file (hello.c) for a particular program ia a sequence of boolean bits organized in 8-bit chunks called bytes. The bytes of text characters are represented on most systems as ASCII. 

`hello.c`
```
#include <stdio.h>

int main ()
{
  printf("Hello, world\n");
  return 0;
}
```

On a unix system the above source file will go through multiple transformations. 

1. Directives (#include statement) will be inserted into the program text. 

2. This program will be transformed into an assembly-language program. Assembly language is useful because it provides a common output language for different compilers for different high-level languages. For example, C compilers and Fortran compilers both generate output in the same assembly language.

3. The assember will translate the assembly code into machine language instructions, packages it in a form known as a relocatable object program. At this point it is a binary file. 

4. The linker will link called functions that are part of the standard C library. The result is a hello file, which is an executable object file that is ready to be loaded into memory and executed by the system. 


### Hardware organization of a System

Buses transfer fixed-size chunks of bytes known as words (8 bytes, 64 bits on a x86-64 system. I/O devices (mouses, hard disk, display) are connected to the I/O bus through controllers or adapters. Main memory is a temporary storage device that holds both a program and the data it manipulates while the processor is e xecuting the program. The CPU executres / interprets the instructions stored in main memory. 

### Memory is a hierarchy

