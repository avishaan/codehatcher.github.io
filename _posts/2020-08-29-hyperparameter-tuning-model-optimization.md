---
title: "Hyperparameter Tuning for Model Optimization" 
excerpt: "Knowing what hyperparameters are available for tuning is an important part of quickly and accurate optimization"
categories:
  - ML
tags:
  - ML
  - Hyperparameters
toc: true
toc_sticky: true
date: 2020-03-28
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>
<script async src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>

## Motivation
This will be a relatively quick list of parameters that we should be considering when performing hyperparameter tuning. If you are looking for ideas on how to iterate through the range of values, check the post on picking values for hyperparameters

## L2 Regularization
The L2 regularization parameter \\( \lambda \\) can be adjusted where higher values will create a cost function that incentivizes "simpler" models by penalizing large weights making the model more linear. This is also known as the weight decay parameter.
\\[ J(w^{[l]},b^{[l]}) = \frac{1}{m}\sum_{i}^{m} L(y^{(i)}, \hat{y}^{(i)}) + L2reg \\]

\\[ L2reg = \frac{\lambda}{2m} \sum_{l=1}^{L} \; ||\mathbf{W}^{[l]}||^2_F\\]
Now as \\( \lambda \uparrow \\) then the \\( \mathbf{W} \downarrow \\) to "compensate"

## Dropout Probability
This is common solution to high variance but the likely-hood of keeping a neuron can be adjusted via a `keep_prob` and that can be adjusted per layer. Most likely input layer and output layer would have `keep_prob=1`
```python
d2 = np.random.rand(a2.shape[0], a2.shape[1]) < keep_prob
# some of d2 will be zero so multiple by a3 to "remove" the nodes
a2 = np.multiple(a3,d3)
# make sure to increase the activation based on missing neuron probability
a3 /= keep_prob
```

## Learning Rate
The learning rate, \\( \alpha \\) conceptually describes the size of the "steps" taken during the gradient descent operation. Large steps may converge faster initially but fail to ultimately converge while small steps may initially converge slower but able to ultimately converge at the minima. This is one of, if not the most, obvious hyperparameters to manipulate.

### Decay Rate
We can decay the learning rate \\( \alpha \\) by a function. That function will also have a decay rate parameter \\( k \\) which can generate a new "dynamic" learning rate \\( \alpha_d \\) dependent on which epoch number the training will be performing
\\[ \alpha_d = \frac{1}{1+k*\text{epoch_num}}\alpha \\]
```python
alpha_d = (1 / (1 + decay_rate*epoch_num)) * alpha
```
#### Manual Decay
For models that may take multiple days to run, a "do it by hand" approach can be a viable option

### Decay Functions
Different decay rate functions *could* also be considered a hyperparameter to be changed. Iterating through different functions would likely be in a random order.
#### Exponential
\\[ \alpha_d = 0.95^{\text{epoch_num}}\alpha \\]
\\[ \alpha_d = \frac{k}{\sqrt{\text{epoch_num}}}\alpha \; \text{or} \; \frac{k}{\sqrt{t}}\alpha \\]
#### Descending Staircase
\\[ \alpha_d =
\begin{cases} 
      3 & t\leq 0 \\\\\\
      2 & 0\leq t\leq 1 \\\\\\
      1 & 1\leq t\leq 2 
   \end{cases}
\\]

## Deep Neural Network Weight
Our DNN/Perceptron models have [starting weights]({% post_url 2020-08-29-weight-initialization-deep-networks %}) that need to be initialized. We can add a factor to this in order to change how the weights are initialized. Overall, this is considered a *low priority* and other optimization parameters should be considered first.

## Activation Functions
Trying and iterating through different activation functions in different layers can be a hyperparameter worth tuning. Sigmoid, Tanh, ReLU are some commonly used examples.

## Batch Size
Picking a batch, or mini-batch, size can be a tunable parameter. A strategy of increasing the batch size as the cost decreases is viable. This makes sense as when batches are small we make bigger but less "precise" jumps while when the batch is large we make slower but more "precise" jumps. In order to get the best of both worlds, start with a small batch and increase it as you converge. One way is to look at the current error and the error when you last decreased and decrease the batch size by some percentage.

## Optimization Algorithm Parameters
Different optimization algorithms have different parameters for adjustment. A couple examples are given for the most common ones but we can always investigate the parameters we need to tune for others. Most likely you will want to increase your learning rate \\( \alpha \\) since you are dampening.
### Gradient Descent with Momentum
Increase the slope of the direction of gradient descent in the direction where there has been faster descent over the past few iterations generally described by \\( \beta \\) which can be tuned
\\[ V_{\partial w^{[l]}}^{\text{corrected}} = \beta V_{\partial w^{[l]}} + (1-\beta)\partial w^{[l]} \\]
\\[ w^{[l]} := w_{\text{prev.}}^{[l]}-\alpha V_{\partial w^{[l]}} \\]
### RMS Prop
Similar as momentum but taking the square of the derivative term. Once again we can tune \\( \beta \\)
\\[ S_{\partial w^{[l]}}^{\text{corrected}} = \beta S_{\partial w^{[l]}} + (1-\beta)(\partial w^{[l]})^2 \\]
\\[ w^{[l]} := w_{\text{prev.}}^{[l]}-\alpha \frac{\partial w}{\sqrt{S_{\partial w^{[l]}}}}\\]
### Adam Optimization
Conceptually a combination of the previous momentum and RMS prop. Here we can tune \\( \beta_V, \; \beta_S, \; \epsilon \\)
\\[ w^{[l]} := w_{\text{prev.}}^{[l]}-\alpha \frac{V_{\partial w^{[l]}}^{\text{corrected}}}{\sqrt{S_{\partial w^{[l]}}^{\text{corrected}}}} \\]