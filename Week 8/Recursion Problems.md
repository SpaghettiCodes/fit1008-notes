##### Factorials
- Determine the number of permutation of a given number of distinct elements
- x! = 1 * 2 * 3 * 4 * 5 * ... * (n - 1) * n
- The factorial problem can be broken down to x! = (n - 1)! * n
	- since `(n - 1)!` calls the factorial function again (Convergence), we are able to use recursion to solve this problem
	- Convergence - the behavior of a sequence where each term is defined in terms of its previous terms
- Base case
	- O! = 1

```python
def factorial(n: int) -> int:
	if n == 0:
		return 1
	else:
		return n * factorial(n - 1) # convergence
```
- The complexity of this function would be O(n)
	- to calculate n, this function would call itself (n - 1) times
	- O(n - 1) * O(1) = O(n)