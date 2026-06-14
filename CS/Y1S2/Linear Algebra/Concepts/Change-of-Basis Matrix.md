# Change-of-Basis Matrix

## Definition

A [[Change-of-Basis Matrix|change-of-basis matrix]] converts coordinate vectors from one basis to another.

If $B=(\mathbf{v}_1,\dots,\mathbf{v}_n)$ is a basis of $\mathbb{R}^n$, then the matrix

$$
P_B=
\begin{pmatrix}
| & | & & |\\
\mathbf{v}_1 & \mathbf{v}_2 & \cdots & \mathbf{v}_n\\
| & | & & |
\end{pmatrix}
$$

converts $B$-coordinates into standard coordinates:

$$
\mathbf{x}=P_B[\mathbf{x}]_B.
$$

## Why It Matters

Changing basis lets us describe the same vector or transformation in a coordinate system that is easier to work with.

The inverse matrix converts standard coordinates back into $B$-coordinates:

$$
[\mathbf{x}]_B=P_B^{-1}\mathbf{x}.
$$

## Appears In

- [[3.5 Bases as Coordinate Systems]]
- [[4.7 Invertible Matrices and Coordinate Systems]]
- [[6.3 Similarity]]
- [[6.4 Diagonalisation]]

## Related

- [[B-coordinates]]
- [[Coordinate Vector]]
- [[Inverse Matrix]]
- [[Similarity]]
