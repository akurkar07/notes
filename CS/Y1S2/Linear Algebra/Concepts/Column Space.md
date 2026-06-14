# Column Space

## Definition

If $A$ is an $m \times n$ matrix, the column space of $A$ is the subspace of $\mathbb{R}^m$ spanned by the columns of $A$.

$$
\operatorname{Col}(A)=\operatorname{Span}\{\text{columns of }A\}.
$$

## Example

If

$$
A=
\begin{pmatrix}
1 & 1\\
1 & 1\\
1 & 1
\end{pmatrix},
$$

then the columns of $A$ are both

$$
\begin{pmatrix}
1\\
1\\
1
\end{pmatrix},
$$

so

$$
\operatorname{Col}(A)=
\operatorname{Span}
\left\{
\begin{pmatrix}
1\\
1\\
1
\end{pmatrix}
\right\}.
$$

This is a line in $\mathbb{R}^3$.

## Why It Matters

The column space is the set of all right-hand sides $\mathbf{b}$ for which the equation $A\mathbf{x}=\mathbf{b}$ is [[Consistent System|consistent]]. In other words, the set of columns and its scalar multiples.

In the example above, the column space is a line in $\mathbb{R}^3$. So:

- if
  $$
  \mathbf{b}=
  \begin{pmatrix}
  2\\
  2\\
  2
  \end{pmatrix},
  $$
  then $\mathbf{b}$ is a scalar multiple of $\begin{pmatrix} 1\\ 1\\ 1 \end{pmatrix},$  so $A\mathbf{x}=\mathbf{b}$ is consistent
- if
  $$
  \mathbf{b}=
  \begin{pmatrix}
  1\\
  2\\
  1
  \end{pmatrix},
  $$
  then $\mathbf{b}$ does not lie on that line, so $A\mathbf{x}=\mathbf{b}$ has no solution

So the column space answers the question: for which vectors $\mathbf{b}$ does $A\mathbf{x}=\mathbf{b}$ have a solution?

## Appears In

- [[2.4 Matrix Equations]]
- [[3.1 Solution Sets and Subspaces]]
- [[3.3 Subspaces]]

## Related

- [[Span]]
- [[Matrix Equation]]
- [[Null Space]]
