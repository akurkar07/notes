# Diagonalisation

## Definition

A matrix is [[Diagonalisation|diagonalisable]] if

$$
A=PDP^{-1}
$$

for some diagonal matrix $D$ and invertible matrix $P$.

That means $D$ has the form

$$
\begin{pmatrix}
{\color{orange} *} & 0 & \cdots & 0\\
0 & {\color{orange} *} & \cdots & 0\\
\vdots & \vdots & \ddots & \vdots\\
0 & 0 & \cdots & {\color{orange} *}
\end{pmatrix},
$$

with zeros off the diagonal.

## Why It Matters

Diagonalisation makes powers of matrices and dynamical systems much easier to analyse.

## Example

For

$$
A=
\begin{pmatrix}
3 & 0\\
0 & 2
\end{pmatrix},
$$

the matrix is already diagonal, so it is diagonalisable with $P=I$ and $D=A$.

Then

$$
A^k=
\begin{pmatrix}
3^k & 0\\
0 & 2^k
\end{pmatrix}.
$$

## Appears In

- [[6.4 Diagonalisation]]
- [[7.3 Discrete Dynamical Systems]]

## Related

- [[Similarity]]
- [[Eigenvalue]]
- [[Eigenvector]]
