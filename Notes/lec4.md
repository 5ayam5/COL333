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

# Lecture 4 (Uninformed Search)

## Simple Reflex Agent
1. Selects action based on the current percepts
2. Operates using *if-then-else* rules
3. Such an agent cannot reach a goal effectively (no such notion present)

## Problem Solving Agents
1. Adopt a goal
2. Perform a sequence of steps with objective of reaching goal

## Search Problem Formulation
1. $S$, the state space
2. $s_0 \in S$, the initial start state
3. $G \subset S$, the set of end states (is usally dynamic and hence defined by a *goal test*)
4. $A: S \times R \to S$, the successor function (R can be any set depending on the "algorithm")

## Modelling Assumptions
1. Agent knows current state
2. Discrete states and actions
3. Known and deterministic action outcomes

## Space State Graph
Constructing a graph using the states and the successor function

## Search Trees
1. $s_0$ is the root node
2. Check if node contains the goal
3. Else *expand* the node
4. Nodes in the tree show states but depict the *plan* for those states instead of actual representation

```py
function TreeSearch(problem, strategy):
    initialise with initial state
    while true:
        if no candidates for expansion, return failure
        choose a leaf node according to strategy
        if node contains goal state return solution
        else expand node and add resulting nodes to search tree
```

