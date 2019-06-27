---
layout: post
title: "Reinforcement Learning Series: Introduction"
author: "Rishabh Agarwal Jain"
tags:
- Reinforcement-learning
image: "/assets/img/2019-06-25-markov-decision-process-interation.jpg"
gallery: false
comments: true
share: true
math: true
references: true
---

## What is Reinforcement Learning(RL)?

The study of decision making in the machines is called Reinforcement learning. 

## History

According to Richard Sutton Book, RL was born after merging of two independent types of research. One originated in the psychology of animal learning, while the other originated in the problem involving optimal control.

## Introduction

Every Reinforcement learning system consists of an agent and an environment. An agent is a learner or decision maker. The environment is typically a set of states the _agent_ is attempting to influence via its choice of _actions_.
The agent interacts with the environment to produce a series of states, actions and rewards at different time stamps $$S_0,A_0,R_1,S_1,A_1,R_2 ... S_T$$. The entire interaction between the agent and environment from start to terminal state is known as an episode.

## How Does the Agent learns? 

Assume a new puppy;  it receives a treat if it follows the owner's commands, and nothing in case it does not follow the command. 
The Agent(puppy) learns to perform well to the owner's command due to the rewards it is receiving. The concept of rewards is the principle behind an agent's learning.

Assume an environment in state $$S_0$$ and time stamp $$T_0$$. An agent interacting with the environment takes action $$A_0$$ using the provided information(by following a policy). At the next timestamp, as the direct consequence of the agent's choice of action $$A_0$$ and environment state $$S_0$$, the environment transitions to a new state $$S_1$$ and gives some reward $$R_1$$ to the interaction agent. Now the agent receives the new state and reward and performs a new action. This cycle goes on.

### One step Dynamics 

The agent gets a reward and the next state based on one-step dynamics of the environment. It denotes the probability of going into state $$s'$$ and getting a reward $$r$$ from the environment after performing action $$a$$ in the state $$s$$ . It is denoted as :

$$p(s', r\vert s,a) = \mathbb{P}(S_{t+1}=s',R_{t+1} = r \vert  S_t = s,A_t = a)$$

$$for \ all\ s,s',a \ and \ r $$


There are two types of tasks in RL, **episodic** and **continuing**.
Episodic tasks terminate when an agent reaches the terminal state $$S_T$$ in the environment.  An agent can start the episode again to make better decisions using the knowledge learned from the previous episode.

In Continuing tasks, an agent interacts with the environment indefinitely. Since the agent does not have the luxury to restart the episode, it has to learn the optimal way to choose an action while simultaneously interacting with the environment. 

Generally, the goal of an agent is to maximise the rewards it received. 
As the agent cannot maximise the rewards after receiving them, it has to learn to maximise the expected future rewards $$G_t$$.

**Note**: Since the agent receives rewards from the environment, it must abide by rules of the environment.

At time step $$t$$.

$$G_t = R_{t+1} + R_{t+2} .... $$

At time step t, the agent picks an action $$A_t$$ to maximise expected rewards $$G_t$$.However, since predicting the rewards in future is difficult, we add a hyperparameter $$\gamma$$ to reflect the confidence in rewards.

$$G_t = R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + ..... \quad and \quad \gamma \in [0,1]$$

It is known as **discounted returns**.

## Markov Decision Process (MDP)

![MDP]({{ "/assets/img/2019-06-25-markov-decision-process-interation.jpg" |  absolute_url }} "Interation in MDP" ){:height="50%" width="75%"}_Agent Environment Interation in a MDP <br> (Image source: Sutton and Barto, Reinforcement Learning)_

A finite MDP $$(S,A,P,R,\gamma)$$ is defined by the following elements:
1. A (finite) set of states$$(S)$$
2. A (finite) set of actions $$A$$
3. The one-step dynamics of the environment.
4. A (finite) set of rewards. 
5. Discount rate $$\gamma \in [0,1] $$.

**Markov Property:** The state and the reward at any time step $$t+1$$ depends on the state at $$t$$ and action at time step $$t$$.

## Policies:

The policy is a mapping from environmental states to actions. There are two types of policies.
1. The deterministic policy is a mapping $$\pi: S\to A$$.
2. The Stochastic policy is a mapping $$\pi: S\to A \in [0,1]$$

$$ \pi (a\vert s) = P(A_t=a\vert S_t=s)$$

The above policy function accepts environment state $$S$$ and action $$A$$ and returns the probability that the agent takes action $$a$$ while in state $$S$$.

## State-Value Function.

For each time stamp, the state value function yields the expected return, if the agent started in that state and then followed the policy for all time stamps.

State value function for a policy $$\pi$$ is represented as:

$$ V_{\pi}(S) = \mathbb{E_\pi}[G_t\vert S_t = s]$$

Interestingly,  it can be computed by recursion also:

$$The \ value \ of\ any\ state = the\ immediate\ reward + the\ discounted\ value\ of\ the\ state\ that\ follows.$$

It is also known as the bellman Equation. Using bellman equation in state value function :

$$ V_\pi(s) = \mathbb{E_\pi}[R_{t+1} + \gamma V_\pi (S_{t+1})\vert  S_t = s]$$

If the agent's policy $$\pi$$ is deterministic, then,

$$V_\pi(s) = \sum_{s' \in S^+ , r \in R} p(s',r\vert s,\pi(s))(r+\gamma V_\pi(s')) $$

Here we  multiply the reward and the discounted value of the next state 
$$( r + \gamma V_\pi(s')$$ by its corresponding probablity 
$$ p(s',r\vert s,\pi(s))$$ and sum over all possibilities to yeild the expected value.

If the agent's policy $$\pi$$ is stochastic, then,

$$V_\pi(s) = \sum_{s' \in S^+ , r \in R,a \in A(s)} \pi(a\vert s)p(s',r\vert s,\pi(s))(r+\gamma V_\pi(s')) $$

### Optimality

$$ \pi ' >= \pi $$ if and only it $$V_{\pi '}(s) >= V_\pi(s)$$ for all $$ s \in S$$. An optimal policy $$\pi'$$ satisfies $$ \pi ' >= \pi $$ for all $$\pi$$.

**Note:** An optimal policy is guaranteed to exist, but may not unique.

## Action-value Function

An action value function for a policy $$\pi$$ is denoted by $$q_\pi$$.The value of taking action $$a$$ in state $$s$$ under policy $$\pi$$ is:

$$q_\pi(s,a) = \mathbb{E_\pi}[G_t\vert S_t = s , A_t = a]$$

i.e.

$$q_\pi(s,a) = \mathbb{E_\pi}[R_{t+1} + \gamma V(S_{t+1})\vert S_t = s , A_t = a]$$

For a deterministic policy $$\pi$$ :

$$V_\pi(s) = q(s,\pi(s)) \ holds \ for \ all \ s\in S$$

Optimal value function can derived from the optimal action value function by:

$$ V^*(s) = \max_{a \in A(s)} Q^*(s,a)$$

$$where \ Q^*(s,a) = \mathbb{E_\pi}[R_{t+1} + \gamma V^* (S_{t+1})\vert S_t = s , A_t = a]$$

$$ \Rightarrow  Q^*(s,a) = \mathbb{E_\pi}[R_{t+1} + \gamma \max_{a' \in A(s)} Q^*(s_{t+1},a')\vert S_t = s , A_t = a]$$

The optimal policy $$\pi^*$$ can be easily obtained from the optimal action-value function $$q^*$$.

$$Interaction \longrightarrow q^* \longrightarrow \pi^*$$

$$\pi^*(s) = argmax_{a\in A(s)}\ q^* (s,a) \ for \ all \ s\in S $$

**Note:** All optimal policies have same action value function $$q^*$$ called optimal action-value function. Moreover, In the case of two actions having the same optimal value function, assign either or all with equal probabilities in the policy. 


