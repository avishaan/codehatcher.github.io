---
title: "Numerical Gradient Checking for Backprop" 
excerpt: "Backprop can be error-prone. Numeric methods for calculating the gradient is computational slow but easy to implement"
categories:
  - machine learning
tags:
  - ml
  - reference
  - math
toc: true
toc_sticky: true
date: 2020-8-29
---
<script>
MathJax = {
  tex: {
    inlineMath: [['$', '$'], ['\\(', '\\)']],
    displayMath: [ ['$$', '$$'], ['\\[', '\\]'] ],
  },
  svg: {
    fontCache: 'global'
  }
};
</script>
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js">
</script>

## Intro
Backprop computes the partials wrt to the weights but can sometimes be difficult to check it's implementation. A numeric method is an easy way to check the analytical implementation. The numeric method is slow and needs to be disabled during *actual* training.

Calculate an estimate of $\small\frac{\partial J}{\partial \theta}$ where $\theta$ are the parameters of the model sometimes denoted as $w$ and $J$ is the cost computed using forward propagation

## Math
\\[ \frac{\partial J}{\partial \theta} \approx \lim_{\varepsilon \to 0} \frac{J(\theta + \varepsilon) - J(\theta - \varepsilon)}{2 \varepsilon} = \frac{\partial J}{\partial \theta_a} \\]

Computing the difference $diff$ between the analytic implementation $\partial \theta$ and the numeric implementation $\partial \theta_a$

\\[ diff = \frac{\vert\vert\partial\theta - \partial\theta_a\vert\vert_2}{\vert\vert\partial\theta\vert\vert_2 + \vert\vert\partial \theta_a\vert\vert_2} \\]

If the difference is small, the numeric approximation and the analytic value suggest a common implementation

## Code
```python

gradapprox = (J_plus-J_minus) / (2*epsilon)
grad = backward_propagation(x, theta)

numerator = np.linalg.norm(grad - gradapprox)                              # Step 1'
    denominator = np.linalg.norm(grad) + np.linalg.norm(gradapprox)                             # Step 2'
    difference = numerator / denominator

if difference < 1e-7:
        print ("The gradient is correct!")
    else:
        print ("The gradient is wrong!")
```