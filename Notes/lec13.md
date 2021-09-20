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

# Lecture 13 (Adversarial Search)

## Game Playing and AI
1. Incorporate the state of other agent in decision-making
1. Goal to win at the end
1. Time that can be taken for the next move is limited

## Game Properties
1. Players - one, two or more
1. Actions - deterministic or stochastic
1. States - fully or patially known
1. Adversarial - agents have opposite utilities
1. Player needs to plan keeping in mind every possible move by opponent

## Game as Search Problem
1. Each alternate level is played by the same player
1. The goals at each level are the opposite of previous level
1. Value of state is max/min of values of children

### Minimax Values
1. $V(s) = \underset{s'\in successors(s)}\max{V(s')}$ for agent
1. $V(s') = \underset{s\in successors(s')}\min{V(s)}$ for adversary

### Adversarial Search
1. Search for optimal **moves** such that minimax value is maximised using search algos
1. Ply is half move

### Minimax Properties
1. Optimal only if adversary also plays optimally
1. Complete
1. Time complexity: $O(b^m)$
1. Space complexity: $O(b\cdot m)$
