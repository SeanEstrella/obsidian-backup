# CSC 349 10-12-23 Lecture Notes

Class: [[CSC 349]]
Date: 10-12-2023
Teacher:
___
## Notes
### Graph Basics
![[IMG_53DE7E2F8C4C-1.jpeg]]
> [!question]- Definition
![[Neighbors]]

### Reachability
> [!todo] Reachability
> **Input**: A graph, G =(V, E), and a vertex v in V.
> **Goal**: A list of all vertices reachable from v.

Pseudocode:
explore(G,v)
Input: A graph G and a vertex v,
Output: Vertices labeled discovered are vertices reachable from v.
1) discovered(v) = true
2) for all neighbors of v, u **do**
3) 	 **if** discovered(u) = false **then**
4)                  explore(G, u)   

