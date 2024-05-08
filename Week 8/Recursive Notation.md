- Unary
	- A single recursive call
- Binary
	- Two recursive call
- n-ary
	- n recursive calls

- Direct recursion
	- Recursive calls are calls to the same function
- Indirect recursion
	- Recursion through two or more methods
		- Method p calls method q, which calls p

- Tail-recursion
	- The result of the recursive call is the result of the function

```python
# this is not a tail-recursion
def factorial(n: int) -> int:
	if n == 0:
		return 1
	else
		return n * factorial(n - 1) # we multiply the recursive call, therefore, it is not a tail-recursion


# this is tho

def factorial(n: int) -> int
	return factorial_aux(n, 1)

def factorial_aux(n, result: int) -> int:
	if n == 0:
		return result
	else:
		return factorial_aux(n - 1, result * n) # recursive call is result of the function

# the use of a result is an accumulator
# an accumulator "accumulates" the result of all the recursion calls
```