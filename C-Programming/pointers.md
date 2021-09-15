---
title: Pointers in C
description: 
published: true
date: 2021-09-15T18:49:58.452Z
tags: pointers, c
editor: markdown
---

Data is stored in computer memory. The CPU reads and writes from this memory. Computer memory, in simple terms, is an array of cells, where each cell has its own number called an address. 

A typical machine has an array of consecutively numbered or addressed memory ells that may be manipulated individually or in contiguous groups. One common situation is any byte can be a *char*, a pair of one-byte cells can be treated as a *short* integer, four adjacent bytes form a *long*. (Note: Is this still up to date with 64 bit architecture..?)

A **pointer** is a group of cells (often two or four) that can hold an address. So if `c` is a *char* and `p` is a pointer that points to it, it could be represented as![pointer.png](/pointer.png)

> Pointers are constrained to point to a particular kind of object / data type. (There is one exception: a “pointer to void” is used to hold any type of pointer but cannot be dereferenced itself.)
{.is-info}

# Operators
## & Address Of Operator
The unary operator `&` gives an address of an object, so the statement

`p=&c;` 

assigns the address of `c` to the variable `p`, and `p` is said to "point to" `c`.

## * Indirection / Dereferencing Operator
The unary operator `*` is the **indirection** or **dereferencing** operator. When applied to a pointer, it accesses the object the pointer points to. 



### Example showing how a pointer is declared and how the unary operators are used
Suppose that `x` and `y` are integers and `ip` is a pointer to `int`.
```
int x=1, y=2, z[10];
int *ip; /* ip is a pointer to an int */

ip = &x; /* ip now points to x */
y = *ip; /* y is now 1 */
*ip = 0; /* x is now 0 */
ip = &z[0]; /* ip now points to z[0] */
```

### Example showing using pointer to access and change the value of an object
```
#include <stdio.h>
int main(void)
{
      int x = 123;
      printf("The value before the change: %d\n", x);
      int* p = &x;
      *p = 456;
      printf("The value after the change: %d\n", x);
}
```
The above will output:
```
The value before the change: 123
The value after the change: 456
```
# Pointers and Function Arguments
Since arguments are passed to functions by value in C, there is no direct way for the called function to alter a variable in the calling function. So we need to pass pointers to the values to be changed.

Pointer arguments enable a function to access and change objects in the function that called it.
## Example - Incorrect Function
```
void swap(int x, int y)  /* WRONG */
{
    int temp;

    temp = x;
    x = y;
    y = temp;
}
swap(a, b);
```
The above function only swaps copies of `a` and `b`.

## Example - Correct Function
```
void swap(int *px, int *py)  /* interchange *px and *py */
{
    int temp;

    temp = *px;
    *px = *py;
    *py = temp;
}
swap(&a, &b);
```
Above, the parameters are declared to be pointers, and the operands are accessed indirectly through them. 

# Pointer to Pointer 
Also known as **double indirection**

# Other notes
* Doesn't matter whether the `*` operator is placed next to the type name or next to the variable name. `some_type* p;` is the same as `some_type *p;`.

* The `*` means different things in different contexts. When in a declaration such as `some_type *p;`, it denotes a pointer type. When used in front of the variable name, as in `*p`, or `*p = some_value;`, the star symbol denotes a dereferencing operator.