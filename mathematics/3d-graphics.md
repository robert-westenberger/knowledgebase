---
title: 3D Graphics
description: 
published: true
date: 2023-02-12T20:48:49.491Z
tags: 3d-graphics
editor: markdown
---

# 3D Cartesian Space
Many, but not all, concepts in 2D directly extend into 3D. We frequently use 2D to establish an understanding of a problem and develop a solution, and then extend that into 3D.

## Extra Dimension, Extra Axis
3D is defined by 3 mutually perpendicular axes. 

In 3D, x and y aren't necessarily the same as they are in 2D. In 3D, any pair of axes defines a plane that contains the two axes and is perpendicular to the third axis. 

For example, the plane containing the x- and y-axes is
the xy plane, which is perpendicular to the z-axis. The xz plane is perpendicular to the y-axis, and the yz plane is perpendicular to the x-axis. Each are a 2D Cartesian coordinate space in its own right. 

![3d-cartesian.png](/3d-cartesian.png)

If we assign +x, +y, and +z to point right, up, and forward, respectively, then the 2D coordinate space of the “ground” is the xz plane, as shown above.

## Specifying Locations in 3D
![specifying-locations-in-3d.png](/specifying-locations-in-3d.png)

## Left-handed vs Right-handed Coordinate Spaces
Not all 3D coord spaces are equal, in the sense that some pairs of coord systems cannot be rotated to line up with eachother. 

There are 2 kinds of coord spaces, left-handed and right-handed. Only spaces of the same kind can be aligned.

They are named that because you can make one with your hands.

### Differences
They differ in the definition of "positive rotation".

The left-hand rule works like this: put your left hand in the “thumbs
up” position, with your thumb pointing towards the positive end of the axis
of rotation. Positive rotation about the axis of rotation is in the direction
that your fingers are curled.

In 3D, there are 48 different combinations to assign axes.

**Everything in this page uses a left-handed coordinate system.** 

The +x, +y, and +z directions point right, up, and forward, respectively

# Vectors
## Negating a Vector
A vector is negated when you add it's additive inverse.

To negate $x$, add to it $-x$.

## Vector Multiplication 
We simply multiply each component of the vector by the scalar.


$$
k\left[\begin{array}{c}
a_1 \\
a_2 \\
\dots \\
a_{n-1} \\
a_n
\end{array}\right]=\left[\begin{array}{c}
a_1 \\
a_2 \\
\dots \\
a_{n-1} \\
a_n
\end{array}\right] k=\left[\begin{array}{c}
k a_1 \\
k a_2 \\
\dots \\
k a_{n-1} \\
k a_n
\end{array}\right]
$$

For 3D vectors, we get

$$
k\left[\begin{array}{l}
x \\
y \\
z
\end{array}\right]=\left[\begin{array}{l}
x \\
y \\
z
\end{array}\right] k=\left[\begin{array}{l}
k x \\
k y \\
k z
\end{array}\right]
$$

A vector may aslso be divided by a nonzero scalar. This is equivalent to multiplying by the reciprocal of the scalar. 

$$
\frac{\mathbf{v}}{k}=\left(\frac{1}{k}\right) \mathbf{v}=\left[\begin{array}{l}
v_x / k \\
v_y / k \\
v_z / k
\end{array}\right]
$$
for $3 \mathrm{D}$ vector $\mathbf{v}$ and nonzero scalar $k$


### Geometric Interpretation
Geometrically, multiplying a vector by a scalar $k$ has the effect of scaling the length by a factor of $|k|$. E.G, to double the length of a vector we would multiply the vector by 2. If $k<0$, then the direction of the vector is flipped.