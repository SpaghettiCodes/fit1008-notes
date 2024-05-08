### Properties
#### Constant growth rate
- If $c$ is any positive constant, $c = O(1)$

#### Sum of O():
- If $f_1(n) = O(g_1(n))$ and $f_2(n) = O(g_2(n))$, then
	- $f_1(n) + f_2(n) = O(max(g_1(n), g_2(n)))$
		- pick the fastest growing component basically

#### Product of O():
- If $f_1(n) = O(g_1(n))$ and $f_2(n) = O(g_2(n)))$, then
	- $f_1(n) \cdot f_2(n) = O(g_1(n) \cdot g_2(n))$

### A few examples
```python
def sum(input_list):
	res = 0
	for item in input_list: # this will repeat for every number of items in n
		res += item
	return res
```
complexity of the method above is `O(n)`, where `n is the number of items`

```python
def sum(input_list):
	res = 0
	for x in range(min(len(input_list), 10)): # this will either repeat for all numbers in input_list, or 10 times
		res += input_list[i]
	return res
```
since this loop will repeat 10 times if the length of the input list is larger than 10, the loop does not depend on input size after n >= 10 (i.e. $n_0 = 10$)
- therefore, complexity is O(1)

```python
def func0(input_of_size_n):
	for x in range(n):
		a = b + 2
		for j in range(100):
			res += func1(res)
		res -= func2(res)
	return res

def func1(something): # Assume O(n)

def func2(something): # Assume O(2^n)
```
- The outer loop `for x in range(n)` runs for n times, O(n)
- The inner loop runs for 100 times
	- Since its a constant number (100), its O(1)
- func1 is O(n)
- func2 is O(2<sup>n</sup>)
- The total complexity is O(n * (1 * (n) + 2<sup>n</sup>)))
- Since we only care the fastest growing complexity, the Big-O notation is:
	- O(n * (2<sup>n</sup>))

#### Additional Notes
- Best-case and worst-case
	- What happens with the algorithm in the best-case and worst-case scenario **given an input of size n**
	- You cannot put the input as small for best-case and the input as large for worst-case
		- **in both best and worst-cases, the input must be assumed to be n**
