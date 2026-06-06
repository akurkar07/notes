# Linear Algebra Mock Exam - Fresh Practice

This mock is written in the style of `comp1043-mock24.pdf`, with fresh questions on the same broad themes.

Time allowed: 2 hours

Answer all questions.

## Question 1. Determinants, eigenvalues, and diagonalisation

Let

$$
A=
\begin{pmatrix}
4 & 1 & 0\\
0 & 4 & 0\\
0 & 0 & 2
\end{pmatrix}.
$$

1. Compute the characteristic polynomial of $A$. `[5 marks]`
2. Find the eigenvalues of $A$, stating their algebraic multiplicities. `[4 marks]`
3. Find a basis for each eigenspace of $A$. `[8 marks]`
4. Determine whether $A$ is diagonalisable. Justify your answer. `[4 marks]`
5. Compute $\det(A)$ in the fastest sensible way, and explain why your method works. `[4 marks]`

Total: `25 marks`

## Question 2. Linear maps and coordinates

Suppose that

$$
B=(u_1,u_2,u_3)
$$

is a basis for $\mathbb{R}^3$ and

$$
C=(v_1,v_2,v_3)
$$

is another basis for $\mathbb{R}^3$.

A linear map

$$
T:\mathbb{R}^3\to\mathbb{R}^3
$$

is determined by

$$
T(u_1)=2v_1-v_2,\qquad
T(u_2)=v_1+v_2+v_3,\qquad
T(u_3)=av_1+2v_3,
$$

where $a\in\mathbb{R}$.

1. Determine the $(B,C)$-matrix of $T$. `[6 marks]`
2. Determine the value of $a$ for which this matrix is singular. `[6 marks]`
3. For the value of $a$ found in part 2, find a basis for the image of $T$ in terms of the $C$-basis vectors. `[6 marks]`
4. For the value of $a$ found in part 2, find a basis for the kernel of $T$ in terms of the $B$-basis vectors. `[7 marks]`

Total: `25 marks`

## Question 3. Subspaces, sums, and intersections

Let

$$
U=
\left\{
\begin{pmatrix}
x_1\\x_2\\x_3\\x_4
\end{pmatrix}
\in\mathbb{R}^4
\;\middle|\;
x_1-x_2+x_4=0,\; x_3=0
\right\}
$$

and

$$
V=\operatorname{Span}\left\{
\begin{pmatrix}
1\\0\\1\\-1
\end{pmatrix},
\begin{pmatrix}
0\\1\\1\\1
\end{pmatrix},
\begin{pmatrix}
1\\1\\2\\0
\end{pmatrix}
\right\}.
$$

1. Find a basis for $U$. `[5 marks]`
2. Find a basis for $V$. `[5 marks]`
3. Determine a basis for $U+V$. `[7 marks]`
4. Determine a basis for $U\cap V$. `[6 marks]`
5. State the dimensions of $U$, $V$, $U+V$, and $U\cap V$, and verify Grassmann's formula in this case. `[2 marks]`

Total: `25 marks`

## Question 4. Short answer and true/false

For each part, answer carefully and justify briefly where appropriate.

1. True or false: If a square matrix has determinant $0$, then $0$ is an eigenvalue. `[3 marks]`
2. True or false: If two matrices are similar, then they have the same eigenvalues with the same algebraic multiplicities. `[3 marks]`
3. True or false: The row space of an $m\times n$ matrix is a subspace of $\mathbb{R}^m$. `[3 marks]`
4. Give an example of a $3\times 3$ matrix with nullity $1$. `[4 marks]`
5. Give an example of a $2\times 2$ real matrix with no real eigenvalues. `[4 marks]`
6. State the rank-nullity theorem for an $m\times n$ matrix. `[2 marks]`
7. Explain why a set containing the zero vector cannot be linearly independent. `[3 marks]`
8. Let
   $$
   P=
   \begin{pmatrix}
   1 & 1\\
   0 & 1
   \end{pmatrix}
   \qquad\text{and}\qquad
   D=
   \begin{pmatrix}
   2 & 0\\
   0 & 5
   \end{pmatrix}.
   $$
   Compute $PDP^{-1}$. `[4 marks]`

Total: `25 marks`

## Optional extension questions

These are not part of the `100 marks` above, but they match the same syllabus style.

1. Let
   $$
   M=
   \begin{pmatrix}
   1 & 2 & 0\\
   0 & 1 & 0\\
   0 & 0 & 3
   \end{pmatrix}.
   $$
   Find the eigenvalues of $M$ and determine whether $M$ is diagonalisable.

2. Let
   $$
   A=
   \begin{pmatrix}
   1 & 2 & 1\\
   0 & 1 & -1
   \end{pmatrix}.
   $$
   Find bases for the column space and null space of $A$.

3. Let $W=\operatorname{Span}\{(1,1,0)^T,(1,-1,0)^T\}$. Find the orthogonal projection of $(2,4,3)^T$ onto $W$.
