---
title: Chapter 1: A Tour of Computer Systems
description: 
published: true
date: 2020-09-05T05:43:49.747Z
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

At the top of the hierarchy are smaller, faster, and costlier per byte storage devices. At the bottom are larger, slower, and cheaper. From top to bottom
1. CPU registers that hold individual words retrieved from cache memory
2. A series of L1 -> LN memory caches
3. Main memory
4. Local secondary storage (SSD/ HDD)
5. Remote secondary storage (distributed file systems, networks, web servers)

### The operating system manages the hardware
* The operating system can be thought of as a layer of software interposed between the application program and the hardware. The OS has two primary purposes: 
1. To protect the hardware form misuse by runaway applications
2. To provide applications with simple and uniform mechanisms for manipulating complicated and often wildly different low-level hardware devices. 

The operating system has some abstractions of its own. 
* A process is the operating system's abstraction for a running program. A single core CPU can appear to run multiple processes concurrently by interleaving processes with a mechanism known as context switching. 
* A process can consist of multiple execution units called threads, each running in the context of the process and sharing the same code and global data. 
* Virtual memory is an abstraction that provides each process with the illusion that it has exclusive use of the main memory. 
* A file is a sequence of bytes. It is an abstraction to represent many i/o device, abstracting away specific i/o technology. 

### Important themes
* Amdahl's law - The main idea is that when we speed up one part of a system, the effect on the overall system performance depends on both how significant the part was and how much it was sped up. 
* Concurrency - the general concept of a system with multiple, simultaneous activities
* Parallelism - the use of concurrency to make a system run faster. 