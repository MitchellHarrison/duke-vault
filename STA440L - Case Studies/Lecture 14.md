# Lecture 14

## Spatial Linear Regression (cont'd)

We previously discussed that as long as the **residuals** are not spatially clustered, our model's assumptions still hold. However, we cannot just calculate Morans $I$ for residuals (for unimportant mathematical reasons), so we use a different function for residuals as follows:

```R
lm.morantest(model, sp_wts_list, alternative = "two.sided")
```

There are two main ways of dealing with spatial dependence in regression models: spatial error models, and spatial lag models.

**Spatial error models**: assume the error terms are correlated; however, independence may still be reasonable - perhaps the residuals are correlated due to an unmeasured confounding variable (and were to measure them, no longer have issues with spatial dependency). It is given by
$$
Y = \mathbf{X}\beta + \lambda \mathbf{W}\mathbf{u} + \epsilon.
$$

**Spatial lag models**: independence of observations is violated due to some underlying spatial process - perhaps the *outcome itself* is associated with the outcome in neighboring spatial areas (and must be handled by incorporating spatial lag as a predictor). It is given by:
$$
Y = \rho \mathbf{W}Y + \mathbf{X}\beta = \epsilon.
$$

We can check which of these two apply by running the following tests:
```R
lm.LMtests(m1, sp_wts_list, test = c("RLMerr", "RLMlag"))
```

We can also test for *both* spatial error dependency and spatial lag with a SARMA test:

```R
lm.LMtests(model, sp_wts_list, test = c("SARMA"))
```

> [!note]
> Running a SARMA test will effect your standard error by reducing the degrees of freedom because we are estimating more predictors.

### Fitting a spatial lag model

```R
model_lag <- lagsarlm(y ~ x1 + x2, data = data, listw = sp_wts_list)
```

To interpret that model, we can run the following. Note that this interpretation is a little tricky because each outcome is used in the model twice: once for the direct effect and once for the indirect effects. That is, once in the $\beta$ term and once in the $\rho \mathbf{W}Y$ term. This will output both the direct and indirect effect, as well at the `total`, which is the traditional "for a one-unit increase in $X_i$" type of interpretation of linear regression coefficients:

```R
sp_wts_sparce <- as(sp_wts_list, "CsparseMatrix")
traces <- trW(sp_wts_sparce, type="MC")
m2_decomp <- impacts(m2, tr = traces, R = 1000)
m2_decomp
```

### Fitting a spatial error model

Fitting an error model is done with the following:

```R
m3 <- errorsarlm(y ~ x1 + x2, data = data, listw = sp_wts_list)
```

The interpretation is the same as standard linear regression interpretations.