# Building Statistical Models (2)

## A Second Example

Researchers were interested in seeing how far gorillas were willing to travel for food, specifically fruit (which has high calorie-density compared to other vegetation).

There are two variables they are concerned with: **frugivory** $\beta_1$ (amount of fruit in the diet) and **availability of fruit** $\beta_2$. There was an interaction term between the two represents by $\beta_3$. Here,

$$
\begin{align*}
\beta_2 &= -0.028 \\
\beta_3 &= -0.13.
\end{align*}
$$

For this example, we will ignore $\beta_1$. Then, the predicted travel is given by

$$
\hat{d} = -0.028x_2 - 0.13 x_1x_2.
$$

Thus, a one-unit increase in *availability of fruit*  ($x_2$) would give a predicted change in $d$ of

$$
-0.028 - 0.13x_1,
$$

where $x_1$ is the *frugivory*. The interaction term means that *availability of fruit* variable **cannot be investigated in isolation**.

## A third example

The Association of Television and Video Viewing (ATVV) was studied alongside fast food intake. Researchers were concerned with the relationship between increased screen-time by children and fast food consumption by those children. The outcome variable was an answer to a survey question: *does your child eat at least one fast-food meal per week?* Adjustments were made for the age and sex of the children, the age of the children's caregiver, and the household income of the child.

First, we will write out the logistic regression formula for the results of the study (presented in the course slides). The *odds ratio* for one-unit increase in hours of TV watched was 1.55, which mean we can **interpret** that for each additional hour of TV watched, there is a 1.55-fold increase in the odds that a child consumes fast food that week.

Therefore, in the case of a child that watches three additional hours, the odds go up by $1.55^3$.

> [!definition]
> A **confounding variable** is one (usually not measured) variable that causes changes in the outcome variable *and* a predictor. This confounding relationship would show a statistically significant relationship between the outcome and a predictor, even if there is no causal effect between them. *This is why we can't make causal statements (yet)!*

For the mathematical interpretation of their model (including some additional variables), let

$$
\begin{align*}
x_1 &= \text{hours watched} \\
x_2 &= \text{age (categorical)} \\
x_3 &= \text{sex} \\
x_4 &= \text{caregiver age} \\
x_5 &= \text{household income}
\end{align*}
$$

Say instead that they build a linear model predicting the number of fast food meals consumed. It would take the form of

$$
\hat{y} = \beta_0 + \beta_1x_1 + \beta_2x_2 + \beta_3x_3 + \beta_4x_4 + \beta_5x_5 + \epsilon_i,
$$

Where $\epsilon \overset{\mathrm{iid}}{\sim}N(0, \sigma^2)$. To instead convert this to a logistic regression model (as used in the study), the formula becomes

$$
log \left(\frac{p_i}{1-p_i}\right) = \beta_0 + \beta_1x_1 + 
\beta_2x_2 + \beta_3x_3 + \beta_4x_4 + \beta_5x_5
$$

where $p_i = \mathbb{P}\left(\mathbb{I}(\ge \text{meal}_i\right))$, the probability that child $i$ eats one or more fast-food meals. Observe that **there is no error term**. This is because we are building a Bernoulli model (because a child either does or does not consume a fast-food meal. Because $\mathbb{E}\left(Bern(p))\right)=p$ and the variance is $Var(Bern(p)) = p(1-p)$, if we know the mean, we can find the variance without an error term.

## Notation

Recall that normal linear regression is represented by
$$
\mathbb{E}\left(Y| \mathbf{X}\beta)\right)=\mathbf{X}\beta,
$$

and a **generalized linear model** is a (usually invertable) function of that expectation. That is,

$$
g[\mathbb{E}\left(Y| \mathbf{X}\beta)\right)]=\mathbf{X}\beta.
$$