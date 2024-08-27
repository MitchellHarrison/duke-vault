# Building Statistical Models (1)

## Example 1

Scientists build a linear regression model to see if reaction time is impacted by exposure to cadmium. Age and sex is recorded, and the possible ages are only 10, 11, and 12. The formula for this model predicts to $\ln(C)$, where $C$ is exposure in $\frac{ug}{g}$ of blood. The model took the form

$$
y_i = \beta_0 + \beta_1x_{1i} + \beta_2x_{2i} + \beta_3x_{3i} + \epsilon_i
$$

where $\epsilon_i \overset{\mathrm{iid}}{\sim}N(0,sig^2)$.

$$
\begin{align*}
y_i &= \text{reaction time} \\
x_{1i} &= \ln(C) \\
x_{2i} &= \text{age}\\
x_{3i} &= \mathbb{I}(\text{sex = male}).
\end{align*}
$$

Importantly, when writing this model, we must include some key things:
1. The subscript $i$'s (unless we write the function in matrix form).
2. The error term $\epsilon$ (unless we denote estimates with $\hat{y}$, $\hat{\beta_0}$, etc.).
3. The distribution of the error terms $\epsilon_i \overset{\mathrm{iid}}{\sim} N(0,sig^2)$, with no subscript $i$ on the $sig^2$, and ensuring all error terms are i.i.d. (this holds with normality assumptions being met).

The model found $\beta_1 = 4.42$. To **interpret this coefficient**, we will say that for every $e$-fold increase in cadmium concentration, we expect the predicted reaction time to increase by 4.42 milliseconds, *controlling for age and sex*. In mathematical notation,

$$
\mathbb{E}\left(y_i | \mathbf{x}\right) = \beta_0 + 4.42 \ln(C) + \cdots .
$$

Researchers found a p-value of $p=0.58$. Thus, we can say that (assuming a significance level of $\alpha = 0.05$) that we reject the null hypothesis that there is an impact on reaction time by cadmium concentration *controlling for age and sex*.

## Mini case study assignment

This assignment is due Thursday. We'll connect our GitHub to Gradescope to submit. We will investigate the Durham Community Survey from 2022 (on course GitHub) to answer questions provided in the repository.

*This assignment has a **maximum** page count of 3 typed pages, including visualizations, etc.*
