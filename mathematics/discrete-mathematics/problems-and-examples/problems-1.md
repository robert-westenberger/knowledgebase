---
title: Problems 1
description: 
published: true
date: 2021-03-13T01:04:50.668Z
tags: computer-science, mathematics, discrete-mathematics
editor: markdown
---

# Problems 1


### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 1
A real number r is called sensible if there exist positive integers $a$ and $b$ such
that $\sqrt{a/b} = r$. For example, setting $a = 2$ and $b = 1$ shows that $\sqrt 2$ is sensible. Prove that $\sqrt[3]2$ is not sensible. (Consider only positive real roots in this problem).

#### Solution
We use proof by contradiction. Suppose that $\sqrt[3]2 = \frac ab$ where a and b are two positive integers.

We cube both sides to get $2 = \frac{a^3}{b^3}$.

We divide both sides to get $2b^3 = a^3$. This implies a is an even integer. If $a^3$ is an even integer, that means that $a$ is an even integer as well.

We can rewrite $a$ as $a=2n$ for some unknown integer $n$. Therefore,
$$(2n)^3 = 2b^3$$
$$8n^3 = 2b^3$$
$$4n^3 = b^3$$

We see that b is also even (its a multiple of 4). Since a and b are both even, they are not coprime numbers, which is a contradiction.

Since we have a contradiction, we must assume that $\sqrt[3] 2$ is irrational. $\blacksquare$


### Problem 1 (From In-Class Problems MIT OCW 6.042J Spring '15)

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

#### Solution (WIP)
$$a=3 \quad b=4 \quad c=5$$

**a)** ![pythag_a.png](/pythag_a.png)
We see that that the square is $(b-a) \medspace x \medspace (b-a)$.

**b)**
![pytthag_b.png](/pytthag_b.png)
Triangles rearranged to form bxb square and a cxc square.
### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 2
Translate the following sentence into a predicate formula: 

*There is a student who has emailed exactly two other people in the class, besides possibly herself.*

The domain of discourse should be the set of students in the class; in addition, the only predicates that you may use are equality and E(x, y), meaning that “x has sent email to y.”
#### Solution

$$
\begin{aligned}
&\exists x \exists y \exists z . E(x, y) \wedge E(x, z) \wedge\\
&x \neq y \wedge x \neq z \wedge y \neq z \wedge\\
&\forall s, E(x, s) \longrightarrow s=x \vee s=y \vee s=z
\end{aligned} \\

\hspace 15.5em \blacksquare
$$

The above is translated to: "There exists students $x$, $y$, and $z$ where $x$ send an email to $y$ AND $x$ sent an email to $z$ AND $x$ is not the same as $y$ AND $x$ is not the same as $z$ and $y$ is not the same as $z$ AND for all students $s$, x sent an email to a student s where the student s is x OR the student s is y OR the student s is z.

### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 3
Express each of the following predicates and propositions in formal logic notation. The domain of discourse is the nonnegative integers, $\natnums$

In addition to the propositional operators, variables and quantifiers, you may define predicates using addition, multiplication, and equality symbols, but no constants (like 0, 1, . . .). For example, the proposition “n is an even number” could be written
$$
\exists m .(m+m=n)
$$

**(a)** n is the sum of three perfect squares.

Since the constant 0 is not allowed to appear explicitly, the predicate “$x = 0$” can’t be written directly, but note that it could be expressed in a simple way as:
$$x + x = x$$

Then the predicate $x>y$ could be expressed 
$$
\exists w. \medspace (y+w=x) \wedge(w \neq 0)
$$

Note that we’ve used “$w \ne 0$” in this formula, even though it’s technically not allowed. But since “$w \ne 0$” is equivalent to the allowed formula “$¬(w + w = w)$,” we can use “$w \ne 0$” with the understanding that it abbreviates the real thing. And now that we’ve shown how to express “$x > y$”, it’s ok to use it too.

**(b)** $x > 1$.
**(c)** $n$ is a prime number. 
**(d)** $n$ is a product of two distinct primes. 
**(e)** There is no largest prime number. 
**(f)** (Goldbach Conjecture) Every even natural number $n > 2$ can be expressed as the sum of two primes. 
**(g)** (Bertrand’s Postulate) If $n > 1$, then there is always at least one prime $p$ such that $n < p < 2n$.

#### Solution (My own answers probably wrong regarding valid quantifier syntax, loop back to this)
a) $\exists m=(m \cdot m=d)\wedge (d+d+d=n)$
b) A unique property of one is that multiplying one by itself is idempotent. Adding one to itself is not. Also, squaring one equals itself. Any number greater than one, when we square it, will be greater than the value we squared.
$$\exists x .(x \ne 0) \wedge (x^x - x \ne 0)$$
$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$ We define $x=1$ as $\forall y . \medspace x y=y$ and then express $x \gt 1$ as $\exists y . \medspace (y=1) \wedge(x>y)$

c) If a number $n$ is prime, it is greater than 0 and there are no numbers $y$ and $z$ that add to it.
$$\exists n.(n \ne 0) \wedge \neg(y + z =n)$$

$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$ IS-PRIME $(n)::=(n>1) \wedge \neg(\exists x \exists y .(x>1) \wedge(y>1) \wedge(x \cdot y=n))$

d) n is a product of two numbers, which themselves are numbers for which there does not exist two numbers that add up to them. 

$$\text {Is-Product-of-Primes}(n)::= \exists x \exists y. \medspace \text{IS-PRIME}(x) \wedge  \text{IS-PRIME}(y) \wedge x \not = y \medspace \wedge x \cdot y = n  $$

e) There is no largest prime number.

$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$  $\neg(\exists p .$ IS-PRIME $(p) \wedge(\forall q .$ IS-PRIME $(q) \longrightarrow p \geq q))$
"There does not exist a prime number $p$ and for all numbers $q$, if $q$ is prime then p is greater than $q$."

f) (Goldbach Conjecture) Every even natural number $n>2$  can be expressed as the sum of two primes.

Define a proposition Is-Two(n) using the fact that two is the only number that Is-Prime and Is-Even (we can use this proposition since its in the question description)

$$\text {Is-Two}(n)::= \text {Is-Prime}(n) \wedge \text {Is-Even}(n) $$

Using the n > 1 and Is-Two estalished above...

$$\text {Is-Greater-Than-Two}(n)::= (n > 1) \medspace \wedge \medspace \neg (\text {Is-Two}(n))$$

$$\text {Is-Sum-of-Primes}(n)::= \exists x \exists y. \medspace \text{IS-PRIME}(x) \wedge  \text{IS-PRIME}(y)  \wedge x + y = n $$

$$\forall n. \medspace \text {Is-Greater-Than-Two}(n) \wedge \text {Is-Sum-of-Primes}(n)$$

My answer is missing the actual implication part...

$$
\forall n \medspace \text {Is-Greater-Than-Two}(n) \longrightarrow  \text {Is-Sum-of-Primes}(n)
$$
$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$ We can define $n \gt 2$ with the formula $\exists y \cdot(y=1) \wedge(x>y+y)$. $n = 2k$ can be expressed as $n=k+k$. The conjecture can be expressed as:

$$
\forall n .((n>2 \wedge \exists k . n=2 k) \longrightarrow \exists p \exists q . \text { IS-PRIME }(p) \wedge \text { IS-PRIME }(q) \wedge(n=p+q)))
$$


g) (Bertrand’s Postulate) If $n > 1$, then there is always at least one prime $p$ such that $n < p < 2n$.

$$\forall n. \medspace n \gt 1 \longrightarrow \exists p. \text { IS-PRIME }(p) \wedge \medspace n \lt p \lt 2n$$

$\textcolor{blue}{Book} \medspace \textcolor{blue} {Answer:}$$\forall n .((n>1) \longrightarrow(\exists p .$ IS-PRIME $(p) \wedge(n<p) \wedge(p<2 n)))$

### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 4
If a set, $A$, is finite, then $|A|<2^{|A|}=|\mathcal{P}(A)|$, and so there is no surjection from set $A$ to its powerset. Show that this is still true if $A$ is infinite. Hint: Remember Russel's paradox and consider $\{x \in A \mid x \notin f(x)\}$ where $f$ is such a surjection.

#### Solution
**Scratch:** Proving by contradiction. 

Suppose there was a surjective function $f$ that maps a set $A$ to its powerset $P(A)$.

Let $W$ be the set of $x$ in $A$ that are not in the image of $f$. 

So by definition we get the following biconditional for all $x$ in $A$.. if $x$ is in $W$ that means that $x$ isn't in the image of $f$ and if $x$ isn't in the image of $f$ that means its in $W$.

We know that every element of $W$ is in $A$ by the definition of the subset of a set.

This means that $W$ is also a member of $P(A)$ by the definition of a powerset (the powerset contains all subsets of its set, $W$ is a subset of $A$ so obviously it will be in the powerset as well).

Since $f$ is a surjection from $A$ to $P(A)$, there exists some $a$ in $A$ whose image is $W$.

So by our earlier biconditional we can replace $W$ with $f(a)$ and get 
$$
(x \in f(a)) \longleftrightarrow(x \notin f(x))
$$
Substituting $a$ for $x$ yields a contradiction, proving there cannot be such an $f$.

**Proof:** 
Proof by contradiction. Suppose there was a surjection $f: A \rightarrow \mathcal{P}(A)$ for some set $A$. Let $W::=\{x \in A \mid x \notin f(x)\}$. So by definition
$$
(x \in W) \longleftrightarrow(x \notin f(x)) \hspace{6em} \text{(1)}
$$
for all $x \in A$. But $W \subseteq A$ by definition and hence is a member of $P(A$). This means that $W = f(a)$ for some $a \in A$, since $f$ is a surjection to $P(A)$. So we have from $(1)$ 
$$
(x \in f(a)) \longleftrightarrow(x \notin f(x))  \hspace{6em} \text{(2)}
$$
for all $x \in A$. Substituting $a$ for $x$ in $(2)$ yields a contradiction, proving there cannot be such an $f$.
$$\hspace{32em} \blacksquare$$

### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 5
**(a)** Prove that 
$$
\exists z. \medspace \lbrack P(z) \wedge Q(z)] \longrightarrow \lbrack \exists x . \medspace P(x) \wedge \exists y . \medspace Q(y)] \hspace{6em} \text{(1)}
$$
is valid. 
**(b)**  Prove that the converse of $(1)$ is not valid by describing a counter model as in Week 2 Notes.
#### Solution (From book)
**(a)**
Assume 
$$
\exists z . \medspace \lbrack P(z) \wedge Q(z)] \hspace{6em} \text{(2)}
$$
That is, $P(z) \wedge Q(z)$ holds for some element $z$ of the domain. Let $c$ be this element, that is, we have $P(c) \wedge Q(c)$.

In particular, $P(c)$ holds by itself. So we conclude (By Existential Generalization) $\exists x \medspace P(x)$. We conclude $\exists y \medspace Q(y)$ similarly. Hence, 

$$
\exists x . P(x) \wedge \exists y . Q(y) \hspace{6em} \text{(3)}
$$
holds. This shows that $(3)$ holds in any interpretation in which $(2)$ holds. Therefore, $(2)$ implies $(3)$ in all interpretations, that $(1)$ is valid. $\hspace{12em} \blacksquare$
**(b)**
We describe a counter model in which $(3)$ is true and $(2)$ is false. 

Let the domain $D$ be $\{\pi, e\}$, $P(x)$ mean "$x=\pi$", and $Q(y)$ mean "$y=e$". Then, $\exists x. P(x)$ is true (let $x$ be $\pi$) and likewise $\exists y. Q(y)$ is true (let $y$ be $e$), so $(3)$ holds.

On the other hand, $Q(\pi)$ is not true, so $P(\pi) \wedge Q(\pi)$ is not true. Likewise, $P(e) \wedge Q(e)$ is not true. Since these are the only elements of $D$, it is not true that there is an element, $z$, of $D$, such that $P(z) \wedge Q(z)$. That is, $(2)$ is not true.
$$\hspace 32em \blacksquare$$
##### Scratch 
The proposition states that if there exists some $z$ for which $P(z)$ and $Q(z)$ are true then there exists some $x$ for which $P(x)$ is true and there exists some y for which $Q(y)$ is true.

Let $D$ be the domain for the variables and $P_0$, and $Q_0$ be some unary predicates on $D$.


We need to show that if $\exists z . \lbrack P(z) \wedge Q(z)]$ holds, then so does $\lbrack \exists x . \medspace P(x) \wedge \exists y . \medspace Q(y)]$.

So suppose $\exists z . \lbrack P(z) \wedge Q(z)]$. So some element $z_0 \in D$ has the property that $P_0 (z) \wedge Q_0 (z)$ is true. 


Suppose $\lbrack \exists x . \medspace P(x) \wedge \exists y . \medspace Q(y)]$. There exists some $x_0 \in D$ that has the property $P_0(x)$ is true and there exists some $y_0 \in D$ that $Q_0(y)$ is true.
### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2005 Set 1 Problem 6
**(a)** Give an exmaple where the following result fails: 
**False Theorem:** For sets $A$, $B$, $C$, and $D$, let 
$$
\begin{aligned}
L &:=(A \cup C) \times(B \cup D) \\
R &:=(A \times B) \cup(C \times D)
\end{aligned}
$$
Then $L=R$.
**(b)** Identify the mistake in the following proof of the False Theorem.

**Bogus proof:** Since $L$ and $R$ are both sets of pairs, its sufficient to prove that $(x, y) \in L \longleftrightarrow (x, y) \in R$ for all $x,y$. 

The proof will be a chain of iff implications. (ignore crappy alignment)

$(x, y) \in L \hspace 2em \text{iff}$ 
$x \in A \cup C$ and $y \in B \cup D \hspace 2em \text{iff}$,
either $x \in A$ or $x \in C,$ and either $y \in B$ or $y \in D \hspace 2em \text{iff}$, 
$(x \in A$ and $y \in B)$ or else $(x \in C$ and $y \in D) \hspace 2em \text{iff}$
$(x, y) \in A \times B,$ or $(x, y) \in C \times D \hspace 2em \text{iff}$
$(x, y) \in(A \times B) \cup(C \times D)=R$

**(c)** Fix the proof to show that $R \subseteq L$.
#### Solution
**Scratch:** 
$A \cup C = \{x \in \mathcal{U} \mid x \in A \vee x \in C\} =U_1$
$B \cup D = \{x \in \mathcal{U} \mid x \in B \vee x \in D\} =U_2$
$A \times B=\{(a, b) \mid a \in A \wedge b \in B\} = CP_1$
$C \times D=\{(c, d) \mid c \in C \wedge d \in D\} = CP_2$
$L$ and $R$ are sets of ordered pairs. 

$L$ is the cartesian product of the unions of sets $A$ and $C$ and $B$ and $D$.
$$L ::= \{x \in \mathcal{U} \mid x \in A \vee x \in C\} \times \{x \in \mathcal{U} \mid x \in B \vee x \in D\}$$
or 
$$L::= U_1 \times U_2=\{(u_1, u_2) \mid u_1 \in U_1 \wedge u_2 \in U_2 \}$$

$R$ is the union of the cartesian product of $A$ and $B$ and the cartesian product of $C$ and $D$.
$$
R ::= \{(a, b) \mid a \in A \wedge b \in B\} \medspace \cup \medspace \{(c, d) \mid c \in C \wedge d \in D\}
$$
or 
$$
R ::= CP_1 \cup CP_2 = \{x \in \mathcal{U} \mid x \in CP_1 \vee x \in CP_2\}
$$

Example where it fails:
set a: a, b, c, d
set b: d, e, f
set c: 1, 2, 3
set d: 4, 5, 6

u1 = {a,b,c,d} ∪ {1,2,3} = {a,b,c,d,1,2,3}.

u2 = b u d {d,e,f} ∪ {4,5,6} = {d,e,f,4,5,6}.
l = u1 x u2 = {{a,d},{a,e},{a,f},{a,4},{a,5},{a,6},{b,d},{b,e},{b,f},{b,4},{b,5},{b,6},{c,d},{c,e},{c,f},{c,4},{c,5},{c,6},{d,d},{d,e},{d,f},{d,4},{d,5},{d,6},{1,d},{1,e},{1,f},{1,4},{1,5},{1,6},{2,d},{2,e},{2,f},{2,4},{2,5},{2,6},{3,d},{3,e},{3,f},{3,4},{3,5},{3,6}}


cp1 = {{a,d},{a, e},{a, f},{ b,d},{ b, e},{ b, f},{ c,d},{ c, e},{ c, f},{ d,d},{ d, e},{ d, f}}
cp2 = {{1,4},{1, 5},{1, 6},{ 2,4},{ 2, 5},{ 2, 6},{ 3,4},{ 3, 5},{ 3, 6}}

r = cp1 u cp2 {{a,d},{a, e},{a, f},{ b,d},{ b, e},{ b, f},{ c,d},{ c, e},{ c, f},{ d,d},{ d, e},{ d, f},  {1,4},{1, 5},{1, 6},{ 2,4},{ 2, 5},{ 2, 6},{ 3,4},{ 3, 5},{ 3, 6}}
**a:** If $A$ = $D$ = $\emptyset$ and $B$ and $C$ are both nonempty, then $L=C \times B \neq \emptyset$, but $R = \emptyset$. 

**b:** It does not necessarily follow that $(x, y) \in (A \times B) \cup (C \times D)$. $(x,y)$ may be in $A \times D$  or $B \times C$ instead.

**d:**
**Proof:** (ignore crappy alignment)
$(x, y) \in L \hspace 2em \text{iff}$ 
$x \in A \cup C$ and $y \in B \cup D \hspace 2em \text{iff}$,
either $x \in A$ or $x \in C,$ and either $y \in B$ or $y \in D \hspace 2em \text{which will be true when}$, 
$(x \in A$ and $y \in B)$ or else $(x \in C$ and $y \in D) \hspace 2em \text{iff}$
$(x, y) \in A \times B,$ or $(x, y) \in C \times D \hspace 2em \text{iff}$
$(x, y) \in(A \times B) \cup(C \times D)=R$


### MIT OCW 6.042J Mathematics for Computer Science Problem Fall 2015 Set 1 Problem 1
Prove that $\log_{4} 6$ is irrational
#### Solution
**Proof by Contradiction:**
Assume to the contrary that $\log_{4} 6$ is rational, so there are two integers $a$ and $b$ where $\log_{4} 6 = a/b$.

This can be rewritten as 
$$ 4^{a/b} = 6$$
$$ 2^{a/b} = 3$$
$$ 2^a = 3^b$$
We get an even number raised to an exponent equal to an odd number raised to an exponent. This is a contradiction, so $\log_{4} 6$ must be irrational. $\blacksquare$

### Discrete Math Workbook 3rd Edition Section 3.2 Question 6
Prove $\sqrt 3$ is irrational.
#### Answer
**Proof:**
Proof by contradiction. Assume $\sqrt 3$ is rational, so there exists $a/b$ where $\sqrt 3 = a/b$.

Square both sides
$3 = (a/b)^2$
$3 = (a^2/b^2)$
$3b^2 = a^2$

It is obvious that $a^2$ must be a multiple of 3, so must $a$ as well.  So for some $k$, $a = 3k$. Plug into our above equation..

$$3b^2 = (3k)^2$$
$$3b^2 = 9k^2$$
$$b^2 = 3k^2$$

Both $a$ and $b$ are divisible by $3$, so they are not coprime integers and they must not be in most reduced form, which is a contradiction. Therefore $\sqrt 3$ must be irrational.
### Discrete Math Workbook 3rd Edition Section 3.2 Question 2
 For each of the statements below, say what method of proof you should use to prove them. Then say how the proof starts and how it ends. Bonus points for filling in the middle.
1. There are no integers $x$ and $y$ such that $x$ is a prime greater than $5$ and $x=6y+3$.
2. For all integers $n$, if $n$ is a multiple of $3$, then $n$ can be written as the sum of consecutive integers. 
3. For all integers $a$ and $b$, if $a^2 + b^2$ is odd, then $a$ or $b$ is odd.
#### Solution
1. Proof by contradiction. Assume there are integers $x$ and $y$ where $x$ is a prime greater than $5$ and $x=6y+3$. This implies $x$ is a divisible by 3, since $y$ is an integer that is multiplied by a multiple of 3 and has 3 added to it. Since $x$ is divisible by a number besides 1 and itself, this is a contradiction to our initial assumption. Therefore $x$ and $y$ do not exist. $\blacksquare$

2. Direct Proof. Assume $n$ is a multiple of $3$ and there are some consecutive integers $x$, $x+1$, and $x+2$ that sum to n. So we have 
$$
n = x + x+1 + x+2 = 3x + 3 = 3(x+1)
$$
$$
n = 3(x+1)
$$
We see that $n$ is equal to the sum of three consecutive integers. That sum can be represented as an integer $x+1$ which itself is a multiple of $3$, so $n$ must be a multiple of $3$. $\blacksquare$
3. Proof by contrapositive. If $a$ and $b$ are even, then $a^2 + b^2$ is even. There are some numbers $x$ and $y$ such that $2x=a$ and $2y=b$. So we get 
$$
a^2 + b^2 = (2x)^2 + (2y)^2 = 4x^2 + 4y^2 = 4(x^2 + y^2)
$$
Since $x^2 + y^2$ is an integer, that is a multiple of 4, so it is even. Therefore, $a^2 + b^2$ is even.

### Discrete Math Workbook 3rd Edition Section 3.2 Question 3
Consider the statement: for all integers $n$, if $n$ is even then $8n$ is even.
a. Prove the statement. What sort of proof are you using?
b. Is the converse true? Prove or disprove.

#### Solution
a. Using a direct proof, assume $n$ is even. So there exists some integer $k$ that $2k=n$. We get $8(2k) = 2(8k)$, therefore $8n$ is even.
b. The converse of this statement is false. It fails when $n=1$, or $n=3$.
### Discrete Math Workbook 3rd Edition Section 3.2 Question 4
The game TENZI comes with $40$ six-sided dice (each numbered $1$ to $6$). Suppose you roll all $40$ dice.
a. Prove that there will be at least seven dice that land on the same number.
b. How many dice would you have to roll before you were guaranteed that some four of them would all match or all be different? Prove your answer.