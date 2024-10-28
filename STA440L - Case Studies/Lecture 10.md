# Lecture 10 - Survival Data

Suppose we had a series of *non-censored* observations $t_1 \cdots t_{n}$ and we thought that these survival times were i.i.d. and came from some distribution with density $f(t)$. **How might we estimate the parameter(s) $\theta$ of that distribution?**

One possible method is to take the MLE such that
$$
\mathcal{L}(\theta|T) = \prod_{i=1}^{n}f(t_i|\theta).
$$

But performing the MLE with censored data requires some special considerations. Because we have the outcome of each observation (whether they failed or not) but not the time-to-failure, we have to use the probability that the failure time (for those that fail) falls after the censoring point. We say that
$$
f(t_i)^{\delta_i}S(t_i)^{1- \delta_i},
$$

Where $S$ is the **survival function**, which denotes the probability of making it to the point in time $t_i$. Thus, an individuals contribution to the likelihood is
thus:
$$
\begin{align*}
f(t_i)^{\delta_i}S(t_i)^{1- \delta_i} &=
\lambda(t_i)^{\delta_i}S(t_i)^{\delta_i}S(t_i)^{1- \delta_i}\\
\Aboxed{&=\lambda(t_i)^{\delta_i}S(t_i)}
\end{align*}
$$

Say we have data with $T \overset{\mathrm{iid}}{\sim}Exp(\lambda)$, where the **hazard** is given by $\lambda$ and the survival function is given by $e^{-\lambda t}$, we would thus have
$$
\mathcal{L}(\lambda|T) = \prod_{i=1}^{n}\lambda^{\delta_i}exp(-\lambda y_i),
$$
where $y_i$ is either censoring time $c_i$ or failure time $t_i$ such that
$$
y_i = \text{min}(t_i, c_i).
$$


## Models

How might we adjust for potential covariates that might be related to our outcome? Is there a way to create a predictive model for survival time? Of course there is, regardless of censorship of the data.

> [!definition]
> An **accelerated failure time (AFT)** model assumes
> $$
> log(T_i) = \beta_0 + \beta_1x_{1i} + \cdots +\beta_px_{\pi}+\epsilon_i.
> $$
> Alternatively, we could exponentiate both sides to arrive at a unit of time $T_i$ instead of $log(T_i)$. For example, if $T$ is time-to-death, a positive $\beta_i$ value means an increase in $\beta_i$ predicts a longer lifespan. Note that for censored data, we would instead be using $Y_i = \text{min}(T_i, C_i)$ as our response.

### Fitting AFT models

We use the `survival` package in R to fit AFT models. For example,
```R
library(survival)
aft_e <- survreg(Surv(t, c) ~ x1 + x2 + x3,
				 data = data, dist = "exponential")
```

### Proportional Hazards Models

A proportional hazards model is given by
$$
\lambda(t) = \lambda_0(t)exp(\beta_0 + \beta_1x_1 + \cdots + \beta_ix_i),
$$
where $\lambda_0$ is the **baseline hazard**, which describes the hazard function for an individual with $\mathbf{X}=\mathbf{0}$. 
> [!definition]
> A **proportional hazards model** is a linear model for the log hazard ratio.

For a one-unit increase in $x_i$, if $\beta_i$ is negative, hazard decreases, which is good for a person in question in time-to-death models. Note that there is no intercept term $\beta_0$ because it is built in to $\lambda_0(t)$

### The Cox proportional hazards model

> [!definition]
> The **Cox proportional hazards model** is given by 
> $$
> \lambda(t) = \lambda_0(t)exp(\beta_0 + \beta_1x_1 + \cdots + \beta_ix_i).
> $$
> It is a proportional hazards model (which is why its formula is identical to the one above. Assuming that there are no tied failure times, suppose we know that there is one failure at time $t_j$. For this failure time, the contribution to the "likelihood" is the probability that individual $j$ fails, *given* that there is exactly one failure in the risk set $\mathcal{R}$ at that time:
> $$
> \mathbb{P}\left(\text{individual $j$ fails}|\text{one failure from } \mathcal{R}(t_j)\right).
> $$

Given that we know someone dies at time $t_j$ and that we don't know which individual it is, the odds of any individual $j$ being the one that dies the probability of person $j$ dying out of the sum of all probabilities of death among all participants. That is,
$$
\frac{\lambda(t_i| \mathbf{X}_j)}{\sum_{k \in \mathcal{R}(t_j)}exp(\mathbf{X}_k^T\beta)}.
$$

#### Fitting the Cox PH model in R

Code to fit a Cox model in R is as follows:

```R
library(survival)
cox <- coxph(Surv(t, c) ~ x1 + x2, data = df)
```
