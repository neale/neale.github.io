---
layout: post
title:  "The Super Effectiveness of Convolutional Neural Nets"
date:   2016-07-14 23:25:05
categories: NN
image: true
---



<!--To start off this **Blog** I thought I would give a history of where Ive been on my short ourney so for, starting with my first encounter with a neural net. A year or so ago I came across an npm package called Synaptic which gives some functions for defining the behavior of artificial neurons.-->

{% if page.image %}
<div class="post-img">
<p align="center">  
<img class="img-responsive img-post" src=" {{site.baseurl}}/img/synapse.jpeg "/>
</p>
</div>
{% endif %}

Prologue
===========

Neural networks have become so pervasive in the machine learning community that I began to wonder if they were really worth all the hype. There are daily publications on arXiv
and on Hacker News about new deep learning techniques and new architectures. Many of these are grad students applying neural networks to a job that doesn't need their 
special sauce. But there are two areas in particular where neural nets have provided such a boost in ability, that its not even fair to compare them to conventional 
machine learning models: object recognition and natural language processing. Object recognition in particular exploded the field of deep learning when Alex Krizhevsky 
trounced the competition at ILSVRC of 2012. Alexnet was an 8 layer convolutional neural network that achieved over 20% better top-5 error on imagenet than the next leading entry. 
This is the equivilant of a toddler competing against a slightly senile old man. It may not seem like a lot, but this advancement was unprecedented and lit a fire of 
research in the computer vision community. 

For my machine learning class in my undergrad I implemented a CNN in Torch and compared it to standard image recognition techniques like Nearest Neighbor clustering and Kernel SVMs. 
I compared the models on the cifar-10 and MNIST datasets. MNIST is a dataset of 60000 images, each of a handwritten digit 0-9. The images are sized 32x32 binary pixels, for a total of 1024 
dimensions. In terms of images this is extremely low dimensional data and makes for a simple, small model. Cifar-10 however, contains RGB images of 10 classes of objects, shown in 
different scales, translations, and rotations. Cifar images have 3072 dimensions, but there are far more latent features contained that need to be extracted. Recognizing airplaces 
in multiple different positions requires a different approach than being able to differentiate different binary images of digits. 

Models
-----------

For MNIST here is the code that I used to generate a fast implementation of a feed forward neural network and a Nearest Neighbor classifier in python and scikit-learn. 
I made these models small because I had a hunch that a simple algorithmm would all that would be required to classify the digits correctly.



```python
def load_data():
  mnist = fetch_mldata('MNIST original')
  X, y = mnist.data / 255., mnist.target
  X_train, X_test = X[:60000], X[60000:]
  y_train, y_test = y[:60000], y[60000:]
  return X_train, X_test, y_train, y_test

def build_clf(X, y, clf_class, **kwargs):
  """build any classifier that implements a fit method with
  given parameters"""

  clf = clf_class(**kwargs)
  clf_fit = clf.fit(X, y)
  return clf_fit


if __name__ == '__main__':
  X_train, X_test, Y_train, Y_test = load_data()
  KNN_hyperparams = {
      'n_neighbors' : 9,
      'n_jobs'      : -1,
      'algorithm'   : 'auto',
      'p'           : 1,
      'leaf_size'   : 10
  }
  MLP_hyperparams = {
      'hidden_layer_sizes' : (512,4),
      'activation'         : 'relu',
      'algorithm'          : 'sgd',
      'batch_size'         : 'auto',
      'alpha'              : 0.01,
      'max_iter'           : 500,
      'verbose'            : True
  }
  print "building KNN"
  knn = build_clf(X_train, Y_train, KNN, **KNN_hyperparams)
  print "KNN Training set score: %f" % knn.score(X_train, Y_train)
  print "KNN Test set score: %f" % knn.score(X_test, Y_test)

  print "building MLP"
  mlp = build_clf(X_train, Y_train, MLPClassifier, **MLP_hyperparams)
  print "MLP 1 Training set score: %f" % mlp.score(X_train, Y_train)
  print "MLP 1 Test set score: %f" % mlp.score(X_test, Y_test)
```


The rest of the code can be found [here](https://github.com/neale/ConvNet/blob/master/linearClassifier/KNN_MLP.py) if you want to implement it yourself.
The neural network took 30 minutes to converge, running on a NVIDIA GTX 970. From there it could do a forward and backward pass in 50+ ms to classify an example. 
If all of this is gibberish you should read my [simplified neural network](http://neale.github.io) post. Both models preformed better than 95%, which is what is expected of human
participants in an equivilant task. 

The Convnets I used were of two different architectures, a small one for MNIST and a deeper network for cifar-10. The MNIST convnet had few weights (60k) and was 
lightly regularized, while the deeper net was a VGG16-style net which was heavily regularized with 16 layers. Here are the presented architectures for both of the convnets


{% if page.image %}
<div class="post-img">
<p align="center">
<img class="img-responsive img-post" src=" {{site.baseurl}}/img/conv_architectures.png" width="600" height="1400" />
</p>

</div>
{% endif %}


For both architectures I used small convolutional filters to minimize parameter growth in such a deep network
if you want to know more details about the architecture I have a research paper posted [here](http://github.com/neale/convnet/blob/master/effect-model-complexity.pdf)
that you should read. The CNN trained for a few hours on MNIST, and for two days on cifar-10 until it finally converged. The results were well worth the wait. 

Here is the larger Convnet model that I used to classify cifar-10, written in torch


```lua

local vgg = nn.Sequential()

-- building block conv layer function
-- One conv layer with a ReLU, 
-- Maybe try and optimize with a leaky ReLU to prevent dead neurons 

local function ConvReLU(nInputPlane, nOutputPlane)
  vgg:add(nn.SpatialConvolution(nInputPlane, nOutputPlane, 3,3, 1,1, 1,1))
  vgg:add(nn.ReLU(true))
  return vgg
end

-- heavy regularization with a .6 dropout probability

ConvReLU(512,512):add(nn.Dropout(0.6))
ConvReLU(512,512):add(nn.Dropout(0.6))
ConvReLU(512,512)
vgg:add(MaxPooling(2,2,2,2):ceil())
vgg:add(nn.View(512))

-- terminate the conv network with a fully connected neural network
-- linear FC units act as a classifier, to consolidate the conv-feature maps into 10 classes
-- final softmax to generate negative log probabilities for each class

clr = nn.Sequential()
clr:add(nn.Dropout(0.5))
clr:add(nn.Linear(512,512))
clr:add(nn.ReLU(true))
clr:add(nn.Dropout(0.5))
clr:add(nn.Linear(512,10))
clr:add(criterion.LogSoftmax())
```


Here are the model results from the benchmarks I ran:



## Testing Configuration

Models were trained and tested the same system

* i7 6700K

* GTX 970

* 32GB DDR4


## Model Benchmarks (Top 1)

{% if page.image %}

<div class="post-img">
<img class="img-responsive img-post" src=" {{site.baseurl}}/img/conv_stats.png" align="center" width="80%" height="80%" />
</div>
{% endif %}

As you can see, the convnet outpreforms every other model by a wide margin. This is because convnets encode features independant of their placement in the image. 
This allows us to train these models end to end without a object detection layer. If the feature is present, the convnet will find it no matter how the feature is translated or rotated. 

CNNs are more effective than any other model in terms of classification speed (a single forward and backward pass can be as low as 50ms), and raw accuracy. But CNNs take much more data and much longer to train than other algorithms. 
This tradeoff is further discussed [in this paper](https://github.com/neale/convnet/blob/master/effect-model-complexity.pdf)




### References:

[1] [torch](http://torch.ch/docs/package-docs.html)

[2] [Andrej karpathy's CS231n class](http://cs231n.github.io/)

[3] [cifar-10](https://www.cs.toronto.edu/~kriz/cifar.html)

[4] [MNIST](http://yann.lecun.com/exdb/mnist/)







