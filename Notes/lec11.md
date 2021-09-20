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

# Lecture 11 (Improving CSP)

## Backtracking Search (with Inference)
```py
function Backtracking(assignment, csp):
    if assignment is complete: return assignment
    var = Select-Unassigned-Variable(Variables(csp), assignment, csp)
    for each value in DomainValues(var, assignment, csp):
        if value is consistent with assignment given Constraints(csp):
            add {var = value} to assignment
            inferences = Inference(csp, var, assignment)
            if inferences != failure:
                add inferences to assignment
                result = Backtracking(assignment, csp)
                if result is not failure: return result
            remove {var = value} from assignment
    return failure
```

### Inference - Forward Checking
Remove values of neighbours which are inconsistent with current assignment of node

## Arc Consistency
1. Arc is consistent iff for any assignment for the source variable, there exists a valid assignment for the sink variable
1. The domain is modified accordingly by removing inconsistent values from the source

### AC-3 Algorithm for Enforcing Arc Consistency
```python
def AC-3(csp):
    queue = queue of all arcs in csp
    while queue is not empty:
        (Xi, Xj) = pop(queue)
        if revise(csp, Xi, Xj):
            if |Di| == 0:
                return False
            for each Xk in Xi.neighbours \ {Xj}:
                add (Xk, Xi) to queue
    return True
```
Complexity of the algorithm is $O(n^2 d^3)$. Backtracking with inference can also use `AC-3` algorithm

### Limitations
We cannot determine if a solution exists until we run a traversal on the graph, even after enforcing consistency

## K-Consistency
1. For each $k$ nodes, any consistent assignment to $k-1$ can be extended to the $k^{th}$ node
1. Arc consistency is special case for $k=2$
