---
geometry:
- top=25mm
- left=20mm
- right=20mm
- bottom=30mm
documentclass: extarticle
fontsize: 12pt
numbersections: true
---

# Lecture 17 (Solving MDPs)

## MDP as Search Tree
1. We use an algorithm similar to expectimax search
1. The probability comes from environment

## Utility of Reward Sequences
1. Different sequences of rewards might have the same total outcome
1. To decide on the ordering, we add a *discount* factor
1. On descending a level, we multiply in the discount for all rewards
1. This helps in convergence of our algorithm too
1. Utility of an infinite sequence is finite

## Optimal Quantities
1. $V^*(s) = \text{expected utility starting in }s\text{ and acting optimally}$
1. $Q^*(s, a)= \text{expected utility starting in }s\text{ taking action }a$
1. $\pi^*(s)= \text{optimal action from }s$

### Formulating - Bellman Equation
1. $V^*(s) = \displaystyle\underset{a}\max{Q^*(s, a)}$
1. $Q^*(s, a) = \displaystyle\sum_{s'}^a{T(s, a, s')\left(R(s, a, s') + \gamma V^*(s')\right)}$
1. $V^*(s) = \displaystyle\underset{a}\max{\sum_{s'}{T(s, a, s')\left(R(s, a, s') + \gamma V^*(s')\right)}}$

### Computing - Value Iteration
$$V_{k+1}(s) = \displaystyle\underset{a}\max{\sum_{s'}{T(s, a, s')\left(R(s, a, s') + \gamma V_k(s')\right)}}$$
Complexity of each iteration is $O(S^2 A)$

### Policy Function
$\pi^*(s) = \underset{a}{argmax} \sum_{s'}{T(s, a, s')\left(R(s, a, s') + \gamma V^*(s')\right)}$
