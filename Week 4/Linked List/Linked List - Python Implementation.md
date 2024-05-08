```python
from abstract_list import List, T

class LinkedList(List[T]):
	def __init__(self) -> None:
		List.__init__(self)
		self.head = None

	def __get_node_at_index(self, index: int) -> Node[T]:
		if 0 <= index and index <= len(self):
			current = self.head
			for i in range(index):
				current = current.link
			return current
		else:
			raise ValueError("Index out of bounds")

	def __setitem__(self, index: int, item: T) -> None:
		node_at_index = self.__get_node_at_index(index)
		node_at_index.item = item

	def __getitem__(self, index: int) -> T:
		node_at_index = self.__get_node_at_index(index)
		return node_at_index.item

	def delete_at_index(self, index: int) -> T:
		if not self.is_empty():
			if index > 0:
				# get the previous node from the node to delete
				previous_node = self.__get_node_at_index(index - 1)
				# get the item of the next node (node to delete), and return that
				item = previous_node.link.item
				# change the previous node link, to link to the next node
				# this basically connects the previous node to the next node, removing the current node from the list
				#          /-----\
				# prev ----       ---- next
				#          deleted
				previous_node.link = previous_node.link.link
			elif index == 0:
				# transfer the head item to the next node
				item = self.head.item
				self.head = self.head.link
			else:
				raise ValueError("Index out of bounds")
			self.length -= 1
			return item
		else:
			raise ValueError("List is Empty")

	def insert(self, index: int, item: T) -> None:
		new_node = Node(item)
		if index == 0:
			# insert at the front is as easy as just replacing self.head
			new_node.link = self.head
			self.head = new_node
		else:
			# inserting at the middle
			# we get the previous node from the index (node index - 1), then change the link to point to our new node
			# we then set our new node to point to whoever the previous node was pointing to
			# prev ---- next
			# becomes        
			# prev ---- new node ---- next 
			previous_node = self.__get_node_at_index(index - 1)
			new_node.link = previous_node.link
			previous_node.link = new_node
		self.length += 1

	def append(self, item: T) -> None:
		self.insert(len(self), item)

	def index(self, item: T) -> int:
		current = self.head
		for i in range(len(self)):
			if current.item != item:
				current = current.link
			else:
				return i
		raise ValueError("Item is not in list")
 ```

#### Analysis
###### `__get_node_at_index`
- The loop executes *index* time always, which are upper-bounded by list size n
- Best Time - O(1)
- Worst Time - O(N), where N is the length of the linked list
- Note that the input size considered here is **length of linked list**

- Every method which uses `__get_node_at_index` inherits the O(1) and O(N) time complexity
	 - `__setitem__`
	 - `__getitem__`
	 - `delete_at_index`
	 - `insert`
		 - and by extension, `append`
###### `index`
- best case O(1): item is in the head node
- worst case O(N), N is length of the linked list: item is at the last node (have to loop thru all the way to the end)
