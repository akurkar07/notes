# Free Variable

## Definition

A free variable is a variable whose column does not contain a [[Pivot|pivot]].

For example, in the matrix

$$
\left(
\begin{array}{cccc|c}
1 & 0 & {\color{orange}3} & 0 & 7 \\
0 & 1 & {\color{orange}-2} & 0 & 1 \\
0 & 0 & {\color{orange}0} & 1 & 4
\end{array}
\right)
$$

the highlighted third column has no [[Pivot|pivot]], so ${\color{orange}x_3}$ is a free variable.

## Why It Matters

Free variables create families of solutions and lead to [[Parametric Form]]. In a [[Homogeneous System]], the existence of a free variable is equivalent to the existence of a nontrivial solution.

## Appears In

- [[2.2 Gaussian Elim and RREF]]
- [[2.3 Parametric Form]]
- [[3.1 Solution Sets and Subspaces]]

## Related

- [[Pivot]]
- [[Parametric Form]]
- [[Solution Set]]
- [[Homogeneous System]]
