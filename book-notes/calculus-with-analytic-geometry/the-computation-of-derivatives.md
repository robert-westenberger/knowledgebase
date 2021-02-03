---
title: Chapter 3: The Computation of Derivatives
description: 
published: true
date: 2021-02-03T19:42:52.662Z
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

The velocity $v$ is $v\frac{ds}{dt}$ and acceleration a is $a=\frac{dv}{dt}$.
In this example $v=3t^2+10t-8$ and $a=6t+10$

---

## 3.2 The Product and Quotient Rules

#### Product rule
$$\frac{d}{dx}(uv)=u\frac{dv}{dx}+v\frac{du}{dx}$$
The derivative of the product of two functions is the first times the derivative of the second plus the second times the derivative of the first. 
#### Quotient rule
$$\frac{d}{dx}(\frac{u}{v})=\frac{v \medspace du/dx -u \medspace dv/dx}{v^2}$$
at all values of $x$ where $v \neq 0$.

The derivative of a quotient is the denominator times the derivative of the numerator minus the numerator times the derivative of the denominator, all divided by the denominator squared.

The quotient rule can be used to extend the power rule to work for negative exponents (since a negative exponent can be rewritten as as a fraction). For example: 
$$x^{-4}=\frac{1}{x^4}$$ 
#### Examples
Derive $\frac{1}{x-1}-\frac{1}{x+1}$.
1) We don't "know" about the chain rule yet.. so we simplify the fraction to $\frac{2}{x^2-1}$ and use the quotient rule to calculate.
## 3.3 Composite Functions and the Chain Rule 
#### Chain Rule
A function like 
$$y=(x^3+2)^5$$
can be decomposed into smaller auxillary functions 
$$y=u^5$$
and 
$$u=x^3+2$$
$y$ can now be described as a function of $u$, and $u$ can be described as a function of $x$.
So we have $y=f(u)$ and $u=g(x)$. Building these pieces back together we have the composite function 
$$y=f(g(x))$$

The derivative of the composed function can be calculated above as
$$\frac{dy}{dx}=\frac{dy}{du}\cdot\frac{du}{dx}$$
#### Power Rule
$$\frac{d}{dx}u^n=nu^{n-1}\frac{du}{dx}$$
## 3.4 Some Trigonometric Derivatives
