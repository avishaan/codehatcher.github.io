---
title: "Activation Functions for CNNs, RNNs, DNNs" 
excerpt: "Knowing which activation functions are available, and how it's changed over the years, gives us choices for optimization and inspiration for new functions"
categories:
  - machine learning
tags:
  - ml
  - math
  - optimization
toc: true
toc_sticky: true
date: 2020-8-29
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>

## Goals
- gain exposure to multiple activation functions
- identify some use cases on where to use one over another
- become inspired to discover and experiment with alternate (unlisted) functions

## Activation Functions
### SiLU / Swish
Non-linear, continuous, **not monotonic**, range \\( \in [\approx -0.28, \infty] \\)

I'm also surprised a non-monotonic function does this well. Sigmoid linear unit aka Swish is not very well known but apparently used by Google researches on deeper models where it performs better than ReLU also being equally computationally efficient.

#### Function / Derivative
\\[ f(x) = \frac{x}{1+e^{-x}}, \; f'(x) = \frac{1+e^{-x} + xe^{-x}}{(e+e^{-x})^2} \\]

#### Pseudocode
```python
def swish(x):
    return x/(1-np.exp(-x))
```

### Sigmoid / Logistic / Soft Step
Non-linear, continuous, monotonic, range \\( \in(0,1) \\)

Very often used for a long period of time and one that is often introduced as the standard when getting started in machine learning. Partly because it is an easy jump coming from linear regression making the way to logistic regression. It's a function many are already familiar from their math background.
#### Function / Derivative
\\[ f(x)=\sigma=\frac{1}{1+e^{-x}} \;, f'(x)=f(x)(1-f(x)) \\]
#### Pseudocode
```python
z = (1/(1 + np.exp(-x)))
```


### Binary Step
Non-linear, Monotonic, range \\( \in{0,1} \\)

A light switch would seem to be a pretty good activation function. In a specific case, if the input is greater than 0 the activation is 1 (on). Zero gradient can be problematic during backprop
#### Function / Derivative
\\[ f(x) = \begin{cases} 0 & \ \text{if } x\lt0\\\ 1 & \ \text{if } x\geq0 \end{cases}
\;, f'(x) = \begin{cases} 0 & \ \text{if } x\ne0\\\ ?? & \ \text{if } x=0 \end{cases} \\]

### Linear / Identity
Monotonic, continuous, approx identity near origin, range \\( \in(-\infty, \infty) \\)

I'm not sure when this is used in practice anymore.

### Tanh
Monotonic, approx identity near origin, range \\( \in (-1,1) \\)

Relatively popular, although not as much since the advent of ReLU. Other than range of values it has very similar properties to sigmoid.
#### Function / Derivative
\\[ f(x) = \tanh{x} = \frac{e^x - e^{-x}}{e^x + e^{-x}} \;, f'(x) = 1 - f(x)^2 \\]

### ReLU
Non-linear, monotonic, range \\( \in [0,\infty) \\)

One of the most popular functions, just looking at it many thought it wouldn't be a viable candidate. It almost makes one think anything is possible when considering the trade-offs below and comparing it to other functions

#### Function / Derivative
\\[ f(x) = \begin{cases} 0 & \ \text{if } x\leq0\\\ x & \ \text{if } x\gt0 \end{cases} \;, f'(x) = \begin{cases} 0 & \ \text{if } x\lt0\\\ 1 & \ \text{if } x\gt0 \end{cases} \\]

### Leaky ReLU
Non-linear, monotonic, range \\( \in (-\infty, \infty)) \\)

Although the new and improved version it can be difficult to see why this is better. This is because it addresses the problem where the ReLU has a 0 gradient when x<0 which would deactivate neurons in that area. Leaky has a small gradient in that section

#### Function / Derivative
\\[ f(x) = \begin{cases} 0.01x & \ \text{if } x\leq0\\\ x & \ \text{if } x\gt0 \end{cases} \;, f'(x) = \begin{cases} 0.01 & \ \text{if } x\lt0\\\ 1 & \ \text{if } x\gt0 \end{cases} \\]

### Parameterised ReLU
Non-linear, monotonic in most useful cases where a>0, approx identity near origin in cases where it isn't used a=1, range \\( (-\infty, \infty) \\)

I appreciate how well named this is. Although it's continuous in some cases and has an approximate identity near the origin in some cases; those don't *seem* to be in situations often encountered.
#### Function / Derivative
\\[ f(x) = \begin{cases} ax & \ \text{if } x\leq0\\\ x & \ \text{if } x\gt0 \end{cases} \;, f'(x) = \begin{cases} a & \ \text{if } x\lt0\\\ 1 & \ \text{if } x\gt0 \end{cases} \\]

## Trade-offs
- An activation function that is **nonlinear** follows the universal approximation theorem can be proven to be a universal function approximator.
- Finite **range** allows for larger learning rates.
- Guaranteed convex error surface for **monotonic** activation functions. The value of the function may decrease even as the input increases.
- **Continuously differentiable** allows gradient based optimization methods less issues during backprop.
- NN learns efficiently when its weights are initialized with small random values for functions which **approximates identity near origin**.
