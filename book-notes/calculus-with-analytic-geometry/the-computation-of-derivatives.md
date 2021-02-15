---
title: Chapter 3: The Computation of Derivatives
description: 
published: true
date: 2021-02-15T22:26:43.859Z
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

In other words, the derivative of a composite function is ..
$$F'(x)=\underbrace{f'}_{\text{derivative of outside function}}\enspace\underbrace{g(x))}_{\text{inside function left alone}}\enspace \underbrace{g'(x))}_{\text{multiplied by derivative of inside function}}$$
#### Power Rule
$$\frac{d}{dx}u^n=nu^{n-1}\frac{du}{dx}$$

##### Examples
Derive 
$$y=\frac{1}{(2-5x)^2}$$ 

This is a composite function so we can use the chain rule. We break out the inner function into a new function 
$$u=2-5x$$
$$u'=-5$$
The original function can now be represented as 
$$y= \frac{1}{u^2} $$
$$y'=-\frac{2}{u^3}$$



Using the chain rule $\frac{d}{dx}y=\frac{dy(u)}{du}\frac{du}{dx}$ ("the derivative of y with respect to x is the derivative of y with respect to u multiplied by the derivative of u with respect to x.

Pop the inner function u into the derivative of the outer function and multiply the whole thing by the derivative of the outside function..
$$y'=-\frac{2}{(2-5x)^3} * 5$$
$$y'=-\frac{10}{(2-5x)^3}$$


---
Derive $y=(5x + 3)^4(4x-3)^7$ with respect to x. 

Using the product rule we get
$$y'(x) = (5x + 3)^4\Big(\frac{d}{dx}((4x - 3)^7)\Big)+(4x-3)^7\Big(\frac{d}{dx}((5x+3)^4)\Big)$$

Use the chain rule to find the derivatives of $\Big(\frac{d}{dx}((4x - 3)^7)\Big)$ and $\Big(\frac{d}{dx}((5x+3)^4)\Big)$...

$7(4x-3)^6 * 4$ or $28(4x-3)^6$ and $4(5x+3)^3 * 5$ or $20(5x+3)^3$

Putting everything into place...
$$y'(x)=(5x+3)^428(4x-3)^6+20(5x+3)^3(4x-3)^7$$ 

(the same above but reordered)
$$y'(x)=20(4x-3)^7(5x+3)^3+28(4x-3)^6(5x+3)^4$$ 

## 3.4 Some Trigonometric Derivatives

$$\frac{d}{dx}sinx=cosx$$
$$\frac{d}{dx}cosx=-sinx$$
$$\frac{d}{dx}tanx=sec^2x$$

Above can be combined with the chain rule. For example, if $u$ is a function..

$$\frac{d}{dx}sin \thinspace u=cos \thinspace u\frac{du}{dx}$$

$$\frac{d}{dx}cos \thinspace u=-sin \thinspace u\frac{du}{dx}$$

### Examples
Derive $y=(1 + tan^2x^2)^2$


## 3.5 Implicit Functions and Fractional Exponents
All functions previously have been explicit functions. The y value is expressed directly in terms of x, for example $y=x^2$ or $y=sin^2(x)$

Below are implicit functions of x.
$$F(x, y) = 0$$
$$x^2 + y^2 = r^2$$
$$\frac{x}{y^3}=1$$
$$2x^2-2xy=5-y^2$$

The relationship between x and y in these examples are entangled with one another.

// todo- show example deriv of  $xy = 1$

We can use implicit differentiation to show that the power rule 
$$\frac{d}{dx}x^n=nx^{n-1}$$
is valid for all fractional exponents $n=p/q$.

We introduce $y$ as a dependent variable 
$$y=x^{p/q}$$
Raising both sides to the $qth$ power yields
$$y^q=x^p$$

By differentiating implicity with respect to x and using the known validity of the power rule for integral exponents, we obtain
$$qy^{q-1}\frac{dy}{dx}=px^{p-1}$$
or 
$$\frac{dy}{dx}=\frac{p}{q}\frac{x^{p-1}}{y^{q-1}}$$

$y^{q-1}=y^q/y=x^P/x^{p/q}$ so
$$\frac{dy}{dx}=\frac{p}{q}\frac{x^{p-1}}{y^{q-1}}=\frac{p}{q}\frac{x^{p-1}}{x^p}\cdot x^{p/q}=\frac{p}{q}x^{p/q-1}$$

### Examples
Derive $\lparen\frac{x^3+8}{x^2}\rparen^{3/4}$. 

1) Use the chain rule to decompose the composite function. 
$$u=\frac{x^3+8}{x^2}$$
$$u'=\frac{x^4-16x}{x^4}=1-\frac{16}{x^3}$$


$$u^{3/4}$$


$$\frac{d}{du}\lparen u^{3/4}\rparen =\frac{3}{4}u^{-1/4}=\frac{3}{4\sqrt[4]u}$$



$$\frac{d}{dx}=\frac{3}{4\sqrt[4]{\frac{8+x^3}{x^2}}} \cdot \lparen 1-\frac{16}{x^3} \rparen$$

The above is equivalent to 

$$\frac{d}{dx}=\frac{3}{4\sqrt[4]{\frac{8+x^3}{x^2}}} \cdot \lparen \frac{x^3 - 16}{x^3} \rparen$$ 

when multiplied..
$$
\frac{3(x^3 - 16)}{4x^3\sqrt[4]{\frac{8}{x^2}+x}}
$$

## Derivatives of Higher Order

A derivative of a derivative is the second derivative. A derivative of that derivative is the third, and of that the nth..

$$
\text{First derivative} \quad f'(x) \quad y' \quad \frac{dy}{dx} \quad \frac{d}{dx}f(x) 

\text{First derivative} \quad f'(x) \quad y' \quad \frac{dy}{dx} \quad \frac{d}{dx}f(x)
$$