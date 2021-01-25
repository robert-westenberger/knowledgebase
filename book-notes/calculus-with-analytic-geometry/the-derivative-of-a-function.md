---
title: Chapter 2: The Derivative of a Function
description: 
published: true
date: 2021-01-25T19:19:01.043Z
tags: mathematics, book-notes
editor: markdown
---

# Chapter 2: The Derivative of a Function

## 2.1 What is calculus? The problem of tangents
Calculus is divided into two main parts.

* **Integral** calculus joins the small pieces together and tells us how much of something is made, overall, by a series of changes.

* **Differential** calculus divides thing into different small pieces and tells us how they change from one moment to the next.

![tangent_to_a_curve.png](/tangent_to_a_curve.png)
Above, the graph of a function (black), and a tangent line to that function (red). The slope of the tangent line is equal to the derivative of the function at the marked point.

The **derivative** of a function of a real variable measures the sensitivity to change of the function value (output value) with respect to a change in its argument (input value).

## 2.2 How to calculate the slope of the tangent

![parabola1.png](/parabola1.png)
Above, we want to calculate the slope of the tangent to this parabola $y=x^2$ at the given point P.

1) Choose a second nearby point Q = (x1, y1) on the curve.
2) Draw the secant line PQ. The slope of the secant is 

$$m_{sec}= slope \hspace{1mm} of \hspace{1mm} PQ = \frac{y1-y0}{x1-x0}$$

3) We let x1 approach x0, so that the variable point Q approaches the fixed point P by sliding along the curve. As this happens, the secant changes direction and visibly approaches the tangent at P as its limiting position. The slope *m* of the tangent is the limiting value approached by the slope $m_{sec}$ of the secant.

$$ m=\underset{Q\rarr P}{lim} \hspace{1mm} m_{sec}=\underset{x_1\rarr x_2}{lim}\frac{y_1 - y_0}{x_1 - x_0}$$   

4) We use the equation of the curve to calculate the slope of the secant. Since P and Q both lie on the curve, we have $y_0={x_0}^2$ $y_1={x_1}^2$ so

$$ m_{sec}=\frac{y_1 - y_0}{x_1 - x_0}=\frac{{x_1}^2 - {x_0}^2}{x_1-x_0}$$   

If we factor the binomials and cancel the common factors we obtain

$$m=\underset{x_1\rarr x_0}{lim}\frac{y_1 - y_0}{x_1 - x_0}=\underset{x_1\rarr x_0}{lim}(x_1 + x_0)$$

We can now see that as $x_1$ gets closer to $x_0$, $x^1$ + $x^0$ becomes more and more nearly equal to $x_0 + x_0 = {2_x}_0$ . Accordingly, 
$$ m= {2_x}_0 $$ 
is the slope of the tangent to the curve $y=x^2$ at the point $(x_0, y_0)$

### Delta notation
Delta notation is the notation of change (the delta of a value).
$$ \Delta x=x_1-x_0$$
Alternatively, 
$$x_1 = x_0 + \Delta x$$

Delta can be used to simplify the formula for calculating the slope of a secant and ultimately the slope of the tangent.

$$m_{sec}=2x_0+\Delta x$$
$$m=\underset{\Delta x \rarr 0}{lim}({2}x_0 + \Delta x)={2}x_0$$

As $\Delta x$ gets closer to 0, ${2}x_0+\Delta x$ becomes more and more nearly equal to ${2}x_0$

The following generalized formulas can be used to calculate the slope of the secant through any two points P and Q corresponding to $x_0$ and $x_0 + \Delta x$. 


$$ m_{sec} = \frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x}$$ 

We then calculate the limit of $m_{sec}$ as $\Delta x$ approaches 0, obtaining a number m that we interpret geometrically as the slope of the tangent to the curve at the point P.

$$m=\underset{\Delta x \rarr 0}{lim}\frac{f(x_0 +\Delta x) - f(x_0)}{\Delta x}$$

Value of this limit is ually denoted by the symbol $f'(x_0)$ read "$f$ prime of $x_0$ in order to emphasize its dependence on both the point $x_0$ and the function $f(x)$ .
Thus we have 

$$f'(x_0)=\underset{\Delta x \rarr 0}{lim}\frac{f(x_0 +\Delta x) - f(x_0)}{\Delta x}$$ 

If $f(x)=x^2$, then $f'(x_0) = {2}x_0$ 


### Calculating tangent line to a function at a point
for example.. calculating 
$f(x)=15-2x^2$ at $x=1$
1) Calculate the derivative of f(x). One possible way is using the limit definition of a derivative given above. The derivative of the above is $-4x$.

2) Calculate the slope of the tangent line by substituting x, which is 1, into the derivative of f(x). The slope is -4.
3) Calculate the y value of the point of tangency by popping the value of x in the original given function.
4) Calculate the equation of the tangent line by putting our values into slope intercept form.

## 2.3 The Definition of the Derivative

#### Finding points on a curve at which tangent is horizontal
1) Calculate the derivative of the function. 
2) Calculate the x coordinates of the points where the tangent is horizontal by setting the derivative equal to 0 and solving for x.
3) Calculate the y coordinates by plugging in the x coordinates of the points using the equation of the curve.

## 2.4 Velocity and Rates of Change

This section introduces two important topics in calculus: velocity ( rate of change of the position of a moving object), and rates of change in general, including acceleration, which is the rate of change of... a rate of change ( the rate of change of velocity).

Using functions we can simulate rate of change, velocity. We can simulate problems about objects falling or being launched vertically, and when they reach their maximum height (when their velocity is 0 before the object makes its descent). From this we can calculate the height an object reaches.

## 2.5 The Concept of a Limit. Two Trigonometric Limits