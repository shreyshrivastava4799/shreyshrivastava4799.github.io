---
layout: post
title: "Generative Adversarial Networks for Image Captioning"
description: "Different ways GANS are being used for Image Captioning."
tags: [ Generative Adversarial Networks, Discrete Data, Image Captioning]
comments: true
---

This framework is composed of two networks, generator and discriminator which are trained adversarially. The generator networks competes with discriminator network to generate data which seems to be sampled from true data distribution and discriminator is supposed to differentiate the real data from generated data.  

This framework alleviates the requirement of explicitly defining a loss function for training. The generator network is trained using adversarial loss through discriminator. The discriminator network predicts whether the generated data is real or fake, based on its correctness and a binary cross-entropy loss is back-propagated. 
    
![](https://paper-attachments.dropbox.com/s_AED4B87E96906FCFAAB13C3BF56A15999CB759039A1AB629C5F835691E1D9373_1589865007418_image.png)

For back-propagation adversarial loss to generator network, end-to-end differentiability need to be ensured. As a consequence the generative network can be used to model only continuous distribution in the current framework. For example : The generation of images using GANs has been highly successful due to image data being continuous variable. 

### Problem of Discretization of Language
In generating textual data (or for any discrete data in general) using GANs, back-propagating gradient estimates for generator would not be defined. The problem is the discrete representation of language in natural language processing. But the problem with using continuous representation is, mapping those vectors back to words, which is implicitly handled in images. 


**How is textual data discrete and problems it causes in back-propagation?**
The generator networks for Image Captioning (or text generating in general) have an LSTM network for language modeling followed by a softmax classifier that outputs a probability distribution for the next word over the vocabulary. This makes the language representation discrete (definition of discrete variable) as only one among the fixed number of words can be selected. 

GANs work by training a generator network that outputs synthetic data, then running a discriminator network on the synthetic data. The gradient of the discriminator network’s output concerning the synthetic data tells you how to change the synthetic data to make it more realistic. You can make slight changes to the synthetic data only if it is based on continuous numbers. If it is based on discrete numbers, there is no way to make a slight change. 

For example, if you output an image with a pixel value of 1.0, you can change that pixel value to 1.0001 on the next step. If you output the word “penguin”, you can’t change that to “penguin + .001” on the next step because there is no such word as “penguin + .001”. You have to go all the way from “penguin” to “ostrich”. [Check this out!](https://www.reddit.com/r/MachineLearning/comments/40ldq6/generative_adversarial_networks_for_text/)

The output word is one with the maximum probability, so it could be thought of as a step function after the softmax layer, which makes dimensions other than the one represented by the “output word” zero. And we already know that step function has gradient zero almost everywhere; thus, propagating gradients through this layer wouldn’t be possible.


         