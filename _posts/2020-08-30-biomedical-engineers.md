---
title: "Do Biomedical Engineers have an Advantage in Machine Learning?" 
excerpt: "Biomedical engineers go through a multidisciplinary training that might make them a good major to transition into machine learning and Artificial Intelligence"
categories:
  - ML
tags:
  - biomedical engineering
  - machine learning
toc: true
toc_sticky: true
date: 2020-8-29
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>
<script async src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>

## Theory
As biomedical engineers (BMEs) we may have a unique view into machine learning and neural networks. We go through university studying multiple disciplines: 
- biology
- anatomy
- programming
- probability
- multivariate calc
- linear algebra
- electrical engineering
- physics

to name a few...

Being exposed to so many different domains allow us to gain intuitions into machine learning that may not come as easy to other disciplines. 

The downside is we may not have the same deep mathematics background required when optimizing problems. Luckily, with the advent of such powerful computational resources, the lack of a deep math background is less of a disadvantage while our multidisciplinary background becomes an incredible advantage. I'd love to see more BMEs consider this field.

Here are some intersection of BME and ML I have seen.
## Activation Functions
### ReLU - biology
Inspired by biology, as of 2017, the rectifier is the most popular activation function for deep neural networks. There was a large biological motivation for it's introduction along with the math (some might say in spite of the math because of the lack of gradient in some portions of the function cause many to theorize it would not be a viable activation function).

There are many theories for activation of neurons. Some of these theories depend on which type of neuron. An endless array for someone to explore thereby becoming a new best practice for an activate function. A BME is in a unique position to understand not only the existing biological inspired activation functions, but have the *potential* to explore something novel.

### Sigmoid - probability
Inspired by probability theory (which BMEs also have to take) was wildly used in 2011. Logistic sigmoid is also how many machine learning students get exposed to theory, even now. Having the necessary background in probability theory gives BMEs an advantage when getting started in this field.

## Deep Representation - anatomy 
<figure style="width: 260px" class="align-right">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/biomedical-engineers/deeprepresentation.jpg" alt="">
  <figcaption>DNN "features"</figcaption>
</figure> 

The intuition behind deep representation makes it easier for BMEs to understand. On the right figure there is the visual output of each layer in the network and as the input to the next layer which creates a more complex representation which is used as an input to the next layer. The final layer becomes the representation in the low dimension; our class label.

We often see this visualized as the first set of neurons "understand" edges / corners, with the next set "understanding" feature groups, and the next "understanding" faces. This progressive understanding of feature with additional complexity has a biological justification/explanation/inspiration (depending on your interpretation).

<figure style="width: 250px" class="align-left">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/posts/biomedical-engineers/visualcortex.jpg" alt="">
  <figcaption>visual cortex path</figcaption>
</figure> 

The anatomical equivalent is shown on the left in a figure whose pathways along the visual cortex which will look very familiar to any BME. Similar to the representation above, here we see V1 "understanding" simple visual forms / edge / corners, followed by feature groups, followed by faces, etc etc. 

Our understanding of the DNN and biological systems are not complete. With our assumptions of the DNN shown to be different; at least to our human visual interpretation. But these similarities still give BMEs an analogy they already understand with which to base their continual learning off of.

## LSTM - electrical engineering
Most BMEs will recognize the components used in describing the internals of an LSTM, specifically, the very common *feed forward* system. There is a lot of work in this field taking this analogy a step further where hardware LSTM circuits are created allowing instant evaluations. I've also seen some fluid mechanic model representations of LSTM which BME's will also be familiar with because their fluid mechanics classes. As above, this doesn't mean a BME is already a master, just that they can more easily intuit a concept due to recognizing an analogous system.

## SGD - physics
Stochiastic gradient descent when considered with momentum; think RMSProp, Adam, etc has an analogy in physics. There is an extensive explanation <a href="https://math.stackexchange.com/questions/2689721/momentum-in-gradient-descent">here</a> which does an incredible job explaining the parallels from a mathematical perspective. Because this concept of moment has a physics parallel, it can make it much easier to gain intuition of how it applies to SGD. Because physics is such an important foundation to inverse kinematics and medical device design, BMEs will have spent much time in this topic.

## Backprop - calc
Taking \\( \small\frac{\partial L}{\partial x^{(n)}}\\) in order to minimize the cost is a multivariate calculus problem that every BME knows intimately well. From thermodynamics to fluid dynamics we've encountered it multiple times. In backpropagation this understanding allows us to direct our cost function to a local, hopefully global, minima. Being familiar with this task in other domains allows us to quickly understand why it is important and how to gain an appropriate intuition.

## Image Transforms - linear algebra
Image transforms rely heavily on linear algebra for efficient implementation. Although, not the only place where linear algebra is used in ML, it's definitely is one of the most visual places. Already having an understanding of linear algebra and matrix methods makes this easy to understand for a BME. Along with image transforms, almost all operations need to be vectorized in order to reduce the amount of time needed to train and use a model. This doesn't mean a BME automatically knows enough to find a better optimized solution, but it can make understanding the implementation and debugging much easier.

## Implementation - programming
Doing everything from programming electrical system simulations, to inverse kinematics simulations, to finite element analysis BMEs are no strangers to engineering models of the real world in order to make a prediction about a future state. We may not be able to code an entire operating system, but we can easily pick up a new programming language allowing us to implement the linear algebra and multivariate calculus based algorithm in order to train and test a machine learning model.

## Conclusion
I don't want this to come off as BMEs are the be all end all, that's certainly not the case. I do think it is a field that happens to be well adapted for many machine learning implementation and research tasks due to their wide skillset listed above.

It's likely something that many startups and employers don't think about; I didn't realize it until I happened to really think about. This is meant to be more of a call to BMEs, if you are thinking of getting into the field, don't hesitate. As well as a call to employers, if you are hesitating hiring someone with a background in Biomedical Engineering, don't.