# Lecture 7 - Multivariate Models

> [!definition]
> **Multivariate models** are models that have more than one outcome.

If we want to investigate five different response variables, it is tempting to simply five different linear models. But those models will give rise to *a lot* of p-values, and our type-I error rate will be inflated. It would be nice if we could model these responses jointly. In comes the multivariate model.

Suppose we have the model
$$
\mathbf{Y}_{n\times k} = \mathbf{X}_{n\times p}\mathbf{B}_{p\times k} + \mathbf{E}_{n\times k}.
$$

Here $\mathbf{Y}$ is a matrix of the $k$ responses for $n$ observations, $\mathbf{B}$ now represents a matrix of the $p$ parameters estimated for each of the $k$ models, and $\mathbf{E}$ is the matrix of errors for each of the $n$ observations in the $k$ models.

It turns out that the matrix least-squares estimate is
$$
\hat{\mathbf{B}} = (\mathbf{X}^T \mathbf{X})^{-1}\mathbf{X}^T \mathbf{Y},
$$

which is very similar to the univariate least-squares estimator. Observe that when $p > n$, $\mathbf{X}^T \mathbf{X}$ is un-invertible. But when $k>n$, there is actually no problem, neither mathematically nor with quality of models.

There are some assumptions for the multivariate model:
1. Independence
2. Linearity: $\mathbb{E}\left(\mathbf{Y}| \mathbf{X}\right) = \mathbf{X}\mathbf{B}$
3. Constant variance: $Var(\mathbf{E}| \mathbf{X}) = \mathbf{\Sigma}$
4. Normality: $\mathbf{E} \sim N_k(\mathbf{0}, \mathbf{\Sigma})$

> [!note]
> We use the `car::Manova(model)` to do joint significance testing across a multivariate model. We can also use `confint(model)` to get confidence intervals.
