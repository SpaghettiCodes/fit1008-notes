```python
from referential_array import ArrayR
from abstract_set import Set, T

class ArraySet(Set[T]):
	MIN_CAPACITY = 1

	def __init__(self) -> None:
		Set.__init__(self)
		self.array = ArrayR(max(self.MIN_CAPACITY, capacity))

	def __len__(self) -> int:
		return self.size

	def is_empty(self) -> bool:
		return len(self) == 0

	def is_full(self) -> bool:
		return len(self) == len(self.array)

	def clear(self) -> None:
		self.size = 0

	def __contains__(self, item: T) -> bool:
		for i in range(self.size):
			if item == self.array[i]:
				return True
		return False

	def add(self, item: T) -> None:
		if item not in self:
			if self.is_full():
				raise Exception("Set is full")
			self.array[self.size] = item
			self.size += 1

	def remove(self, item: T) -> None:
		for i in range(self.size):
			if item == self.array[i]:
				# replace the current value with the last value in the set
				# since set is unordered, we do not need to care of the order
				self.array[i] = self.array[self.size - 1]
				self.size -= 1
				return
		raise KeyError(item)

	def union(self, other: Set[T]) -> None:
		res = ArraySet(len(self) + len(other))

		for i in range(len(self)):
			res.array[i] = self.array[i]
		res.size = self.size

		for j in range(len(other)):
			res.add(other.array[k])

		return res

	def intersection(self, other: Set[T]) -> None:
		res = ArraySet(min(len(self), len(other))

		added_elements = 0
		for x in range(self.count):
			if self.array[x] in other:
				res.array[added_elements] = self.array[x]
				added_elements += 1
		res.size = added_elements
		return res

	def difference(self, other: Set[T]) -> None:
		res = ArraySet(len(self))

		added_elements = 0
		for x in range(self.count):
			if self.array[x] not in other:
				res.array[added_elements] = self.array[x]
				added_elements += 1
		res.size = added_elements
		return res
```

#### Analysis
- `__init__` is once again, O(N) due to ArrayR initialization, where N is capacity
- `__contains__` is O(N * comp)
	- O(N) due to the loop iterating for N times, where N is the size of the set
	- O(comp) depends on the type of items we are comparing
- `add` is O(N * comp)
	- O(N * comp) as `if item not in self` has a time complexity of O(N * comp) (`__contains__`)
	- every other operation after `if item not in self` is O(1)
- `remove` is O(N * comp)
	- `for i in range(self.size)` has a complexity of O(N)
	- `if item == self.array` has a complexity of O(comp)
		- since this is in the loop, the complexity is O(N * comp)
	- the rest of the operation are O(1)
- [[Set Array - Union, Intersection, Difference|union, intersection and difference time complexity]]
