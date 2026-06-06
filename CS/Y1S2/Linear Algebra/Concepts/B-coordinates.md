# B-coordinates

## Definition

If $B=(\mathbf{v}_1,\dots,\mathbf{v}_m)$ is a [[Basis|basis]] for a subspace $V$, and

$$
\mathbf{x}=c_1\mathbf{v}_1+\cdots+c_m\mathbf{v}_m,
$$

then the coefficients $c_1,\dots,c_m$ are the [[B-coordinates|$B$-coordinates]] of $\mathbf{x}$.

The coordinate vector is

$$
[\mathbf{x}]_B=
\begin{pmatrix}
c_1\\
\vdots\\
c_m
\end{pmatrix}.
$$

## Why It Matters

$B$-coordinates describe a vector relative to a chosen basis instead of the standard basis.

If the columns of a matrix $B$ form a basis, then

$$
\mathbf{x}=B[\mathbf{x}]_B
\qquad\text{and}\qquad
[\mathbf{x}]_B=B^{-1}\mathbf{x}.
$$

## Appears In

- [[3.5 Bases as Coordinate Systems]]
- [[4.7 Invertible Matrices and Coordinate Systems]]

## Related

- [[Basis]]
- [[Dimension]]
- [[Inverse Matrix]]
