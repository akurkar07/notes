# Linear Algebra Mock Exam - Additional Practice

This mock is written in the style of the mock exam in `Downloads/comp1043-mock24.pdf`, with fresh questions on similar themes.

Time allowed: 2 hours

Answer all questions.

## Question 1. Matrices, determinants, and diagonalisation

Let

$$
A=
\begin{pmatrix}
1 & 2 & 0\\
0 & 3 & 1\\
0 & 0 & 3
\end{pmatrix}.
$$

1. Compute the characteristic polynomial of $A$. `[5 marks]`
2. Find the eigenvalues of $A$, stating their algebraic multiplicities. `[4 marks]`
3. Find a basis for each eigenspace of $A$. `[8 marks]`
4. Determine whether $A$ is diagonalisable. Justify your answer. `[4 marks]`
5. Compute $\det(A)$ in the fastest sensible way, and explain why your method works. `[4 marks]`

Total: `25 marks`

## Question 2. Linear maps and change of basis

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
T:\mathbb{R}^3 \to \mathbb{R}^3
$$

is determined by

$$
T(u_1)=v_1+v_2,\qquad
T(u_2)=2v_2-v_3,\qquad
T(u_3)=cv_1+v_3,
$$

where $c\in\mathbb{R}$.

1. Determine the $(B,C)$-matrix of $T$. `[6 marks]`
2. Determine the $(B,B)$-matrix of $T$ in the special case that
   $$
   v_1=u_1,\qquad v_2=u_1+u_2,\qquad v_3=u_3.
   $$
   `[7 marks]`
3. For the special case $c=1$, find a basis for the image of $T$ in terms of the $C$-basis vectors. `[6 marks]`
4. For the special case $c=1$, find a basis for the kernel of $T$ in terms of the $B$-basis vectors. `[6 marks]`

Total: `25 marks`

## Question 3. Subspaces, rank, and null spaces

Let

$$
U=\operatorname{Span}\left\{
\begin{pmatrix}
1\\0\\1\\0
\end{pmatrix},
\begin{pmatrix}
0\\1\\1\\0
\end{pmatrix},
\begin{pmatrix}
1\\1\\2\\0
\end{pmatrix}
\right\}
$$

and

$$
V=\left\{
\begin{pmatrix}
x_1\\x_2\\x_3\\x_4
\end{pmatrix}\in\mathbb{R}^4
\;\middle|\;
x_1+x_2-x_3=0,\; x_4=0
\right\}.
$$

1. Find a basis for $U$. `[6 marks]`
2. Find a basis for $V$. `[5 marks]`
3. Determine a basis for $U+V$. `[6 marks]`
4. Determine a basis for $U\cap V$. `[6 marks]`
5. State the dimensions of $U$, $V$, $U+V$, and $U\cap V$, and verify Grassmann's formula in this case. `[2 marks]`

Total: `25 marks`

## Question 4. Short answer and true/false

For each part, answer carefully and justify briefly where appropriate.

1. True or false: Similar matrices always have the same determinant and the same characteristic polynomial. `[3 marks]`
2. True or false: If a $3\times 3$ matrix has eigenvalue $2$ with algebraic multiplicity $3$, then it must be diagonalisable. `[3 marks]`
3. True or false: The column space of an $m\times n$ matrix is a subspace of $\mathbb{R}^n$. `[3 marks]`
4. Give the reduced row echelon form of a $3\times 4$ matrix whose null space has dimension $2$. `[4 marks]`
5. Give an example of a $2\times 2$ matrix that is invertible but not diagonalisable. `[4 marks]`
6. State the relation between rank and nullity for an $m\times n$ matrix. `[2 marks]`
7. Explain why $0$ is an eigenvalue of a square matrix if and only if the matrix is singular. `[3 marks]`
8. Let
   $$
   B=
   \begin{pmatrix}
   0 & -1\\
   1 & 0
   \end{pmatrix}.
   $$
   Compute $B^2$ and state whether $B$ has any real eigenvalues. `[3 marks]`

Total: `25 marks`

## Optional extension questions

These are not part of the `100 marks` above, but they match the same syllabus style.

1. Let
   $$
   A=
   \begin{pmatrix}
   4 & -1\\
   4 & 0
   \end{pmatrix}.
   $$
   Find its eigenvalues and determine whether it is diagonalisable.

2. Show that every $2\times 2$ matrix with a single eigenvalue $\lambda_0$ of algebraic multiplicity $2$ and geometric multiplicity $1$ is similar to
   $$
   \begin{pmatrix}
   \lambda_0 & 1\\
   0 & \lambda_0
   \end{pmatrix}.
   $$

3. Let
   $$
   C=
   \begin{pmatrix}
   0 & 0 & 0 & 0\\
   1 & 1 & 1 & 1\\
   0 & 0 & 0 & 0\\
   1 & 1 & 1 & 1
   \end{pmatrix}.
   $$
   Find its characteristic polynomial and a basis for each eigenspace.
