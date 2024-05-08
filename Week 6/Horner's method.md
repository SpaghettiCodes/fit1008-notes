Let 
h = key value returned by a hash function
a<sub>n</sub> = character code in n position
n = character's position

$h = ((...(a_0\;x+{a_1})\;x\;+\;...\;+\;a_{n-3})\;x\;+\;a_{n-2}\;)\;x\;+\;a_{n-1}\;)\;x\;+\;a_n$ 
- Horner's method allow us to evaluate polynomials at O(n) time instead of the naive method of O(n<sup>2</sup>)

- Using Horner's method, we can mod at each step, thus casting out multiples of TABLESIZE
	- The result will be the same result as just modding once
#### Example
- Assume 101 is TABLESIZE
```python
def hash(word: str) -> int:
	value = 0
	for char in word:
		value = (value * 31 + ord(char)) % 101
	return value
```
