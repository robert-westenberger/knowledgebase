---
title: Sequences
description: 
published: true
date: 2021-07-23T18:20:58.973Z
tags: discrete-mathematics
editor: markdown
---

A **sequence** is a function from a subset of the set of integers (usually either the set $\{0,1,2, \ldots\}$ or the set $\{1,2,3, \ldots\})$ to a set $S$. We use the notation $a_{n}$ to denote the image of the integer $n$. We call $a_{n}$ a term of the sequence.

Unlike sets, the elements in a sequence can be **duplicate** and they have a particular **order**. 

Sequences of the form $a_{1}, a_{2}, \ldots, a_{n}$ are often used in computer science. These finite sequences are also called **strings**. This string is also denoted by $a_{1} a_{2} \ldots a_{n} .$  The **length** of a string is the number of terms in this string. The empty string, denoted by $\lambda$, is the string that has no terms. The empty string has length zero.
# Geometric Progression
A **geometric progression** is a sequence of the form
$$
a, a r, a r^{2}, \ldots, a r^{n}, \ldots
$$
where the **initial term** $a$ and the **common ratio** $r$ are real numbers.

It is a discrete analogue of the exponential function $f(x)=ar^x$.


# Arithmetic Progression
An **arithmetic progression** is a sequence of the form
$$
a, a+d, a+2 d, \ldots, a+n d, \ldots
$$
where the **initial term** $a$ and the **common difference** $d$ are real numbers.

It is a discrete analogue of the linear function $f(x)=dx+a$.