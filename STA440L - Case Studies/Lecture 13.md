# Lecture 13 - Spatial Data

> [!note]
> We can use the `sf` package in R to interact with simple feature data structures, which are used to work with geo-spacial geometries. 

## Neighbors

Counties that are close together spatially may be similar. One definition of "close" is to consider its **neighbors**. A *neighbor* is an observation that is **contiguous** to another (i.e., they share a border or point in common). Observe that closeness does not always mean euclidian space. For example, two cocktails that are otherwise the same except for the type of liquor (e.g., gin vs. vodka martini) may be close in "cocktail space."

> [!definition]
> A **spatial weight matrix** is a square matrix that identifies whether observations are neighbors (or more generally, the adjacency metric between all pairwise relationships).

## Moran's I

We can use a spacial weight matrix to calculate spatial correlation. The most common way of doing so is using **Moran's I**. It is effectively a value (from -1 to 1) that is effectively the correlation formula weighted by the spatial weight matrix. We calculate Moran's I with R using the following code. Here, the data are North Carolina counties (with population values) and 

```R
library(spdep)

# get the weight matrix
sp_wts <- poly2nb(nc, row.names=nc$name, queen = T)

# binary adjacency matrix
sp_mat <- nb2mat(sp_wts, style='B')

# row-standardized adjacency matrix
sp_mat_std <- nb2mat(sp_wts, style='W')

# converts to weight list
sp_mat_list <- nb2listw(sp_wts, style='B')

# calculate Moran's I
moran(nc$partial/nc$pop, sp_mat_list, nrow(nc), sum(sp_mat))
```

Here, positive $I$ values suggest positive spacial correlation (i.e., clustering). To get a p-value for this, we can run the following, which will output a p-value for how confident we are that such clustering exists:

```R
moran.mc(nc$partial/nc$pop, sp_mat_list, nsim = 999)
```

## Spatial regression

We can't do normal linear regression in spatial data because we don't have independence based on geography. A lack of independence normally forbids regression. However, if we fit a model using models that don't have independence due to spatial clustering, we have to check the **clustering of the residuals**. If there is no spatial clustering of residuals, our results are still sound. If there is spatial clustering, we have violated independence and must reject our findings (at least until next lecture).