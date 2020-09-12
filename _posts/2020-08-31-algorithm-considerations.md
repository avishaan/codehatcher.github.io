---
title: "Product Considerations when Incorporating Machine Learning" 
excerpt: "As will any software engineering field, it's important to consider technical tradeoffs so that we can maximize customer value."
categories:
  - machine learning
  - product strategy
tags:
  - ml
  - product strategy
toc: true
toc_sticky: true
date: 2019-2-10
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>

## Goals
Anytime a product/feature is considered multiple domains must come together and find a balance. In the advance of any new technology, whether its XR, AR/VR, DL, ML/AI, crypto, mobile, Web 2.0, and whatever else came before my time, it's easy for a team to get caught up in the shiny new tech. When considering the integration of machine learning, there are some things to think about.

## Training Data Size
### Number of Examples
The more data the better everyone always says. Knowing how much data you have is an important step. Having a small amount of data doesn't mean you can't leverage ML at all, it just requires some expectation management on which algorithms you can use. The algorithms used will give different user experiences which may or may not be valuable to a user. Maybe you don't have the data to predict the disease the patient will get, but still know they will need to be hospitalized. That can be enough in some cases.

If you don't have *enough* data, there are a few things you can try, not all of which are technical:
- license data
- use Mechanical Turk
- try a different algorithm
- scrape data (within legal limits)
- create synthetic data
  - Unreal Engine
  - Maya
  - Unity
- use transfer learning to train the last layers of an existing model

### Number of Features
The number of examples in the training set is often in our mind, but we forget to consider the ratio of features/examples. If the training data has a large feature to example ratio, we need to choose a high bias low variance algorithm such as: linear regression, naive bayes, *linear* SVM. If we have a low feature to example ratio, we can use low bias high variance algorithms such as: KNN, decision trees, *kernel* SVM for example.

## Accuracy Metrics
Getting the highest level of accuracy is not always necessary, or feasible. Knowing how people will use the product will give insight into how the requirements of this should be structured. Are they looking for predictions or perhaps just for screening. With user research, you'll have an idea of what metrics you will need to achieve to get the desired user experience. Some metrics to consider:
- accuracy, auc, precision, recall, f1 score
- RMSE, RAE, MAE, RSE, R<sup>2</sup>
- other center average, cluster center average, cluster center max distance

## Training Time
This typically will be related to the accuracy, higher accuracy requirements generally mean longer training time. Certain algorithms may require longer training time such as an NN with high convergence. Any hyperparameter available will likely have to be explored and tuned as the required accuracy increases. You may also be retraining an algorithm as new data becomes available, depending on the user requirements longer re-train times may be unacceptable.

## Prediction Time
This doesn't get talked about a lot but I've experienced prediction time constraints in products. As an example, having a requirement of speech recognition in real-time is a significantly more difficult problem then batch recognizing for later use. Being aware of how this will change the user experience of the product is an extremely important consideration.

## Next Steps
There is a post that is a guide for when you use different types of algorithms. This can help narrow the search when the user requirements have been defined and it's time to de-risk a potential new feature.