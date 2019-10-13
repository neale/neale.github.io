---
layout: default
---

I'm Neale Ratzlaff, I'm a Deep Learning and Computer Vision researcher
I'm current interning at Horizon Robotics, working on exploration in deep reinforcement learning

I live in Corvallis, originally from Portland - all in Oregon &#x1F332;.

I'm currently a PhD candidate under Dr. <a href="https://web.engr.oregonstate.edu/~lif/" class="landing-link">Fuxin Li</a> at Oregon State University</p>
I'm broadly interested in variational inference, generative models, adversarial defenses, and information geometry. Broadly, I want to create AI agents which we can trust. This means I spend a lot of time thinking about uncertainty, alignment, and paperclips.

        
I've worked at Horizon Robotics, [Intel](https://vimeo.com/170280447), and [Tektronix](https://www.tek.com/)


# Papers

### [HyperGAN: A Generative Model for Diverse Performant Neural Networks.](http://proceedings.mlr.press/v97/ratzlaff19a/ratzlaff19a.pdf) **Ratzlaff**, Fuxin (ICML 2019)

Code: [HyperGAN Github repo](https://github.com/neale/HyperGAN)

We learn an implicit ensemble using a neural generating network. Trained by maximum likelihood, the generator learns to sample from the posterior of model parameters which fit the data. 
The generated model parameters achieve high accuracy, yet are distinct with different predictive distributions. 
We enforce diversity by regularizing the intermediate representations to be well-distributed, while not harming the flexibility of the output distribution.  
<div style="text-align:center"><img src="/hypergan.png" /></div>

---------

### [Unifying Bilateral Filtering and Adversarial Training for Robust Neural Networks.](https://arxiv.org/abs/1804.01635) **Ratzlaff**, Fuxin (_arxiv_ preprint) 2018

Code: [Github repo](https://github.com/neale/adversarial-toolbox)

We use an adaptive bilateral filter to smooth the purturbations left by adversarial attacks. We view our method as a piecewise projection of the high frequency perturbations, back to the natural image manifold. Our method is simple, effective, and practical, unlike many other projection defenses

![BFNet](/BFNet.png)

---------

# Theses


### [Methods for Detection and Recovery of Out-of-Distribution Examples.](https://ir.library.oregonstate.edu/concern/graduate_thesis_or_dissertations/mw22vb88d) M.S. Degree Computer Science. Oregon State University (2018)

<div style="text-align:center"><img src="/class.png" /> <a       /> <img src="/density.png"/> </div>

---------

# Code

I maintain and work on various other projects, all deep learning related. Pretty mnuch all of them are in PyTorch. 

* [Adversarial Autoencoders](github.com/neale/adversarial-autoencoders)
* [Improved Wasserstein GAN](github.com/neale/Improved-WGAN)
* [Compositional Pattern Producing Networks](github.com/neale/CPPN)

---------



<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```