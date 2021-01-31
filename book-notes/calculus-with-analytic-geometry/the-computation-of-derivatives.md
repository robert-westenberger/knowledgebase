---
title: Chapter 3: The Computation of Derivatives
description: 
published: true
date: 2021-01-31T01:29:44.836Z
tags: mathematics, book-notes, calculus
editor: markdown
---

# The Computation of Derivatives
## 3.1 Derivatives of Polynomials

1) The derivative of a constant is 0.
2) **Power rule** - If n is a positive integer, then 
$$\frac{d}{dx}x^n=nx^{n-1}$$
The derivative of $x^n$ is obtained by bringing the exponent n down in front as a coefficient, then subtracting $1$ from it to form the new exponent $n-1$
3) If $c$ is a constant and $u = f(x)$ is a differentiable function of $x$, then
$$\frac{d}{dx}(cu)=c\frac{du}{dx}$$
The derivative of a constant times a function equals the constant times the derivative of the function.
4) If $u=f(x)$ and $v=g(x)$ are function of x, then
$$\frac{d}{dx}(u+v)=\frac{du}{dx}+\frac{dv}{dx}$$
Combining rules two and three, we see that 
$$\frac{d}{dx}cx^n=cnx^{n-1}$$

4) If $u = f(x)$ and $v=g(x)$ are functions of x, then
$$\frac{d}{dx}(u+v)=\frac{du}{dx}+\frac{dv}{dx}$$

The derivative of the sum of two functions equals the sum of the individual derivatives. 

In essentially the same way, the derivative of a difference equals the difference of the derivatives

$$\frac{d}{dx}(u-v)=\frac{du}{dx}-\frac{dv}{dx}$$
These results can be extended without difficulty to any finite number of terms.
$$\frac{d}{dx}(u-v+w)=\frac{du}{dx}-\frac{dv}{dx}+\frac{dw}{dx}$$

### Examples
Derive $y=(3x-2)^4$
1) It is a polynomial but not in standard polynomial form. Later on in the book we'll have a formula that can be used here. **So we have to expand by the binomial theorem / binomial expansion theorem.**
2) The expanded polynomial is $81x^4-216x^3+216x^2-96x+16$
3) Using above rules, we can calculate
$\frac{dy}{dx}=324x^3-648x^2+432x-96$

---
An object moves on a straight line in such a way that it's position $s$ at time $t$ is given by 
$$s = t^3 +5t^2-8t$$


## 3.2
## 3.3 Skip me
## 3.4