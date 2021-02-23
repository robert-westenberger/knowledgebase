---
title: Chapter 1: Problems
description: 
published: true
date: 2021-02-23T19:06:29.001Z
tags: computer-science, mathematics, book-notes, discrete-mathematics
editor: markdown
---

# Problem: Mathematics for Computer Science

## Problem 1  (From Problem Set 1 MIT OCW 6.042J Fall '05)
A real number r is called sensible if there exist positive integers $a$ and $b$ such
that $\sqrt{a/b} = r$. For example, setting $a = 2$ and $b = 1$ shows that $\sqrt 2$ is sensible. Prove that $\sqrt[3]2$ is not sensible. (Consider only positive real roots in this problem).

### Solution
We use proof by contradiction. Suppose that $\sqrt[3]2 = \frac ab$ where a and b are two positive integers.

We cube both sides to get $2 = \frac{a^3}{b^3}$.

We divide both sides to get $2b^3 = a^3$. This implies a is an even integer. If $a^3$ is an even integer, that means that $a$ is an even integer as well.

We can rewrite $a$ as $a=2n$ for some unknown integer $n$. Therefore,
$$(2n)^3 = 2b^3$$
$$8n^3 = 2b^3$$
$$4n^3 = b^3$$

We see that b is also even (its a multiple of 4). Since a and b are both even, they are not coprime numbers, which is a contradiction.

Since we have a contradiction, we must assume that $\sqrt[3] 2$ is irrational. $\blacksquare$

## Problem 1 (From In-Class Problems MIT OCW 6.042J Spring '15
The Pythagorean Theorem says that if a and b are the lengths of the sides of a right triangle, and c is the length of its hypotenuse, then
$$a^2 + b^2 = c^2$$
In this problem we'll examine a  particularly simple “proof without words” of the theorem.

Suppose you are given four different colored copies of a right triangle with sides of lengths a, b and c, along with a suitably sized square, shown below.![pythagorean_theorem_problem.png](/pythagorean_theorem_problem.png)

**(a)** You will first arrange the square and four triangles so they form a $c \medspace x \medspace c$ square. From this arrangement you will see that the square is $(b - a) \medspace x \medspace (b-a)$

**(b)** You will then arrange the same shapes so they form two squares, one $a \medspace x \medspace a$ and the other $b \medspace x \medspace b$.
You know that he area of an $s \medspace x \medspace s$ square is $s^2$. Appealing to the principle that **area is preserved by rearranging**, we can conclude that $a^2 + b^2 = c^2$ as claimed.
One concern is that there might be something special about the shape of these particular triangles and squares that makes the rearranging possible - for exmaple, suppose $a=b$. 
**(c)** How would you respond to this concern?
**(d)** Another concern is that a number of facts about right triangles, squares and lines are being implicitly assumed in justifying the rearrangements into squares. Enumerate some of these assumed facts.

### Solution

$$a=3 \quad b=4 \quad c=5$$

**a)** ![pythag_a.png](/pythag_a.png)
We see that that the square is $(b-a) \medspace x \medspace (b-a)$.

**b)**
![pytthag_b.png](/pytthag_b.png)