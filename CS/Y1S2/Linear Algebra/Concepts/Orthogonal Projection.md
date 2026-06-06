# Orthogonal Projection

## Definition

The [[Orthogonal Projection|orthogonal projection]] of $\mathbf{x}$ onto a subspace $W$ is the vector in $W$ closest to $\mathbf{x}$.

## Why It Matters

Projection gives the best approximation to a vector from within a subspace.

It is the key geometric idea behind least squares.

## Example

Project

$$
\mathbf{x}=
\begin{pmatrix}
3\\
1
\end{pmatrix}
$$

onto the line spanned by

$$
\mathbf{u}=
\begin{pmatrix}
1\\
1
\end{pmatrix}.
$$

Then

$$
\operatorname{proj}_{\operatorname{Span}\{\mathbf{u}\}}(\mathbf{x})
=
\frac{\mathbf{x}\cdot \mathbf{u}}{\mathbf{u}\cdot \mathbf{u}}\mathbf{u}
=
\frac{4}{2}
\begin{pmatrix}
1\\
1
\end{pmatrix}
=
\begin{pmatrix}
2\\
2
\end{pmatrix}.
$$

## Appears In

- [[8.3 Orthogonal Projection]]
- [[8.5 The Method of Least Squares]]

## Related

- [[Orthogonal Complement]]
- [[Dot Product]]
- [[Column Space]]
- [[Least Squares]]
