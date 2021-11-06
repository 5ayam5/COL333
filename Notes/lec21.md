---
geometry:
- top=25mm
- left=20mm
- right=20mm
- bottom=30mm
documentclass: extarticle
fontsize: 12pt
numbersections: true
title: Lecture 21 (Active RL)
--- 

# Properties of Q-Learning
1. Q-Learning converges to optimal policy even if agent acts sub-optimally
1. Exploration is enough
1. Off-policy algorithm: convergence to optimal policy even if agent acts sub-optimally

# SARSA Learning
1. Updates using $(s, a, r, s', a')$
1. $Q(s, a) \gets (1 - \alpha) Q(s, a) + \alpha \left[r + \gamma Q(s', a')\right]$
1. More realistic when adversaries control policy
1. On-policy algorithm

# Active Reinforcement Learning
Exploration vs exploitation trade-off

## Exploration Strategy

### $\epsilon$ Greedy
1. With small $\epsilon$ probability explore
1. Otherwise exploit
1. Exploration is very slow
1. Not very active of a strategy

### Exploration Functions
1. They make you hallucinate
1. $f(u, n) = u + k / n$, $n$ is number of times the state has been visited and $u$ is the Q-value
1. States are more likely to be visited if they haven't been visited earlier
1. $Q(s, a) \gets_\alpha r + \gamma \underset{a'}{\max}(f(Q(s', a'), N(s', a')))$ ($\gets_\alpha$ is the update involving the previous value of $Q(s, a)$ and factor of $\alpha$)
1. We can also induce $\epsilon$ greedy in this algorithm

### Upper Confidence Bound
1. Similar to $\epsilon$ greedy but preference given to those actions which have potential to being optimal
1. $\displaystyle a_t = \underset{a \in A}{arg\,max}\left[\hat{Q}(a) + \sqrt{\frac{2\log t}{N_t(a)}}\right]$

## Multi-arm Bandits
1. Single state but multiple actions
1. It is an example of exploration vs exploitation strategyi
1. Environment generates the probability distribution
1. Monte-Carlo evaluation is done - averaging the Q-value:
$$Q(a) = \mathbb{E}[R(a)] \approx \hat{Q}_t(a) = \frac{1}{N_t(a)}\sum_{t=1}^T r_t 1(a_t = a)$$

# Problem of Generalization
1. Having too many state spaces can make RL very slow
1. Can instead use feature based representation
1. Features are combined using functions
1. This helps in generalizing the states

## Linear Value Functions
$$V(s) = \sum_{i=1}^n w_i f_i(s)$$
$$Q(s, a) = \sum_{i=1}^n w_1 f_i(s, a)$$
1. The goal of Q-learning is to now estimate these weights from experiences
1. Once the weights are learnt, the resulting Q-value will be close to the actual Q-value
1. For this to work efficiently, we need substantial states

### Approximate Q-Learning
Updates happens as:
$$Q(s, a) \gets Q(s, a) + \alpha (difference)$$
$$w_m \gets w_m + \alpha \left[r + \gamma \underset{a}{\max}Q(s', a') - Q(s, a)\right] f_m(s, a)$$
