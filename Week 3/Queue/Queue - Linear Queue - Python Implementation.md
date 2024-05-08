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
		self.rear += 1

	def serve(self) -> T:
		if self.is_empty():
			raise Exception("Queue is empty")
		self.length -= 1
		item = self.array[self.front]
		self.front += 1
		return item

	def __len__(self) -> int:
		return self.length

	def is_empty(self) -> bool:
		return len(self) == 0

	def is_full(self) -> bool:
		return self.rear == len(self.array)

	def clear(self):
		Queue.clear(self)
		self.front = 0
		self.rear = 0
```
#### Problem
- You can only append and server for `max_capacity` times
	- This is due to rear is only able to be incremented forward
		- is_full checks if the rear is equal to the length of the array
		- There is no way for the rear to "[[Queue - Circular Queue|cycle]]" back to the front to use back discarded space
			- All cells before front are all inaccessible and wasted

![[Pasted image 20240413222955.png]]
rear goes all the way after the array and cannot "[[Queue - Circular Queue|cycle]]" back, the first 4 spaces are wasted
#### Analysis
- `__init__` complexity is O(N) due to ArrayR initialization
- The rest of the methods are all O(1)
