# Linearly Dependent

## Definition

A set of vectors is [[Linearly Dependent|linearly dependent]] if at least one vector in the set is redundant.

Equivalently, the set

$$
\{\mathbf{v}_1,\mathbf{v}_2,\dots,\mathbf{v}_k\}
$$

is linearly dependent if there exist scalars $c_1,c_2,\dots,c_k$, not all zero, such that

$$
c_1\mathbf{v}_1+c_2\mathbf{v}_2+\cdots+c_k\mathbf{v}_k=\mathbf{0}.
$$

## Why It Matters

A [[Basis|basis]] cannot contain redundant vectors, so a linearly dependent spanning set must be reduced before it can become a basis.

If one vector is in the [[Span|span]] of the others, removing it does not change the span.

## Example

The set

$$
\left\{
\begin{pmatrix}
1\\
0
\end{pmatrix},
\begin{pmatrix}
0\\
1
\end{pmatrix},
\begin{pmatrix}
1\\
1
\end{pmatrix}
\right\}
$$

is linearly dependent because the third vector is the sum of the first two.

## Appears In

- [[3.2 Linear Independence]]
- [[3.4 Basis and Dimension]]

## Related

- [[Linear Independence]]
- [[Span]]
- [[Basis]]
