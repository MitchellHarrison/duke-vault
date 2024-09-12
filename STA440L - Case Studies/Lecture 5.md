# Generalized Linear Models

## Bayesian modeling

Choosing our prior is the first task of Bayesian regression. In the case of our mini case study where we were predicting quality of life scores, we need a prior for our intercept term. Although the ordinal scores (1-5) can never be positive, the *intercept* term could very well be. So, we shouldn't choose a prior that only has non-negative support.

Say we want to use a normal prior. We may also want to choose a **hyperprior**. That is, a distribution over one of the parameters of our normal prior. For $\sigma^2$, we would have to choose a prior that has non-negative support because variance cannot be negative. Similar support considerations should be made for each of our prior choices.

## Generalized Linear Models

A generalized linear model is a broad and flexible class of models consisting of three components:
1. An assumed distribution of the outcome $Y$ (which follows an *exponential family*).
2. The linear predictor $\mathbf{X}\beta$ consisting of observed covariates and unknown parameters of interest.
3. An invertible **link function** $g$ relating the conditional expectation of $Y$ with the linear predictor
$$
\mathbb{E}\left(Y| \mathbf{X}\right) = g^{-1}(\mathbf{X}\beta).
$$

### Link Functions

The easiest example of link functions is with logistic regression. We know that our response has some distribution such that $Y \sim Bern(p)$, and $\mathbb{E}\left(Y\right)=p$. To relate $p$ (which we are trying to estimate) to the model $\mathbf{X}\beta$, we use the *logit function*
$$
log \left(\frac{p}{1-p}\right).
$$

This function gives us the last piece of our model:
$$
log \left(\frac{p}{1-p}\right) = \mathbf{X}\beta.
$$

Because the logit function lets our $p$ interface with our model (instead of modeling $p = \mathbf{X}\beta$ directly), we call it the **link function**. In this case, $p = \mathbf{X}\beta$ *is* a valid GLM (where $g(p) = p$), but it could result in predicted values of $p$ that are outside of the range $[0,1]$. Since $p$ is a probability, these results are invalid. 

> [!note]
> The model $p = \mathbf{X}\beta$ is a **linear probability model**, and is sometimes fit. It has some nice interpretations (predicted effects on probability for one-unit change in $X_i$), but is less common than logistic regression.
