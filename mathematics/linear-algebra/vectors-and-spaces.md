---
title: Vectors and Spaces
description: 
published: true
date: 2020-11-20T21:19:38.724Z
tags: mathematics, linear-algebra
editor: markdown
---

# Vectors & Spaces


## Vectors
* A **vector** is something that has both **magnitude** and **direction**. 
* Velocity is a vector for example. It has a speed and a direction. 
* They can be added together and multiplied by numbers to produce another vector of the same kind. Any object that can satisfy these two properties can be considered a vector.
* There are a few different kinds of vectors...
#### Geometric vectors
* Frequently represented as a ray (line segment with definite direction).  

#### Polynomials / functions
* You can add functions, and get other functions. You can multiply functions by a number and get other functions.. so that means they are vectors (satisfies the two properties).
* Polynomials are a **vector subspace** of the space of functions. 

#### $\Reals^n$
* Sets of real numbers of the same size / length can can be added together and multiplied. So vectorspace of $\Reals^n$

## Linear combinations
* Vectors are added with *v+w*. 
The sum, **u + v**, of two vectors, **u** and **v**, is constructed by placing **u**, at some arbitrary location, and then placing **v** such that **v**'s tail point coincides with **u**'s tip point, and **u + v** is the vector that start's at **u**'s tail point, and ends at **v**'s tip point.
* We multiply them by numbers c and d to get *cv* and *dw*.
$$ cv + dw = c\begin{bmatrix}
1 \\
1 
\end{bmatrix} +d
\begin{bmatrix}
2 \\
3 
\end{bmatrix} = 
\begin{bmatrix}
c + 2d \\
c + 3d 
\end{bmatrix}$$

