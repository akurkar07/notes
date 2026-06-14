# Subspace

## Definition

A [[Subspace|subspace]] of $\mathbb{R}^n$ is a subset $V$ of $\mathbb{R}^n$ satisfying:

1. `Non-emptiness`: the zero vector is in $V$.
2. `Closure under addition`: if $\mathbf{u}$ and $\mathbf{v}$ are in $V$, then $\mathbf{u}+\mathbf{v}$ is also in $V$.
3. `Closure under scalar multiplication`: if $\mathbf{v}$ is in $V$ and $c$ is in $\mathbb{R}$, then $c\mathbf{v}$ is also in $V$.

A subset of $\mathbb{R}^n$ is just any collection of vectors in $\mathbb{R}^n$.

As a consequence:

- if $\mathbf{v}$ is in $V$, then every scalar multiple of $\mathbf{v}$ is also in $V$
- if $\mathbf{u}, \mathbf{v}$ are in $V$, then every vector in $\operatorname{Span}\{\mathbf{u},\mathbf{v}\}$ is also in $V$
- more generally, if $\mathbf{v}_1,\dots,\mathbf{v}_p$ are in $V$, then $\operatorname{Span}\{\mathbf{v}_1,\dots,\mathbf{v}_p\}$ is contained in $V$
#### Examples

- $\mathbb{R}^n$ is a subspace of itself.
- $\{0\}$ is a subspace of $\mathbb{R}^n$.
- A line through the origin is a subspace.
- A plane through the origin is a subspace.

#### Non-examples

- A line not containing the origin is not a subspace.
- The unit circle is not a subspace.
- The first quadrant in $\mathbb{R}^2$ is not a subspace because it is not closed under scalar multiplication by negative numbers.
- The union of a line and a plane in $\mathbb{R}^3$ is not a subspace because it is not closed under addition.

## Why It Matters

[[Span|Spans]] are important examples of subspaces, and later [[Solution Set|solution sets]] connect naturally to subspace questions.

For example, consider the line

$$
V = \operatorname{Span}\left\{
\begin{pmatrix}
1\\
2
\end{pmatrix}
\right\}
=
\left\{
t
\begin{pmatrix}
1\\
2
\end{pmatrix}
\mid t \in \mathbb{R}
\right\}.
$$

This is a subspace of $\mathbb{R}^2$ because:

- it contains the zero vector when $t=0$
- adding two vectors on the line keeps you on the line
- multiplying a vector on the line by a scalar keeps you on the line

By contrast, the shifted line

$$
\left\{
\begin{pmatrix}
1\\
0
\end{pmatrix}
+
t
\begin{pmatrix}
1\\
2
\end{pmatrix}
\mid t \in \mathbb{R}
\right\}
$$

is not a subspace, because it does not pass through the origin.

This idea becomes especially important in [[3.3 Subspaces]], where [[Column Space|column spaces]] and [[Null Space|null spaces]] are introduced as standard examples of subspaces.

## Appears In

- [[1 Vectors & Spans]]
- [[3.1 Solution Sets and Subspaces]]
- [[3.3 Subspaces]]

## Related

- [[Span]]
- [[Solution Set]]
- [[Column Space]]
- [[Null Space]]
