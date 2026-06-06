## 1.1 Linear Combinations

A [[Linear Combination|linear combination]] is the sum of vectors multiplied by weights. The linear combination of a single vector (or the sum of colinear vectors) is a line.

### Example in LaTeX:
A linear combination of vectors $\mathbf{v}_1$ and $\mathbf{v}_2$ can be written as:
$$
\mathbf{w} = c_1 \mathbf{v}_1 + c_2 \mathbf{v}_2
$$
where $c_1, c_2 \in \mathbb{R}$.

## 1.2 Vector Equations and Spans

If no solutions exist for a system of equations, that system is called [[Inconsistent System|inconsistent]]. 
If $\geq 1$ solution exists, the system is [[Consistent System|consistent]].

### Spans
A [[Span|span]] represents all [[Linear Combination|linear combinations]] of a set of vectors. 
In symbols:
$$
\text{Span}\{\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_k\} = \{x_1\mathbf{v}_1 + x_2\mathbf{v}_2 + \cdots + x_k\mathbf{v}_k \mid x_1, x_2, \dots, x_k \in \mathbb{R}\}
$$
$$
\text{Span}\{\emptyset\} = \{\mathbf{0}\}
$$

#### Why Do We Need Spans?
Spans are fundamental in linear algebra because they help us understand the structure of vector spaces. For example:
- **Basis and Dimension**: The span of a set of vectors determines the dimension of the space they cover.
- **Applications**: Spans are used in solving systems of equations, understanding transformations, and analysing data in higher dimensions.
- **Later Topics**: Concepts like linear independence, basis, and [[Subspace|subspaces]] build directly on the idea of spans.

##### Note (Consistency and Span)

Here are two ways of saying the same thing:

1. A vector $\mathbf{b}$ is in the [[Span|span]] of $\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_k$.
2. The vector equation $x_1\mathbf{v}_1 + x_2\mathbf{v}_2 + \cdots + x_k\mathbf{v}_k = \mathbf{b}$ is [[Consistent System|consistent]].

Later, we will develop a procedure for answering the question “is $\mathbf{b}$ in the span of $\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_k$?” in every circumstance. This will be a by-product of developing a process to find all the solutions of vector equations.



