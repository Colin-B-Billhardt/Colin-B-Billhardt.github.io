---
title: 'PyTorch Guide'
date: 2013-08-14
permalink: /posts/2013/08/pytorch-guide/
tags:
  - Learning
  - Guide
  - Machine Learning
---
An adequate guide to becoming adequate with PyTorch
======

You've just learned the basics of neural networks in your college class and are now eager to train models to predict or classify anything that crosses your mind. You quickly search for a dataset and realise that almost everyone recommends you start with MNIST or CIFAR10. These names mean nothing to you but you take the first step and download MNIST. You expand the zip folder and realise it's a dataset of handwritten digits. "This should be easy" you tell yourself - you open up your IDE of choice and get ready to code a NN that correctly classifies the handwritten digits . You stare blankly at the screen - you know what you need: hidden layers, an activation and a loss function, and some arbitrarily small LR but for some reason you can't figure out how to start. What library should I use? How do I make layers? How does the back propagation work?

If this sounds familiar then don't worry as you're not alone. This is exactly how I felt after I naively thought I had learned everything after my ML2 course at University. In this article I will be walking through how to build your first basic NN using the MNIST dataset as well as explaining what each line of code does and why it's needed.

Firtly we need to decide what library we're going to use. As you can tell from the title of the article, we will be using PyTorch as this is the simplest but also one of the most robust and featurefull libraries Python offers. If you wish to learn how to use TensorFlow or Keras, there are plenty of good tutorials available online. 

So, we begin with deciding on roughly what the specifications of our model (we can tweak and adjust certain parameters later!). We know that MNIST is a classification problem with 10 possible target classes (0–9). This tells us a few key things about how our model needs to be designed. Firstly, we need to choose a loss function that fits our data. Since we are dealing with multiple target classes - cross-entropy loss is ideal. Secondly our activation function, which if you recall your classes, introduces non-linearity into the model needs to be carefully chosen.

Okay, you have now made some key decisions regarding your model architecure but now you've actually got to code it somehow. In PyTorch this is done by defining a class which has two main functions:


------
