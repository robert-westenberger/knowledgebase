---
title: Linear Algebra for Game Developers
description: Notes taken from http://blog.wolfire.com/2009/07/linear-algebra-for-game-developers-part-1/
published: true
date: 2023-02-11T21:26:55.981Z
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

![pythag_vector_length.jpeg](/pythag_vector_length.jpeg)

To calculate the speed of a ship, we use

$$
|V| = \sqrt{4^2+3^2} = \sqrt{25} = 5
$$

This works with 3D bectors as well. The length of a vector with components $(x,y,z)$ is 

$$
\sqrt{x^2+y^2+z^2}
$$

## Distance
If the player $P$ is at $(3,3)$ and there is an explosion $E$ at $(1,2)$, we need to find the distance between them to see how much damage the player takes. 

We combine vector subtraction and length. We subtract $P-E$ to get the vector between them, and then find the length of that vector to get the distance between them. 
![vector-distance.jpeg](/vector-distance.jpeg)

Order doesn't matter, $|E-P|$ give's the same result.

$$
\text{Distance} = |P-E| = |(3,3)-(1,2)| = |(2,1)| = \sqrt{22+12} = \sqrt5 = 2.23
$$

## Normalization
When dealing with directions (as opposed to positions or velocities), it is important that they have a unit length (length of 1). It makes things easier for us. 

A vector with length $1$ is **normalized**. 

### Example
A gun is pointing in the direction of (1,0) that shoots a bullet at 20 m/s. What is the velocity of the bullet? Since the direction has length 1, we can multiply the direction and the bullet speed to get the bullet velocity (20, 0). If the direction of the bector had any other length, we couldn't do this -- the bullet would be too fast or slow. 

### Normalizing a Vector
Divide each component by the vector's length. 

#### Example
We want to normalize a vector $V$ with components $(3,4)$, we divide each component by its length, $5$, to get $(\frac{3}{5},\frac{4}{5})$. 

Pythagorean theorem is used to prove that is has length 1:

$$
(\frac35)^2 + (\frac45)^2 = \frac{9}{25} + \frac{16}{25} = \frac{25}{25} = 1
$$

## Dot Product
To get the dot product of two vectors: 
- multiply the components 
- add them together.

$$
(a_1,a_2) \centerdot (b_1,b_2) = a_1b_2 + a_2b_2
$$

### Example Calculation
$$
(3,2)\centerdot(1,4) = 3*1 + 2*4 
$$

### Example Applications
![dot-product-simple.jpeg](/dot-product-simple.jpeg)


When vectors are pointing in () the dot product is
same direction = positive 
perpendicular = 0
opposite directions = negative

Proportional to how much vectors point in the same direction. 

#### Field of view
We have a guard at position $G(1,3)$ facing in the direction $D(1,1)$ with a $180\degree$ field of view. We have a hero sneaking by at position $H(3,2)$. 

We can determine if he is in the guard's FOV by checking the sign of $D \cdot V$ (the vector from the guard to the hero). 

$$
V = H-G = (3,2)-(1,3) = (3-1,2-3) = (2,-1)
$$
$$
D \cdot V = (1,1)\cdot(2,-1) = 1*2+1*-1 = 2-1 = 1
$$

Since $1$ is positive, the hero is in the guard's field of view.![dot-product-field-of-view.jpeg](/dot-product-field-of-view.jpeg)

### Exact equation
$$ AB = |A||B|cos \theta $$

Where $\theta$ (pronounced theta) is the angle between $A$ and $B$. This allows us to solve for $\theta$ if we want to find out the angle.

$$ \theta = a\cos(\frac{[AB]}{[|A||B|]})$$

If $A$ and $B$ are normalized, then the equation is 

$$\theta=a\cos(AB)$$


#### FOV 2
This time, the guard's FOV is only $120\degree$. 

First, get the normalized vector's for the direction the guard is facing $(D')$, and the direction from the guard to the hero $(V')$. Then, we check the angle between them. If it is greater than $60$ (half the FOV), then the hero is not seen. 

$$
D' = \frac{D}{|D|} = \frac{(1,1)}{\sqrt{1^2+1^2}} =  \frac{(1,1)}{\sqrt2} = (0.71,0.71)
$$

$$
V' = \frac{V}{|V|} = \frac{(2,-1)}{\sqrt(2^2+(-1)^2)} = \frac{(2,-1)}{\sqrt5} = (0.89,-0.45)
$$

$$
\theta = a\cos(D'V') = a\cos(0.71*0.89 + 0.71*(-0.45)) = a\cos(0.31) = 72
$$

The angle between the center of the guard's vision and the hero is $72$, so the guard does not see him.

![dot-product-fov-2.jpeg](/dot-product-fov-2.jpeg)

### In C++ GLSL inspired syntax
In code, it's pretty simple.
```
//Initialize starting vectors
vec2 guard_pos = vec2(1,3);
vec2 guard_facing = vec2(1,1);
vec2 hero_pos = vec2(3,2);

//Prepare normalized vectors
vec2 guard_facing_n = normalize(guard_facing);
vec2 guard_to_hero = normalize(hero_pos - guard_pos);

//Check angle
float angle = acos(dot(guard_facing_n, guard_to_hero));
```

## Cross Product

### Example Applications
Let's say you have a boat that has cannons that fire to the left and right. Given that the boat is facing along the direction vector $(2,1)$, in which directions do the cannons fire?

#### 2D
To rotate $90\degree$ clockwise, flip the two vector components, and then switch the sign of the second component. $(a,b)$ becomes $(b,-a)$.

If the boat is facing $(2,1)$, the right facing cannon fires toward $(-1, 2). The left facing cannon fires in the opposite direction, so we flip both signs to get $(-1, 2)$.
![cross-product-1.jpeg](/cross-product-1.jpeg)

#### 3D
![cross-product-2.jpeg](/cross-product-2.jpeg)
Let's revisit our sailing ship. We have a vector for the direction of the mast $M$, going straight up $(0,1,0)$, and the direction of the north-north-east wind $W(1,0,2)$, and we want to find the direction the sail S should stick out in order to best catch the wind. The sail has to be perpendicular to the mast, and also perpendicular to the wind. To solve this, we can use the cross product: $S = M \times W$.

The cross product of $A(a_1,a_2,a_3))$ and $B(b_1,b_2,b_3))$ is:

$$(a_2b_3-a_3b_2, a_3b_1-a_1b_3, a_1b_2-a_2b_1)$$

Now we can plug in our numbers to solve our problem. 

$$S = M\times W = (0,1,0)\times (1,0,2) = ([1*2-0*0], [0*1-0*2], [0*0-1*1]) = (2,0,-1)$$

##### In C++ GLSL inspired syntax
```
vec3 cross(vec3 a, vec3 b) {
    vec3 result;
    result[0] = a[1] * b[2] - a[2] * b[1];
    result[1] = a[2] * b[0] - a[0] * b[2];
    result[2] = a[0] * b[1] - a[1] * b[0];
    return result;
}
```

#### 3D Surface Normals
Another common use for cross product in games is to find surface normals -- the direciton that a surface is facing. 

The basic expression for lighting in games is $N \cdot L$, where $N$ is the surface normal, and $L$ is the normalized light direction. This is what makes surfaces bright when they face towards the light, and dark when they don't.
##### Example 
Take a triangle with vertex vectors $A$, $B$ and $C$. How do we find the direction that the triangle is facing? It seems tricky, but we have the tools to do it now. We can use subtraction to get the direction from $A$ to $C(C-A)$ 'Edge 1' and $A$ to $B(B-A)$ 'Edge 2', and then use the cross product to find a new vector $N$ perpendicular to both of them... the surface normal.

![cross-product-surface-normals.jpeg](/cross-product-surface-normals.jpeg)

##### In C++ GLSL inspired syntax
```
vec3 GetTriangleNormal(vec3 a, vec3 b, vec3 c) {
    vec3 edge1 = b-a;
    vec3 edge2 = c-a;
    vec3 normal = cross(edge1,edge2);
    return normal;
}
```

# Transformation Matrix

## Basis Vectors
Let's say we're making an Asteroids game on really old hardware, and we want to have a simple 2D space ship that can rotate freely. The ship model looks like this:
