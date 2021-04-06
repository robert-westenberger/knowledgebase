---
title: Discrete Mathematics 7th Edition Section 1.5 Exercises
description: 
published: true
date: 2021-04-06T02:04:07.394Z
tags: discrete-mathematics
editor: markdown
---

# 1.5 Nested Quantifiers

## 1 
Translate these statements into English, where the domain
for each variable consists of all real numbers.
**a** $\forall x \exists y(x<y)$
**b** $\forall x \forall y(((x \geq 0) \wedge(y \geq 0)) \rightarrow(x y \geq 0))$
**c** $\forall x \forall y \exists z(x y=z)$

### Solution
a. For every $x$ there exists a $y$ where $x$ is less than $y$
b. For every $x$ and every $y$ if $x$ is positive and $y$ is positive then the product of $x$ and $y$ will be positive.
c. For all real numbers $x$ and $y$ there exists a number $z$ that is the product of $x$ and $y$.

## 3 
Let $Q(x, y)$ be the statement “x has sent an e-mail message
to y,” where the domain for both x and y consists of
all students in your class. Express each of these quantifications
in English.
a) $\exists x \exists y Q(x, y)$
b) $\exists x \forall y Q(x, y)$
c) $\forall x \exists y Q(x, y \mid)$
d) $\exists y \forall x Q(x, y)$
e) $\forall y \exists x Q(x, y)$
f) $\forall x \forall y Q(x, y)$
### Solution
a) There exists a student x who has emailed another student y
b) There exists a student x who has emailed every other student
c) All students have emailed at least one student in class.
d) There exists a student y who has received an email from everybody
e) Every student has received an email from student X
f) All students have sent and received an email from eachother

## 19
Express each of these statements using mathematical and
logical operators, predicates, and quantifiers, where the
domain consists of all integers.
**a)** The sum of two negative integers is negative.
**b)** The difference of two positive integers is not necessarily
positive.
**c)** The sum of the squares of two integers is greater than
or equal to the square of their sum.
**d)** The absolute value of the product of two integers is
the product of their absolute values.
### Solution
**a)** 
$$
\forall x \forall y ((x \lt 0 \wedge y \lt 0) \rarr (x+y \lt 0))
$$
**b)**
$$
\forall x \forall y \exists z((x \lt 0 \wedge y \lt 0) \wedge (z \lt 0 \vee z \gt 0 \vee z = 0) \rarr (x-y = z))
$$
Book answer is 
$$\neg \forall x \forall y((x>0) \wedge(y>0) \rightarrow(x-y>0))$$
**c)** $\forall x \forall y\left(x^{2}+y^{2} \geq(x+y)^{2}\right)$
**d)** $\forall x \forall y(|x y|=|x||y|)$
## 21
Use predicates, quantifiers, logical connectives, and mathematical operators to express the statement that every positive integer is the sum of the squares of four integers.
### Solution
