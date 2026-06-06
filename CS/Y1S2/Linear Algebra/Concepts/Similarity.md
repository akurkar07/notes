# Similarity

## Definition

Matrices $A$ and $B$ are [[Similarity|similar]] if

$$
A=PBP^{-1}
$$

for some invertible matrix $P$.

## Why It Matters

Similar matrices represent the same linear transformation in different coordinate systems.

## Example

If

$$
B=
\begin{pmatrix}
2 & 0\\
0 & 3
\end{pmatrix},
\qquad
P=
\begin{pmatrix}
1 & 1\\
0 & 1
\end{pmatrix},
$$

then

$$
PBP^{-1}=
\begin{pmatrix}
2 & 1\\
0 & 3
\end{pmatrix}.
$$

So these two matrices are similar.

## Appears In

- [[6.3 Similarity]]
- [[6.4 Diagonalisation]]

## Related

- [[Diagonalisation]]
- [[Basis]]
- [[Inverse Matrix]]
