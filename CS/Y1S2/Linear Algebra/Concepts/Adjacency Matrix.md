# Adjacency Matrix

## Definition

An [[Adjacency Matrix|adjacency matrix]] represents a graph as a square matrix.

If a graph has vertices $v_1,\dots,v_n$, then its adjacency matrix $A$ is the $n\times n$ matrix whose entry $a_{ij}$ records whether there is an edge from $v_j$ to $v_i$.

For an unweighted graph:

$$
a_{ij}=
\begin{cases}
1 & \text{if there is an edge from } v_j \text{ to } v_i,\\
0 & \text{otherwise.}
\end{cases}
$$

For a weighted graph, $a_{ij}$ can store the weight of the edge instead of just $0$ or $1$.

## Example

Suppose a directed graph has vertices $v_1,v_2,v_3$ and edges

$$
v_1\to v_2,\qquad v_1\to v_3,\qquad v_2\to v_3,\qquad v_3\to v_1.
$$

<svg viewBox="0 0 320 240" width="360" role="img" aria-label="Directed graph with vertices v1, v2, and v3">
  <defs>
    <marker id="arrowhead" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" fill="#334155" />
    </marker>
  </defs>
  <line x1="146" y1="60" x2="69" y2="169" stroke="#334155" stroke-width="2" marker-end="url(#arrowhead)" />
  <line x1="174" y1="60" x2="251" y2="169" stroke="#334155" stroke-width="2" marker-end="url(#arrowhead)" />
  <line x1="81" y1="190" x2="239" y2="190" stroke="#334155" stroke-width="2" marker-end="url(#arrowhead)" />
  <path d="M249 174 Q236 88 174 60" fill="none" stroke="#334155" stroke-width="2" marker-end="url(#arrowhead)" />
  <circle cx="160" cy="40" r="22" fill="#f9c74f" stroke="#334155" stroke-width="2" />
  <circle cx="55" cy="190" r="22" fill="#43aa8b" stroke="#334155" stroke-width="2" />
  <circle cx="265" cy="190" r="22" fill="#577590" stroke="#334155" stroke-width="2" />
  <text x="160" y="46" text-anchor="middle" font-size="18" fill="#111827">v1</text>
  <text x="55" y="196" text-anchor="middle" font-size="18" fill="#111827">v2</text>
  <text x="265" y="196" text-anchor="middle" font-size="18" fill="#ffffff">v3</text>
</svg>

Using columns as sources and rows as targets, the adjacency matrix is:

The row and column colours match the vertex colours: each entry is read from the column vertex to the row vertex.

<table style="border-collapse: collapse; text-align: center;">
  <thead>
    <tr>
      <th style="border: none; background: transparent;"></th>
      <th style="background: #f9c74f; color: #111827; padding: 0.4rem 0.7rem;">from v<sub>1</sub></th>
      <th style="background: #43aa8b; color: #111827; padding: 0.4rem 0.7rem;">from v<sub>2</sub></th>
      <th style="background: #577590; color: #ffffff; padding: 0.4rem 0.7rem;">from v<sub>3</sub></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th style="background: #f9c74f; color: #111827; padding: 0.4rem 0.7rem;">to v<sub>1</sub></th>
      <td style="padding: 0.4rem 0.7rem;">0</td>
      <td style="padding: 0.4rem 0.7rem;">0</td>
      <td style="background: linear-gradient(135deg, #577590 0 50%, #f9c74f 50% 100%); color: #111827; padding: 0.4rem 0.7rem;"><strong>1</strong></td>
    </tr>
    <tr>
      <th style="background: #43aa8b; color: #111827; padding: 0.4rem 0.7rem;">to v<sub>2</sub></th>
      <td style="background: linear-gradient(135deg, #f9c74f 0 50%, #43aa8b 50% 100%); color: #111827; padding: 0.4rem 0.7rem;"><strong>1</strong></td>
      <td style="padding: 0.4rem 0.7rem;">0</td>
      <td style="padding: 0.4rem 0.7rem;">0</td>
    </tr>
    <tr>
      <th style="background: #577590; color: #ffffff; padding: 0.4rem 0.7rem;">to v<sub>3</sub></th>
      <td style="background: linear-gradient(135deg, #f9c74f 0 50%, #577590 50% 100%); color: #111827; padding: 0.4rem 0.7rem;"><strong>1</strong></td>
      <td style="background: linear-gradient(135deg, #43aa8b 0 50%, #577590 50% 100%); color: #111827; padding: 0.4rem 0.7rem;"><strong>1</strong></td>
      <td style="padding: 0.4rem 0.7rem;">0</td>
    </tr>
  </tbody>
</table>

Equivalently,

$$
A=
\begin{pmatrix}
0 & 0 & 1\\
1 & 0 & 0\\
1 & 1 & 0
\end{pmatrix}.
$$

For example:

- $a_{21}=1$ because there is an edge from $v_1$ to $v_2$
- $a_{13}=1$ because there is an edge from $v_3$ to $v_1$
- $a_{12}=0$ because there is no edge from $v_2$ to $v_1$

## Why It Matters

Adjacency matrices let us study graphs using matrix operations.

For an unweighted graph, the entry $(A^k)_{ij}$ counts the number of walks of length $k$ from $v_j$ to $v_i$.

So powers of an adjacency matrix connect graph paths to [[4.4 Matrix Multiplication|matrix multiplication]] and [[7.3 Discrete Dynamical Systems|discrete dynamical systems]].

## Appears In

- [[7.1 Basic Graph Theory]]

## Related

- [[Stochastic Matrix]]
- [[Matrix Transformation]]
- [[Eigenvalue]]
