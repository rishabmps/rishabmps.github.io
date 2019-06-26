---
layout: post
title: "Generative Adversarial Networks"
author: "Rishabh Agarwal Jain"
tags:
- GANs
image: "/assets/img/thumbnail/saddle_min.jpg"
gallery: false
comments: true
share: true
math: true
---


Generative Adversarial Networks, commonly referred to as GANs, are a combination of two networks that are regularly trying to outbid each other. GANs are based on a game theory scenario where the generator network($$G$$) competes against the discriminator network(D). They were first introduced in the year $$2014$$ by the team of researchers at the University of Montreal, Canada (Goodfellow et al., 2014c)<sup>[1]</sup>.

GANs can be used in visual as well as non-visual domains.  Most GAN research papers from the silicon valley companies and associated research labs talk about visual(Computer Vision) applications of GANs. Very few research papers cator to non-vision applications of GANs. Hence, there is a vast potential for research in the field.

For now, Let's focus on the visual domain.

## How does a GAN model work?

GAN take a random noise as an input to the model and produces realistic looking images using a differentiable function called discriminator. Choice of input noise vector varies the output image. 

Generator's goal is to ult as there are no correct labels for the generated picture and, no clear way to compute the loss that will maximize the probability to re-create a training data set.

Here comes the role of a discriminator in GANs. It is a standard image classifier ( usually CNN based) trained to distinguish generated images from the real ones. It assigns a probability near $$0$$(zero) to the generated images and near $$1$$(one) to the authentic images from training dataset. On the other hand, the generator tries to output images which the discriminator will assign a near $$1$$(one) probability in its current state. Hence, the term adversarial in GANs, it highlights that the two networks compete with each other.

[Insert Image](Image)

The generator takes a random noise value z and maps it to the output value x. Wherever the generator(G) assigns more values of z, the probability distribution over x, represented by the model(G) becomes denser. Meanwhile, the discriminator(D) outputs high values wherever the density of the real data is greater than the generated data.

The generator changes the sample it produces to move uphill along the function learned by the discriminator(D). It moves the samples into the area where the model distribution is not yet dense enough.

Eventually, at convergence, the generator's distribution matches the real data distribution, and then the discriminator outputs a probability of $$\frac{1}{2}$$ everywhere. As a result, every point in the distribution is like to both generated as well as real dataset image. This state of the system is known as the Nash equilibrium.

## Nash Equilibrium.

<blockquote>
    <p> Given a stable state of systems, involving, the interactions of different participants, in which no participant can gain with a unilateral change of strategy if the strategy of others remain unchanged.  Such systems are said to be in the state of Nash Equilibrium.</p>
</blockquote>

For Example:

Consider a state of two players playing the game of rock-paper-scissors, and choosing their moves randomly from three choices with equal probability. This state would be in Nash equilibrium as no player can increase their chances of winning by altering their strategy, given that the opponent still chooses randomly. 

Generally, in neural networks, model parameters are plotted against a loss function, and an optimizer is used to identify weights for which the loss is minimum. On the other hand, GANs consist of two different loss functions, one for the discriminator and the other for generator.

For a value function Fn, the generator would like to minimize it, and the discriminator would like to maximize it. Given this situation, it may be possible to obtain a state of Nash equilibrium where the system is at maximum with respect to the discriminator and minimum with respect to the generator.  It means that the system is in a saddle point.

![Generator Minimum]({{ "/assets/img/thumbnail/saddle_min.jpg" | absolute_url }} "Saddle Point for generator" ){:height="50%" width="75%"}_Minimum with respect to the generator_ 

![Discriminator Maximum]({{ "/assets/img/thumbnail/saddle_max.jpg" | absolute_url }} "Saddle Point for generator" ){:height="50%" width="75%"}_Maximum with respect to the discriminator_

Above images are generated from the Matlab code below.

<script src="https://gist.github.com/rishabmps/36fef4c3e1750890ef18fa27a2e4099f.js"></script>

If both networks are big enough, then equilibrium can be reached. However, practically it is a daunting task, and more often then not, convergence is not achieved. Hence, designing an algorithm for finding the equilibrium of GAN involving high dimensional continuous cost function is still a niche research problem.

