---
geometry:
- top=25mm
- left=20mm
- right=20mm
- bottom=30mm
documentclass: extarticle
fontsize: 12pt
numbersections: true
title: Lecture 18 (Better Computations for Value Function)
--- 

Water flowing from goal states to the other states is a good analogy to visualise value iteration.

# Asynchronous Dynamic Programming
1. Back up states individually
1. It is guaranteed to converge if all states continue to be selected

## In-Place Dynamic Programming
1. Synchronous value iteration stored two copies of value function, the old and new state
1. In-place iteration only stores a single copy of the value funciton
1. Saves space (and convergence is quicker?)

## Prioritised Sweeping
1. Use magnitude of Bellman error (change in the value of $v(s)$) to guide state selection
1. Backup the state with the largest error
1. Use a priority queue and add neighbours to queue after update

# Problems with Value Iteration
The optimal policy converges much before the values converge.

## Policy Iteration
1. Calculate the utilities for some fixed policy until convergence
1. Update policy using one step look ahead with resulting converged utilities as future values
1. Repeat the above until the policy converges
1. Can directly solve the Bellman equation in $O(s^3)$
1. Alternatively, we can also perform a few iterations to get an idea about the value function instead of the exact value
