# Null Space

## Definition

If $A$ is an $m \times n$ matrix, the null space of $A$ is the set of all solutions of the homogeneous equation $A\mathbf{x}=0$.

$$
\operatorname{Nul}(A)=\{\mathbf{x}\in\mathbb{R}^n \mid A\mathbf{x}=0\}.
$$

## Example

If

$$
A=
\begin{pmatrix}
1 & 2 & -1 & 0\\
2 & 4 & 1 & 3\\
0 & 0 & 3 & 3
\end{pmatrix},
$$

then row reducing gives

$$
\begin{pmatrix}
1 & 2 & -1 & 0\\
2 & 4 & 1 & 3\\
0 & 0 & 3 & 3
\end{pmatrix}
\xrightarrow{\text{RREF}}
\begin{pmatrix}
1 & 2 & 0 & 1\\
0 & 0 & 1 & 1\\
0 & 0 & 0 & 0
\end{pmatrix}.
$$

So the equation $A\mathbf{x}=0$ becomes

$$
x_1+2x_2+x_4=0,
$$

$$
x_3+x_4=0.
$$

The pivot variables are $x_1$ and $x_3$. The free variables are $x_2$ and $x_4$.

Let

$$
x_2=s,\qquad x_4=t.
$$

Then

$$
x_1=-2s-t,
\qquad
x_3=-t.
$$

which means

$$
\begin{pmatrix}
x_1\\
x_2\\
x_3\\
x_4
\end{pmatrix}
=
s
\begin{pmatrix}
-2\\
1\\
0\\
0
\end{pmatrix}
+
t
\begin{pmatrix}
-1\\
0\\
-1\\
1
\end{pmatrix}.
$$

Therefore,

$$
\operatorname{Nul}(A)=
\operatorname{Span}
\left\{
\begin{pmatrix}
-2\\
1\\
0\\
0
\end{pmatrix},
\begin{pmatrix}
-1\\
0\\
-1\\
1
\end{pmatrix}
\right\}.
$$

This is a two-dimensional subspace of $\mathbb{R}^4$.

## Why It Matters

The null space is a [[Subspace|subspace]] and describes all homogeneous solutions of a matrix equation.

In the example above, the null space is a two-dimensional subspace of $\mathbb{R}^4$. So:

- if
  $$
  \mathbf{x}=
  \begin{pmatrix}
  -3\\
  1\\
  -1\\
  1
  \end{pmatrix},
  $$
  then $\mathbf{x}$ lies in that null space, so $A\mathbf{x}=0$
- if
  $$
  \mathbf{x}=
  \begin{pmatrix}
  1\\
  0\\
  0\\
  0
  \end{pmatrix},
  $$
  then $\mathbf{x}$ does not lie in that null space, so $A\mathbf{x}\neq 0$

So the null space answers the question: which vectors $\mathbf{x}$ get sent to zero by the matrix $A$?

## Appears In

- [[3.1 Solution Sets and Subspaces]]
- [[3.3 Subspaces]]

## Related

- [[Homogeneous System]]
- [[Solution Set]]
- [[Column Space]]
