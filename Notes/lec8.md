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

# Lecture 8 (Informed Search)

## Greedy Best-First Search
Best-first search but $f(n)=h(n)$

## A* Search
Combines UCS and Greedy Best-First Search by using $f(n)=g(n)+h(n)$, where $g(n)$ is cost incurred until now. Surprisingly this algo is optimal for tree-search if heuristic is admissible.

### Admissible Heuristic
Let $h^*(n)$ be actual shortest path. $h$ is admissible if $h(n)\leq h^*(n)\ \forall n$. Only those heuristics are optimal (in A* search) which are admissible.

### Consistent Heuristic
An admissible heuristic is consistent if for every state $s$ and for every successor $s'$, $h(s)\leq c(s,s')+h(s')$ (inspired from triangle inequality). This implies that $f(n)$ only increases along the path and the `graph-search` algo also gives optimal solution.

