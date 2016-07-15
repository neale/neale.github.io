---
layout: 
title:  "The Super Effectiveness of Convolutional Neural Nets"
date:   2016-07-14 23:25:05
categories: Object Recognition
image: true
---



To start off this **Blog** I thought I would give a history of where Ive been on my short ourney so for, starting with my first encounter with a neural net. A year or so ago I came across an npm package called Synaptic which gives some functions for defining the behavior of artificial neurons.

{% if page.image %}
<div class="post-img">
<img class="img-responsive img-post" src=" {{site.baseurl}}/img/synapse.jpeg "/>
</div>
{% endif %}

Specifically, Synaptic is a javascript library that offeres highly abstracted views on NN functionalities. The easiest demo offered is a MLP (multi layered perceptron) that can learn the functionality of an XOR gate. 

Here is the MLP that trains an XOR gate: 

<h1>XOR1.js</h1>

<div class="highlight"><pre><span class="o">&gt;&gt;&gt;</span> <span class="n">help</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>
<span class="n">Help</span> <span class="n">on</span> <span class="nb">int</span> <span class="nb">object</span><span class="p">:</span>
<span class="p">(</span><span class="n">etc</span> <span class="n">etc</span><span class="p">)</span>

<span class="o">&gt;&gt;&gt;</span> <span class="nb">dir</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>
<span class="p">[</span><span class="s">&#39;__abs__&#39;</span><span class="p">,</span> <span class="s">&#39;__add__&#39;</span><span class="p">,</span> <span class="o">...</span><span class="p">]</span>

<span class="o">&gt;&gt;&gt;</span> <span class="nb">abs</span><span class="o">.</span><span class="n">__doc__</span>
<span class="s">&#39;abs(number) -&gt; number</span>

<span class="n">Return</span> <span class="n">the</span> <span class="n">absolute</span> <span class="n">value</span> <span class="n">of</span> <span class="n">the</span> <span class="n">argument</span><span class="o">.</span><span class="s">&#39;</span>
</pre></div>
</code>


Easy right? But wait, this is javascript. Surely as a neural net is scaled this will become extremely slow, you have to pay the price for abstraction. Its the law of equivilant coding exchange. Lets dig into how this is acheived so easily with javascript what is usually so confusing in Matlab or C++. This is only feasible because of the underlying C++ core of node. In order to acheive measurable performance upgrades, typically either algorithms must be optimized, or choose a faster "to the metal" language. Luckily, node being s the best of both worlds, it has compiled C++ where speed matters, and javascript where it might not. Here is an implementation of the same MLP in pure C++



