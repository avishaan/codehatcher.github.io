---
title: "Ceiling Analysis to Evaluate Optimization Potential " 
excerpt: "Focusing on the module with the most potential gives direction on where to optimize the model pipeline"
categories:
  - machine learning
  - engineering strategy
tags:
  - ml
  - engineering strategy
  - optimization
  - ceiling analysis
toc: true
toc_sticky: true
date: 2019-1-11
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
<script async src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>

## Intro
Ceiling analysis is a rational method to understand the maximum potential of a machine learning pipeline. I have used the below to direct an engineering and product team successful in prioritization of work. It can allow at least two strategies to emerge
1. What opportunity is there on the product side to fulfill the requirements?
2. Where should the engineering team focus their development efforts for the maximum performance increase?

### Product Consideration
Knowing the potential of a machine learning pipeline allows the product team to coordinate with business, users, and designs to manage expectations. If the ceiling analysis determines a module is unable to reach a performance level specified in a requirement or user story, adjustments can be made and new requirements prioritized.

### Analysis
Assume the following contrived machine learning pipeline where intermediate steps must be performed until `predict_age` and `predict_reaction` (facial reaction) can be performed. Assume an overall accuracy for each prediction at 80% for simplicity

<div class="mermaid" font-size='50px'>
graph TD
	A(input_image) --> B(remove_background)
	B --> C(detect_face)
	C -->D(detect_eyes)
	C -->E(detect_nose)
	C -->F(detect_mouth)
  D & E & F --> G(predict_reaction)
  D & E & F --> H(predict_age)
</div>


To decide where engineering time should be spent a ceiling analysis should be performed to see where in the machine learning pipeline has the most opportunity for improvement. This is done by assuming that an individual component has a 100% accuracy rate and see how that affects the entire pipeline. There is a component to this that comes from understanding the standard of art, this only focuses on the numbers.

|Pipeline Component|Accuracy|Opportunity
|----|----|----|
|Overall|80%|N/A|
|`remove_background`|80.1%|0.1%|
|`detect_face`|81.2%|1.1%|
|`detect_nose`|89.9%|8.7%|
|`detect_mouth`|93.2%|3.2%|
|`predict_reaction`|100%|6.8%|

From this quick analysis, we see which component has the largest opportunity for improvement. The caveat to this is mentioned in the outro. What is clear from the ceiling analysis is the `remove_background` module works as well as it can and has minimal opportunity for improvement.

## Considerations & Nuance
There are a couple of other considerations not mentioned in standard ceiling analysis and that is the understanding of the current state of art. As an example, even if an individual component has a low accuracy rate, perhaps it is still state of the art and has no room for improvement. Personally, I'll assign it an additional score and take that into account when doing my analysis. I find this is helpful when discussing as a team the next steps. 
It's also important to consider the product impact as that can give alternate insight on where to focus efforts.

## Outro
This is another lesson in **don't trust your intuition if you have another option**. Intuition and experience can be wrong at times, it can't hurt to spend a couple of minutes doing a quick check before spending weeks performing a task. I adopted this technique from the book *The Pragmatic Programmer* and just applied it to the machine learning domain. I believe it can be applied to many engineering disciplines.