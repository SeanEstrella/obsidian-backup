# Homework 1

> [!help] Question 1
> Rank the following running times in order from fastest to slowest:
> - $17n$
> - $n!$
> -  $42n\log_b (n)$
> -  $n^3$
> -  $36$
> -  $367n^2\log_b (n)$
> - $2^n$
> - $log_b(n)$
> -  $n^n$

- $17n$ - linear
- $n!$ - factorial
-  $42n\log_b (n)$ - constant\*logarithmic
- $n^3$ - cubic
- $36$ - constant
- $367n^2\log_b (n)$ - exponential \* logarithmic
- $2^n$ - exponential 
- $log_b(n)$ - logarithmic
- $n^n$

> [!help] Question 2
> Solve the following recurrence relations:
> - $T(n) = T\left(\frac{n}{2}\right) + O(n)$
> - $T(n) = T\left(\frac{n}{2}\right) + O(n^2)$
> - $T(n) = 3T\left(\frac{n}{3}\right) + O(1)$
> - $T(n) = T\left(\frac{n}{3}\right) + O(n)$

> [!help] Question 3
> 2) In justifying our matrix multiplication algorithm, we accepted the following property: If $X$ and $Y$ are $n × n$ matrices and 
>  $$ X = \begin{bmatrix} A & B \\ C & D \end{bmatrix}$$ $$Y = \begin{bmatrix} E & F \\ G & H \end{bmatrix}$$

> [!help] Question 4
> Suppose that you are given a sorted list of distinct integers $\{{a_1, a_{2,}\dots a_n}\}$. Design and analyze a divide-and-conquer algorithm that determines whether there exists an index $i$ such that $a_i = i.$ For example, in $\{{−10, −4, 3, 41}\}$, $a_3 = 3$, and in ${4, 7, 19, 20}$ there is no such $i$.

> [!help] Question 8
> Note: It is saying that you can not sort the elements, the elements are fundamentally not sortable 
> Asking if there is a strict majory