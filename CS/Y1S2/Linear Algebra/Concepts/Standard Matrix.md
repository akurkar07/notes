# Standard Matrix

## Definition

The [[Standard Matrix|standard matrix]] of a linear transformation is the matrix that represents the transformation using the standard basis.

If

$$
T:\mathbb{R}^n\to\mathbb{R}^m
$$

is linear, then its standard matrix is

$$
A=
\begin{pmatrix}
| & | & & |\\
T(\mathbf{e}_1) & T(\mathbf{e}_2) & \cdots & T(\mathbf{e}_n)\\
| & | & & |
\end{pmatrix},
$$

where $\mathbf{e}_1,\dots,\mathbf{e}_n$ are the standard basis vectors.

## Why It Matters

The standard matrix lets us compute the transformation using ordinary matrix multiplication:

$$
T(\mathbf{x})=A\mathbf{x}.
$$

Its columns are the outputs of the standard basis vectors.

## Appears In

- [[4.3 Linear Transformations]]
- [[4.6 The Invertible Matrix Theorem]]

## Related

- [[Linear Transformation]]
- [[Matrix Transformation]]
- [[Column Space]]
- [[Kernel]]
