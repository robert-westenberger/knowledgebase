---
title: Pointers and Memory
description: 
published: true
date: 2021-10-18T01:07:22.081Z
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

In the above, the `ptr` variable gets a reference to a local variable from `TAB()`. Since that local variable is just going to be deallocated, if that pointer is dereferenced it will 