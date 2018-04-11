---
layout: post
title: Teaching Myself Variational Inference
categories: Data Science
---

The Main thing that's going on: Approximate that complicated posterior $p(y \mid x)$ with a simpler distribution $q(y)$. Usually make q independent so that it's easier to work with. 
Apparently that is not too broad of an assumption.  (q only has to model y for the particular finite x that we actually saw, not the full relation between x and y). 
This assumes that your observations are independent? Or what? 
A particular q in Q is specified by setting some **variational parameters** -- the knobs on Q that you can turn to get a good approximation

 To get at a q(y), we still need to retain p(y | x), which may differ for each input x.

Variational methods don't require any sampling, so they are fast and deterministic. So then what's the catch? 
Why is MCMC the alternative? How do you set up MCMC to do the same thing?

Catch: You have to carefully choosing the objective function that decides whether q is a good approximation to p, and exploit the simple structure of q.

Ways to think about Variational Inference
* An extension of Expectation Maximization to the case of non Gaussian Mixture Models

Examples/Buzzwords (i.e. things that I don't know what they mean or reference at all)
* Mean Field Approximation
* Markov Random Fields
* Loopy belief propagation
* Tree-reweighted belief propagation
* Expectation propagation.

## What is inference anyways? 
You observe some of the variables (input to your system). You want to infer the values of some of the other variables (output of your system).
You give a little to get a little. 


