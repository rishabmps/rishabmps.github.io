---
layout: post
title: "Reinforcement Learning Series: Dynamic Programming"
author: "Rishabh Agarwal Jain"
tags:
- Reinforcement-learning
image: "/assets/img/thumbnail/saddle_min.jpg"
gallery: false
comments: true
share: true
math: true
---

## Dynamic Programming

In Dynamic Programming, the agent has full knowledge of the Markov Decision Process(MDP) that characterises the environment. It is much easier than the reinforcement learning setting, where the agent initially knows nothing about how the environment decides states and rewards, and it must learn entirely from the interactions to build a policy.

Let us take an example of a 2X2 grid. The goal of agent is to find the optimal policy.

// Image

There are different ways to solve for the agent's goal.

## Iterative Method

Let us say that we are trying to evaluate a stochastic policy where the agent selects an action uniformly from the available discrete actions.In case of above example:

$$ i.e.\quad \pi(right|s_1) = \frac{1}{2} ,\quad \pi(down|s_1) = \frac{1}{2}$$

$$ similarly\quad \pi(left|s_2) = \frac{1}{2} ,\quad \pi(down|s_2) = \frac{1}{2}$$

$$ and\quad \pi(up|s_3) = \frac{1}{2} ,\quad \pi(right|s_2) = \frac{1}{2}$$

Now, given a policy $$\pi$$ , how to determine the $$v_\pi (s)$$ for all $$s \in S$$ .

By evaluating the Bellman equation for all states, we get the following: 

$$v_\pi (s_1) = \frac{1}{2} (-1 + v_\pi (s_2)) + \frac{1}{2} (-3 + v_\pi (s_3))$$

$$v_\pi (s_2) = \frac{1}{2} (-1 + v_\pi (s_1)) + \frac{1}{2} (5 + v_\pi (s_4))$$

$$v_\pi (s_3) = \frac{1}{2} (-1 + v_\pi (s_1)) + \frac{1}{2} (5 + v_\pi (s_4))$$

$$v_\pi (s_4) = 0$$

Aforementioned represents a system of equations with different variables. It can be solved to find the value function for all states. 

However, In a real-world situation, the number of states in an environment is enormous, making it impossible to solve using a system of equations.

## Iterative Policy Evaluation

Instead of solving the system directly, we could start with a guess for the value of each state. Then improve the guess value by iterating over states using the Bellman equation.  

For Example:

//Image 2

$$ V(s_1) \longleftarrow \frac{1}{2} (-1 + V (s_2)) + \frac{1}{2} (-3 + V (s_3))$$ 

$$ V (s_1) \longleftarrow \frac{1}{2} (-1 + 0) + \frac{1}{2} (-3 + 0) = -2$$ 

Similarly calculate $$V_2 , V_3 , V_4 $$ by using the latest state values.

The Process can continue until value function converges or does not change much. A new hyperparameter $$\Delta$$ is introduced to denote the min change required for value function update.

![Iterative Policy Evaluation]({{ "/assets/img/2019-06-26-iterative-policy-evaluation.jpg" |  absolute_url }} "Iterative Policy Evaluation" ){:height="60%" width="85%"}_Algorithm for Iterative Policy Evaluation <br> (Image source: Sutton and Barto, Reinforcement Learning)_

### Action value Estimates

To estimate acton values $$(Q)$$, we need an algorithm that accepts an estimate $$V$$ of the state value funtion $$v_\pi$$ along with the one step dynamcics of the MDP process.


<pre class="algorithm" style="display:hidden;"> 
% This quicksort algorithm is extracted from Chapter 7, Introduction 
        % to Algorithms (3rd edition)
        \begin{algorithm}
        \caption{Action Value Estimatation}
        \begin{algorithmic}
            \INPUT State-value function $V$
            \OUTPUT Action-value function $Q$
            \FOR{$s \in S$}
                \FOR{$a \in \mathcal{A}(s)$}
                    \STATE $Q(s,a) \leftarrow \sum_{s' \in S,r \in R}p(s',r|s,a)(r+\gamma V(s'))$
                \ENDFOR
            \ENDFOR
            \RETURN $Q$
        \end{algorithmic}
        \end{algorithm}
</pre>

## Policy Improvement

Given a policy $$\pi$$ we estimate the value function $$v_\pi$$ using the algorithm called Iterative Policy Evaluation. But the policy used here might not be an optimal polcy. Hence, a new method is required to update the policy $$\pi$$ to $$\pi^*$$ , such that $$ \pi^*>=\pi  $$ i.e. $$v_{\pi^*}(s)>=v_\pi(s) \ for \ all \ s \in S $$.

![Policy Improvement]({{ "/assets/img/policy_improvement.jpg" |  absolute_url }} "Policy Improvement" ){:height="50%" width="65%"}_policy improvement Process_

<pre class="algorithm" style="display:hidden;"> 
% This quicksort algorithm is extracted from Chapter 7, Introduction 
        % to Algorithms (3rd edition)
        \begin{algorithm}
        \caption{Policy Improvement}
        \begin{algorithmic}
            \INPUT MDP, State-value function $V$
            \OUTPUT Policy $\pi'$
            \FOR{$s \in S$}
                \FOR{$a \in \mathcal{A}(s)$}
                    \STATE $Q(s,a) \leftarrow \sum_{s' \in S,r \in R}p(s',r|s,a)(r+\gamma V(s'))$
                \ENDFOR
                \STATE $\pi'(s) \leftarrow \arg \max_{a \in \mathcal{A}(s)} Q(s,a)$
            \ENDFOR
            \RETURN $\pi'$
        \end{algorithmic}
        \end{algorithm}
</pre>



## Policy Iteration

Combination of policy evaluation and policy improvement is know as Policy Iteration. It is guarenteed to find the optimal policy for any finite MDP.

Policy transition over the course of algorithm is depicted below.

$$\pi_0 \xrightarrow[]{\text{evaluation}} v_{\pi_0} \xrightarrow[]{\text{improve}}
\pi_1 \xrightarrow[]{\text{evaluation}} v_{\pi_1} \xrightarrow[]{\text{improve}}
\pi_2 \xrightarrow[]{\text{evaluation}} \dots \xrightarrow[]{\text{improve}}
\pi_* \xrightarrow[]{\text{evaluation}} v_*$$

Psedocode for the algorithm:

![Policy Iteration]({{ "/assets/img/2019-06-26-policy-iteration.jpg" |  absolute_url }} "Policy Iteration" ){:height="60%" width="85%"}_Algorithm for Policy Iteration <br> (Image source: Sutton and Barto, Reinforcement Learning)_




