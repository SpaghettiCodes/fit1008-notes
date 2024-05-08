#### Fibonacci
```python
def fib(n: int) -> int:
	if n == 0 or n == 1:
		return n
	else:
		return fib(n - 1) + fib(n - 2)
```
- This have a time complexity of O(2<sup>n</sup>)
![[Pasted image 20240422150828.png]]
![[Pasted image 20240422150813.png]]
- This is hot garbage
	- This is because fib() CANNOT remember that it already calculated fib(3), and would recalculate fib(3) again for the +RHS, even though +LHS already calculated it
	- This forms the above binary tree, hence O(2<sup>n</sup>)
![[Pasted image 20240422150952.png]]
- We can improve this by keeping track of the 2 previously computed values via an accumulators
![[Pasted image 20240422151225.png]]

```python
def fib(n : int) -> int:
	return fib_aux(n, 0, 1)

def fib_aux(n: int, fm2: int, fm1: int) -> int:
	if n == 0:
		return fm2
	else
		return fib_aux(n - 1, fm1, fm2 + fm1)
# fm2 - the value before the last
# fm1 - the last value computed
```

- Call Tree
![[Pasted image 20240422151354.png]]

- This new algorithm has a complexity of O(n)
	- The accumulators make recomputation unnecessary