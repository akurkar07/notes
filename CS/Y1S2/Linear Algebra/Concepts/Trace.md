# Trace

## Definition

The [[Trace|trace]] of a square matrix $A$ is the sum of its diagonal entries.

It is written

$$
\operatorname{tr}(A).
$$

If

$$
A=
\begin{pmatrix}
a_{11} & a_{12} & \cdots & a_{1n}\\
a_{21} & a_{22} & \cdots & a_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
a_{n1} & a_{n2} & \cdots & a_{nn}
\end{pmatrix},
$$

then

$$
\operatorname{tr}(A)=a_{11}+a_{22}+\cdots+a_{nn}.
$$

## Why It Matters

The trace appears naturally in the characteristic polynomial of a $2\times 2$ matrix:

$$
p_A(\lambda)=\lambda^2-\operatorname{tr}(A)\lambda+\det(A).
$$

It is also preserved under [[Similarity|similarity]].

## Example

For

$$
A=
\begin{pmatrix}
1 & 4\\
2 & 3
\end{pmatrix},
$$

the diagonal entries are $1$ and $3$, so

$$
\operatorname{tr}(A)=1+3=4.
$$

## Appears In

- [[6.2 The Characteristic Polynomial]]
- [[6.3 Similarity]]

## Related

- [[Characteristic Polynomial]]
- [[Determinant]]
- [[Similarity]]
