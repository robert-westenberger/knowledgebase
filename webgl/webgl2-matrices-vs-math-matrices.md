---
title: WebGL2 Matrices vs Math Matrices
description: Notes taken from https://webgl2fundamentals.org/webgl/lessons/webgl-matrix-vs-math.html
published: true
date: 2023-02-20T00:01:35.000Z
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

We can't structure a 4x4 matrix like this :
```
const some4x4TranslationMatrix = [
   1,  0,  0,  tx,
   0,  1,  0,  ty,
   0,  0,  1,  tx,
   0,  0,  0,  1,
];
```
because each of the column's of a 4x4 matrix often has a meaning. The first, second, and third columns are often considered the x, y, and z axis respectively and the last column is the position or translation.

So that means to get the Z axis, you'd have to do this:

```
const zAxis = [
  some4x4Matrix[2],
  some4x4Matrix[6],
  some4x4Matrix[10],
];
```

The way WebGL gets around this is to call rows "columns".

```
const some4x4TranslationMatrix = [
   1,  0,  0,  0,   // this is column 0
   0,  1,  0,  0,   // this is column 1
   0,  0,  1,  0,   // this is column 2
  tx, ty, tz,  1,   // this is column 3
];
```

Now it matches the math definition. Comparing to the example above, if we want the Z axis all we need to do is 
```
const zAxis = some4x4Matrix.slice(8, 11);
```

## Matrices in OpenGL
For those familiar with C++, OpenGL itself requires the 16 values of a 4x4 matrix to be consecutive in memory so in C++ we could create a `Vec4` struct or class
```
// C++
struct Vec4 {
  float x;
  float y;
  float z;
  float w;
};
```

and we could create a 4x4 matrix from 4 of them

```
// C++
struct Mat4x4 {
  Vec4 x_axis;
  Vec4 y_axis;
  Vec4 z_axis;
  Vec4 translation;
}
```

or just 
```
// C++
struct Mat4x4 {
  Vec4 column[4];
}
```

Unfortunately it looks nothing like the math version when you actually declare one statically in code.

```
// C++
Mat4x4 someTranslationMatrix = {
  {  1,  0,  0,  0, },
  {  0,  1,  0,  0, },
  {  0,  0,  1,  0, },
  { tx, ty, tz,  1, },
};
```

Or back to JavaScript where we don't generally have something like C++ structs.

```
const someTranslationMatrix = [
   1,  0,  0,  0,
   0,  1,  0,  0,
   0,  0,  1,  0,
  tx, ty, tz,  1,
];
```

**Every other single dimensional array that is treated as a 2 dimensional array, rows go across.**
```
const someTranslationMatrix = [
   1,  0,  0,  0,  // row 0
   0,  1,  0,  0,  // row 1
   0,  0,  1,  0,  // row 2
  tx, ty, tz,  1,  // row 3
];
```