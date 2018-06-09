

What's A GBM? 
What's Ensemble, Bagging and Boosting?

#### Bagging
* many __independent__ predictors
* model averaging techniques

#### Boosting
* sequential predictors
* 
The inspiration is from linear regression. When you fit a linear regression model, you hope that there is no real pattern in the residuals. As in the residuals appear to be randomly distributed around the 0 line. 

How is this idea carried forward into gradient boosted trees 
* Do this iteratively! leverage the patterns in residuals to strengthen a model with weak predictions and make it better

A real derivation of boosting 

When is random forest better than gradient boosted trees? 

WHEN NOT TO USE DEEP LEARNING
* Everything is an exercise in the bias/variance tradeoff. If you don’t have a lot of data it’s probably better to go with a simple model (high bias/low variance) than a really complex one (low bias/high variance).
* You don’t need Google-scale data to use deep learning $\Rightarrow$ think about transfer learning

One-shot learning. 
NLP embedding projects

But what about random forests now? What's so good about a random forest? 

## What is a decision tree?
* As recursive partitioning only uses the best binary questions to grow a decision tree 
* central divide to split data points, so decision trees are robust against extreme values (i.e. outliers).

The good: 
* robust to outliers

The bad: 
Using the best binary question to split the data at the start may not lead to the most accurate predictions. Sometimes, less effective splits used initially may lead to even better predictions subsequently.

To resolve this, we can choose different combinations of binary questions to grow multiple trees, and then use the aggregated prediction of those trees. This technique is called a random forest. Or, instead of combining binary questions randomly, we can strategically select them, such that the prediction accuracy for each subsequent tree improves incrementally. Then, a weighted average of predictions from all trees is taken. This technique is called gradient boosting.

While random forest and gradient boosting tend to produce more accurate predictions, their complexity renders the solution harder to visualize. Hence, they are often called “black-boxes”. On the other hand, predictions from a decision tree can be examined using a tree diagram. Learning which predictors are important allows us to plan more targeted interventions.

## Random Forest

The good: 
* Random Forests require almost no input preparation. They can handle binary features, categorical features, numerical features without any need for scaling.
* Random Forests perform implicit feature selection and provide a pretty good indicator of feature importance.
* Random Forests are very quick to train. The random feature sub-setting that aims at diversifying individual trees, is at the same time a great performance optimization! Tuning down the fraction of features that is considered at any given node can let you easily work on datasets with thousands of features.
* Random Forests are pretty tough to beat.This is why they make for excellent benchmark models.
* It’s really hard to build a bad Random Forest! Since random forests are not very sensitive to the specific hyper-parameters 

The fugly:
* They are not so intepretable. Once you average out that many trees, it's really hard to tell which decision can be traced back to what

