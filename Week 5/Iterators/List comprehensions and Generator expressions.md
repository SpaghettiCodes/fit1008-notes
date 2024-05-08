List comprehensions creates a list from another list using mathematic-like notation

Example:
```python
[3 * x for x in range(10)]
[x for x in A if x % 2 == 0]
```

This allows us to quickly create a new array that perform some operation for every element OR select a subset of elements that meet the condition

Generator Expressions is exactly the same as List Comprehensions, EXCEPT it returns an iterator instead of a list

Example:
```python
A = (3 * x for x in range(10))

next(A) # returns 0
next(A) # returns 3

for x in A:
	print(x) # prints out 6, 9, 12, 15 ... , 30
```