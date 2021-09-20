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

# Lecture 15 (More Adversarial Searches)

## Ordering - Iterative Deepening
1. We can increase the depth where we use the evaluation function at the "depth"
1. On increasing depth, use the previous evaluation to order the nodes which were evaluated earlier

## Expectimax Search
Chance comes into picture when:

1. Action of adversary isn't known
1. Natural possibility of chance (rolling of dice etc)

### Algorithm
```python
def value(state):
    if the state is a terminal state: return the state’s utility
    if the next agent is MAX: return max-value(state)
    if the next agent is EXP: return exp-value(state)

def exp-value(state):
    initialize v = 0
    for each successor of state:
        p = probability(successor)
        v += p * value(successor)
    return v
```
Pruning cannot be performed

### Depth Limited Expectimax
Using heuristic to evaluate the value at depth limit

## General Minimax
1. Useful when there are multiple (> 2) players
1. Utility is represented as a tuple
1. Each player maximises its own component

## Maximum Expected Utility
1. Choosing Actions that maximise expected utility
1. Agent can be in multiple states with certain probability
1. $U = \sum_i{p_i U(S_i)}$
