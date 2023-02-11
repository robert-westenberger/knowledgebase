---
title: Linear Algebra for Game Developers
description: Notes taken from http://blog.wolfire.com/2009/07/linear-algebra-for-game-developers-part-1/
published: true
date: 2023-02-11T18:10:30.972Z
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
3. Second frame. We add his velocity (1,2) to his position (1,3) to get his new position of (2,5). Then, add his acceleration (0,1) to his velocity (1,2) to get (1, 1).

**Usually in games the player controls a character's acceleration with the keyboard or gamepad, and the game calculates the new veolcity and position using physics integration (via vector addition). It's an integration problem, we are just using an approximate brute-forec approach.** 

## Vector Subtraction
Useful for getting a vector that points from one position to another. 

## Example
Player is standing at (1,2) with a rifle, and an enemy is at (4,3). To get the vector that the bullet must travel to hit the enemy, you can subtract the player's position from the robot's position. 

$$
(4,3)-(1,2) = (4-1, 3-2) = (3,1)
$$

![vector_subtraction_example.jpeg](/vector_subtraction_example.jpeg)

## Scalar-vector multiplication
In the context of vectors, individual numbers are called **scalars**. $(3,4)$ is a vector, $5$ is a scalar.

In games, it's often useful to multiply a vector by a scalar. 

### Example
We can simulate basic air resistance by multiplying the player's velocity by $0.9$ every frame. We just multiply each component of the vector by the scalar. 

If the player's starting velocity is $(10, 20)$

$$
0.9*(10,20) = (0.9*10, 0.9*20) = (9,18)
$$

## Length 
If we have a ship with velocity vector $V(4,3)$, we might to know it's speed as well, in order to calculate how much fuel is used or how much the screen should shake. 

To do that, we need to find the length/magnitude of vector $V$. The length of a vector is often written using $||$ for short, so the length of $V$ is $|V|$.


$V$ is a right triangle with sides $4$ and $3$, and use the pythagorean theorem to find the hyptonuse: $x^2 + y^2=h^2$. That is, the length of a vector $H$ with components $(x,y)$ is $\sqrt{x^2+y^2}$.