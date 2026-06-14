# Basis

## Definition

Let $V$ be a [[Subspace|subspace]] of $\mathbb{R}^n$. A [[Basis|basis]] of $V$ is a list of vectors in $V$ that:

1. spans $V$
2. is [[Linear Independence|linearly independent]]

So a basis is a spanning set with no redundancy.

## Why It Matters

A basis gives a compact way to describe every vector in a subspace.

For example, the plane

$$
V=
\left\{
\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}
\in\mathbb{R}^3
\mid x+2y=z
\right\}
$$

comes from the homogeneous system

$$
x+2y-z=0,
$$

with augmented matrix

$$
\left(
\begin{array}{ccc|c}
1 & 2 & -1 & 0
\end{array}
\right).
$$

Solving for $x$ gives

$$
x=-2y+z.
$$

So the parametric form in $x,y,z$ is

$$
\left\{
\begin{aligned}
x &= -2y+z\\
y &= y\\
z &= z
\end{aligned}
\right.
$$

and the parametric vector form is

$$
\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}
=
y
\begin{pmatrix}
-2\\
1\\
0
\end{pmatrix}
+
z
\begin{pmatrix}
1\\
0\\
1
\end{pmatrix}.
$$

This shows that every vector in the plane is a linear combination of these two vectors.

So the plane $V$ has basis

$$
\left\{
\begin{pmatrix}
-2\\
1\\
0
\end{pmatrix},
\begin{pmatrix}
1\\
0\\
1
\end{pmatrix}
\right\},
$$

because these two vectors span the plane, and they are not scalar multiples of each other, so they are [[Linear Independence|linearly independent]].

## Appears In

- [[3.4 Basis and Dimension]]
- [[3.5 Bases as Coordinate Systems]]

## Related

- [[Dimension]]
- [[Span]]
- [[Linear Independence]]
- [[Subspace]]
