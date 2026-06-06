# Projection Matrix

## Definition

A [[Projection Matrix|projection matrix]] is a matrix $P$ that sends each vector to its projection onto a subspace.

For projection onto the column space of a matrix $A$ with independent columns,

$$
P=A(A^TA)^{-1}A^T.
$$

## Why It Matters

Projection matrices give a matrix form of [[Orthogonal Projection|orthogonal projection]].

In least squares, $A\hat{\mathbf{x}}$ is the projection of $\mathbf{b}$ onto $\operatorname{Col}(A)$.

## Appears In

- [[8.3 Orthogonal Projection]]
- [[8.5 The Method of Least Squares]]

## Related

- [[Orthogonal Projection]]
- [[Least Squares]]
- [[Normal Equations]]
- [[Column Space]]
