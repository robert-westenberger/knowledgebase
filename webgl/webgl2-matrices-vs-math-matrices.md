---
title: WebGL2 Matrices vs Math Matrices
description: Notes taken from https://webgl2fundamentals.org/webgl/lessons/webgl-matrix-vs-math.html
published: true
date: 2023-02-19T23:50:12.993Z
tags: matrix, webgl, linear-algebra
editor: markdown
---

In programming, rows are horizontal and columns are vertical. 

```
const m3x3 = [
  0, 1, 2,  // row 0
  3, 4, 5,  // row 1
  6, 7, 8,  // row 2
];
 
const m4x4 = [
   0,  1,  2,  3,  // row 0 
   4,  5,  6,  7,  // row 1
   8,  9, 10, 11,  // row 2
  12, 13, 14, 15,  // row 3
];
```

To make a $3x3$ 2D translation matrix the translation values `tx` and `ty` go in locations 6 and 7.

```
const some3x3TranslationMatrix = [
   1,  0,  0,
   0,  1,  0,
  tx, ty,  1,
];
```
**Math notation**:
$$
\left[\begin{array}{lll}
1 & 0 & \mathrm{tx} \\
0 & 1 & \mathrm{ty} \\
0 & 0 & 1
\end{array}\right]
$$

Or for a $4x4$ 3D matrix the translation goes in locations 12, 13, and 14

```
const some4x4TranslationMatrix = [
   1,  0,  0,  0,
   0,  1,  0,  0,
   0,  0,  1,  0,
  tx, ty, tz,  1,
];
```
**Math notation**:
$$
\left[\begin{array}{llll}
1 & 0 & 0 & t x \\
0 & 1 & 0 & t y \\
0 & 0 & 1 & t z \\
0 & 0 & 0 & 1
\end{array}\right]
$$