---
title: "Weight Initialization in Deep Neural Networks" 
excerpt: "A set of strategies for weight initialization preventing DNNs from having problems like vanishing or exploding gradients"
categories:
  - ML
tags:
  - ML
  - Optimization
toc: true
toc_sticky: true
date: 2019-04-28
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>
<script async src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>

## Motivation
Training neural networks, especially in very deep DNN's, can be difficult if the weights aren't initialized correctly and cause issues such as vanishing (slope becomes zero) or exploding (slope becomes huge) gradients.

### Intuition
Imagine a DNN where the # of layers \\( l \in [50...200+] \\) becomes very large. This means that our hypothesis will be based on many preceding weights \\() w^{[l]} \\) of those layers and will be conceptually similar to:
\\[ w^{[l]}w^{[l-1]}w^{[l-2]}w^{[l-3]}...w^{[3]}w^{[2]}w^{[1]}x_n = \hat{y} \\]
Taking an example of the weight being a little larger than the identity matrix
\\[ w^{[l]} = \begin{bmatrix} 1.6 & 0 \\\ 0 & 1.6 \\\ \end{bmatrix} \\]
We can see how \\( \hat{y} \\) would become very large *and explode*

The opposite would happen if our weights were initialized to a relatively small value such as:
\\[ w^{[l]} = \begin{bmatrix} 0.4 & 0 \\\ 0 & 0.4 \\\ \end{bmatrix} \\]
We can see how \\( \hat{y} \\) would become very small *and disappear*

## Weight Initialization
Picking our initialized values carefully can partially solve this problem. Intuitively, when you have a large number of nodes in a layer, you'll want each weight term to be smaller since there are more contributions to the next layer

### Zero Initialization
**Don't do this!** Initializing the weights to all zeros will cause symmetry in your network that will make it perform as if it is a simple logistic regression regardless of the number of layers it has.

### Sigmoid Initialization
Set the variance:
 \\[ Var[w_i] = \frac{1}{n} \\]
```python
w[l] = np.random.randn(shape) * np.sqrt(1/n[l-1])
```

### ReLU Initialization
Set the variance:
 \\[ Var[w_i] = \frac{2}{n} \\]
```python
w[l] = np.random.randn(shape) * np.sqrt(2/n[l-1])
```

### Xavier Initialization
For \\( \tanh \\) set the variance:
\\[ Var[w_i] = \sqrt{\frac{1}{n^{[l-1]}}} \\]