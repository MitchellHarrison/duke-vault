# Spectral Theory and Computation

## Spectral Analysis

Let $A_jx_j = \lambda_jx_j$, where $A$ is a matrix and $x$ is a vector. That is $\lambda_j$ is eigenvalue $j$. Thus, we can see that scaling by $\alpha$ gives:
$$
(\alpha A)x_j = (\alpha\lambda_j)xj.
$$

This scaling is called **spectral scaling** by $\alpha$. We can also **shift** a matrix by a constant $\mu$ by performing
$$
(A+ \mu I)x_j = (\lambda_j + \mu)x_j.
$$
where $I$ is the identity matrix. Here, eigenvectors remain the same.

In linear algebra, we often say that we can transform a space from $x$ to $y$. This is denoted by $T:x \rightarrow y$. In these transformations, we can observe the *span*, which is all possible linear combinations of vector in that space. We will call this span $V$, and denote it with
$$
V = \text{span}\{x_j, j=1:n\}.
$$

Say we want to change space $y$. This will be the same space, but with different basis vectors. We will denote it with
$$
V = \text{span}\{x_j, j=1:n\} = \text{span}\{y_1, \cdots , y_{n}\}.
$$

> [!definition]
> **Spectral information** is what is known as *latent*. Latent information comes from within a system instead of from without. For example, eigenvalues and eigenvectors come from within the structure of a matrix. No outside data, etc. is required.

## Eigenvalue Decomposition (EVD)

This is one type of **spectral decomposition**, because eigenvalues are *latent*. Eigenvalue decomposition is written as 
$$
A = X\Lambda X^{-1},
$$
where $A$ is a square matrix, $X$ is an $n\times n$ matrix where column $i$ is the $i$th eigenvector of $A$, and $\Lambda$ is a diagonal matrix where entry $i$ on the diagonal is the $i$th eigenvalue. We can exponentiate $A$. Observe that
$$
A^2 = X \Lambda X^{-1}X \Lambda X^{-1} = X\Lambda^2X^{-1}.
$$
This works for any exponent $A^{n}$.
