# Kernel

## Definition

If

$$
T:\mathbb{R}^n\to\mathbb{R}^m
$$

is a [[Linear Transformation|linear transformation]], then the [[Kernel|kernel]] of $T$ is

$$
\ker(T)=\{\mathbf{x}\in\mathbb{R}^n \mid T(\mathbf{x})=\mathbf{0}\}.
$$

## Why It Matters

The kernel tells us which input vectors get sent to zero.

If $T(\mathbf{x})=A\mathbf{x}$ is a matrix transformation, then

$$
\ker(T)=\operatorname{Nul}(A),
$$

so the kernel is exactly the [[Null Space|null space]] of the standard matrix.

Also:

- $T$ is [[One-to-one Transformation|one-to-one]] if and only if $\ker(T)=\{\mathbf{0}\}$
- a nontrivial kernel means different inputs can have the same output

## Appears In

- [[4.3 Linear Transformations]]
- [[4.6 The Invertible Matrix Theorem]]

## Related

- [[Null Space]]
- [[Linear Transformation]]
- [[One-to-one Transformation]]
- [[Column Space]]
