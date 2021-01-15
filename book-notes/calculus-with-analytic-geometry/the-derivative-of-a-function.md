---
title: Chapter 2: The Derivative of a Function
description: 
published: true
date: 2021-01-15T18:59:26.870Z
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

The following generalized formulas can be used to calculate the slope of the secant through any two points P and Q corresponding to $x_0$ and $x_0 + \Delta x$