---
layout: post
title: Statistical Experiements & Significance Testing
categories: Data Science
---

## A/B Testing
Two Groups...
Two Treatments...
Which will come out on top??

Test statistic- metric that you use to compare group A to group B. Usually it's some kind of a binary variable. 
Examples: click or no click, buy don't buy

## Hypothesis Tests
Bidirectional two way hypothesis test- extreme chance results in either direction of the tail could count towards the p-value

## Resampling
__Boostrap__- how reliable is your estimate? Is there sampling bias?
__Permutation__- test hypothesis

##Steps to a Permutation Test
1. Combine the results from both groups A & B
2. shuffle the combined data and radomly drwa (__Without replacement__) a resample of the same size as group B
3. Repeat for group A. Or I guess this would just be the complement anyways so whatever. 
4. Recalculate the test statistic for permuted groups. This constitutes one permutation distribution of the test statistic
5. Repeat R times
6. Compile a permutation distribution of the test statistic.

__Statisticallyy Significant__- observed differences lies outside most of the permutation distribution, then we can safely conclude that __chance was NOT at play__

