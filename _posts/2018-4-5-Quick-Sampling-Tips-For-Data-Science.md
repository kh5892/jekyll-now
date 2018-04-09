---
layout: post
title: Quick Post: Sampling Distributions 
categories: Data Science
---

## Bias
Definition: measurement/sampling errors that are systematic and produced from poor sampling methodology.  

## Standard Error
Definition: measures variability of sampling

$$ SE = \frac{\sigma}{\sqrt{n}}$$

Where $\sigma$ is the standard deviation of the sample. 

Square-root of n rule: to halve the standard error, the sample size must increase 4 times. 

## The Bootstrap
Definition: sampling with replacement

The algorithm: 
+ Subroutine to find mean of one sample. Repeat R times
  1. Draw a sample value, record, replace
  2. Repeat n times
  3. Record the mean of the n resampled values 
+ Use the results of the subroutine to 
  * calculate standard deviation 
  * histogram
  * confidence interval

Fun fact: Bagging = Bootstrap + Aggregating 

Misconception: Bootstrap doesn't create more data, it merely informs us about how lots of additional samples would behave when drawn from a population like our original sample.
So then what is the point of bootstrapping ever then? Major and only application I know of is decision trees. -

## Confidence Intervals
Confidence interval is really synonymous with standard error. 
Definition confidence level: the number of confidence intervals, constructed in the same way from the same population, expected to contain the statistic of interest. 

X% confidence itnerval around a sample estimate should, on average, contain similar sample estimates x% of the time. 

Algorithm for Bootstrap Confidence Interval: 
1. Draw a random sample of size n with replacement
2. Record statistic of interest from sample
3. Repeat R times
4. Trip off the x% ends. 

Confidence intervals answer the question: "Given a **sampling procedure** and a **population**, what is the probability that..."

Confidence intervals __DO NOT__ answer the question: "Given a sample result, what is the probability that (something is true about the population)"

So then how do we really use confidence intervals? 
  * Understand how variable oyour sample result might be 
  * Learn whether a larger sample is needed 

There's nothing that a confidence interval can do for you if your sample size is too small. 
The question that 

