Date Created: 11-11-2023
___
## Definition

If a problem has an optimal substructure, then an [[Optimal Solution]] to the problem contains within it optimal solutions to the subproblems. This property is crucial for the correctness of dynamic programming and greedy algorithm approaches.

## Importance in Dynamic Programming
- **Solution Composition**: Allows large problems to be broken down into smaller problems and then reassembled to form a solution for the larger problem.
- **Efficiency**: Ensures that solving each subproblem independently and combining their solutions is an effective strategy.

## Examples of Optimal Substructure
### **Shortest Path Problems (e.g., Dijkstra’s Algorithm, Bellman-Ford Algorithm)**
1) **Problem**: Finding the shortest path from a source node to all other nodes in a weighted graph.
2) **Optimal Substructure**: The shortest path from node A to node C passing through B includes the shortest path from A to B. If you know the shortest path from A to B and B to C, you can construct the shortest path from A to C.
3) **Application**: Dynamic programming algorithms for shortest paths, like Bellman-Ford, rely on this property to iteratively build up the shortest path solutions.

###  **0/1 Knapsack Problem**
 1) **Problem**: Given items with specific weights and values, determine the maximum value that can be accommodated in a knapsack of a given capacity.
 2) **Optimal Substructure**: The optimal solution for a knapsack of capacity `W` with `n` items involves finding the optimal solution for a knapsack of capacity `W - w_n` (excluding the nth item) and `W` with `n-1` items, and then choosing the better of the two.
 3) **Application**: In dynamic programming solutions, the value table is filled based on previous computations, adhering to this principle.
### **Matrix Chain Multiplication**
1) **Problem**: Determining the most efficient way to multiply a chain of matrices.
2) **Optimal Substructure**: The problem of multiplying matrices `A[i]...A[j]` can be split into multiplying `A[i]...A[k]` and `A[k+1]...A[j]` for some value `k`, and the optimal way to multiply `A[i]...A[j]` includes the optimal ways to multiply these two subsequences.
3) **Application**: Dynamic programming solves this by considering all possible places to split the matrix chain and choosing the one that minimizes the number of multiplications.
### **Longest Common Subsequence**
1) **Problem**: Finding the longest subsequence common to all sequences in a set of sequences (not necessarily contiguous).
2) **Optimal Substructure**: If the last characters of two sequences match, they are part of the longest common subsequence, and the problem reduces to finding the longest common subsequence of the sequences without their last characters.
3) **Application**: This property allows a dynamic programming solution to build a table from smaller solutions to larger ones.
### **Coin Change Problem**
1) **Problem**: Given an unlimited supply of coins of given denominations, find the minimum number of coins required to make a certain amount of change.
2) **Optimal Substructure**: The optimal solution for making change for an amount `N` includes the optimal solution for making change for `N - C`, where `C` is a coin denomination.
3) **Application**: Dynamic programming solutions build up a table of solutions for all amounts up to `N`, using the solutions of smaller amounts.