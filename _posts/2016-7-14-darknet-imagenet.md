---
layout: post
title:  "Realtime Object Recognition and Localization"
date:   2015-01-12 23:25:05
categories: NN
image: true
---

<!-- Buffer -->


{% if page.image %}
<div class="post-img">
<img class="img-responsive img-post" src=" {{site.baseurl}}/img/darknet.png"/>
</div>
{% endif %}
 

{% if page.image %}
<div class="post-img">
<p align="center">  
<img class="img-responsive img-post" src=" {{site.baseurl}}/img/TBA.png "/>
</p>
</div>
{% endif %}


One of the worst things about deep learning is the ubiquity of Nvidia. No matter how many hopefuls cry AMD, there is no software stack
that can outpreform CUDA when it comes to training and deploying deep neural networks. GPUs are densely noded, which means they have hundreds
of low-compute execution cores that can chunk through parallelized problems much faster than a normal CPU. CPUs may have even 16 to 32 cores,
but their increased capability is wasted on doing simple matrix multiplication. The thing about deep nets, is that they need *lots* of 
matrix multiplication. With a GPU, training a neural network with millions of parameters can take days instead of months. For the largest 
models, like training on the ILSVRC imagenet dataset, training on a CPU would take years. Because of this difference in capability, 
scientists and engineers do not even consider using a CPU for training or deployment, because they can see a 100x increase in speed with a 
GPU. 

# Refinement
Always in technology we improve and refine. Often imporvement comes with high power consumption and large form factors. Computers in the 
1960s were monolithic machines that consumed vast amounts of power. The IBM Electronic Multiplier consumed 8000W and cost $5000 dollars (2016)
a month to rent. `

But I think I've done better than anyone else, 
Hardware acceleration coming soon.................

