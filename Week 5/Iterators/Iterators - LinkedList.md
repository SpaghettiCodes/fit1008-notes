```python
class LinkListIterator(Generic[T]):
	def __init__(self, node: Node[T]) -> None:
		self.current = node # takes a list node as a argument, and initializes the iterator to start at that node

	def __iter__(self):
		return self # MUST return an object that has the __next__ method

	def __next__(self) -> T:
		"""
		Return the next element, then iterate to the next element in the list
		"""
		if self.current is not None:
			item = self.current.item
			self.current = self.current.link
			return item 
		else:
			raise StopIteration
```

##### Implementing __next__
- From the current node, we would need to traverse to the next node
	(i.e. `a -> b -> c, we whould traverse to b from a` ) (the self.link has the next value we would want)
- If we are at the last node (i.e. the iterator is at None, as the last node will have it's link set to None), we would just raise StopIteration

The LinkedList would need a `__iter__` method in order to use the `iter()` method

```python
def __iter__(self) -> LinkListIterator[T]:
	# returns the iterator pointing to the node at the head of the list
	return LinkListIterator(self.head)
```

This makes our List class **iterable**

Note that our List class is **iterable**, as it defines an `__iter__` method that returns an iterator.
Our LinkedListIterator, on the other hand, is an **iterator**, since it implements both `__iter__` and `__next__`
