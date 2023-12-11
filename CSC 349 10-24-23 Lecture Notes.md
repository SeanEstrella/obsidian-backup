# CSC 349 10-24-23 Lecture Notes

Class: [[]]
Date: 10-24-2023
Teacher:
___
## Notes

Depth First Search
- LIFO
- Data: Structure is a stack
Breadth First Search
- FIFO
- Queue
Fringe 
- Start data structure in initial element
- while fringe not emptry:
	- take element x from fringe
	- mark x as visited
	- for every neighbor y or x
		- put y in fringe
BFS uses way more memory for its queue that dfs does for its stack

Algorithm design 

Design and analyze an algorithm which takes as an input an undirected graph, G, and an edge,  
e = (u, v), and determines whether G has a cycle containing e.

Name: edge_in_cycle(G, e)
Input: A graph, an edge(u, v)
Output: TRUE, if e is part of a cycle in G,
			FALSE, otherwise 

A cyc