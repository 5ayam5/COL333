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

# Lecture 12 (Local Search)

## Exploitiong Problem Structure
1. Problem specific optimisations to speed up CSP solving
1. Disconnected components can be independently solved
1. Tree-structured CSPs can be easily solved in $O(nd^2)$ time
1. Instantiate some variables and solve on the pruned graph
    - Find a subset of variables S, such that the remaining constraint graph becomes a tree after the removal of S (S is a cycle cut set)

## Iterative Approaches to Solving CSPs - Local Search
1. Take an assignment with unsatisfied constraints
1. Reassign variable values
1. Repeat: till CSP does not have a solution
    i. Variable selection - randomly select any conflicted variable
    i. Choose a new value which has the least number of conflicts - heuristic functions

Above idea is called "hill climbing" with $h(x)$. Generic idea is:

1. Start at a state
1. Repeat: move to best neighbouring neighbour
1. If no neighbour better than current, return

## Optimisation Problems - Generic Setup
- Local search is an example of optimisation problem
- We attempt to minimise the cost function
- Compared to search algorithms, notion of "path" from initial state to goal state isn't important here

## Preventing Stagnating at Local Maxima - Simulated Annealing
1. Allow some bad moves to escape local maxima
1. Repeat:
    i. Let $X_i$ be a random neighbour of $X$
    i. If $E_i>E$, $X\gets X_i$ and $E\gets E_i$
    i. Else, with some probability $p$, $X\gets X_i$ and $E\gets E_i$
1. This algorithm is a form of Monte-Carlo Search
1. $p$ is higher when $|E_i-E|$ is low and vice-versa
1. Exact formulation of $p=\exp{-\displaystyle\frac{E-E_i}{T}}$, $T$ is the dynamic variable that slowly reduces to $0$ over time

## Local Beam Search
1. Track $k$ states
1. Begin with $k$ randomly sampled states
1. Loop:
    i. Generate successors of each of the $k$ states
    i. If any of them has the goal, algorithm halts
    i. Select only the $k$ best successors from the list and repeat
1. States become concentrated in a small region of space
