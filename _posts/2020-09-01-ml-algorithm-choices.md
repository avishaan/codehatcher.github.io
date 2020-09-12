---
title: "Choosing an Appropriate ML Algorithm for a Product" 
excerpt: "Picking the right ML algorithm requires careful consideration of the user, product, team, and business"
categories:
  - machine learning
  - engineering execution
tags:
  - ml
  - algorithm options
toc: true
toc_sticky: true
date: 2019-5-29
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>

## Goals
Having a good idea of which ML algorithm needs to be considered when creating a new product/feature is important when trying to reduce engineering time. Starting with an incorrect algorithm can be an exercise in futility. This article will only talk about algorithm types and not [about the parameter nor hyperparameters]({% post_url 2020-08-29-hyperparameter-tuning-model-optimization %}) you'll need to explore for each. 
### Supervised Learning
When the requirement calls for understanding the relationship between the input and output data, this is the class of algorithms that will be used. Whether it's predicting a future state or classifying an object, this type of learning generally requires a labeled dataset.

#### Classification
##### Single Category
The single category will still be two-class where the answer might be yes/no, dog/muffin, or positive/negative.
- SVM: large features, linear
- locally deep SVM: large features
- perceptron: fast train
- logistic regression: fast train
- Bayes point machine
- decision forest: accuracy, fast train
- boasted decision tree: accuracy, fast train
- neural network: long training, high accuracy
##### Multiclass
Multi-class/category allows something similar to identifying what type of dog from the choice of poodle, collie, frenchie, and westie.
- multiclass logistic regression: fast train
- neural network: long training, high accuracy
- decision forest: accuracy, fast training
- decision jungle: small memory footprint
- one-v-all: based on two-class classifier

#### Value Prediction
Forecast the future by understanding the contribution of input variables to its output.
##### Regression
- ordinal: rank ordered categories
- Poisson
- fast forest quantile: predicting a distribution
- decision forest: fast training
- neural network: high accuracy, long train
- bayesian: linear model, small datasets
- linear regression: fast training

### Unsupervised Learning
In the product world, I don't think we use unsupervised learning enough. I would even go so far as to say that unsupervised learning should be a tool used by the product team to analyze some of the results of marketing exercises **before** building a new product/feature. Unsupervised can be used as a pre-training step at times.
#### Structure Discovery
Use this to segment/group the users, predict user preferences and tastes, and determine potential redundancy.
##### Clustering
- k-means
- principal component analysis
- mean-shift clustering
- DBSCAN
#### Anomaly Detection
Find the unusual and rate data points and outliers that are anomalous or even redundant. Abnormal sensor inputs from an engine could be used to predict engine failure.
- single class SVM
- PCA
- robust covariance
- isolation forest
- autoencoders

## Conclusion
Above was a relatively small list with some direction on how to decide what a product manager needs to create a powerful user experience. Instead of being an exhaustive list of options with parameters, this can be used in an exploratory guide. Other posts will have more into the details of the algorithms and will be more geared to machine learning engineers.