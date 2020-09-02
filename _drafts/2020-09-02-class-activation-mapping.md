---
title: "Visual Explanation of Neural Networks via CAM" 
excerpt: "Understanding the spatially important features of Deep and Convolutional Neural Networks using Class Activation Mapping"
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

## Motivation
Class activation mapping is an important tool when explaining and optimizing deep networks. In addition to the *more* obvious often suggested use case of gaining insight visually into how the network is making decisions. The article will reference a set of tools with use cases in case they are required in the future. References to specific implementations are in the outro.

## Insight into Optimization
The class activation mapping can give insight into optimizing and exploring predictions that had *unreasonable* predictions by giving some sort of visual clue as to what the model was "focused" on. 

## Weakly-supervised Localization
<figure style='width: 50%' class='align-center'>
  <a href='/assets/posts/class-activation-mapping/dog-cat-orig.jpg'><img src='/assets/posts/class-activation-mapping/dog-cat-orig.jpg'></a>
  <figcaption>dog cat original input</figcaption>
</figure>
The class activation maps, in this case specifically the gradient classification maps, show "where" the network determined the classification. If there was high bias or high variance this would give clues on how to optimize.
<figure class='half'>
  <a href='/assets/posts/class-activation-mapping/dog-detected.jpg'><img src='/assets/posts/class-activation-mapping/dog-detected.jpg'></a>
  <a href='/assets/posts/class-activation-mapping/cat-detected.jpg'><img src='/assets/posts/class-activation-mapping/cat-detected.jpg'></a>
  <figcaption>dog CAM (left) cat CAM (right)</figcaption>
</figure>

## Weakly-supervised Segmentation
Semantic segmentation is typically an expensive annotation task as it requires assigning each pixel in the image to an object/background class. There are variations of this where an algorithm can perform a segmentation with a weak localization seed. However, with an incorrect seed, that algorithm would not work. Using the above mentioned CAM map in combination Kolesnikov's work allows this to act as a reasonable seed obtaining an relatively high Intersection over Union (IoU) score.

Although, these may not be as good as the ground truth or other algorithms. It's important to consider the product perspective by understanding how the users would respond to this method of segmentation. Would it be acceptable? Likely, yes.

<figure style='width: 100%' class='align-center'>
  <a href='/assets/posts/class-activation-mapping/segmentation.jpg'><img src='/assets/posts/class-activation-mapping/segmentation.jpg'></a>
  <figcaption>segmentation comparison</figcaption>
</figure>

## Outro
There are other interesting use cases, which will be mentioned in other posts. Most of the above insight comes from a combination of the Grad-CAM, Discriminative Localization, and Google's *convets learning exploration* which takes from Chollet's *Deep Learning with Python*. This article didn't go over the map or implementation as that's all available in the paper. 
