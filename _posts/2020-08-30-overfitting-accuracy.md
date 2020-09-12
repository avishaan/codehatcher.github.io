---
title: "Increase Validation Accuracy in Cases of High Variance" 
excerpt: "How can we make sure the representation learned by our model will be applicable to data the model has never seen before. Overfitting can reduce the validation accuracy of our data."
categories:
  - machine learning
tags:
  - ml
  - overfitting
  - optimization
toc: true
toc_sticky: true
date: 2020-8-29
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>
<script async src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>

# Intro
This is a central problem in machine learning; how do we make sure the parameters of a model generalize well to problems the model hasn't seen *presented in our cross-validation set* and not just to the training data. An example of how this presents maybe when the validation accuracy is relatively low ~70% but our training accuracy ~100%

# Strategies
## Cost Regularization
### Ridge - L2 Regularization
Includes a "squared magnitude" of the weights as a penalty term in the loss function
\\[ J(w^{[l]},b^{[l]}) = \frac{1}{m}\sum_{i}^{m} L(y^{(i)}, \hat{y}^{(i)}) + L2reg \\]
assuming 4-layer NN...
\\[ L2reg = {\frac{1}{m} \frac{\lambda}{2} \sum\limits_l\sum\limits_k\sum\limits_j W_{k,j}^{[l]2} }\\]
```python
L2_regularization_cost = (1/m)*(lambd/2)*(np.sum(np.square(W1))
                       + np.sum(np.square(W2))
                       + np.sum(np.square(W3)))
```
### Lasso - L1 Regularization
L.A.S.S.O. - Least Absolute Shrinkage and Selection Operator looks at something like the absolute value of magnitude. Most of the time we'll opt for L2 Regularization
\\[ J(w^{[l]},b^{[l]}) = \frac{1}{m}\sum_{i}^{m} L(y^{(i)}, \hat{y}^{(i)}) + L1reg \\]
\\[ L1reg = \frac{\lambda}{2m} \sum_{l=1}^{L} \; ||\mathbf{W}^{[l]}||^1\\]

### Adaptive Regularization
Multiple algorithms implement this for us but intuitively this would change the \\( \lambda \\) of regularization as the model trains. See article on hyperparameter tuning for more details

## Inverted Dropout
Remove some neurons randomly so that the network can't be dependent on only a subset of the input features and needs to find a way to generalize. By scaling the weights based on the `keep_prob` we have a network that is trained and doesn't need scaled weights at test time.
```python
d2 = np.random.rand(a2.shape[0], a2.shape[1]) < keep_prob
# some of d2 will be zero so multiple by a3 to "remove" the nodes
a2 = np.multiple(a3,d3)
# make sure to increase the activation based on missing neuron probability
a3 /= keep_prob
```
When implementing the above the cost function is constantly changing making it difficult to debug. We can implement without dropout, check everything is working, and then enable dropout and hope there are no bugs.
## Synthetic Data Augmentation
Including data that has been rendered in 3d using software like Unity, Maya, Blender, or even the new Unreal 5 engine (which is spectacular btw) are especially interesting options. It's become good enough that you can achieve non-trivial accuracy strictly using rendered data.
Here I would recommend adjusting camera angles, camera distances, light angles, number of light sources, and of course any other characteristics of the data. Obviously, for objects that have a high amount of variability that can't be easily encoded and iterated would not be as feasible.

## Image Data Manipulation
Mostly relevant to CV (computer vision) problems where our input vector represents an image. Reference the article on ImageDataNet on how to set up a generator in a TensorFlow specific workflow.

### Flip
Flip the image across an axis. If flipping across an axis not orthogonal to a basis then consider performing a fill and crop of missing and extruding space. This can be checked visually.
```python
np.flip(); np.flipud(); np.flip(lr); # numpy based
cv2.flip(data, flipcode);  # opencv based
tf.image.flip_left_right(); tf.image.flip_up_down(); # tensorflow based
```
### Rotation
Rotate an image around an axis. If you rotate at something not divisible by 90<sup>o</sup> then you'll need to deal with the "excess" image. Crop to a square and resize assuming the subject remains in the crop is reasonable. Visual inspection is useful.

### Skew
Similar considerations, understand what the output will visually look like, check that, and the new frame should still contain your subject.

### Noise
Depending on the use case this will likely not help. I haven't a situation where it has helped. Certainly use random noise if this is going to be tried.

### Subtle Distortion
Other miscellaneous distortions can be used. Now is a good time to call up your Adobe Photoshop friend to bounce some ideas off of.

## Batch Norm
Although generally used as an optimization algorithm, this can contribute slightly to reduce overfitting. Even though the contribution is slight, because it has other benefits and is so easy to implement it is likely worth implementing. Each mini-batch would be scaled by the mean via \\( \beta \\) and variance via \\( \gamma \\) on just that mini-batch which means it will add some noise into the activations of the hidden layer.

Do not combine with inverse dropout.
{: .notice}

## Combination
Adding L2 regularization to inverse drop out is a viable often used strategy especially when the input features are image-related data.

## Early Stopping
Stopping the training when the training error \\( J \\) begins to diverge from the dev set error is a viable, albeit surprising, method for reducing overfitting. This is interesting from a psychological standpoint, but I won't go into that here.

## Reduce Input Features
Manually remove input features by keeping which features to keep. Can use a model selection algorithm for this.