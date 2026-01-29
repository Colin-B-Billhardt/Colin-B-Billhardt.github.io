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

```python
import torch
import torch.nn as nn

class Net(nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = nn.Linear(28, 28)
        self.fc2 = nn.Linear(28, 10)

    def forward(self, x):
      x = torch.relu(self.fc1(x))
      return self.fc2(x)
```

In the code block above, I've defined our class with the constructor function and the forward function. The constructor function is where we define our model architecure, namely the amount and size of our layers. Going through the constructor function line by line, you will first see that we have called the initialization functioun from the super() class. This line executes the initialiation function from the nn.Module class which we are inheriting from. Next we are defining our layers. To define the structure of a layer we need to define two parameters: the input size and the output feature size. Also note that the input size of a layer must match the output size of the previous layer. 

The forward function defines our forward propogation behaviour. Without it, we wouldn't be able to calculate the output of our model. The first line in the function is applying the ReLU activation function to the output of the fc1 layer. In the next line we return the output of the fc2 layer which takes the activation ouput we calculated in the line before as input.

So far this should all make sense. Next we will be going through how to load our data.

```python
from torch.utils.data import Dataset
from torchvision import datasets
from torchvision.transforms import ToTensor

training_data = datasets.FashionMNIST(
    root = "data", 
    train = True,
    download = True,
    transform = ToTensor()
)

test_data = datasets.FashionMNIST(
    root = "data",
    train = False,
    download = True,
    transform = ToTensor()
)
```
To better understand better what each library is used for, I have only imported the necessary libraries for each code block however, you are free to import all libraries at the begining if you are following along at home. It is often easier to work with data if we load it directly from PyTorch instead of downloading the dataset from online. 

```python
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr = 0.01) #our optimizer is applying the weights update formula?

from torch.utils.data import DataLoader

#we need the train loader to turn the label into a tensor (plus some other stuff?) also turns data into batches
train_loader = DataLoader(training_data, batch_size=64, shuffle=True) 
```
In the above code snippet we defining our loss function, which in this case is Cross Entropy Loss, as well as our optimizer. The optimizer has the job of adjusting the weights in our model and therfore takes the model.parameters() function, and a learning rate as inputs.

To transform our data such that it is split into smaller batches (to improve the run-time of our model) we use the DataLoader function. It also helps transform our labels (true output values) from integers into tensors.

```python
for epoch in range(5): 
    for input, label in train_loader:
    
        output = model(input)
        
        loss = criterion(output, label)
        

        #backward pass

        optimizer.zero_grad()
        loss.backwards()
        optimizer.step()
```

Finally we have reached training loop. This is the final piece of our puzzle. Our first loop is for each epoch we want to train the model for while the next loop is iterating through the inputs and labels of our training data (which is in our train_loder variable). Our model prediction is called by passing the training input into the model instance and the loss is then calculated by passing the output and the target output into our criterion. 

Now we have calculated the forward pass as well as the loss its time for us to begin the backward pass. The last 3 lines of code in our training loop succintly accomplish this. Optimizer.zero_grad() stores the gradients while loss.backwards() calls the backwards function from the nn.Module class and optimzer.step() is applying the weight update formula to all of our trainable parameters.

------
