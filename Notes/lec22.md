---
geometry:
- top=25mm
- left=20mm
- right=20mm
- bottom=30mm
documentclass: extarticle
fontsize: 12pt
numbersections: true
title: Lecture 22 (Probabilistic Reasoning)
--- 

# Uncertainity in AI
1. Guess values of unobserved variables from observed variables (evidence)
1. Generate a model to obtain the unobserved variables using probabilistic reasoning

# Random Variables
1. Used to represent the uncertain variable
1. It can take values from a domain

# Joint Distribution
1. Combined distribution of a set of variables
$$P(X_1=x_1, X_2=x_2, \ldots, X_n=x_n) = P(x_1, x_2, \ldots, x_n)$$
1. They obey the following conditions:
$$P(x_1, x_2, \ldots, x_n) \geq 0$$
$$\sum_{(x_1, x_2, \ldots, x_n)} P(x_1, x_2, \ldots, x_n) = 1$$
1. However, this is not feasible since the size of the table will be $O(d^n)$

# Events
An event $E$ is a set of outcomes.
$$P(E) = \sum_{(x_1, x_2, \ldots, x_n) \in E} P(x_1, x_2, \ldots, x_n)$$

# Marginalization
Reduce (marginalize) variables by collapsing rows by adding liklihoods
$$P(x_1, x_2, \ldots, x_{i-1}, x_{i+1}, \ldots, x_n) = \sum_{x_i} P(x_1, x_2, \ldots, x_n)$$

# Conditional Probabilities
Probability of some variables given fixed values of others
$$P(x_1, x_2, \ldots, x_{i-1}, x_{i+1}, \ldots, x_n | x_i) = \frac{P(x_1, x_2, \ldots, x_{i-1}, x_{i+1}, \ldots, x_n)}{P(x_i)}$$

# Product Rule
$$P(y) P(x|y) = P(x, y)$$

# Chain Rule
$$\prod_{i=1}^n P(X_i | X_1, X_2, \ldots, X_{i-1})$$

# Bayes Rule
$$P(cause | effect) = \frac{P(effect | cause) P(cause)}{P(effect)}$$

# Independence
$$X \perp\!\!\!\!\perp Y \iff P(x, y) = P(x) P(y)$$

# Bayesian Network
1. It is also called as **Probabilistic Graphical Networks**
1. Encodes how variables locally infulence each other
1. Helps in describing complex joint distributions
1. The involve *entities* (RVs) and *interactions* (dependence)
1. They are DAGs
1. They are represented as a conditional probability table for each node wrt its parents
$$P(X | (a_1, a_2, \ldots, a_n))$$
1. They implicitly encode joint distributions
1. The complete joint distribution is given as:
$$P(x_1, x_2, \ldots, x_n) = \prod_{i=1}^n P(x_i | parents(X_i))$$
