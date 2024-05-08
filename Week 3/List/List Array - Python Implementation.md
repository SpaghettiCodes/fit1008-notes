```python
from referential_array import ArrayR
from abstract_list import List, T

class ArrayList(List[T]):
	MIN_CAPCITY = 1

	def __init__(self, max_capacity: int) -> None:
		List.__init__(self)
		self.array = ArrayR(max(self.MIN_CAPCITY, max_capacity))

	def __getitem__(self, index: int) -> T:
		return self.array[index]

	def __setitem__(self, index: int, value: T) -> None:
		self.array[index] = value

	def index(self, item: T) -> int:
		# a linear (sequential / serial) search
		# start and one end of the list, advance until the element is found
		for i in range(len(self)):
			if item == self.array[i]:
				return i
		raise ValueError("Item not in list")

	def __shuffle_left(self, start: int) -> None:
		# shuffles all element from (start + 1) to the left
		# self.__shuffle_left(1)
		# [1, _empty_, 2, 3, 4] => [1, 2, 3, 4, _empty_]
		for i in range(start, len(self) - 1):
			self.array[i] = self.array[i + 1]

	def __shuffle_right(self, start: int) -> None:
		# shuffles all element from start to the left
		# self.__shuffle_left(1)
		# [1, 2, 3, 4, _empty_] => [1, _empty_, 2, 3, 4]
		for i in range(len(self) - 1, start, -1):
			self.array[i] = self.array[i - 1]

	def delete_at_index(self, index: T) -> T:
		item = self.array[index]
		# shuffle all elements at the right side of the deleted element to the left
		self.__shuffle_left(index):
		self.length -= 1
		return item

	def __resize(self) -> None:
		new_array = ArrayR(len(self) * 2)
		for i in range(len(self)):
			new_array[i] = self.array[i]
		self.array = new_array		

	def append(self, item: T) -> None:
		self.insert(len(self), item)

	def insert(self, where: int, item: T) -> None:
		if len(self) == len(self.array):
			# if the current array is full, create a new one with more space
			self.__resize()
		# shuffle every element to the right first
		self.__shuffle_right(where)
		self.array[where] = item
		self.length += 1
```

#### Note
Since List is an **ordered ADT**, all operation that modifies the array **must maintain their relative order**
- these operation includes:
	- creating a new array in `append`
	- `delete_at_index`
	- `remove`
#### Analysis
###### `__init__`
- Call to ArrayR() is O(N), N is max_capacity
###### `index`
- `index` has a time complexity of O(1) at best, O(n) at worst
	- O(1) - loop stops at the first iteration
		- When the item we are looking for is at the start of the list
	- O(n) - loop goes all the way for n times
		- When the item we are looking for is at the end of the list
	- Note that this N represents the length of the list
###### `delete_at_index`
- `delete_at_index` has a time complexity of O(1) at best, O(N) at worst
	- O(1) when index is at the last position
		- the loop does not start (we do not need to shuffle left)
		- `for x in range(len(self) - 1, len(self) - 1)`
	- O(N) when the index is at the head
		- every other element (n - 1 count) will need to be shuffled left 
		- `for x in range(0, len(self) - 1)`
###### `remove`
```python
def remove(self, item: T) -> None:
	index = self.index(item)
	self.delete_at_index(index)
```
- Since index have a best case of O(1) (item is found at the head of the list), and worst case of O(N) (item is found last), the best case of `index` is the worst case of `delete_at_index` (recall `delete_at_index` complexity).
	- Since we care the highest rate of complexity, the time complexity of `remove` is `O(N)` for both worst and best.
###### `insert`
- `insert` has a best case of O(1) and worst case of O(N)
	- O(1) when the index to insert is at the back
		- `__shuffle_right`'s inner loop does not run
		- `for x in range(len(self) - 1, len(self), -1)`
	- O(N) when the index to insert is at the front 
		- `__shuffle_right`'s inner loop runs from (the last element in the array) to (the beginning of the array)
		- `for x in range(len(self) - 1, 0, -1)`
###### `append`
- `append` just calls `insert`, so the time complexity is the same

The rest of the operations are O(1)