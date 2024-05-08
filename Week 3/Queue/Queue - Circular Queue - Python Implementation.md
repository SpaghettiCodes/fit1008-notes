```python
from referential_array import ArrayR
from abstract_queue import Queue, T

class Queue(Queue[T]):
	MIN_CAPACITY = 1

	def __init__(self, max_capacity: int) -> None:
		Queue.__init__(self)
		self.front = 0
		self.rear = 0
		self.array = ArrayR(max(self.MIN_CAPACITY, max_capacity))

	def append(self, item: T) -> None:
		if self.is_full():
			raise Exception("Queue is full")
		self.array[self.rear] = item
		self.length += 1
		# this allows rear to "loop back" to the start when self.rear > len(self.array)
		self.rear = (self.rear + 1) % len(self.array)

	def serve(self) -> T:
		if self.is_empty():
			raise Exception("Queue is empty")
		self.length -= 1
		item = self.array[self.front]
		self.front = (self.front + 1) % len(self.array)
		return item

	def __len__(self) -> int:
		return self.length

	def is_empty(self) -> bool:
		return len(self) == 0

	def is_full(self) -> bool:
		return len(self) == len(self.array)

	def clear(self):
		Queue.clear(self)
		self.front = 0
		self.rear = 0
```

#### Analysis
- `__init__` complexity is O(N) due to ArrayR initialization
- The rest of the methods are all O(1)