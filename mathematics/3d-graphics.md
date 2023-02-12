---
title: 3D Graphics
description: 
published: true
date: 2023-02-12T00:20:09.865Z
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