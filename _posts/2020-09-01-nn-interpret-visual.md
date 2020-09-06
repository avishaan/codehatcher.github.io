---
title: "Neural Network Interpretability Visually" 
excerpt: "Understanding the activation of a network with the help of semantic dictionaries and non-neg matrix factorization to increase network performance."
categories:
  - ML
tags:
  - ML
  - Optimization
  - Semantic Dictionary
toc: true
toc_sticky: true
date: 2020-8-29
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>

## Motivation
It's important to be able to understand the activation of the layers of a network. This is very similar to the post that references *deep representations* and it's parallel to how the visual cortex of the brain processes images. Increased understanding allows a direct benefit to creating models as well as to satiating the innate curiosity everyone has. This additional understanding allows:
- debugging when accuracy is low
- investigating issues of overfitting and bias
- optimization when there are performance issues

The below will include a couple of techniques used to help increase the understanding of the intermediate network. This will be very similar to previous posts on this topic but expanded with different techniques allowing additional insight. The topics are via many different papers that were combined into a distill publication but the Google Brain team.

Most of the examples are taken via the Goog-LeNet image classification model. This was done because, for whatever reason, the neurons in this model have representations that seem particularly meaningful to a human.

## Semantic Dictionaries
These allow the assignment of meaningful names to activation groups instead of the abstract numerical values which are commonly used. As an example, the activation of "dog nose" can be understood by taking the visualization of the neuron activation and sorting them by how large an activation occurred. The insight from this visually describes the network in a manner conducive to human understanding. 

One big benefit over using text descriptions includes the detail associated with an image being *worth 1,000 words*. Often, the visualizations displayed have no equivalence in English and would otherwise be difficult to describe. Below is the difference between: floppy ears, dog nose, and cat head.

<figure class='align-center'> <video autoplay='autoplay' loop='loop' muted>
    <source src='{{ site.baseurl }}/assets/posts/nn-interpret-visual/semantic-dictionary.webm' type='video/webm'>
  </video>
  <figcaption>semantic dictionary visualization via distill.pub</figcaption>
</figure>

## Non-negative matrix factorization
Using non-negative matrix factorization visualizations can be constructed to explain how the network behaves on a particular image. The downside of this is the same downside mentioned above for saliency maps.

The benefit is the newly grouped neurons may have more useful, albeit less detailed, information to a human being. The trade-off of detail to *usability* is commonly encountered in product development if not in pure engineering disciplines. Matrix factorization gives us different strategies for "grouping" a matrix.

This strategy gives a way to show a combination of a color-coded heatmap for the activation of neurons not only show where the activation is highest but includes a color key that corresponds to the feature visualization

<figure class='align-center'> <video autoplay='autoplay' loop='loop' muted> <source src='{{ site.baseurl }}/assets/posts/nn-interpret-visual/matrix-factorization.webm' type='video/webm'> </video> <figcaption>neuron activation grouping using matrix factorization via distill.pub</figcaption> </figure> 

## Outro
There are many more techniques available that weren't discussed that may be useful. As well as new techniques being created all the time. If visualization of the network activations is required, this is a good place to start. Eventually, there will be some visualization methods available that use AR/VR.