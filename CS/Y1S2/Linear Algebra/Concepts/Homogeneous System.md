# Homogeneous System

## Definition

A system of linear equations of the form $Ax = 0$ is called `homogeneous`.

A system of linear equations of the form $Ax = b \quad \text{for } b \neq 0$ is called `inhomogeneous`.

As augmented matrices, these look like:

### Homogeneous Example

$$
\left\{
\begin{aligned}
x_1 + 2x_2 - x_3 &= 0 \\
3x_1 - x_2 + 4x_3 &= 0
\end{aligned}
\right.
\quad \Longrightarrow \quad
\left(
\begin{array}{ccc|c}
1 & 2 & -1 & {\color{orange}0} \\
3 & -1 & 4 & {\color{orange}0}
\end{array}
\right)
$$

### Inhomogeneous Example

$$
\left\{
\begin{aligned}
x_1 + 2x_2 - x_3 &= 5 \\
3x_1 - x_2 + 4x_3 &= -2
\end{aligned}
\right.
\quad \Longrightarrow \quad
\left(
\begin{array}{ccc|c}
1 & 2 & -1 & {\color{orange}5} \\
3 & -1 & 4 & {\color{orange}-2}
\end{array}
\right)
$$

## Why It Matters

A homogeneous system always has the solution $x = 0$, called the `trivial solution`. Any nonzero solution is called `nontrivial`.

Also,

$$
Ax = 0 \text{ has a nontrivial solution}
\Longleftrightarrow
\text{there is a free variable}
\Longleftrightarrow
A \text{ has a column without a pivot position.}
$$

Here, “free variable” refers to [[Free Variable]] and “pivot position” refers to [[Pivot]].

This makes homogeneous systems the natural starting point for understanding [[Solution Set|solution sets]] and [[Subspace|subspaces]].

## Appears In

- [[3.1 Solution Sets and Subspaces]]

## Related

- [[Free Variable]]
- [[Pivot]]
- [[Solution Set]]
- [[Subspace]]
