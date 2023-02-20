---
title: WebGL2 2D Matrices
description: Notes taken from https://webgl2fundamentals.org/webgl/lessons/webgl-2d-matrices.html
published: true
date: 2023-02-20T00:30:52.517Z
tags: matrix, webgl
editor: markdown
---

Performing scale, rotation, and translation operations separately are order dependent. Doing translation, rotation, and then scale would have a different result.

The same operations can be done with matrix math.

For 2D we use a 3x3 matrix. 

$$
\begin{array}{|c|c|c|}
\hline 1.0 & 2.0 & 3.0 \\
\hline \hline 4.0 & 5.0 & 6.0 \\
\hline \hline 7.0 & 8.0 & 9.0 \\
\hline
\end{array}
$$

To do the math we multiply the position down the columns of the matrix and add up the results. Our positions only have 2 values, x and y, but to do this math we need 3 values so we'll use 1 for the third value.

If we want to do a translation, the matrix would be

$$
\begin{array}{|c|c|c|}
\hline 1.0 & 0.0 & 0.0 \\
\hline \hline 0.0 & 1.0 & 0.0 \\
\hline \hline \text { tx } & \text { ty } & 1.0 \\
\hline
\end{array}
$$

$$
\begin{array}{r}
\text { newX }=\mathrm{x} * 1.0+ \\
\mathrm{y} * \mathrm{0.0}+ \\
1 * \mathrm{tx}
\end{array}
\begin{aligned}
\text { newY }= & x * 0.0+ \\
& y * 1.0+ \\
& 1 * t y
\end{aligned}
\begin{aligned}
\text { extra }= & \mathrm{x} * 0.0+ \\
& \mathrm{y} * 0.0+ \\
& 1 * 1.0
\end{aligned}
$$


## Rotation Matrix

$$
\begin{aligned}
& s=\text { Math.sin(angleToRotateInRadians) } ; \\
& c=\text { Math.cos(angleToRotateInRadians) } ;
\end{aligned}
$$


$$
\begin{array}{|c|c|c|}
\hline \mathrm{c} & -\mathrm{s} & 0.0 \\
\hline \hline \mathrm{s} & \mathrm{c} & 0.0 \\
\hline \hline 0.0 & 0.0 & 1.0 \\
\hline
\end{array}
$$

Simplifying the operations, we get 

$$
\begin{aligned}
& \text { newX }=x * c+y * s \text {; } \\
& \text { newY }=x *-s+y * c ; \\
&
\end{aligned}
$$