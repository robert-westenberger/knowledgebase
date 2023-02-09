---
title: Linear Algebra for Game Developers
description: Notes taken from http://blog.wolfire.com/2009/07/linear-algebra-for-game-developers-part-1/
published: true
date: 2023-02-09T15:43:06.958Z
tags: linear-algebra, 3d-graphics
editor: markdown
---

# Vectors
In games, vectors are used to store positions, directions, and velocities. Below are some 2D examples.

![vector_examples.jpeg](/vector_examples.jpeg)

The position vector indicates the man is standing 2 units east and 1 unit north of the origin. The velocity vector indicates that in one unit of time, the plane will be 2 units west and 3 units north of it's origin. The direction vector tells us the gun is pointed to the right. 

A vector by itself is just a set of numbers. It is given meaning only by it's context. For example, in the above position vector, we say `(2,1)` but 2 what? 1 what? If we say the units are meters, and positive numbers are north and east, and negative numbers are south and west, we can say `(2, 1)` means the person is `2` meters north and `1` meter east of the origin.


## Vector Addition
