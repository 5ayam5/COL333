---
geometry:
- top=25mm
- left=20mm
- right=20mm
- bottom=30mm
documentclass: extarticle
fontsize: 12pt
numbersections: true
title: Lecture 20 (Model Free Reinforcement Learning)
--- 

# Idea
We skip the computation of the model ($\hat{T}, \hat{R}$) and just compute the value functions

# Direct Evaluation
1. Approximates the value function: $V^\pi(s)$
1. We compute the average of the discounted rewards for each state

## Pros
1. Saves model estimation cost
1. With large number of episodes, the correct value function is computed

## Cons
1. Each state is independent of the other, which makes the algorithm inefficient
1. Bellman characterization is ignored

# Policy Evaluation
1. We attempt to use the Bellman equation but skip computation of $T$ and $R$
1. This can be done by taking samples of outcomes $s'$ by doing the action and averaging it
1. Assumes that we can re-visit at the original state

# Temporal Difference
1. Generalise the above to learn from every experience
1. Make updates for each transition instead of re-setting like it was done in Policy Evaluation
$$sample = R(s, \pi(s), s') + \gamma V^\pi(s')$$
$$V^\pi(s) \gets (1 - \alpha) V^\pi(s) + (\alpha)sample$$
$$\implies V^\pi(s) \gets V^\pi(s) + \alpha (sample - V^\pi(s))$$
1. We cannot find the optimal policy from this computation

# Q-Learning

## Q-Value Iteration
$$Q_{k+1}(s, a) \gets \sum_{s'} T(s, a, s')\left[R(s, a, s') + \gamma \underset{a'}{\max}(Q_k(s', a'))\right]$$

# Idea for Q-Learning
$$sample = R(s, \pi(s), s') + \gamma \underset{a'}{\max}(Q_k(s', a'))$$
$$Q(s, a) \gets (1 - \alpha)Q(s, a) + (\alpha)sample$$
