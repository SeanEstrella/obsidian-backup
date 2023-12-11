## Complexity
> [!Definition]
> A *decision problem* is a problem for which any proposed solution can be quickly checked for correctness

For a decision problem:
- There exists a "checking algorithm" $C$, that takes as input:
    - The given instance of the problem, $I$, and
    - The proposed solution, $S$
- $C$ outputs `true` if and only if $S$ is a solution for instance $I$.
- Ideally, the running time of $C$ on any instance ($I$, $C$), to be polynomial in $|I|$.

*I think of C as a "grading algorithm".*
> [!Definition]
> The class of all decision problems for which C runs in polynomial time is denoted by *NP*


- NP can be checked in polynomial time
    - Knapsack
        - Optimization problem can convert to decision problem:
            - Introduce a threshold held and check that your solution meets that threshold
- P can be checked and solved in polynomial time
    - Minimum Spanning Tree
    - Longest Increasing Subsequence
    - Independent Set on Trees
    - Many, many others

More Complete Definitions
1) P (Polynomial Time)
    - The class P consists of decision problems that can be solved in polynomial time by a deterministic Turing machine.
    - Basically a problem is in P if there exists an algorithm that can solve any instance of the problem in time that is a polynomial function of the size of the input
    - These Problems are considered to be efficiently solvable or tractable
2) NP (Nondeterministic Polynomial Time)
    - Can be verified in polynomial time but not solved. This is based in a hypothetic nondeterministic Turing machine.
    - It doesnt mean that a problem can necessarily be solved quickly but if a solution is given then you can verify its correctness quickly.
3) NP-Complete
    - A problem is NP-Complete if it is in NP, and every problem in NP can be reduced to it in polynomial time. These are the hardest problems in NP,
    - If any NP-Complete problem can be solved in polynomial time, then every problem in NP can also be solved in polynomial time, effectively meaning P = NP. NP-Complete problems serve as a benchmark fr the intractability of computational problems.
4) NP-Hard
    - Represent being at least as hard as the most difficult problems in NP. They are also not required to be in NP
    - No guarantee that there is quickly verifiable solution

Independent Set Problem
- Description: Given a graph and a number k, the Independent Set problem asks whether there is a set of k vertices in the graph, none of which are adjacent to each other.
- NP-Complete
    - Finding set is difficult but checking independence and size is easy
Vertex Cover:
 - Description: Given a graph and a number k, the vertex cover problem asks whether there is a set of k vertices such that every edge in the graph is incident to at least on vertext in the set.
 - NP-Complete
     - The Vertex Cover problem is also NP-Complete. Like the Independent Set problem, a solution can be verified quickly (check if the set of vertices covers all edges and is of size k), but finding the set is difficult.

3-SAT Problem
1) Construct a Graph from 3-SAT Instance
    - For each clause in the 3-SAT formula, create a triangle in the graph (a triangle is a complete graph of three nodes). Each vertex in the triangle represents a literal in the clause.
    - Connect vertices representing complementary literals (e.g., �X and ¬�¬X) across different triangles. These edges ensure that both a literal and its negation can't be in the independent set simultaneously, mimicking the constraint that they can't be true at the same time in a satisfying assignment.
2) Set Independent Set Size:
    - The size $k$ of the independent set you're looking for is set to the number of clauses in the 3-SAT formula. This ensures that for the graph to have an independent set of size $k$, each triangle (representing a clause) must contribute exactly one vertex (i.e., one true literal) to the independent set.
3) 
    - If the constructed graph has an independent set of size �k, this corresponds to a satisfying assignment for the 3-SAT instance, where the literals corresponding to the vertices in the independent set are set to true.
    - Conversely, if the 3-SAT instance is satisfiable, there will be an independent set of size �k in the constructed graph.

![[Pasted image 20231207092818.png]]
NP-Complete