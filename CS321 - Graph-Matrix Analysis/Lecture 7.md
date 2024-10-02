# Lecture 7

## The Graph Laplacian

Let us define a graph $G(V,E,W)$ where $W$ is the **weight**. This graph will be undirected. We will define the adjacency matrix as
$$
A:\; A(i,j) > 0 \iff (i,j) \in E.
$$

We can also define matrix $B$:

$$
B(:,\ell) = \pm (e_i - e_j), \; \ell = (i,j)\in E.
$$

We also have the *diagonal matrix* $D$ such that $D = \text{diag}(d)$ contains the degrees on the diagonal. We will define a new matrix $L$, which we will call the **Laplacian Matrix**.

> [!definition]
> **Weights** map each edge with a real number value (this is that edge's weight). That is, $W:E \rightarrow \mathbb{R}$. Because we will deal with graphs with positive weights, we can say that $W:E \rightarrow \mathbb{R}_+$.

> [!note]
> If a graph is unweighted, $W = 1$ for all edges.

The laplacian matrix $L$ can be formed by $L=BB^T$. Alternatively (but equivalently), we can say that $L = D-A$. That is,
$$
L = BB^T = D-A.
$$
