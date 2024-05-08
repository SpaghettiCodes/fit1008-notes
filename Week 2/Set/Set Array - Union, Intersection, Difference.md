#### Union
```python
def union(self, other: Set[T]) -> None:
	res = ArraySet(len(self) + len(other))

	for i in range(len(self)):
		res.array[i] = self.array[i]
	res.size = self.size

	for j in range(len(other)):
		res.add(other.array[k]) # O(n * comp), n is size of res

	return res
```
- ArraySet's initialization will allocate length of current set + length of the other set of memory
	- O(n + m)
- first for loop `for i in range(len(self))` is going to loop through N times
	- O(n)
- Second for loop `for j in range(len(other))` is going to loop through M times
	- `res.add(other.array[k])` has a time complexity of O((n + m) * comp)
	- This entire loop has a complexity of O(m * (n + m) * comp)
- Final complexity = O(m * (n + m) * comp), n is length of current set, m is length of other set of memory

#### Intersection
```python
def intersection(self, other: Set[T]) -> None:
	res = ArraySet(min(len(self), len(other))

	added_elements = 0
	for x in range(self.count):
		if self.array[x] in other:
			res.array[added_elements] = self.array[x]
			added_elements += 1
	res.size = added_elements
	return res
```
- ArraySet's initialization will allocate the minimum length between length of current set and length of the other set.
	- O(min(n, m))
- `for x in range(self.count)` will loop through n times
	- `if self.array[x] in other` has a time complexity of O(m * comp)
	- The total complexity of the loop is O(n * m * comp)
- The final complexity is O(n * m * comp)
	- O(min(n, m)) is discarded as O(n * m * comp)  will increase at a faster rate compared to O(n) and O(m)

#### Difference
```python
	def difference(self, other: Set[T]) -> None:
		res = ArraySet(len(self))

		added_elements = 0
		for x in range(len(self.count)):
			if self.array[x] not in other:
				res.array[added_elements] = self.array[x]
				added_elements += 1
		res.size = added_elements
		return res
```
- ArraySet's initialization will allocate (the length of the current set) memory
	- O(n)
- `for x in range(len(self.count))` will loop n times
	- `if self.array[x] not in other` has a time complexity of O(m * comp)
	- The total complexity of this loop is O(n * m * comp)
- The final complexity is O(n * m * comp)