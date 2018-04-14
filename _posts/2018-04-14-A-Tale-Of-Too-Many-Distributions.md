---
layout: post
title: Too Many Distributions!!
categories: Data Science
---

## Normal Distributions
Question: how do you tell how close a sample is to the normal distribution? 

Visually? Use a QQ-plot! What does a QQ-plot do?
1. sorts z-scores from Low to High
2. plots z-scores on y-axis
3. x-axis is the coresponding quantile of a normal distribution for that value's rank. It's like sorting and then x-axis gives the ranking
4. If it roughtly lies along the diagonal line, then there's a good chance it's normal. This means that there is a 1-1 correspondence between 
z-score and quantile which makes perfect sense

## Long-Tailed Distributions/heavy tailed
How can you tell if your sample has long tail? How can you tell if your data is "normal in the middle", but with much longer tails?
Again! A QQ-plot!!

When points are far below the line for low values and far above the line for high values, this means that you should expect extreme values much more. 
Why is this true? Well if the lower quantiles lie far below the diagonal this means 

## Student's t-Distribution
Normally shaped, but with __thicker__ and __longer__ tails. 

Why are they useful/why should we care?: Well distirbutions of sample means are typically shaped like a t-distribution! You fit a t-distribution to your distribution of sample means depending on how large the sample is. 
What question does it answer? What is the sampling distribution of the mean of a sample, drawn from a larger population? This distribution allows you to tie in the factor of sampling variation into your analysis.

The larger the sample, the more normally shaped the t-distribution becomes. Hmm...I need to work with this more. See it in action

Confidence intervals with t-distributions. If s is the sample standard deviation or the standard error, a 90% confidence interval is the following: 


$$\bar{x} \pm t_{n-1} \times (0.05) \times \frac{s}{n}$$


You have the factor of 0.05 because you're trimming 5% of both ends of the sample. The $t_{n-1}$ is the t-statistic with $n -1$ degrees of freedom.  

Not frequently used in industry data science actually. Most issues with __sampling error__ can be answered by empirical bootstrap sampling. Interesting! 

## Binomial/Bernoulli Distribution 
You have to know something about the probability of one trial happening/ocurring and then you can use the binomial distribution to estimate the probability of observing success or failure in a fixed number of trials 

Mean: 

$$\mathbb{E}[\text{ successes in n trials }] = n \times p$$

This makes a great deal of intuititve sense.

Variance: 

$$ n \times p \times (1-p)$$

__The binomial distribution converges to the normal distribution in limit__

## Poisson Distribution
The best distribution for events/time period. Distribution where you have to wait for the next event to come up. 
Used for modeling a process that produces events randomly at a given overall rate. 

So you know the average rate of arrivals, but the Poisson can be useful when you are asking questions about the distribution of events per time union when you sample many such time units 

What you know is this average overall rate which is parameterized by:
Mean
$$\lambda$$


The mean is somehow the same as the variance. That doesn't sound very attractive to me. 
Variance:

$$\lambda$$

__Assumption__: the rate $\lambda$ stays __constant__ over period being considered. 
You have to divide time periods or areas of space into segments where the rate is roughly equal. I guess I don't completely understand this so I'm gonna need to see some examples. 

Basically we're __COUNTING__ the number of events that happen in a span of time

## Exponential Distribution 
Used for modeling the distribution of time between events. Waiting time. 
In contrast to poisson, we're modeling the time/space __between__ events

## Estimating Failure Rate
How do you estimate rare events? You kind of hack it. 
You can apply a goodness-of-fit test (Chi-Square Test) to various rates to determine how well they fit on observed data. 

## Weibull Distribution
What happens when event rate doesn't remain fixed?? The rate of failure increases as time goes on. 
Event rate is allowed to change as specified by a shape parameter $\beta$


$$\beta = \begin{cases} > 1, \quad \text{probability of an event increases over time}\\ < 1, \quad \text{probability of an event decreases over time} \end{cases}$$

__Scale parameter__ $\eta$ is a scale parameter expressed in terms of characteristic life instead of event rate


