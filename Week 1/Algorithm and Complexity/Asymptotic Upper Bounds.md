We do not count the exact number of elementary steps
- difficult, time-consuming and error-prone
We determine the most expensive parts of the code

### Asymptotic
- approaching a value or curve arbitrarily closely, but never quite reaching it
- "getting as close as you like to some limit"

### Big-O notation
- assume we have two functions $f(n)$ and $g(n)$ defined on $n ∈ N$.
- $f(n) = O(g(n))$ if the following is true:
	- there are 2 positive constants $n_0$ and $c$ such that for all $n \ge n_0$ 
		- $0 \le f(n) \le c \cdot g(n)$ 
			- all runtime must be between 0 and $c \cdot g(n)$
		- for all values of $n \ge n_0$ , $f(n)$ grows at the same rate or slower than $g(n)$ as $n$ increases
	- $g(n)$ is the asymptotic upper bound for $f(n)$ as $n$ approaches infinity

![[Asymptotic-upper-lower-and-tight-bounds-of-a-function-from-a-c.png]]
