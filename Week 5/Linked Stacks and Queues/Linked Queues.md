Pre-req: [[Queue ADT]]

```python
from typing import TypeVar
from abstract_queue import Queue
from node import Node
T = TypeVar('T')

class LinkQueue(Stack[T]):
	def __init__(self):
		Stack.__init__(self)
		self.top = None
		self.rear = None

	def is_empty(self) -> bool:
		return self.front is None

	def is_full(self):
		return False

	def clear(self):
		Stack.clear()
		self.top = None
		self.rear = None

	def append(self, item: T):
		new_node = Node(item)
		if self.is_empty():
			self.front = new_node
		else:
			self.rear.link = new_node
		self.rear = new_node
		self.length += 1

	def serve(self):
		if not self.is_empty():
			item = self.front.item
			self.front = self.front.link
			self.length -= 1
			if self.is_empty():
				self.rear = None
			return item
		else:
			raise ValueError("Queue is empty")
```

##### Append
- Linear array implementation
	- array is full: raise exception
	- Increase rear and add the item at position marked by rear
- Linked list
	- Create a new node that contains item
		- ensure this new node points to `None`
	- Link current rear to it
	- Make a new node the new rear

##### Serve
- Linear array implementation
	- empty: raise exception
	- Remember item to return
	- increase front
	- return item
- Linked list
	- Almost identical
	- Once again, just move front along