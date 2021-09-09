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

## Forward Checking
Remove values of neighbours which are inconsistent with current assignment of node

## Arc Consistency
Arc is consistent if for any assignment for the source variable, there exists a valid assignment for the sink variable. The domain is modified accordingly

