Class: [[CSC 349]]
Date: 11-09-2023
Teacher:
___
## Notes

1) Do I understand the Problem Statement?
2) Do I understand what a subproblem is?
3) How do i use the subproblem solution(s) to solve the subproblem

Note: All of these problems can be seen as selection problems. For the quiz he wants the max number or whatever is desired
> [!Question] Question 2
> A contiguous subsequence of a list S is a subsequence made up of consecutive
> elements of S. For instance, if $\{\begin{array}{rrrrrrr} 5&15&-30&10&-5&40&10 \end{array}\}$ then $\{\begin{array}{rrr} 15&−30&10\end{array}\}$ is a contiguous subsequence but $\{\begin{array}{rrr} 5&5&40\end{array}\}$ is not. Give a dynamic programming algorithm for the following task: You are given a list of numbers,  {$a1, a2, . . . , a_n$}. You should return the contiguous subsequence of maximum sum (a subsequence of length zero has sum zero). For the preceding example, the answer would be {$10, −5, 40, 10$} with a sum of $55$.

> [!Question] Question 3

Itinerary 1: 0 29 31 91 120
0 ⇾ 29: 1 
	→ 1^2 = 1
29 ⇾ 61: 2 
	→ 2^2 = 4
61 ⇾ 91: 0 
	→ 0^2 = 0
91 ⇾ 120: 1
	→ 1^2 = 1
Penalty = 1 + 4 + 0 +1

Itinerary 2:
$\begin{array}{rrrrr}  0&\rightarrow&29&\rightarrow&30&\rightarrow&59&\rightarrow&90\end{array}$

$$
\begin{array}{|c|C|C|C|C|C|C|C|9}
0& \space\rightarrow29 & \rightarrow 30 & \rightarrow 59 & \rightarrow 90\\
& 1 & 555 & 888\\ 
\end{array}
\
$$

Penalty = 4

$Penalty = (30 - x^2)$

j is index penultimate stop 

1) Definition (meaning) of cell
	1) $T_i$ = The penalty associated with the best itinerary that starts at $a_0$ and ends at $a_i$
2) Base Case:
	1) $T_i = 0$
3) Solution:
		$T_n$
4) Formula
		$$\min_{i < j}(T_j + (30 - x_{ji})^2)$$

>[!Question] Question 4
>Firestones is considering opening a series of restaurants along Highway 1. The $n$ possible locations are along the highway, and the distances of these locations from the downtown San Luis Obispo are, in miles and in increasing order, $m_1, m_2, ..., m_n$. The constraints are: 
> - At each location, Firestones may open at most one restaurant. The expected profit from opening a restaurant at location $i$ is $p_i$, where $p_i > 0$ and $i = 1, 2, . . . , n$.  
> - Any two restaurants must be at least k miles apart, where k is a positive integer.  
> 
>  Give a dynamic programming algorithm to compute the maximum expected total profit subject to the given constraints

Examples problem to explore algorithm:
$K=10 \rightarrow$ The minimum distance of any two restaurants must be
$D = \begin{array}{rrrrrr}9&11&12&21&27&33 \end{array}$ $\rightarrow$ distances of these locations
$P = \begin{array}{rrrrrr}100&50&70&10&70&5 \end{array}$ $\rightarrow$ Profit from opening a restaurant at location
$T = ?$

- This can be understood as either the max distance between compatible elements, or the last element which represents the maximum profit

$T = \begin{array}{rrrrrr}0&50&70&60&100&70 \end{array}$
- Reconstruction is kind of easier
Or
$T = \begin{array}{rrrrrr}0&50&70&80&100&100 \end{array}$
- For this solution we just have to index in the last entry:
- Binary Search for sorted entry
- Reconstruction is kind of hard

1) Definition (meaning) of cell
		$T_i$ = The profit associated with the locations starting at $m_{1}$ to $m_n$
2) Base Case:
		$T_i = 0$
3) Solution:
		$T_n$
4) Formula

| 1   |
| --- |
| 1    |


