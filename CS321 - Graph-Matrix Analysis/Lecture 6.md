# Lecture 6

Say we have a constant $\alpha \in \mathbb{C}$ such that $|\alpha| < 1$. With some light series analysis, we can arrive at the summation $S$,
$$
S_k = 1 + \alpha + \cdots + \alpha^k = \frac{1- \alpha^{k+1}}{1 - \alpha}.
$$

Observe that as $k \rightarrow \infty$, the solution goes to $\frac{1}{1-\alpha}$. We can do something similar with matrices, assuming that $A \ne I$:

$$
\begin{align*}
S_k &= I + A + \cdots + A^k \\
(I-A)S_k &= I - A^{k+1} 
\end{align*}
$$

Assuming that $A$ has a radius $\rho(A) < 1$ and that $(I - A)^{-1}$ exists, we can see that $I - A^{k+1} \rightarrow I$ as $k \rightarrow \infty$. Equivalently,

$$
(I-A)\sum_{k=1}^{\infty}A^k = I.
$$

Because $S_k = \sum_{k=1}^{\infty}A^k$, we can see that $S_k$ is the inverse of $(I-A)$, because multiplying them together results in the identity matrix $I$. In a graph context, $S_k$ represents the possible results of a $k$-step walk.

