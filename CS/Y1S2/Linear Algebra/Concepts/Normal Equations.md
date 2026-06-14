# Normal Equations

## Definition

The [[Normal Equations|normal equations]] are the equations used to find a least-squares solution to

$$
A\mathbf{x}=\mathbf{b}.
$$

They are

$$
A^TA\hat{\mathbf{x}}=A^T\mathbf{b}.
$$

## Why It Matters

When $A\mathbf{x}=\mathbf{b}$ is inconsistent, the normal equations find the vector $\hat{\mathbf{x}}$ that makes $A\hat{\mathbf{x}}$ as close as possible to $\mathbf{b}$.

Geometrically, $A\hat{\mathbf{x}}$ is the [[Orthogonal Projection|orthogonal projection]] of $\mathbf{b}$ onto the [[Column Space|column space]] of $A$.

## Appears In

- [[8.5 The Method of Least Squares]]

## Related

- [[Least Squares]]
- [[Transpose]]
- [[Orthogonal Projection]]
- [[Column Space]]
