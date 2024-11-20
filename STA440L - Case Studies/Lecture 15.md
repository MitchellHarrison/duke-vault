# Lecture 15 - Causal Inference (1)

We will use the 12 greek olympians as our outcome variable today. For now, we will consider a treatment $A$ taking on values of 0 or 1, and outcome $Y$ taking on values 0 or 1.

We define a **potential outcome** $Y^{a=1}$ as the outcome that *would be observed* if treatment $a=1$ was given (this may not have happened in reality). $Y^{a=0}$ is the potential outcome that would be observed if treatment $a=0$ was given.

These potential outcomes are known as **counterfactuals**. Before treatment $A$ happens, there are two potential outcomes. After $A$ happens, then a counterfactual exists.

> [!definition]
> The **sharp null hypothesis** states that there is no effect for *all* individuals. This is a very strong hypothesis, because most treatments will help at least *some* people. It states that $Y_i^{a=1}=Y_i^{a=0}$ for all $i$.

> [!definition]
> We will also introduce **causal consistency**, which states that the observed outcome $Y$ is related to the observed treatment and counterfactuals by $Y = Y^{a=1}A + Y^{a=0}(1-A)$. This is, in effect, the law of total probability. This is an assumption that we make, but it would be a little ridiculous if the assumption did not hold.

We usually care about some difference in potential outcomes, for instance $Y_i^{a=1}-Y_i^{a=0}$. However, we only get to observe one real-world observation, so we cannot get both $Y^{(\cdot)}$ values for an individual. That is, we only see $A$ and $Y$.

**Inference** occurs when one individual's treatment affects the outcome of another individual. Having no interference is an important part of SUTVA.

> [!definition]
> The **Stable Unit Treatment Value Assumption** (SUTVA) essentially states that there are only two potential outcomes: there is no interference, and that there is only one version of treatment and one version of non-treatment (or that multiple versions of each of these are irrelevant). One example of of having multiple "versions" may be a generic medicine and a brand-name medicine of the same chemistry. There are multiple pills, but their differences are irrelevant, so we maintain SUTVA.

## Average causal effects

Let's now move to average causal effects, defined in terms of expectation. An **average causal effect** is the individual causal effects, averaged across the entire population. Observe that the sharp null hypothesis implies no average causal effect.

We can define the causal risk difference in terms of expectation:
$$
\mathbb{E}\left(Y^{a=1}\right) \ne \mathbb{E}\left(Y^{a=0}\right),
$$
and the *associational* risk difference:
$$
\mathbb{E}\left(Y|A=1\right) - \mathbb{E}\left(Y|A=0\right).
$$
The difference between the two is the key factor of causal inference. We want to know when we state that a treatment is *causal* instead of just *associative*.
