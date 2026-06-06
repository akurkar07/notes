# Eigenvalue

## Definition

A scalar $\lambda$ is an [[Eigenvalue|eigenvalue]] of $A$ if there exists a nonzero vector $\mathbf{x}$ such that

$$
A\mathbf{x}=\lambda \mathbf{x}.
$$

## Why It Matters

Eigenvalues describe the stretch factors of the special directions determined by eigenvectors.

They control diagonalisation and long-term dynamical behaviour.

An eigenvalue can appear more than once as a root of the characteristic polynomial. That count is its [[Algebraic Multiplicity|algebraic multiplicity]].

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
\end{pmatrix},
\qquad
A
\begin{pmatrix}
0\\
1
\end{pmatrix}
=
2
\begin{pmatrix}
0\\
1
\end{pmatrix}.
$$

So the eigenvalues are

$$
3 \quad \text{and} \quad 2.
$$

## Appears In

- [[6.1 Eigenvalues and Eigenvectors]]
- [[6.2 The Characteristic Polynomial]]
- [[6.4 Diagonalisation]]
- [[7.3 Discrete Dynamical Systems]]

## Related

- [[Eigenvector]]
- [[Characteristic Polynomial]]
- [[Diagonalisation]]
- [[Algebraic Multiplicity]]
- [[Geometric Multiplicity]]
