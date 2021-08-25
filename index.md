---
layout: default
---

I'm Neale Ratzlaff, &#x1F332; &#x1F332; a Deep Learning and Computer Vision researcher, working on Bayesian deep learning, with applications to computer vision and deep reinforcement learning

I did my PhD under Dr. [Fuxin Li](https://web.engr.oregonstate.edu/~lif/) at Oregon State University.
I'm broadly interested in variational inference with implicit distributions, generative models, uncertainty quantification, and information geometry. It's important to create AI agents which we can trust, meaning I spend a lot of time thinking about alignment and paperclips.

Currently I'm interested in leveraging particle-based variational inference to create better Bayesian neural networks. We can learn these intractable distributions even for complex neural networks. The resulting distributions have numerous benefits over single models, and even bootstrapped ensembles. 
        
I've worked at [Horizon Robotics](https://horizon.ai/), [Intel](https://vimeo.com/170280447), and [Tektronix](https://www.tek.com/)
<div style="text-align:center"><img src="/images/horizon_logo.png" /> <img src="/images/intel_logo.png"/> <img src="/images/tek_logo.png"/> </div>

# News

* I successfully defended my dissertation on uncertainty quantification in deep learning with implicit distributions over neural networks

* I accepted a research scientist position at HRL Laboratories in Malibu, CA. 


# Papers

### [Contrastive Identification of Covariate Shift in Image Data](https://arxiv.org/abs/2108.08000)

 Matthew L. Olson, Thuy-Vy Nguyen, Gaurav Dixit, **Neale Ratzlaff**, Weng-Keen Wong, Minsuk Kahng (IEEE VIS) 2021,
 
We design and evaluate a new visual interface that facilitates the comparison of the local distributions of training and test data. We conduct a quantitative user study on multi-attribute facial data to compare the learned latent representations of ImageNet CNNs vs. density ratio models, with two user analytic workflows.


<div style="text-align:center"><img src="/images/vis_pic.png" /></div>

-----------------


### [Generative Particle Variational Inference via Estimation of Functional Gradients](https://proceedings.mlr.press/v139/ratzlaff21a.html)

 **Ratzlaff**<sup>☨</sup>, Bai<sup>☨</sup>, Fuxin, Xu. (ICML) 2021, 

(☨): Equal Contribution

Code: coming very soon

Slides and Talk: [ICML landing page](https://icml.cc/virtual/2021/poster/9249)
 
We introduce a new method for Bayesian deep learning: GPVI, that fuses the flexibility of particle-based variational methods, with the efficiency of generative samplers. We construct a neural sampler that is trained with the functional gradient of the KL-divergence between the empirical sampling distribution and the target distribution. We show that GPVI accurately models the posterior distribution when applied to density estimation and Bayesian neural networks. This work also features a new method for estimating the inverse of the input-output jacobian without invertibility restrictions. 


<div style="text-align:center"><img src="/images/2class-sin.png" /></div>

---------------


### [Avoiding Side-Effects in Complex Environments.](https://arxiv.org/abs/2006.06547)

 Turner<sup>☨</sup>, **Ratzlaff**<sup>☨</sup>, Tadepalli. (**NeurIPS**) 2020, **Spotlight talk**

(☨): Equal Contribution

Code: [Github Repo](https://github.com/neale/avoiding-side-effects)

We introduce reinforcement learning agents that can accomplish goals without incurring side effects. Standard RL agents collect reward at any cost, often unsustainably ruining the environment around them. The attainable utility penalty (AUP) penalizes agents for acting in a way that decreases in their ability to achieve unknown future goals. We extend AUP to the deep RL case, and show that our AUP agents can act in difficult environments with stochastic dynamics, without incurring side effects. 

<div style="text-align:center"><img src="/images/aup_paper.png" /></div>

-------------


### [Implicit Generative Modeling for Efficient Exploration.](https://arxiv.org/abs/1911.08017)

 **Ratzlaff**, Bai, Fuxin, Xu. (**ICML**) 2020

We model uncertainty estimation as an intrinsic reward for efficient exploration. We introduce an implicit generative modeling approach to estimate a Bayesian uncertainty of the agent’s belief of theenvironment dynamics.  We approximate the posterior through multiple draws from our generative model. The variance of the dynamic models' output is used as an intrinsic reward for exploration. We design a training algorithm for our generative model based on amortized Stein Variational Gradient Descent, to ensure the parameter distribution is a nontrivial approximation to the true posterior. 

<div style="text-align:center"><img src="/images/RLpaper_hypergan.png" /></div>

-------------

### [HyperGAN: A Generative Model for Diverse Performant Neural Networks.](http://proceedings.mlr.press/v97/ratzlaff19a/ratzlaff19a.pdf)

 **Ratzlaff**, Fuxin. (**ICML**) 2019

Code: [HyperGAN Github repo](https://github.com/neale/HyperGAN)

Talk: ICML Oral [Slideshare](https://slideslive.com/38917398/general-ml)

We learn an implicit ensemble using a neural generating network. Trained by maximum likelihood, the generator learns to sample from the posterior of model parameters which fit the data. 
The generated model parameters achieve high accuracy, yet are distinct with different predictive distributions. 
We enforce diversity by regularizing the intermediate representations to be well-distributed, while not harming the flexibility of the output distribution.  

<div style="text-align:center"><img src="/images/hypergan.png" /></div>

---------

### [Unifying Bilateral Filtering and Adversarial Training for Robust Neural Networks.](https://arxiv.org/abs/1804.01635)

 **Ratzlaff**, Fuxin. (_arxiv_ preprint) 2018

Code: [Github repo](https://github.com/neale/adversarial-toolbox)

We use an adaptive bilateral filter to smooth the purturbations left by adversarial attacks. We view our method as a piecewise projection of the high frequency perturbations, back to the natural image manifold. Our method is simple, effective, and practical, unlike many other projection defenses

![BFNet](/images/BFNet.png)

---------

# Theses


### [Methods for Detection and Recovery of Out-of-Distribution Examples.](https://ir.library.oregonstate.edu/concern/graduate_thesis_or_dissertations/mw22vb88d) M.S. Degree Computer Science. Oregon State University (2018)

<div style="text-align:center"><img src="/images/class.png" /> <img src="/images/density.png"/> </div>

---------

# Code

I maintain and work on various other projects, all deep learning related. Pretty much all of them are in PyTorch. 

* [Adversarial Autoencoders](https://github.com/neale/adversarial-autoencoder)
* [Improved Wasserstein GAN](https://github.com/neale/Improved-WGAN)
* [Compositional Pattern Producing Networks](https://github.com/neale/CPPN)
* [Satisfiable Neural Networks (PySMT-DNN)](https://github.com/neale/PySMTDNN)

---------

# Generative Art

Inspired by [Hardmaru](http://blog.otoro.net/), I build evolutionary creative machines. There is gallery of examples [here](./gen_art.html)

