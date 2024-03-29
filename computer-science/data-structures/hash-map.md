---
title: Hash Map
description: 
published: true
date: 2021-10-20T18:48:13.572Z
tags: data-structures
editor: markdown
---

A hash map is an associative array / dictionary composed of a collection of key value pairs, such that each possible key appears at most once in the collection. 

A hash table uses a **hash function** to compute an index (also code a **hash code**), into an array of **buckets** or **slots**, from which the desired value can be found. 

Internally, hash tables use an array as storage and uses a hash function to generate an index where an element is to be inserted or located from. 

# Hash Functions
A hash function takes data of an arbitrary size and converts it to a fixed size. 

It is a function $H: X \rightarrow \lbrack0, M)$ that takes an element $x \in X$ and associates to it a positive integer $H(x)=m$, where $m \in\lbrack0, M)$.

$X$ can be bounded or an unbounded set of values, while $M$ is always $0<M<\infty$.

Hash functions should always be deterministic, and not computationally expensive.
## Hash Collisions
When two pieces of data are hashed to the same value, this is called a hash collision.

## Division Hashing
The simplest hash function, it just uses the modulo opeartor to return a hash value. 

$H_{\text {division }}(x)=x \quad \bmod M$ , where $H_{\text {division }}: X \rightarrow\lbrack0, M)$

## Multiplicative Hashing

```
//multiplicative_hash.c
#define hash_a (uint32_t) 2654435769
#define hash_w 32
#define hash_m 3

uint32_t hashf_multip(uint32_t x, uint32_t m) {
    return (x * hash_a) >> (hash_w - m);
}
```

Above, a good choice for $A$ is $A=\phi * 2^{w}$, where $w$ is the machine word size and $\phi$ is the golden ratio. When $A=\phi * 2^{w}$, the general multiplicative hash is called a fibonacci hash function. 

## Hashing Strings
```
//hash.c
#define INIT <some_value>
#define MULTIP <some_value>

uint32_t hashf_generic(char* str) {
    uint32_t hash = INIT;
    char c;
    while((c*=str++)) {
        hash = MULTIP * hash + c;
    }
    return hash;
}
```

# Implementing Hash Tables
Data is stored in an array, where each key-value pair has its own unique index(or **bucket**). 

The bucket hash $_{\text {function }}($ key $) \rightarrow$ bucket $\lbrack<$ key, value $\left.>)\right]$


## Handling Hash Collisions
Depending on how we plan to handle hash collisions, there are two ways to implement a hash table
### Method 1 - Separate Chaining
* Each bucket references a linked list (or dynamic array) that contains none, one, or more kv entries.
* To add a new entry, we compute the bucket with our hash function, and we append the key value pair to the corresponding bucket's linked list. If the key already exists, we just update the value. 
* To get an entry, we compute the bucket with the hash function and then traverse the corresponding linked list until we find the key.
* Instead of linked lists or dynamic arrays, we can use red-black trees if the number of elements contained exceeds a certain threshhold. 
### Method 2 - Open Addressing
* No linked lists. There is just one kv per bucket.
* If there is a collision, we probe the array to find another suitable bucket for our entry, and we add the entry to the newly found empty location.
* Various algos for probing. The simplest one is linear probing - jumping to the next available bucket.
* Deleting an existing entry is a complex operation. 

