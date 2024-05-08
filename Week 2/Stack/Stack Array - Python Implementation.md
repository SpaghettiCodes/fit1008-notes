[[Stack ADT - Python Implementation]]
```python
from referenctial_array import ArrayR
from abstract_stack import Stack, T

class ArrayStack(Stack[T]):
	MIN_CAPACITY = 1
	
	def __init__(self, max_capacity: int) -> None:
		Stack.__init__(self)
		self.array = ArrayR(max(MIN_CAPACITY, max_capacity))

	def is_full(self) -> bool:
		return len(self) == len(self.array)

	def push(self, item: ) -> None:
		if self.is_full():
			raise Exception("Stack is full")

		self.array[len(self)] = item
		self.length += 1

	def pop(self) -> None:
		if self.is_empty():
			raise Exception("Stack is empty")

		self.length -= 1
		return self.array[self.length]

	def peek(self) -> T:
		if self.is_empty()
			raise Exception("Stack is empty")
		return self.array[self.length - 1]
```

#### Analysis
- `__init__` is O(N)
	- the initialization of ArrayR is O(N)
- `push, pop, peek` are all O(1)