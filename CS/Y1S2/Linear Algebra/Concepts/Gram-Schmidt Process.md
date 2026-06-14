# Gram-Schmidt Process

## Definition

The [[Gram-Schmidt Process|Gram-Schmidt process]] takes a linearly independent set and constructs an orthogonal, or after normalization orthonormal, set with the same span.

## Why It Matters

It turns awkward bases into cleaner ones that are easier to use for projections and coordinates.

## Example

Starting with

$$
\mathbf{v}_1=
\begin{pmatrix}
1\\
0
\end{pmatrix},
\qquad
\mathbf{v}_2=
\begin{pmatrix}
1\\
1
\end{pmatrix},
$$

we keep

$$
\mathbf{u}_1=\mathbf{v}_1
$$

and subtract the projection of $\mathbf{v}_2$ onto $\mathbf{u}_1$:

$$
\mathbf{u}_2=
\mathbf{v}_2-
\frac{\mathbf{v}_2\cdot \mathbf{u}_1}{\mathbf{u}_1\cdot \mathbf{u}_1}\mathbf{u}_1
=
\begin{pmatrix}
1\\
1
\end{pmatrix}
-
\begin{pmatrix}
1\\
0
\end{pmatrix}
=
\begin{pmatrix}
0\\
1
\end{pmatrix}.
$$

So the resulting orthogonal set is the standard basis.

## Appears In

- [[8.4 Orthogonal Sets]]

## Related

- [[Orthogonal Set]]
- [[Orthonormal Set]]
- [[Orthogonal Projection]]
