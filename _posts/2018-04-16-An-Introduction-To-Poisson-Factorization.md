---
layout: post
title: Starting to Think About Poisson Factorization
categories: Recommendation Systems
---

##Realistic Things It Captures
1. People are different
2. Items are different
3. People only have a finite amount of money to spend

## What is Posterior Inference Again? 
The goal is to uncover hidden behavior/properties about the user and also the items
First you estimate some kind of a preference vector and look for spikes

##How does this compare to usual matrix factorization methods?
1. This is better because it takes into account __budgets__. Items that you did buy say more about your personality or the quality of the item than items that you didn't buy because you have a finite budget. Apparently classical matrix factorization overestimatese budget.

##So what do you do about them priors? 
Gamma priors on users 
Gamma priors on items 
...nothing new so far
But wait! Now we're putting a Gamma prior on the rate parameter too? What will this actually achieve?

##Why is the Gamma a good idea?
* Naturally sparse
* "gamma prior on rate parameter controls average size of representation"...? Okay...?

## What's the Actual Algorithm?
1. Subroutine: for each user i
    * Sample activity from Gamma prior
    * Sample user preference from gamma prior with user activity as parameter
2. Subroutine: for each item i
    * Sample popularity of item from gamma
    * sample attribute 
3. Sample rating $\sim$ Poisson(<user, item>)

## Pipeline:
1. First fit posterior
2. Use Hierarchical Poisson Factorization to make actual recommendations
  * The score for ranking is just the average poisson parameter given observation: 
  ## \mathbb{E}[\langle \theta_u, \beta_i \rangle| \vec{y}]##
  * Score tells you the probability of unconsumed item to be consumed in the future
3. 

##Questions remaining
1. why isn't feedback a problem?
2. Does hierarchical structure capture "more diversity"? How? I am not convinced.
3. How do you pick K, the number of latent features?
4. How do you pick initial gamma parameters?

## What is the motivation for switching from o
