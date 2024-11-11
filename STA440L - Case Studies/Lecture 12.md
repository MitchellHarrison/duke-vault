# Lecture 12

## Ordinal regression

Say we have a pain survey post-surgery that is on an ordinal scale from 1 to 10. These are "numbers," but they don't necessarily have a linear relationship. That is, a 6 isn't necessarily exactly twice as severe as a 3. However, even if the data isn't linear, it is certainly ordered. We are trying to measure the effect of a licorice mouthwash being given for throat pan after surgery.

There are some problems using an ordinary least squares (OLS) regression for this use case. We can instead use a broad class of models called **cumulative link models**. Logistic regression is also a member of this class.

We might consider an outcome $Y$ that looks at all ooutcomes at once. For $j$ total ordered categories, we might model the cumulative probability for observation $i$:
$$
\begin{align*}
\gamma_{ij}&=\mathbb{P}\left(Y_i\le j\right) \\
&= \mathbb{P}\left(Y_i=1\right) + \cdots + 
\mathbb{P}\left(Y_i=j\right)
\end{align*}
$$
> [!note]
> Note that $\gamma_{ij}$ is limited to values from 0 to 1, as it is a probability. We might consider a model
> $$
> logit(\gamma_{ij}) = \beta_{0j} + \beta_1x_{i1} + \cdots 
> + \beta_px_{ip}.
> $$

 In this model, the $B_{0j}$ term represents the log odds of being in category $j$ if all other $\beta$ terms are 0. The $\beta_1$ through $\beta_p$ terms signify that, for a one-unit increase in $x_i$, there is an increase of $\beta_i$ in the log-odds of being in category $j$.

Crucially, **we do not index the non-intercept terms by $j$**. This is due to the *proportional odds assumption*: we assume the relationship between all thresholds are proportionate to one another. That is, no matter how we split the data into two thresholds (e.g., "3 and above" and "2 and below"), the $\beta$ terms (other than the intercept) stay the same.

### Coding the model

To fit an ordinal regression model, we use the `MASS` package.

```R
model <- MASS:polr(y ~ x_1 + x_2, data = data)
```

To see the exponentiated coefficients, we run

```R
exp(coef(model))
```

## Multinomial regression models

We can extend our regression further to look at response variables that are categorical but non-ordered. Say we want to predict the type of diet for some number of alligators. We have three possible categories of diet: fish, invertebrates, or other (usually mammals or birds). We want to know if we can predict the dietary preferences of an alligator based on its weight and sex.

Enter **multinomial regression**. In effect, we pick a baseline category (e.g., fish) and do a logistic regression for all other categories. In this case, we would have "fish vs invertebrates" and "fish vs other". Note that we never compare "fish vs fish," and so for a response variable with $k$ categories, we will build $k-1$ models.

We make an assumption here: we assume that the probability of being in category $A$ or $B$ shouldn't depend on whether or not category $C$ is an option. The important part of this assumption is the odds ratio. For example, if $A$ and $B$ are the only options that the population is split $50:50$, if we add $C$ as an option, if the $A:B:C$ odds are $25:25:50$, that's fine, because the ratios $50:50$ and $25:25$ are equivalent. This assumption is the **relevance of independent alternatives**.