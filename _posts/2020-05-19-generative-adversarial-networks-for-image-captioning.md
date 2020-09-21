---
layout: post
title: "Generative Adversarial Networks for Image Captioning"
description: "Guide to setup readonly mode for some users in django admin"
tags: [ Generative Adversarial Networks, Discrete Data, Image Captioning]
comments: true
---

This framework is composed of two networks, generator and discriminator which are trained adversarially. The generator networks competes with discriminator network to generate data which seems to be sampled from true data distribution and discriminator is supposed to differentiate the real data from generated data.  

This framework alleviates the requirement of explicitly defining a loss function for training. The generator network is trained using adversarial loss through discriminator. The discriminator network predicts whether the generated data is real or fake, based on its correctness and a binary cross-entropy loss is back-propagated. 
    
![](https://paper-attachments.dropbox.com/s_AED4B87E96906FCFAAB13C3BF56A15999CB759039A1AB629C5F835691E1D9373_1589865007418_image.png)

For back-propagation adversarial loss to generator network, end-to-end differentiability need to be ensured. As a consequence the generative network can be used to model only continuous distribution in the current framework. For example : The generation of images using GANs has been highly successful due to image data being continuous variable. 

### Problem of Discretization of Language
Generating words is not same as generating images
images can be represented using continous pixels but words can't be 
we can actually represent words using continous representation such as word2vec but then at time of mapping back these vectors to word can be problematic. 
you will predict a vector which won't be exact same to any of the vectors so you will maybe try knn or cosine similarity to find the vector closest to your predicted vector this can be inaccurate and at the same time computationally inefficient. 

### Using Policy Gradients for Image Captioning 
In reinforcement learning formulation of Image Captioning, generation of sequence of words can be considered as actions which is guided by a policy $$\pi_\theta$$.

