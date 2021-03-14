---
title: Proofs Involving Sets
description: 
published: true
date: 2021-03-14T01:30:08.617Z
tags: mathematics, discrete-mathematics
editor: markdown
---

# How to Prove $a \in A$

* To show $\mathbf{a} \in\{\mathbf{x}: \mathbf{P}(\mathbf{x})\}$ 	
	* show that $P(a)$ is true.

* To show $\mathbf{a} \in\{\mathbf{x} \in \mathbf{S}: \mathbf{P}(\mathbf{x})\}$
	* Verify that $a \in S$
  * Show that $P(a)$ is true.
  
  
## Examples
### Example 1
$A=\{x: x \in \mathbb{N}$ and $7 \mid x\}$
This set has form $A = \{x:P(x)\}$ where $P(x)$ is the open sentence $(x \in \mathbb{N}) \wedge(7 \mid x)$. Thus $21 \in A$ because $P(21)$ is true. Similarly, $7, 14, 28, 35$ etc are all elements of $A$. But $8 \notin A$ for example because $P(8)$ is false. Likewise, $-14 \notin A$ because $P(-14)$ is false. 

### Example 2
$A=\{X \in \mathscr{P}(\mathbb{N}):|X|=3\}$
We know that $\{4,13,45\}\in A$ because $\{4,13,45\} \in \mathscr{P}(\mathbb{N})$ and $|\{4,13,45\}|=3$.
However, $\{1,2,3,4\} \notin A$ because $|\{1,2,3,4\}| \neq 3$

### Example 3
$B=\{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod \medspace 5)\}$

$(8,23)\in B$ because $(8,23) \in \mathbb{Z} \times \mathbb{Z}$ and $8 \equiv 23(\bmod \medspace 5)$.
Likewise, $(100, 75) \in B$, $(102, 77) \in B$ etc., but $(6, 10) \notin B$

Suppose $n \in \mathbb{Z}$ and consider the ordered pair $(4 n+3,9 n-2)$. Does this ordered pair belong in $B$? To answer this, we observe that $(4 n+3,9 n-2) \in \mathbb{Z} \times \mathbb{Z}$. Next, we observe $(4 n+3)-(9 n-2)=-5 n+5=5(1-n)$, so $5 \mid((4 n+3)-(9 n-2))$, which means $(4 n+3) \equiv(9 n-2)(\bmod 5)$. Therefore we have established that $(4 n+3,9 n-2)$ meets the requirements for belonging to $B$, so $(4 n+3,9 n-2) \in B$ for every $n \in \mathbb{Z}$.

### Example 4
$C=\left\{3 x^{3}+2: x \in \mathbb{Z}\right\}$

Elements of this set consist of all the values $3x^3 + 2$ where $x$ is an integer. Thus $-22 \in C$ because $-22=3(-2)^{3}+2$. You can confirm $-1 \in C$ and $5 \in C$. $0 \notin C$ and $\frac 12 \notin C$ etc.

# How to Prove $A \subseteq B$
To prove $A \subseteq B$, we need to prove
$$a \in A \longrightarrow a \in B$$
This can be proved directly, assuming $a \in A$ and deducing $a \in B$.

The contrapositive approach is another option: Assume $a \notin B$ and deduce $a \notin A$.


If $A$ and $B$ are sets, then $\mathscr{P}(A) \cup \mathscr{P}(B) \subseteq \mathscr{P}(A \cup B)$. 

A small example of this...
$$
\begin{aligned}
\mathscr{P}(A) \cup \mathscr{P}(B) &=\{\varnothing,\{1\},\{2\},\{1,2\}\} \cup\{\varnothing,\{2\},\{3\},\{2,3\}\} \\
&=\{\varnothing,\{1\},\{2\},\{3\},\{1,2\},\{2,3\}\} .
\end{aligned}
$$

Also $\mathscr{P}(A \cup B)=\mathscr{P}(\{1,2,3\})=\{\varnothing,\{1\},\{2\},\{3\},\{1,2\},\{2,3\},\{1,3\},\{1,2,3\}\}$. So even though $\mathscr{P}(A) \cup \mathscr{P}(B) \neq \mathscr{P}(A \cup B)$, it is true that $\mathscr{P}(A) \cup \mathscr{P}(B) \subseteq \mathscr{P}(A \cup B)$ for this particular $A$ and $B$.
## Examples
### Example 1
Prove that $\{x \in \mathbb{Z}: 18 \mid x\} \subseteq\{x \in \mathbb{Z}: 6 \mid x\}$
(Prove the set of integers that are divisible by 18 is a subset of the set of integers that are divisible by 6) 
**Proof:**
1. Suppose  $a \in\{x \in \mathbb{Z}: 18 \mid x\}$.
	(Our supposition)
  
2. This means that $a \in \Z$ and $18 \vert a$.
	(Subsitute in $a$ for $x$ in the notation for the set).

3. By definition of divisibility, there is an integer $c$ for which $a = 18c$.

4. Consequently, $a=6(3c)$, and from this we deduce $6 \vert a$.

5. Therefore $a$ is one of the integers that $6$ divides, so $a \in\{x \in \mathbb{Z}: 6 \mid x\}$.

6. We've shown $a \in\{x \in \mathbb{Z}: 18 \mid x\}$ implies $a \in\{x \in \mathbb{Z}: 6 \mid x\}$, so it follows that $\{x \in \mathbb{Z}: 18 \mid x\} \subseteq\{x \in \mathbb{Z}: 6 \mid x\}$. $\blacksquare$
### Example 2
Prove that $\{x \in \mathbb{Z}: 2 \mid x\} \cap\{x \in \mathbb{Z}: 9 \mid x\} \subseteq\{x \in \mathbb{Z}: 6 \mid x\}$
(Prove the intersection between the set of all integers divisibly by $2$ and integers divisible by $9$ is the subset of all integers divisible by $6$)
**Proof:** 
1. Suppose $a \in\{x \in \mathbb{Z}: 2 \mid x\} \cap\{x \in \mathbb{Z}: 9 \mid x\}$
	(Suppose $a$ is in the intersection between two sets.. ints divis by $2$ and ints divis by $9$)
  
2. By definition of intersection, this means $a \in\{x \in \mathbb{Z}: 2 \mid x\}$ and $a \in\{x \in \mathbb{Z}: 9 \mid x\}$.
	(Use definition of intersection to establish $a$ is in both sets of integers)
3. Since $a \in\{x \in \mathbb{Z}: 2 \mid x\}$ we know $2 \vert a$, so $a=2c$ for some $c \in \Z$. Thus $a$ is even.
	(Use $a$'s membership to this particular set to establish some more information about $a$)
4. Since $a \in\{x \in \mathbb{Z}: 9 \mid x\}$ we know $9 \vert a$, so $a=9d$ for some $d \in \Z$.
	(Same as 3, more information about $a$)

5. As $a$ is even, $a=9d$ implies $d$ is even.
	(More logical insights about $a$)
  
6. Then $d=2e$ for some integer $e$, and we have $a=9 d=9(2 e)=6(3 e)$.
	(Use insights from previous steps to establish $a$ is also a multiple of $6$)

7. From $a=6(3 e)$, we conclude $6 \vert a$, and this means $a \in\{x \in \mathbb{Z}: 6 \mid x\}$.
	( Since $a$ is divisible by $6$ it must also by in the set of all ints divis by $6$ )
8. We have shown that $a \in\{x \in \mathbb{Z}: 2 \mid x\} \cap\{x \in \mathbb{Z}: 9 \mid x\}$ implies $a \in\{x \in \mathbb{Z}: 6 \mid x\}$, so it follows that $\{x \in \mathbb{Z}: 2 \mid x\} \cap\{x \in \mathbb{Z}: 9 \mid x\} \subseteq\{x \in \mathbb{Z}: 6 \mid x\}$. $\blacksquare$
### Example 3
Prove that $\{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod 6)\} \subseteq\{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod 3)\}$
(Prove the set of ordered pairs that have the same remainder for modulo $6$ is the subset of ordered pairs that have the same remainder for modulo $3$)

**Proof:** 
1. Suppose $(a, b) \in\{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod 6)\}$
2. This means that $(a, b) \in \mathbb{Z} \times \mathbb{Z}$ and $a \equiv b(\bmod 6)$.
3. Consequently $6 \mid(a-b)$, so $a-b=6c$ for some integer $c$.
4. It follows that $a-b=3(2c)$, and this means that $3 \vert (a-b)$, so $a \equiv b(\text{mod} 3)$.
5. Thus $(a, b) \in\{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod 3)\}$.
6. We've now seen that $(a, b) \in\{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod 6)\}$ implies $(a, b) \in \{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod 3)\}$, so it follows that $\{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod 6)\} \subseteq \{(x, y) \in \mathbb{Z} \times \mathbb{Z}: x \equiv y(\bmod 3)\}$ $\blacksquare$

### Example 4: Prove that if $A$ and $B$ are sets, then $\mathscr{P}(A) \cup \mathscr{P}(B) \subseteq \mathscr{P}(A \cup B)$
**Theorem:** If $A$ and $B$ are sets, then $\mathscr{P}(A) \cup \mathscr{P}(B) \subseteq \mathscr{P}(A \cup B)$
**Proof:** 
1. Suppose $X \in \mathscr{P}(A) \cup \mathscr{P}(B)$.

2. By definition of union, this means $X \in \mathscr{P}(A)$ or $X \in \mathscr{P}(B)$.

3. Therefore $X \subseteq A$ or $X \subseteq B$ (by definition of power sets). We consider cases.

4. **Case 1:** Suppose $X \subseteq A$. Then $X \subseteq A \cup B$, and this means $X \in \mathscr{P}(A \cup B)$. 

5. **Case 2:** Suppose $X \subseteq B$. Then $X \subseteq A \cup B$, and this means $X \in \mathscr{P}(A \cup B)$. 

6. (We do not need to consider the case where $X \subseteq A$ **and** $X \subseteq B$ because that is taken care of by either of our cases). The above cases show $X \in \mathscr{P}(A \cup B)$.

7. Thus we've shown that $X \in \mathscr{P}(A) \cup \mathscr{P}(B)$ implies $X \in \mathscr{P}(A \cup B)$, and this completes the proof that $\mathscr{P}(A) \cup \mathscr{P}(B) \subseteq \mathscr{P}(A \cup B)$ $\blacksquare$

### Example 5
**Theorem:** Suppose $A$ and $B$ are sets. If $\mathscr{P}(A) \subseteq \mathscr{P}(B)$ then $A \subseteq B$.

**Proof:** 
1. We use direct proof. Assume $\mathscr{P}(A) \subseteq \mathscr{P}(B)$
2. Based on this assumption, we must now show $A \subseteq B$.
3. To show $A \subseteq B$, suppose that $a \in A$.
4. Then the one-element set $\{a\}$ is a subset of $A$, so $\{a\} \in \mathscr{P}(A)$
5. But then, since $\mathscr{P}(A) \subseteq \mathscr{P}(B)$, it follows that $\{a\} \in \mathscr{P}(B)$.
6. This means that $\{a\} \subseteq B$, hence $a \in B$.
7. We've shown that $a \in A$ implies $a \in B$, so therefore $A \subseteq B$. $\blacksquare$

# How to Prove $A = B$
Prove that both $A \subseteq B$ **and** $B \subseteq A$.

## Examples

### Example 1
**Theorem:** $\{n \in \mathbb{Z}: 35 \mid n\}=\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\}$

**Proof:** 
1. First we show $\{n \in \mathbb{Z}: 35 \mid n\} \subseteq\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\}$.
2. Suppose $a \in\{n \in \mathbb{Z}: 35 \mid n\}$.
3. This means that $35 \vert a$, so $a=35c$ for some $c \in Z$. Thus $a=5(7c)$ and $a=7(5c)$.
4. From $a=5(7c)$ it follows that $5 \vert a$, so $a \in\{n \in \mathbb{Z}: 5 \mid n\}$. 
5. From $a=7(5c)$ it follows that $7 \vert a$, so $a \in\{n \in \mathbb{Z}: 7 \mid n\}$.
6. As $a$ belongs to both $\{n \in \mathbb{Z}: 5 \mid n\}$ and $\{n \in \mathbb{Z}: 7 \mid n\}$, we get $a \in\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\}$. Thus we've shown that $\{n \in \mathbb{Z}: 35 \mid n\} \subseteq\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\}$. 
7. Next we show $\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\} \subseteq\{n \in \mathbb{Z}: 35 \mid n\}$
8. Suppose $a \in\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\}$.
9. By definition of intersection, this means that $a \in\{n \in \mathbb{Z}: 5 \mid n\}$ and $a \in\{n \in \mathbb{Z}: 7 \mid n\}$
10. Therefore it follows that $5 \vert a$ and $7 \vert a$.
11. By definition of divisibility, there are integers $c$ and $d$ where $a=5c$ and $a=7d$. 
12. Then $a$ has both $5$ and $7$ as prime factors, so the prime factorization of $a$ must include factors of $5$ and $7$. Hence $5 \cdot 7 =35$ divides $a$, so $a \in\{n \in \mathbb{Z}: 35 \mid n\}$.
13. We've now shown that $\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\} \subseteq\{n \in \mathbb{Z}: 35 \mid n\}$.
14. At this point we've shown that $\{n \in \mathbb{Z}: 35 \mid n\} \subseteq\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\}$ and $\{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\} \subseteq\{n \in \mathbb{Z}: 35 \mid n\}$, so we've proved $\{n \in \mathbb{Z}: 35 \mid n\}= \{n \in \mathbb{Z}: 5 \mid n\} \cap\{n \in \mathbb{Z}: 7 \mid n\}$. $\blacksquare$

### Example 2
