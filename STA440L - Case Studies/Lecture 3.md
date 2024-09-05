# Model / Variable Selection

**Things that we are looking for in the case study**
1. Mathematical model with coefficients, independent variables, etc.
2. How did we choose the type of model and the variables included?
3. From the perspective of urban planners, sometimes answers don't come from data. For example "lower housing costs" is different from "build lower-cost housing." The latter may or may not do the former, so be careful.
4. Defend your handling of missing values.

## Lecture Notes

Say we are trying to model FEV1 (the amount of air that one can force from their lungs in one second) based on height and age. Building a linear regression model, neither dependent variable shows $p<0.05$. However, when building two models with one dependent variable each, both models show those variables at $p<0.05$. This is likely due to collinearity between those two variables. In this case, height and age are usually strongly positively correlated to a point. In this study, all participants were teenagers, so that correlation is likely to hold.

> [!definition]
> **Cross-validation** is a common method for choosing a model. Basically, we break our data into multiple smaller datasets, re-fit the same model, and compare results.

> [!note]
> Recall that if the null hypothesis is true, then **p-values should follow a $\text{Uniform}(0,1)$ distribution**.

#### Word of caution

Often, especially when using stepwise variable selection, we run into an issue where we artificially select variables that are significant, even if those variables are only significant by chance in real life. Thus, *stepwise variable selection has a high type-I error rate.*

If we go out and collect our data again, stepwise-selected variables may be completely different each time. So basing our variables may be a dangerous game without outside context.

