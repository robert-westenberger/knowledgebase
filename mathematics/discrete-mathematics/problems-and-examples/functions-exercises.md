---
title: Functions Exercises
description: 
published: true
date: 2021-04-12T18:48:42.264Z
tags: discrete-mathematics
editor: markdown
---

# Rosen Discrete Mathematics 7th Edition Section 2.3

## Tell why a function is partial
Remember that a function $f$ from $A$ to $B$ has the property that each element of $A$ has been assigned to exactly one element of $B$.
### 1 
Why is $f$ not a function from $\mathbf{R}$ to $\mathbf{R}$ if 
**a)** $f(x)=1 / x$
**b)** $f(x)=\sqrt{x}$
**c)** $f(x)=\pm \sqrt{\left(x^{2}+1\right)}$

#### Solution
**a)** $f(0)$ is not defined for any value.
**b)** Negative square roots are undefined, or complex numbers (not real numbers).
**c)** There are multiple values in the domain that map to single values of the codomain. 

## Find domain and range of functions
the domain is the set of possible inputs for which the function is defined, and the range is the
set of all possible outputs on these inputs.
### 7 
Find the domain and range of these functions.
**a)** the function that assigns to each pair of positive integers
the maximum of these two integers
**b)** the function that assigns to each positive integer the
number of the digits $0, 1, 2, 3, 4, 5, 6, 7, 8, 9$ that do
not appear as decimal digits of the integer
**c)** the function that assigns to a bit string the number of
times the block $11$ appears
**d)** the function that assigns to a bit string the numerical
position of the first $1$ in the string and that assigns the
value $0$ to a bit string consisting of all $0$s
#### Solution
**a)** The domain is the set of ordered pairs ($\Z^+$, $\Z^+$) and the range is $\Z^+$.
**b)** The domain is $\Z^+$. The base 10 representation of an integer has to have at least one digit, and at most nine digits do not appear, so the number of missing digits could be any number less than 9. Thus the range is $\{0,1,2,3,4,5,6,7,8,9\}$. 
**c)** The domain is the set of bit strings and the range is $\N$ (set of natural numbers)
**d)** The domain is the set of bit strings and the range is $\N$ (if the string contains no $1$s then the value is $0$ by definition, or its position could be $1,2,3, \ldots$.

## Determine whether a function is onto
A function is onto when its range is the entire codomain. 
### 15 
Determine whether the function $f: \mathbf{Z} \times \mathbf{Z} \rightarrow \mathbf{Z}$ is onto if 
**a)** $f(m, n)=m+n$
**b)** $f(m, n)=m^{2}+n^{2}$
**c)** $f(m, n)=m$
**d)** $f(m, n)=|n|$
**e)** $f(m, n)=m-n$

#### Solution
**a)** Given any integer $n$, $f(0, n) = n$ so this is onto.
**b)** No, the range contains no negative integers.
**c)** Yes this is onto (similar to reasoning for a)
**d)** No, similar to reasoning for b(no neg ints)
**e)** Yes, $f(m, 0)$ maps all integers

## Determine whether a function is bijective
(remember a function is bijective when each value of the domain is mapped to the codomain exactly once)

One way to determine whether a function is a bijection is to try to construct its inverse.
### 23 
Determine whether each of these functions ia bijection from $\R$ to $\R$
**a)** $f(x)=2 x+1$
**b)** $f(x)=x^{2}+1$
**c)** $f(x)=x^{3}$
**d)** $f(x)=\left(x^{2}+1\right) /\left(x^{2}+2\right)$

#### Solution
**a)** yes
**b)** no ( not injective, the codomain has no negative $\R$
**c)** this is a bijection since it has an inverse function.
**d)**