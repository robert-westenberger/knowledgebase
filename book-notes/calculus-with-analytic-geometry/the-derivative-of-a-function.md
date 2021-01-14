---
title: Chapter 2: The Derivative of a Function
description: 
published: true
date: 2021-01-14T17:15:25.527Z
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
Above, we want to calculate the slope of the tangent to this parabola at the given point P.

1) Choose a second nearby point Q = (x1, y1) on the curve.
2) Draw the secant line PQ. The slope of the secant is 

$$m_{sec}= slope \hspace{1mm} of \hspace{1mm} PQ = \frac{y1-y0}{x1-x0}$$

3) We let x1 approach x0, so that the variable point Q approaches the fixed point P by sliding along the curve. As this happens, the secant changes direction and visibly approaches the tangent at P as its limiting position. The slope *m* of the tangent is the limiting value approached by the slope $m_{sec}$ of the secant.