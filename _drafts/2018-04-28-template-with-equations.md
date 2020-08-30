---
title: "Template" 
excerpt: "Linear Algebra reference especially useful when vectorizing Machine Learning operations and understanding intuition for algorithms"
categories:
  - ML
tags:
  - ML
  - Reference
  - Math
toc: true
toc_sticky: true
date: 2020-8-29
---
<script id="MathJax-script" async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML"></script>
<script async src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>

## Motivation
I focus on properties that help give an intuition on what is happening. I try to avoid rote calculation since machines are wonderful at computation. Machines aren't great at debugging themselves, that's where intuition comes in.

A reference that maps common iterative mathematical syntax to linear algebra syntax is helpful to have around when implementing Machine Learning algorithms. A quick reference can mean the difference between understanding a topic or finding the bug in your code. Here are some of the common equations, axioms, and theorems I personally reference on a regular basis. 

Assuming \\( \mathbf{A}, \mathbf{B}, \mathbf{C} \in \mathbb{R}^2 \\) and also \\( \vec{r}, \vec{s}, \vec{t} \in \mathbb{R}^{2 \times 1} \\)
\\[
    \begin{bmatrix}
    A_{1,1} & A_{1,2} \\\
    A_{2,1} & A_{2,2} \\\
    \end{bmatrix}
\\]

## Mechanics

### Transpose
The transpose of a matrix is the mirror of it across the diagonal.
\\[ {\left(\mathbf{A}^\intercal \right)}_ {i,j} = \mathbf{A}_{j,i}^\intercal  \\]

### Scalar Projection
The scalar projection of two vectors; magnitude component of projection. Can also think about as the norm of the vector proj or as the length of proj if \\( \mathbb{R}^2 \\)
\\[ Proj_{\vec{r}}(s) = \frac{\vec{r} \cdot \vec{s}}{||\vec{r}||} = ||\vec{s}||\cos{\theta} = \vec{s} \cdot \hat{r} = \left\||\vec {s} |\right\|{\frac {\vec {s} \cdot \vec {r} }{\left\||\vec {s} |\right\|\,\left\||\vec {r} |\right\|}} \\]

### Vector Projection
The vector projection of two vectors; magnitude and direction components of the projection. Can also think about as a combination of the scalar projection and direction
\\[ Proj_{\vec{r}}(\vec{s}) = Proj_{\vec{r}}(s) \cdot \hat{r} = \frac{\vec{a}\cdot\vec{b}}{||\vec{r}||}\frac{\vec{r}}{||\vec{r}||} = \frac{\vec{s}\cdot\vec{r}}{\vec{r}\cdot\vec{r}}\vec{r} \\]

### Vector Rejection
The vector rejection is the component of the projected vector \\( \vec{s} \\) that isn't a linear combination of projectee vector \\( \vec{r} \\) such that the vector rejection added to the vector projection equals the projected vector 
\\[ Reject_{\vec{r}}(\vec{s}) =  \vec{s} - Proj_{\vec{r}}(\vec{s}) = \vec{s} - \frac{\vec{s}\cdot\vec{r}}{\vec{r}\cdot\vec{r}}\vec{r}\\]

### Inner Product
The inner product operation a.k.a. "dot product" is defined between two vectors. This can be used to understand how "similar" two vectors are. Useful trick to seeing how similar two vectors are; take the dot product of two normalized vectors, `if=1` they are same `if=0` means they are orthogonal.
\\[ \vec{r} \cdot \vec{s} = \langle\vec{r}, \vec{s}\rangle = \sum_{k}r_i s_i \\]

### Matrix Product
The matrix product operation a.k.a "standard product" is defined between two matrices
\\[ \mathbf{C} = \mathbf{AB} \\]
\\[ C_{i,j} = \sum_{k}A_{i,k}B_{k,j} \\]

### Miscellaneous
Some miscellaneous properties general manipulation handy for gaining insight and intuition into various properties encountered
\\[ \vec{r} \cdot \vec{r} = ||\vec{r}||^2 \\]
\\[ \vec{r} \cdot \vec{s} = ||\vec{r}|| \, ||\vec{s}|| \cos{\theta} \\]


## Matrices
### Linear Transformation
I generally think of this as wanting to *transform* the plane (when in 2d) so that an initial vector \\( \vec{v} \\) can "move" to a new location \\( \vec{v}_t \\). The instruction set that details how to move a vector from one basis to another is the transform matrix.

Start with \\( \vec{v} = \tiny\begin{bmatrix} 5\\\ 7 \end{bmatrix} \\) in \\( \hat{i} = \tiny\begin{bmatrix} 1\\\ 0 \end{bmatrix}, \normalsize\hat{j} = \tiny\begin{bmatrix} 0\\\ 1 \end{bmatrix}  \\) and you want to know \\( \vec{v}_t \\) in a space where the basis is transformed to \\( \vec{i}_t = \tiny\begin{bmatrix} 3\\\ -2 \end{bmatrix}, \normalsize\vec{j}_t = \tiny\begin{bmatrix} 2\\\ 1 \end{bmatrix} \\). We can get what the transformed vector will look like in our normalized basis as such

\\[ \vec{v}_t = \begin{bmatrix} 3 & -2 \\\ 2 & 1 \\\ \end{bmatrix} \begin{bmatrix} 5 \\\ 7 \end{bmatrix} = \begin{bmatrix} 1 \\\ -17 \end{bmatrix}\\]

### Inverse
Can be thought of as doing a transformation in reverse. Think about the opposite situation above where perhaps we knew the transformation matrix above and \\( \vec{v}_t \\) but wanted to find \\( \vec{v} \\). We can use the inverse of the transform matrix to reverse what we've done.

\\[ \vec{v} = \begin{bmatrix} 3 & -2 \\\ 2 & 1 \\\ \end{bmatrix}^{-1} \begin{bmatrix} 1 \\\ 17 \end{bmatrix} = \begin{bmatrix} 5 \\\ 7 \end{bmatrix}\\]

When we take the product of a transformation and the inverse of the transformation we get the identity matrix.

\\[ \mathbf{T}\mathbf{T}^{-1} = \mathbf{I} \\]

### Composition
Can be thought of as doing one transform then another. You could do then one by one (think of performing a rotation and then a shear) or you could use the composition and transform it to the end state in one operation. This is synonymous with function composition

\\[ y = g(f(x))\,\, or \,\, v_t = s(r(v)) \\]

Assume \\( \mathbf{R,S} \in \mathbb{R}^2, \vec{v} \in \mathbb{R}^{2 \times 1}\\) where \\( \mathbf{R} \\) is the rotation transform, \\( \mathbf{S} \\) is the shear transform and \\( \vec{v} \\) as the input vector.

\\[ \vec{v}_t = \mathbf{SR}\vec{v} = \begin{bmatrix} 1 & 1 \\\ 0 & 1 \\\ \end{bmatrix} \begin{bmatrix} 0 & -1 \\\ 1 & 0 \\\ \end{bmatrix} \begin{bmatrix} x \\\ y \end{bmatrix} \\]

instead of doing the two transformations separately we, could compose them into a single transform such that \\( \mathbf{C} \\) is our composition matrix that combines the rotation and shear transform

\\[ \vec{v}_t = \mathbf{SR}\vec{v} = \mathbf{C}\vec{v} = \begin{bmatrix} 1 & -1 \\\ 1 & 0 \\\ \end{bmatrix} \begin{bmatrix} x \\\ y \end{bmatrix} \\]

Now is a good time to remind ourselves the matrix product is not commutative. It's easy to intuit from the rotation shear example above (its why I picked it :) )
\\[ \mathbf{SR} \ne \mathbf{RS} \\]

### Singular / Degenerate
This is a matrix that can't be inverted. A reason for this is the transformation reduces the basis *perhaps it collapses a whole set of vectors in the input to a lower dimension in the output* such as that happens when an entire line of input vectors are collapsed into a point. It can't be inverted because by definition a function can only map 1 input to 1 output and in order to undo the collapse you would have to map 1 output to multiple inputs. Something that a function can't do.

Square matrices are singular if their determinant is 0

### Determinant
Is a scalar of a matrix that describes how the area of any object in the transformed space has changed due to the transformation. By paying attention to how one square transforms, you'll know how any object has transformed.

Determinant of 0 suggests that the transformation has collapsed into a lower dimension (no longer at full rank) and that the system of equations are linearly dependent. We can't reverse this with a function so it doesn't have an inverse.

Determinant which is negative "flips" the space the object is on across one of the basis (this is how I think about it)