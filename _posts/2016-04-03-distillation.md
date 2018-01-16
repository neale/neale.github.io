---
layout: post
title:  "Breaking Defensive Distillation with L-BFGS"
date:   2017-05-12 23:25:05
categories: NN 
image: true
mathjax: true
---

Defensive distillation was a good idea: the authors basically fuzz the gradients of the network by training a second smaller network on the softmax outputs of the original network. 

So that a training sample of the second network has a distribution of $$\textit{soft labels}$$ assigned as the label, instead of a single hard label where $$ \hat{y} = \textit{argmax}(f(x)) $$. This increases the number of features that need to be changed by an adversarial attack, in order to change the output label. That's a high level overview, I recommend the actual paper [here](https://arxiv.org/pdf/1511.04508.pdf)


This worked pretty well at first, until it was broken by [Carlini and Wagner](https://arxiv.org/pdf/1607.04311.pdf) with an iterative method that targets logits instead of the softmax output. 
Distillation relies heavily on the temperature of the primary network in order to train the distillation net. 
Which controls the distribution of soft labels that each example is assigned. 
Recap: a softmax output creates a $$[0, 1]$$ normalized distribution from the incoming logits. 

$$ F(y = \textit{softmax}(Z(\theta, x) / T)$$

$$ \textit{softmax}() = \frac{e^{zj}}{\sum_{k} e^{z_k}} $$

Where the temperature $$T$$ controls the shape of the output distribtion. 
When $$T \rightarrow \infty$$ the output becomes uniform, when $$T \rightarrow 0$$ the distribution become unimodal. 


