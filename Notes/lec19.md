---
geometry:
- top=25mm
- left=20mm
- right=20mm
- bottom=30mm
documentclass: extarticle
fontsize: 12pt
numbersections: true
title: Lecture 19 (Reinforcement Learning)
--- 

# Setup
1. Similar to MDP but reward function $R$ and transition probability $T$ isn't known
1. Thus, we explore different actions and *learn* details about the environment and find the optimal policy
1. This algorithm is an *online* algorithm unlike MDP which is *offline*
1. Environment gives the reward after the action - action-reward loop
1. Humans learn from experiences in life

# Difference from other Learning Problems
1. Supervised learning is like feeding data of both $x, y$; goal is to find a mapping
1. Unsupervised learning is feeding data of only $x$; goal is to find the structure
1. Reinforcement learning is given state-action pairs; goal is to maximise reward
1. Unlike the other two, RL is evaluative feedback

# RL Agents
1. Utility-based agent
1. Q-learning
1. Reflex agent

# RL Approaches
1. Passive learning
1. Active learning

## Passive Learning
1. Input is the policy
1. No information about $T$ or $R$
1. Run multiple instances (episodes/trials) and estimate the value function

### Model-Based RL
1. From experiences *normalise* to estimate $\hat{T}(s, a, s')$ and then discover $\hat{R}(s, a, s')$
1. Now, use these values to estimate the optimal policy using value/policy iteration
