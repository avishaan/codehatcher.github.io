---
title: "Reducing Bias to Increase Test Set Accuracy" 
excerpt: "Gradient Class Activation Mapping provides a method that can be used to visually explore possible biases in the CNNs and DNNs"
categories:
  - ML
tags:
  - ML
  - Neural Network
  - Optimization
  - Class Activation Mapping
toc: true
toc_sticky: true
date: 2020-8-29
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>
<script async src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>

## Motivation
Visual insight is an important tool that allows engineers to understand what a deep neural network is doing. Not only to satiate curiosity, but also to give insight which can be used for optimization of the machine learning algorithm. This article will give a brief overview of a technique to identify biases in the categorization of an object so that the team can focus how to reduce the bias and increase the test set accuracy.

At best, high bias models  will not generalize well to a production environment. At worst it may even perpetuate stereotypes in race, gender, age that may cause legal ramifications for the company.

## Bias Identification
The example given in the Grad-CAM research shows an ImageNet pretrained VGG-16 model used in a binary classification task of *doctor* vs *nurse*. In this case the gender balanced test set generalizes poorly even though it achieved good validation accuracy. When looking at the class activation maps for two detections, there is some data as to why that may be the case.

<figure style='width: 100%' class='align-center'>
  <a href='/assets/posts/reduce-bias-gradcam/biased-cam.jpg'><img src='/assets/posts/reduce-bias-gradcam/biased-cam.jpg'></a>
  <figcaption>biased decision class activation mapping</figcaption>
</figure>

In the figure above, it seems the model was focused on the face to decide if the person was a nurse. This would easily strike *most* humans as an inaccurate method. With this visual insight, the model can optimized to have a higher test rate accuracy.

<figure style='width: 100%' class='align-center'>
  <a href='/assets/posts/reduce-bias-gradcam/unbiased-cam.jpg'><img src='/assets/posts/reduce-bias-gradcam/unbiased-cam.jpg'></a>
  <figcaption>unbiased decision class activation mapping</figcaption>
</figure>

Ah, much better. It seems the model is now focused on the coat, sleeves, and stethoscope which intuitively makes sense. The retrained model can be optimized to retrain better and look at the right regions

## Outro
This article didn't go over the map or implementation as that's all available in the paper. The main takeaway is exposure to various tools that can be used while creating a product to make sure it serves its users.
