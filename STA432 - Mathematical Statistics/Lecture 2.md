# Intro to Point Estimation

We have some data $X$ that are being collected, and we want to learn something about from where the data are generated. First, we need to aggregate our data.

> [!definition]
> Let $X_1\cdots,X_{n}$ be observable random variables of interest. Then $T=\delta$ is some function of $\mathbf{X}$ is a **statistic** where $\delta$ is a real-values function. Note that statistics *cannot* be a function of any unknown values.

## Statistics
Let $X \sim N(\mu, \sigma^2)$. $X$ *is* a statistic, because the function $\delta = X$ (i.e., the identity function) returns $X$. Thus, random variables are statistics. Crucially, all statistics are also random variables.

Let $X_1, \cdots, X_{n} \overset{\mathrm{iid}}{\sim} N(\theta, \sigma^2)$. Say we know $\sigma^2$ but $\theta$ is unknown. Let $\bar X$ be the mean,
$$
\bar X = \frac{1}{n} \sum_{i=1}^{n}X_i.
$$
This is also a statistic, as it is a real-valued function of known quantities. Similarly, the *median* is a statistic. However, the function
$$
\frac{\hat{X}-\mu}{\sigma/\sqrt{n}}
$$
is **not** a statistic. Because $\mu$ is unknown in our case, a function that contains it cannot be a statistic. However, if there was no $\mu$ in the function, because $\sigma$ and $n$ are known, that would be a statistic.

> [!note]
> *Constants* are statistics as well, just not typically very useful ones.

## Point estimation
> [!definition]
> **Point estimation** of parameters $\theta$, where $\theta$ is assumed to be unknown but has a *true* fixed value. We construct these using estimators for $\theta$ that take the form
> $$
> \theta = \hat{\theta} = \delta(\mathbf{X}),
> $$
> where $\delta$ is a function of the data $\mathbf{X}$.

### Point estimator example
Let $X_1, \cdots, X_{n} \overset{\mathrm{iid}}{\sim}N(\mu, \sigma^2)$. Our unknown parameter of interest $\theta$ is $\mu$. One possible estimator of $\theta$ is $\bar X$, the mean of the observed data. Another would be a firm integer guess, like 5. Thus we can say,
$$
\begin{align*}
\delta_1(\mathbf{X}) &= \bar X \\
\delta_2(X) &= 5.
\end{align*}
$$
But how do we know which of these estimators is "better"? We need to calculate both *accuracy* and *precision* for each, then compare them.
> [!definition]
> **Accuracy** tells us how often, on average, we get the correct values of $\theta$. That is,
> $$
> E[\delta(\mathbf{X})|\theta] - \theta
> $$
> should be as small as possible.

> [!definition]
> **Variance** describes the variability of our estimator. This is represented by
> $$
> Var(\delta(\mathbf{X})|\theta),
> $$
> and should be as small as possible. 

However, both accuracy and variance are conditional on the true parameter $\theta$. Thus, these quantities are not calculable directly. Thus, we introduce the concept of **loss**.

# Loss
We want estimators that are close to the unknown true parameter $\theta$. But there could be any number of possible values for $\theta$.

> [!definition]
> **Closeness** describes how much we are willing to "pay" to be $\ell(\theta,a)$ away from the true value of $\theta$. Here,
> $$
> \ell(\theta,a)
> $$
> is the **loss function**

For example, if we let $\ell$ be
$$
\ell(\theta,a) = (\theta-a)^2,
$$
this is the *squared-error loss* function. The expected value of this function is the **mean-squared error**, or MSE. Also, importantly, **risk** is defined as
$$
R_\delta(\theta) = \mathbb{E}_{X|\theta}[\ell(\theta, \delta(\mathbf{X}))].
$$
That is, the expected loss given a loss function $\ell$.

## Accuracy / Precision example
