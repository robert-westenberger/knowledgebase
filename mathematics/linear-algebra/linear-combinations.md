---
title: Linear Combinations
description: 
published: true
date: 2020-10-19T17:54:34.724Z
tags: mathematics, linear-algebra
editor: markdown
---

# Linear Combinations
Given two vectors v and w, a linear combination of v and w is any vector of the form 
$$\textit{a}\textbf{v}+\textit{b}\textbf{w}$$ 
where a and b are scalars. 

#### Examples
* The vector (6, 8, 10) is a linear combination of vectors (1, 1, 1) and (1, 2, 3) since

$$\begin{bmatrix}
6 \\ 8 \\ 10
\end{bmatrix} =4 \begin{bmatrix}
1 \\ 1 \\ 1
\end{bmatrix} + 2 \begin{bmatrix}
1\\ 2 \\ 3
\end{bmatrix}$$

* The vector (9, 6) can be written as a linear combination of the vectors (1, 2) and (1, -4). We are looking for scalars x~1~ and x~2~ so that 

$$x_1\begin{bmatrix}
1\\ 2 
\end{bmatrix} + x_2\begin{bmatrix}
1 \\ -4
\end{bmatrix} = \begin{bmatrix}
9\\6
\end{bmatrix}$$