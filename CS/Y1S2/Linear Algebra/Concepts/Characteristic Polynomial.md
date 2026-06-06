# Characteristic Polynomial

## Definition

The [[Characteristic Polynomial|characteristic polynomial]] of a square matrix $A$ is

$$
p_A(\lambda)=\det(A-\lambda I).
$$

For a $2\times 2$ matrix, this can be written as

$$
\lambda^2-\operatorname{tr}(A)\lambda+\det(A).
$$

Here $\operatorname{tr}(A)$ is the [[Trace|trace]] of $A$.

## Why It Matters

Its roots are the [[Eigenvalue|eigenvalues]] of $A$, so it converts the eigenvalue problem into a determinant computation.

## Example

For

$$
A=
\begin{pmatrix}
2 & 0\\
0 & 5
\end{pmatrix},
$$

we get

$$
p_A(\lambda)=
\det
\begin{pmatrix}
2-\lambda & 0\\
0 & 5-\lambda
\end{pmatrix}
=(2-\lambda)(5-\lambda).
$$

So the eigenvalues are $2$ and $5$.

## Appears In

- [[6.2 The Characteristic Polynomial]]
- [[6.5 Complex Eigenvalues]]

## Related

- [[Determinant]]
- [[Eigenvalue]]
- [[Diagonalisation]]
