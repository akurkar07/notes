# Least Squares

## Definition

The [[Least Squares|least-squares]] problem seeks $\hat{\mathbf{x}}$ minimizing

$$
\|A\mathbf{x}-\mathbf{b}\|.
$$

## Why It Matters

It gives the best approximate solution when $A\mathbf{x}=\mathbf{b}$ is inconsistent.

## Example

If

$$
A=
\begin{pmatrix}
1\\
1
\end{pmatrix},
\qquad
\mathbf{b}=
\begin{pmatrix}
1\\
3
\end{pmatrix},
$$

then the least-squares solution solves

$$
A^TA\hat{x}=A^T\mathbf{b}.
$$

This gives

$$
2\hat{x}=4,
\qquad
\hat{x}=2.
$$

## Appears In

- [[8.5 The Method of Least Squares]]

## Related

- [[Orthogonal Projection]]
- [[Column Space]]
- [[Dot Product]]
