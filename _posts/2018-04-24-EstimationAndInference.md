---
layout: post
title: Teaching Myself Variational Inference
categories: Data Science
---

When __shouldn't__ OLS be used? 
1. errors are __correlated__ or have __unequal variance__ (consider a GLM instead)
2. error distribution is long-tailed (robust estimator)
3. Collinearity, then the estimators are biased (ridge regression)

## Goodness of Fit(RSS)
Use solve(A,b) and use crossprod(x,y)

## Inference

We are going to assume errors are normally distributed and i.i.d.: 

$$\epsilon \sim N(0,\sigma^2I)$$

$$ y = X\beta + \epsilon \Rightarrow y \sim N(X\beta, \sigma^2I)$$

Linear combinations of normally distributed variables is again normal, 

$$ \hat{\beta} = (X^TX)^{-1}X^Ty \sim N(\beta, (X^TX)^{-1}\sigma^2)$$

## Hypothesis Tests to Compare Models 
Let $\omega$ indicate small model and $\Omega$ indicate a bigger model. If we want to check which model we prefer, a good test statistic to go buy would be formulated as: 

$$\frac{RSS_{\omega}-RSS_{\Omega}}{RSS_{\Omega}} $$

Likelihood ratio testing produces the same test statistic: 

$$\frac{\max_{\beta, \sigma \in \omega}L(\beta, \sigma, y)}{\max_{\beta, \sigma \in \Omega}L(\beta, \sigma, y)} $$

Since this is a linear model, notice that: 

$$ L (\hat{\beta}, \hat{\sigma}, y) \prop \hat{\sigma}^{-n}$$

If the number of parameters of model $\Omega$ is $p$ and the number of dimensions of the smaller model $\omega$ is of dimension q, then we use the F-statistic: 

$$ F = \frac{(RSS_{\omega}-RSS_{\Omega})/(p-q)}{RSS_{\Omega}/(n-p)} \sim F_{p-q, n-p} $$

__Degrees of Freedom__: the number of observations (data points) - parameters (i.e. $n - p$ or $n -q$).

So the RSS in this degrees of freedom notation is: 
$$ F = \frac{(RSS_{\omega}-RSS_{\Omega})/(df_{\omega}-df_{\Omega})}{RSS_{\Omega}/df_{\Omega}} \sim F_{p-q, n-p} $$

## Testing Examples:
1. Test of all predictors
2. Test just one predictor
3. Test a pair of predictors 
4. Test a subspace
