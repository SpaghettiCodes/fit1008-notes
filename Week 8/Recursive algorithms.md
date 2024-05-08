[[Recursive algorithms|What is recursion]]

- Solve a large problem by reducing it to one or more sub-problems (Divide and conquer)
	- Sub-problems are
		- same kind of original
		- simpler to solve
- Each of the sub-problems are solved using the same algorithm until the sub problems become so "simple" that they can be solved w/o any further reductions
	- this is known as base case

##### What kind of problems can be solved using recursion
- Must be able to be decomposed into smaller similar problems (Decomposition)
- Must be so simple that it can be solved w/o further decomposition at some point (must have a base case)
- Solution to original problem can be computed by combining solutions of subproblems (Combination)

##### General algorithm
```python
def solve(problem):
	if problem is simple: # Base Case
		solve directly
	else:
		p1, p2, p3, ... = decompose(problem) # Decomposition
		ans1 = solve(p1)
		ans2 = solve(p2)
		ans3 = solve(p3)
		...

		return ans1 + ans2 + ans3 + ... # Combination
```

[[Recursion Problems|Examples]]
