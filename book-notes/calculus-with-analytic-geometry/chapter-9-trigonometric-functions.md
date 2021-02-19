---
title: Chapter 9: Trigonometric Functions
description: 
published: true
date: 2021-02-19T03:13:58.988Z
tags: mathematics, book-notes, calculus
editor: markdown
---

# Trigonometric Functions
## 9.5 The Inverse Trigonometric Functions

Recall that inverse functions are functions that "reverse" another function. For example

$$f(x) = 3x - 4$$
$$f^{-1}(y) = \frac{4+ y}{3}$$

Our function $f(x)$ multiplies $x$ by 3 and subtracts 4 from the result. The inverse of that operation would be adding 4 to y and diving the result by 3. 

Just like there are 6 trig functions, there are 6 inverse trig functions. 

$$
\begin{aligned}
\frac{d}{d x}\left(\sin ^{-1} x\right) &=\frac{1}{\sqrt{1-x^{2}}} & \frac{d}{d x}\left(\cos ^{-1} x\right) &=-\frac{1}{\sqrt{1-x^{2}}} \\
\frac{d}{d x}\left(\tan ^{-1} x\right) &=\frac{1}{1+x^{2}} & \frac{d}{d x}\left(\cot ^{-1} x\right) &=-\frac{1}{1+x^{2}} \\
\frac{d}{d x}\left(\sec ^{-1} x\right) &=\frac{1}{|x| \sqrt{x^{2}-1}} & \frac{d}{d x}\left(\csc ^{-1} x\right) &=-\frac{1}{|x| \sqrt{x^{2}-1}}
\end{aligned}
$$

### Inverse sine
$$
y=\sin ^{-1} x \quad \Leftrightarrow \quad \sin y=x \quad \text { for } \quad-\frac{\pi}{2} \leq y \leq \frac{\pi}{2}
$$

Evaluating an inverse trig function is the same as asking what angle ($y$) did we plug into the regular trig function to get $x$. The range for y values $\frac{\pi}{2} \leq y \leq \frac{\pi}{2}$ is 
