---
layout: post
title: "Reinforcement Learning Series: Dynamic Programming"
author: "Rishabh Agarwal Jain"
tags:
- Reinforcement learning
image: "/assets/img/thumbnail/saddle_min.jpg"
gallery: true
comments: true
share: true
math: true
---

## Markov Decision Process (MDP)

A finite MDP $$(S,A,P,R,\gamma)$$ is defined by the following elements:
1. A (finite) set of states$$(S)$$
2. A (finite) set of actions $$A$$
3. The one-step dynamics of the environment.
4. A (finite) set of rewards. 
5. Discount rate $$\gamma \in [0,1] $$.

**Markov Property:** The state and the reward at any time step $$t+1$$ depends on the state at $$t$$ and action at time step $$t$$.