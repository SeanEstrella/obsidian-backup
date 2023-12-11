Date Created: 11-10-2023
___

## Definition
Dynamic Programming is a method for solving complex problems by being able to break 
down to simpler subproblems. It applies to problems that have the properties of 
[[Overlapping Subproblems]] and [[Optimal Substructure]]

## Approaches in Dynamic Programming

1. **Top-Down Approach (Memoization)**: This approach involves writing the problem as a recursive algorithm and then storing the result of each subproblem in a data structure (like an array or a hash table). Before computing a subproblem, you first check whether it has already been solved. If yes, you use the stored result; if not, you compute and store the result.
    
2. **Bottom-Up Approach (Tabulation)**: This approach involves filling up a DP table iteratively and using these table entries to solve larger subproblems. This method starts with the smallest subproblems and uses their solutions to build up solutions to larger subproblems.

## Advantages of Dynamic Programming

1. **Efficiency**: Reduces time complexity significantly, often from exponential to polynomial.
2. **Guaranteed Optimality**: With correct formulation, DP ensures the optimal solution is found.
3. **Applicability**: Useful in a wide range of fields including computer science, economics, engineering.

## Challenges in Dynamic Programming

1. **Identifying DP Applicability**: Recognizing that a problem can be solved by DP is not always straightforward.
2. **Memory Usage**: DP solutions can require significant memory to store the subproblem solutions.
3. **Designing the State and Formulating the Problem**: Deciding how to define the state and the recurrence relation can be challenging.