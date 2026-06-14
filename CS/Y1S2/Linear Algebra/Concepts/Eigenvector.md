# Eigenvector

## Definition

A nonzero vector $\mathbf{x}$ is an [[Eigenvector|eigenvector]] of $A$ if

$$
A\mathbf{x}=\lambda \mathbf{x}
$$

for some scalar $\lambda$.

## Why It Matters

Eigenvectors are directions that a matrix preserves, up to scaling.

They form the basis used in diagonalisation when enough independent eigenvectors exist.

## Example

Let

$$
A=
\begin{pmatrix}
3 & 0\\
0 & 2
\end{pmatrix}.
$$

Then

$$
\begin{pmatrix}
1\\
0
\end{pmatrix}
\quad \text{is an eigenvector with eigenvalue } 3,
$$

because

$$
A
\begin{pmatrix}
1\\
0
\end{pmatrix}
=
3
\begin{pmatrix}
1\\
0
\end{pmatrix}.
$$

Also,

$$
\begin{pmatrix}
0\\
1
\end{pmatrix}
\quad \text{is an eigenvector with eigenvalue } 2.
$$

## Appears In

- [[6.1 Eigenvalues and Eigenvectors]]
- [[6.4 Diagonalisation]]

## Related

- [[Eigenvalue]]
- [[Diagonalisation]]
