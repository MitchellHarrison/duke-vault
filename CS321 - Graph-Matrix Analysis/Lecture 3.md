# Lecture 3

> [!definition]
> Let $A_c$ be a **probability transition matrix** where $A \ge 0$. It is such that each column $i$ sums to 1, and each non-zero value in that column represents the probability of traversal from node $i$ to one of its neighbors. We commonly denote it with
> $$
> e^Tx.
> $$
> That is,
> $$
>e^T(b_1, \cdots ,b_{n}) = (\beta_1, \cdots ,\beta_{n}).
>$$
> Matrices with non-negative values with columns that sum to 1 are called **column-stochastic matrices**, and they can always be denoted by $e^TA = e^T$, since all columns sum to 1 and $e$ is a vector of all 1's. Feel free to do the matrix multiplication to show this fact.

We know that $1 \in \lambda(A)$. That is, 1 is an *eigenvalue* of $A$. If this eigenvalue only occurs once (i.e., it has multiplicity 1) and there is a left-eigenvector associated with $\lambda = 1$, then there must exist $Av = 1v$. That is, there is a right-eigenvector such that $v>0$ is $A$ is *reversible*.

> [!note]
> If $A$ is reversible, the graph $G$ that $A$ represents is a connected graph. Thus *if $A$ is irreducible, $G$ is **always** connected.* This right-vector $v$ is called a **Perron-Frobenius vector**, and it is has strictly positive values only.

Let $A^k = X\Lambda^kY^{-1}$ be a diagonalizable matrix such that $k \ge 1$. All eigenvalues exist such that $|\lambda_i| < 1$ except for the *Perron-eigenvalue*, which is $\lambda_{P} = 1$. As $k \rightarrow \infty$, all values less than 1 will approach 0 and all values equal to 1 will remain at 1. 

Let $A$ and $B$ be different column-stochastic matrices. For $t \in[0,1]$,
$$
C(t) = tA + (1-t)B.
$$
That is, if $A$ and $B$ have connected endpoints, any point between them is $C(t)$ for some $t$.

If we let $A$ represent the world-wide web, then $B$ would represent a random jump from $A$. In PageRank words, we can allow ourselves to have probability $t=\alpha$ of jumping somewhere adjacent to our current position and a probability $1-\alpha$ to jumping somewhere random, even somewhere far from our current position. This is the random jumping that the PageRank algorithm did to search for pages to rank. In PageRank's case, $\alpha=0.85$. That is,
$$
C(\alpha) = \alpha A + (1-\alpha)fe^T,
$$
where $(1-\alpha)f$ is specific guidance given to the model as a vector. One concern is that $f$ could be bought by advertisers. While the Google team promised that they wouldn't allow that to happen, the market disagreed, and we are left with what we have now: sponsored search. This $f$ also gives rise to the entire SEO industry.