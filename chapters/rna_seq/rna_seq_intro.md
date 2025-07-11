# Identifying differentially expressed genes using RNA-seq

## RNA-seq and the data-generation process

## Read counts as proxy for gene expression level

## Linear model for one gene
Although RNA-seq can measure the expression of all genes, we build separate a model for each gene.
Consider a gene $g$ and the simple case where there are two conditions, say diseased vs. healthy.
Let $Y_g$ be the random variable representing read count (normalized by sequencing depth). 
Let $x$ be an indicator variable (1 for diseased and 0 for healthy). 
Then we can use the linear model idea from earlier (TODO link) :
```{math}
E[Y_g] = \beta_{0} + \beta_{1} x
Var (Y_g) = ${\sigma}^2$.
```
As is, this model violates some of the assumptions of the simple linear model.
First, $Y_g$ represents discrete counts and so violates the assumption of the response variable following a normal distribution. 
Next, as is typical with count data, the variance of $Y_g$ is greater for larger values of $Y_g$.

## Linear model with transformed response

## Generalized linear model


## Multiple testing correction


