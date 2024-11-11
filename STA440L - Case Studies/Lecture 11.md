# Lecture 11

## Brier Score

> [!definition]
> For binary outcomes, the **Brier score** is simply the MSE of the prediction. A 0 is perfectly predicted and a 1 corresponds to being "perfectly incorrect." The Brier score is given by
> $$
B = \frac{1}{n}\sum_{i=1}^{n}(\hat{p}_i - Y_i)^2.
> $$
> The lower the Brier score, the better. We can calculate it in R by doing the following:
> ```R
> mean((data$preds - data$outcome)^2)
>```

## Chi-square test

Under our null hypothesis $H_0$, we have independence between our predictors and outcome, this implies that joint probabilities should be equal to products of marginal distributions. The **chi-square test** compares the observed frequencies in each cell to the expected count under $H_0$; if the total differences are large enough, we reject $H_0$.

## Fisher's exact test

The chi-square test relies on asymptotic results, which might not be appropriate if we have small cell counts (common rules of thumb are $>5$ or $>10$ in each cell. **Fisher's exact test** calculates an exact p-value under a specific distributional assumption.
