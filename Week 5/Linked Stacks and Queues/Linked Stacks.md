Pre-req: [[Stack ADT]]

```python
from typing import TypeVar
from abstract_stack import Stack
from node import Node
T = TypeVar('T')

class LinkStack(Stack[T]):
	def __init__(self):
		Stack.__init__(self)
		self.top = None

	def is_full(self):
		return False

	def clear(self):
		Stack.clear()
		self.top = None

	def push(self, item: T):
		new_node = Node(item)
		new_node.link = self.top
		self.top = new_node
		self.length += 1

	def pop(self):
		if not self.is_empty():
			item = self.top.item
			self.top = self.top.link
			self.length -= 1
			return item
		else:
			raise ValueError("Stack is empty")
```

##### Push
- In the array implementation, we 
	- raised exception if the array is full, 
	- add the item in the position marked as top (same as the length of the list)
	- increase top
- For the linked data structure, we just need to
	- Create a new node that contains the item
	- Link it to the current top
	- Make the new node the new top

##### Pop
- In the array implementation, we
	- raised exception if the array is empty
	- remember the top item
	- decrease top
	- return the item
- For the Linked data structure, it is identical, except we change the top.

#### Disadvantages and Advantages of Stacks
##### Advantages
- Good to resize
	- Push: Never full so no need to copy, just add the element at the top
	- Pop: uses less memory when elements are popped
- Needs less space than the array if the array is less than half full
##### Disadvantages
- Needs more space than an array if the array is relatively full
- A bit slower
	- Constant time, but a bigger constant
	- Very insignificant tho