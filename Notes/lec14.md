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

# Lecture 14 ($\alpha$-$\beta$ Pruning)

## General Idea - $X$ Version
1. $X$ is MIN or MAX
1. Consider a node $n$ which is being explored currently
1. Let $a$ be *best* value parent of $X$ can get along any choice on current path from the root
1. If value at $n$ becomes *worse* than $a$, $\sim X$ will not consider this node and hence we don't explore further children of $a$

## Algorithm
$\alpha$: MAX’s best option on path to root

$\beta$: MIN’s best option on path to root
```python
def max-value(state, alpha, beta):
    initialize v = -INF
    for each successor of state:
        v = max(v, value(successor, alpha, beta))
        if v >= beta:
            return v
        alpha = max(alpha, v)
    return v
```
```python
def min-value(state , alpha, beta):
    initialize v = +INF
    for each successor of state:
        v = min(v, value(successor, alpha, beta))
        if v <= alpha:
            return v
        beta = min(beta, v)
    return v
```

## Properties
1. Doesn't affect minimax value at root
1. It is a form of meta-reasoning
1. Ordering of nodes matters, but best ordering cannot be found
1. Time complexity: $O(b^{m/2})$ if best ordering used, else $O(b^{3m/4})$ on average


## Cutting Off Search
1. Time complexity is very large
1. Depth-Limited search is done, use heuristic for non-terminal node at "max" depth
1. Evaluation function is usually weighted sum of features
