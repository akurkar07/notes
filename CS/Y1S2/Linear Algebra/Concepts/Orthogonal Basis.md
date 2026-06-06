# Orthogonal Basis

## Definition

An [[Orthogonal Basis|orthogonal basis]] is a basis whose vectors are pairwise orthogonal.

So it must:

- span the subspace;
- be [[Linear Independence|linearly independent]];
- have pairwise dot products equal to $0$.

## Why It Matters

Orthogonal bases make coordinate calculations easier.

If $\{\mathbf{u}_1,\dots,\mathbf{u}_m\}$ is an orthogonal basis for $W$, then the projection of $\mathbf{x}$ onto $W$ is

$$
\operatorname{proj}_W(\mathbf{x})
=
\frac{\mathbf{x}\cdot\mathbf{u}_1}{\mathbf{u}_1\cdot\mathbf{u}_1}\mathbf{u}_1
+\cdots+
\frac{\mathbf{x}\cdot\mathbf{u}_m}{\mathbf{u}_m\cdot\mathbf{u}_m}\mathbf{u}_m.
$$

## Appears In

- [[8.4 Orthogonal Sets]]
- [[8.3 Orthogonal Projection]]

## Related

- [[Orthogonal Set]]
- [[Orthonormal Set]]
- [[Gram-Schmidt Process]]
- [[Orthogonal Projection]]
