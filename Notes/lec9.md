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

# Lecture 9 ()

## Iterative Deepening A* (IDA*)
Limit value of $f$ and perform A* interatively increasing the value of $f$.

## Weighted A*
A* but $f'(n)=g(n)+w\times h(n)$, this might lead to $w\times h(n)$ not being admissible.

## Anytime Search
Weighted A* but decrease $w$ in each iteration of the algo finding better solutions with time.

## Admissible Heuristics
Problem relaxation - ignore rules, increase possibilities and assumes a super-graph of actual state space.

## Effective Branching Factor
1. Let A* generate N nodes before finding solution at depth d
2. Then, effective branching factor is $b^*=\sqrt[d]{N}$
3. This is used to determine the efficiency of the heuristic

## Combining Heuristic
1. $h_2$ dominates $h_1$ if both are admissible and $h_2>h_1$ for all nodes
2. Dominating heuristics perform better or same as non-dominating heuristics
3. Thus, we can take max of a set of heuristics to get a better performing algorithm
4. Heuristic functions form a lattice

