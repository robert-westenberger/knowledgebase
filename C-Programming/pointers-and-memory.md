---
title: Pointers and Memory
description: 
published: true
date: 2021-10-18T01:44:56.990Z
tags: pointers, c-lang
editor: markdown
---

(Notes from [pointersandmemory.pdf](/pointersandmemory.pdf) )

Pointers allow different sections of code to share information easily. Also, they allow for "linked" data structures like linked lists and binary trees.

![ptr_diagram.png](/ptr_diagram.png)

Above, `int num` is 42 and `int* numPtr` is a pointer to num. Dereferencing `numPtr` will return the int 42. 

A NULL pointer is a pointer that points to nothing. 

# Bad Pointers
When a pointer is first allocated, it doesn't point to anything. The pointer is uninitialized or "bad". Dereferencing a pointer can cause undefined behavior and corrupt a random area of memory, leading to bugs.

# Two Levels
One useful way to think about pointer code is that it works on two levels, the pointer level and the pointee level. **Both** levels need to be initialized and connected for things to work. So
1) The pointer must be allocated
2) The pointee must be allocated
3) The pointer must be assigned to the pointee

# Local Memory
```
// Local storage example
int Square(int num) {
	int result;
	result = num * num;
	return result;
}
```
Above, `num` and `result` are both local variables. Their lifetime (the span between when they are allocated and deallocated) lasts from when their containing function is entered, to when the function is exited. 
## Allocation and Deallocation
A variable is allocated when it is given an area of memory to store its value. A variable is deallocated when the system reclaims the memory from the variable, so it no longer has an area to store its value. The most common memory related error is using a deallocated variable.

## Small Local Memory Example
```
void Foo(int a) { // (1) Locals (a, b, i, scores) allocated when Foo runs
	int i;
	float scores[100]; // This array of 100 floats is allocated locally.
	a = a + 1; // (2) Local storage is used by the computation
	for (i=0; i<a; i++) {
		Bar(i + a); // (3) Locals continue to exist undisturbed,
	} // even during calls to other functions.
} // (4) The locals are all deallocated when the function exits.
```

## The & Bug (Returning a pointer to a local variable)
```
int* TAB() {
	int temp;
	return(&temp); // return a pointer to the local int
}
void Victim() {
	int* ptr;
	ptr = TAB();
	*ptr = 42; // Runtime error! The pointee was local to TAB
}
```

In the above, the `ptr` variable gets a reference to a local variable from `TAB()`. Since that local variable is just going to be deallocated, if that pointer is dereferenced it will result in undefined behavior because its not pointing to anything. 

# Reference Parameters
1. Have a single copy of the value of interest, the "master" copy.
2. Pass pointers to that value to any function which wants to see or change the value.
3. Functions can deference their pointer to see or change the vlaue of interest. 
4. Functions must remember that they do not have their own local copies. If they dereference their pointer and change the value, they really are changing the master value. If a function wants a local copy to change safely, the function must explicitly allocate and initialize such a local copy.


## ** variables
If the variable of interest to be passed around multiple functions is a pointer, then we would need a pointer to that pointer. 

# Heap Memory
Also known as "dynamic" memory. The programmer explicitly requests the allocation of a memory "block" of a particular size, and the block continues to be allocated until the programmer explicitly requests that it be deallocated.