#### X<sup>n</sup>
- X<sup>12</sup> can be done as X<sup>6</sup> * X<sup>6</sup>
- X<sup>6</sup> can be done as X<sup>3</sup> * X<sup>3</sup>
- X<sup>3</sup> can be done as X<sup>1</sup> * X<sup>1</sup> * X
	- note that **this algo will decompose the problem to X<sup>1</sup>, which allows X to multiply with itself as we backtrack from the recursive call**
- The problem can be broken into smaller problems (compute X<sup>x // 2</sup>) and does have a base case (X<sup>1</sup> = X)

```python
def power(x: int, n: int) -> int:
	tmp = 1
	if n > 0:
		tmp = power(x, n // 2)
		if n % 2 == 0:
			tmp = tmp * tmp
		else:
			tmp = tmp * tmp * x
	return tmp

# defo not tail recursive
```

##### Implementing Iteration w/ a Runtime Stack
- Since function calls are added to a stack (programs have a stack and a heap), we actually can change this recursion algo to iteration by simulating this stack memory
	- Each recursive call reserves a new stack area for its variables

```python
def power(x: int, n: int) -> 
	save = Stack(n)
	while n > 0:
		save.push(n)
		n = n // 2

	tmp = 1
	while not save.is_empty():
		if save.pop() % 2 == 0:
			tmp = tmp * tmp
		else:
			tmp = tmp * tmp * x
	return tmp
```