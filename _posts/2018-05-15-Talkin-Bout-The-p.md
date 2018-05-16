---
layout: post
title: A Deeper Understanding of P-Value...But For a Layman
categories: Interviews
---

#Explain it to Me like I'm 5 What Is a P-Value??!!

## First a little riddle to get us started: 

This is a popular facebook data science interview question so it's probably good to go through this process anyways although it is quite a ways irrelevant from the subject at hand for the day. 

Ahem. So say you have three friends at a bar and they're all peak drunk. You're still in college because you're an eternal student and you missed class today because you also eternally don't have your shit together. You ask your three drunk friends if we have an exam next week. Because your so close to your friends you know that: 

$$ \begin{cases} P(\text{Drunk Friend Says Yes} | \text{Exam}) = \frac{2}{3} \\ P(\text{Drunk Friend Says Yes} | \text{No Exam}) = \frac{1}{3} \end{cases}$$

Okay great so if all three of your drunk ass friends independently concur and say that there is a an exam next week, what is the probabiilty that you actually do have an exam?

So immediately, I will take a Bayesian approach to this problem because it sounds like we're working with conditional probabiilty and updating with more data. Great. Do we remember Bayes Law? 

$$ P(E|YYY) = \frac{P(YYY|E)P(E|YYY)P(E)}{P(YYY)}$$

Now since we're Bayesian, we know that Bayes rule goes hand in hand with law of total probability because we're smart and we went to college: 

$$ P(YYY) = P(YYY|E)P(E) + P(YYY|E^c)P(E^c)$$

Substituting in we get something that makes us feel warm and fuzzy inside (because it's a familiar form, not because it's particularly illuminating at the moment): 

$$ P(E|YYY) = \frac{P(YYY|E)P(E)}{P(YYY|E)P(E) + P(YYY|E^c)P(E^c)}$$

Great! So what are the ingredients of a great Bayesian? 

1. A prior 
2. A posterior
3. An update of some kind

Unfortunately we don't have a prior ($P(E)$). Now would be a great time to blow your interviewer's mind and ask for a prior distribution. And by blow someone's mind, I mean assert your stance as a fancy Bayesian who lives by her own damn rules. Once you know the prior, you can easily solve for $P(E|YYY)$, if you make the trivial trivial algebraic calculation: 

$$ P(YYY|E) = (P(Y|E))^3 = (2/3)^2$$

and so forth. 

## Great so now we're in a Bayesian Mood. Now can we talk about what a p-value is? 

Okay so a really straightforward way to think about the differnce between a Bayesian Vs. Frequentist: 

* Bayesian: You are given ONE set of data and you can fit a whole population of models to your one set of observations
* Frequentist: You have ONE model/hypothesis, but you can generate many data sets out of this model.

So if we have a set of data and we're questioning if this set of data could possibly come from the specific model ($H_0$), the Bayesian would want to calculate $P(H_0|D)$ or the probability that model $H_0$ holds given our observation set D. However, remember Bayes rule + Law of Total Probabiilty? 

The reason why we use p-values is to show that an event or a data set is too unlikely to happen by pure chance

$$ P(H_0|D) = \frac{P(D|H_0)P(H_0)}{P(D|H_0)P(H_0) + P(D|H_0^c)P(H_0^c)}$$

Notice we run into a similar problem that we did before in the facebook problem. We don't have a prior!! What is $P(H_0)$. What's worse, we can't even imagine what $P(D|H_0^c)$ is. What is $H_0^c$ for a Bayesian? A distribution of models? Blech our fancy Bayesian is confused. 

## Frequentist p-value to the rescueeeee
Our fundamental Bayesian problem is that we can't fix our model $H_0$ so we can't figure out what $P(D|H_0^c)$ is. 

However, the frequentist comes up with a clever solution because the frequentist says that okay so let's fix or model instead $H_0$ and produce many different sets of data from it. We can tell how likely our given observations set $D$ is to be generated from the model, by comparing it to the other data sets that the model simulated. 

Great! But how in the world do you compare sets of data with one another? We could accept our limitations as lame humans and map this high dimensional problem to 1d with a test statistic. The ideal test statistic maps every set of simulated data into a frequency count/histogram. All we have to do is like up our observation point with this historgram! WHOO!

How do we measure how close is close? Intuitively you would probably say, well if our observation point is far enough down the tail, then the counts of similar simulated data would be low enough and we're good. Actually the frequentist is even smarter than that! Instead of relying on the probability density function to measure likely/unlikely, she's gonna use the CDF. 

What's the benefit? Well, with a CDF the p-values to the right of the $\alpha$ mark are uniformly distributed. (come back to this. This point clearly needs to be proved or illustrated for deeper understanding). 

Small quick addendum: if you're going to use a 2-tail test, which most likely you will be, the $alpha$ levels at each tail is actually $\frac{\alpha}{2}$. So in the case of 5%, the right and left tails should have CDF $\geq 2.5$ amd $\leq -2.5$

##All the Ways to Cheat the Frequentist
Because $P(H_0 \text{ is significant}) \propto $ Uniform, if you perform the hypothesis test over and over again, the probability of significance is additive and will increase. In this way it's always possible for you to debunk your null hypothesis. In this instance when we want to test our hypothesis over and over again, we have to make a mulitple hypothesis correction or (Bonferroni correction if you're European and you drink straight olive oil instead of water). 

##Another addendum: Let's not get confused between t-value and p-value
t-value measure the number of standard deviations your sample is from the mean. This is completely different from $P(D|H_0)$. However, there is one instance in which all of this statistical "fat" works out in your favor. When the population distribution is indeed Gaussian, then the t-value = p-value. 

##Open for further exploration:
* So then WTF is a F-statistic? 
* Is there some way to describe degrees of freedom for a complete dodo brain? 
* How do you answer the following problem: Given n samples from a uniform distribution[0,d], how do you figure out what d is? 
