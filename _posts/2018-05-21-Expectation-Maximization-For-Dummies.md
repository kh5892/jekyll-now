---
layout: post
title: EM Algorithm for dummies 
categories: machine learning
---

This is definitely needlessly specific and probably stupid to try to motivate every single line of the proof of expecation maximization without implmenting it, but I want to make math seem a little less mythical and hopefully help someone else or at least mostly me. Maybe if I go into such fervored specificity, then I will be able to intuit and remember this commonly used algorithm more easily.  

# Ingredients: 
* Jensen's Inequality

Notation: 
* x := data
* $\theta := $ parameters
* z := hidden latent parameters

End goal: find $\theta$ such that maximizes log likelihood of the parameters: 

$$ L(\theta) = \ln P(x|\theta)$$

Bring in the hidden variables. This is kind of like a harmless triangulation because you can just marginalize out any of these hidden variables anyways. What is the most innocuous way to introduce an arbitrary new parameter? __By marginalizing out__

$$ \ln (\sum_{z} P(x|z, \theta)P(z|\theta)) $$

A good way to think about this is that you have to multiply out the z, but keep the $\theta$ and hence why we are multiplying by the marginal: $P(z|\theta)$.

The next step would be to introduce an intermediary point $\tilde{\theta}$. What is the most innocuous way to introduce an unrelated intermediate likelihood point set? __By multiplying by 1__:

$$ \ln (\sum_z \frac{P(z|x, \tilde{\theta})}{P(z|x, \tilde{\theta})} P(x|z, \theta) P(z|\theta)) $$

Now we can use Jensen's inequality to get a lower bound and to isolate the likelihoods so that you can work on those alone. Easy trick? 

$$ \geq  \sum_z \ln \frac{P(z|x, \tilde{\theta})}{P(z|x, \tilde{\theta})} P(x|z, \theta) P(z|\theta) $$

Re-arranging the fraction. This is the truly mystifying part for me and seemingly aesthetically motivated. To make things symmetric between the tops and bottoms of the likelihood, let's just pull out $P(z|x, \tilde{\theta})$ from the fraction. these are actually just the $\lambda$ weights of the generalized Jensen's inequality: 

$$ =  \sum_z \ln \underbrace{P(z|x, \tilde{\theta})} \frac{P(x|z, \theta) P(z|\theta)}{P(z|x, \tilde{\theta})}  $$

And now more magic. We introduce the likelihood of this new unrelated intermediate parameter $\ln P(x|\tilde{theta})$ by adding 0:

$$ =  \sum_z \ln P(z|x, \tilde{\theta}) \frac{P(x|z, \theta) P(z|\theta)}{P(z|x, \tilde{\theta})} -\ln P(x|\tilde{theta}) + L(\tilde{\theta}) $$

Pull in the log likelihood to further symmetrize the fraction: 

$$ =  \sum_z \ln P(z|x, \tilde{\theta}) \frac{P(x|z, \theta) P(z|\theta)}{P(z|x, \tilde{\theta})P(x|\tilde{theta})} + L(\tilde{\theta}) $$

Notice that this looks a little wonky. And now here's something that I didn't even realize: $P(x|z, \theta)P(z|\theta) = P(x,z|z,\theta) = P(x,z|\theta)$. Again, there was no need to be this specific, but it's nice to verify: 

$$ =  \sum_z \ln P(z|x, \tilde{\theta}) \frac{P(x,z|\theta)}{P(x,z|\tilde{\theta})} + L(\tilde{\theta}) $$

So much symmetry. But what does this really mean? 

$$ L(\theta)- L(\tilde{\theta}) \geq  \sum_z \ln P(z|x, \tilde{\theta}) \frac{P(x,z|\theta)}{P(x,z|\tilde{\theta})} $$

You got a concrete bound on the RHS. How nice!

So I guess the final takeaway that I am getting out of this derivation is that the authors clearly had a clear intuitive picture of what was going on underneath. Like they knew that there were going to be hidden parameters $z$ so they had to introduce those in a harmless way. And they also knew that they would be bouncing between different sets of parameters $\theta$ and $\tilde{\theta}$ so they knew they had to introduce this set of parameters in an inocuous way as well. 



