---
title: "ImageDataNet: Generator for Training and Validation"
excerpt_separator: "<!--more-->"
classes: wide
categories:
  - ML
  - Notes
tags:
  - ML
  - Notes
  - Tensorflow
  - Keras
  - ImageNet
---

Organization is a key when it comes to performance of our engineering team. When it comes to training and validation of an ML algorithm, there are some best practices. Using the `ImageDataGenerator` class from Keras gives us an easy way to organize a dataset. Maintaining this from the in-house tagging we have, to CI/CD, and through release giving us a shorter release cycle with fewer bugs. ImageNet will automatically label these images for us removing a coding step.

### File Structure
Firstly, start off by understanding the file structure. The root directory `/images`, as an example, could be a Kaggle file you have unzipped with the images you want to train on.

<div class="mermaid">
graph BT
  Images --> Training --> Cats --> 1.jpg
  Cats --> 2.jpg
  Cats --> 3.jpg
  Training --> Dogs --> 4.jpg
  Dogs --> 5.jpg
  Dogs --> 6.jpg

  Images --> Validation --> vcat[Cats] --> 7.jpg
  vcat[Cats] --> 8.jpg
  Validation --> vdog[Dogs] --> 9.jpg
  vdog[Dogs] --> 10.jpg

</div>
<script async src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>

<!--more-->
### Training Image Generator
The image generator can perform some manipulations on the fly; this makes it handy to play around with some alternative options without preprocessing an entire training set. Here, we will normalize via `rescale` and change the dimensions via `target_size`.

```python
from tensorflow.keras.preprocessing.image
import ImageDataGenerator

train_datagen = ImageDataGenerator(rescale=1.0/255)
training_dir = '/tmp/images'

train_generator = train_datagen.flow_from_directory(
        training_dir,
        target_size=(120, 120),
        batch_size=20,
        class_mode='binary'
        )
```
### Validation Image Generator
Similarly to the aforementioned training generator, we can create a generator for our validation set

```python
test_datagen = ImageDataGenerator(rescale=1.0/255)

validation_generator = test_datagen.flow_from_directory(
        validation_dir,
        target_size=(120, 120),
        batch_size=20,
        class_mode='binary'
         )
```

And go ahead and train like usual, but using the generators instead

```python
model.fit(train_generator,
      validation_data=validation_generator,
      steps_per_epoch=100,
      epochs=15,
      validation_steps=50,
      verbose=2
      )
```