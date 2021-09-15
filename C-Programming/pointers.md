---
title: Pointers in C
description: 
published: true
date: 2021-09-15T18:24:45.596Z
tags: pointers, c
editor: markdown
---

Data is stored in computer memory. The CPU reads and writes from this memory. Computer memory, in simple terms, is an array of cells, where each cell has its own number called an address. 

A typical machine has an array of consecutively numbered or addressed memory ells that may be manipulated individually or in contiguous groups. One common situation is any byte can be a *char*, a pair of one-byte cells can be treated as a *short* integer, four adjacent bytes form a *long*. (Note: Is this still up to date with 64 bit architecture..?)

A **pointer** is a group of cells (often two or four) that can hold an address. So if `c` is a *char* and `p` is a pointer that points to it, it could be represented as![pointer.png](/pointer.png)

The unary operator `&` gives an address of an object, so the statement

`p=&c;` 

assigns the address of `c` to the variable `p`, and `p` is said to "point to" `c`.

The unary operator `*` is the **indirection** or **dereferencing** operator. When applied to a pointer, it accesses the object the pointer points to. 

> Pointers are constrained to point to a particular kind of object / data type.
{.is-info}

## Example showing how a pointer is declared and how the unary operators are used
Suppose that `x` and `y` are integers and `ip` is a pointer to `int`.
```
int x=1, y=2, z[10];
int *ip; /* ip is a pointer to an int */

ip = &x; /* ip now points to x */
y = *ip; /* y is now 1 */
*ip = 0; /* x is now 0 */
ip = &z[0]; /* ip now points to z[0] */
```


# Pointer to Pointer 
Also known as **double indirection**