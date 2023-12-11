---
aliases:
  - Subproblems
---
Date Created: 11-11-2023
___
## Definition
In the context of [[Algorithm Design]], a problem is said to have overlapping subproblems if the
problem can be broken down into sub-problems that are used multiple times.

Relevant to [[Divide-and-Conquer]], where subproblems are generally distinct, overlapping 
subproblems recur multiple times during the computation.

## Characteristics and Identification
When a [[Recursion|Recursive Algorithm]] repeatedly calls itself with the same parameters, it is a sign of overlapping subproblems

[[Tree|Tree Representation]] can be a visualization of what subproblems look like, since if a problem has subproblems, then the subproblem will appear multiple times in the nodes of the tree. 


## Examples
1) Fibonacci Sequence: Calculating the nth Fibonacci number using a naive recursive approach involves recalculating the same Fibonacci numbers multiple times.
2) Shortest Paths: In [[Graph Algorithms]] like Floyd-Warshall, the same subpaths are considered multiple times when computing the shortest paths between all pairs of vertices.
3) **Knapsack Problem**: In the 0/1 Knapsack problem, the same subproblems of whether to include or exclude an item resurface in the recursive exploration.

## Visualization Techniques
- **Recursive Tree**: Drawing the recursion tree for a problem can visually demonstrate the presence of overlapping subproblems.
- **Tabulation Matrix or Array**: In the implementation of DP solutions, the table or array often shows repetitive calls being filled in, indicating overlap.

