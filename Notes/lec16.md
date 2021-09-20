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

# Lecture 16 (Markov Decision Processes)

## Intuition for Formalisation
1. Start state
1. Good and bad goal states
1. Small "living" rewards are given (+ve or -ve)
1. Large rewards on reaching a goal state (+ve or -ve)
1. Agent's goal is to maximise sum of rewards
1. Rewards are instantaneous

## Markov Decision Process (MDP)
1. Set of states $S$
1. Set of actions $A$
1. Transition function $T(s, a, s')$ gives $P(s'|s, a)$
1. Reward function $R(s, a, s') ($= $R(s')$ sometimes), small negative values for irrelevant states as "cost of breathing"
1. Start state $S_0$
1. Possibly ternimation states

## Policies
1. For each state, we need an optimal policy $\pi^*:S\to A$
1. Optimal policy maximises expected utility
1. Agent looks up policy on arriving at state

### Policies in terms of Reward
1. Invalid transitions can be penalised more
1. This creates urgency to reach goal state soon
1. Large negative reward can be harmful since agent will then just reach a terminal state (irrespective of good/bad)

## Markov Assumption in MDPs
1. Next state only depends on current state and current action
1. Past states and actions are irrelevant
