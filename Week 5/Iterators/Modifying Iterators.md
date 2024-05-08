Add more methods that allows us to modify the iterable object (usually not a good idea)

Example:
From [[Iterators - LinkedList]]
```python
class LinkListIterator(Generic[T]):
	def __init__(self, alist: LinkList[T]) -> None:
		self.list = a_list
		self.current = node
		self.previous = None

	def __iter__(self):
			return self 

	def __next__(self) -> T:
		"""
		Return the next value in the sequence, then move to the next element in the list
		"""
		if self.current is not None:
			item = self.current.item
			self.previous = self.current
			self.current = self.current.link
			return item 
		else:
			raise StopIteration

	def has_next(self):
		return self.current is not None

	def peek(self):
		try:
			return self.current.item
		except AttributeError:
			raise StopIteration("no more elements in list")

	def delete(self) -> T:
		"""
		Returns the next item and deletes the associated node. Raises StopIteration if there is no next item.
		"""
		if not self.has_next():
			raise StopIteration("no more elements in list")

		else:
			item = self.current.item
			self.current = self.current.link

			if self.previous is None:
				self.list.head = self.current # aaand thats why we needed the list
			else:
				self.previous.link = self.current

			self.list.length -= 1

		return item
```

```
Additional operations that is defined

delete: return item pointed by current and removes that node

add: adds an item right before current

has_next: returns True if there is a next item to be processed (i.e. current is not at the end of the list)

peek: returns the next item w/o moving along, raises StopIteration if there is no next item
```

