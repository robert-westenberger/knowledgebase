---
title: Linear Algebra for Game Developers
description: Notes taken from http://blog.wolfire.com/2009/07/linear-algebra-for-game-developers-part-1/
published: true
date: 2023-02-09T17:17:45.459Z
tags: linear-algebra, 3d-graphics
editor: markdown
---

# Vectors
In games, vectors are used to store positions, directions, and velocities. Below are some 2D examples.

![vector_examples.jpeg](/vector_examples.jpeg)

The position vector indicates the man is standing 2 units east and 1 unit north of the origin. The velocity vector indicates that in one unit of time, the plane will be 2 units west and 3 units north of it's origin. The direction vector tells us the gun is pointed to the right. 

A vector by itself is just a set of numbers. It is given meaning only by it's context. For example, in the above position vector, we say `(2,1)` but 2 what? 1 what? If we say the units are meters, and positive numbers are north and east, and negative numbers are south and west, we can say `(2, 1)` means the person is `2` meters north and `1` meter east of the origin.


## Vector Addition
One of the most common applications in games for vector addition is physics integration. Any physically-based object will likely have vectors for position, velocity, and acceleration. For every frame, these vectors need to be integrated (we have to add the velocity to the position, and the acceleration to the velocity.



To add vectors together, just add each component together separately. For example

$$
(0,1,4) + (3,-2,5) = (0+3, 1-2, 4+5) = (3,-1,9)
$$

### Example
Below, we see mario jump and land over the course of 8 frames.
![mario-parabola.jpeg](/mario-parabola.jpeg)

In this example, mario starts at position $(0,0)$. As he starts to jump, his velocity is $(1,3)$. He is moving upward quickly, but also to the right. His acceleration throughout is $(0, -1)$ because gravity is pulling him down.

So what's happening frame by frame is: 
1. Mario is stationary at $(0,0)$.
2. He jumps, up and to the right. We add his velocity of $(1,3)$ to his current position of $(0,0)$ to get the new position of $(1,3)$. Then, add his acceleration $(0,-1)$ to his velocity $(1,3)$ to get his new velocity $(1,2)$.
3. 