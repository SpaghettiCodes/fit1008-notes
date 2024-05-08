```python
from ArrayR import ArrayR
from SortedList import SortedList, T

class SortedArrayList(SortedList[T]):
	def __init__(self) -> None:
		SortedArrayList.__init__(self)

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

	def __getitem__(self, index: int) -> T:
		return self.array[index]

	def delete_at_index(self, index: int) -> T:
		item = self.array[index]
		# shuffle all elements at the right side of the deleted element to the left
		self.__shuffle_left(index):
		self.length -= 1
		return item

	def __index_to_add(self, item: T) -> int:
		# a variation of the binary search that returns the position to add a new object instead of raising an exception
		low = 0
		high = len(self) - 1
		while low <= high:
			mid = (low + high) // 2
			if self.array[mid] > item:
				high = mid - 1
			elif self.array[mid] < item:
				low = mid + 1
			else:
				return mid
		return low

	def index(self, item: T) -> None:
		low = 0
		high = len(self) - 1
		while low <= high:
			mid = (low + high) // 2
			if self.array[mid] > item:
				high = mid - 1
			elif self.array[mid] == item:
				return mid
			else:
				low = mid + 1
		raise ValueError("item is not in list")

	def add(self, item: T) -> None:
		index = self.__index_to_add(item)
		self.__shuffle_right(index)
		self.array[index] = item
		self.length += 1
```

#### Analysis
###### `index`
- We used [[Binary Search]] algorithm
- The complexity is the same as Binary Search (Best: O(1), Worst: O(log N))

###### `add`
- Best case O(log N)
	- If the element is added to the last
		- `__index_to_add` time complexity is O(log N)
		- `__shuffle_right` time complexity is O(1)
		- O(log N) + O(1) = O(log N)
	- Best case **isn't** O(1) as even if the element to add is in the middle, `__shuffle_right` would still need to shuffle (mid's position) elements (which is O(N))
- Worst case O(N)
	- If the element is added in the front
		- The time complexity to `__shuffle_right` if the element is added to the front is O(N)
			- we need to shuffle (length) elements
		- This overrides `__index_to_add`'s time complexity (element added to front: O(log N)), as O(N) grows faster than O(log N)
		- O(log N) + O(N) = O(N)

###### `add` (linear search)
- The best / worst case is O(N)
	- If the element is added to the last
		- Linear search time complexity is O(N)
		- `__shuffle_right` time complexity is O(1)
		- O(N) + O(1) = O(N)
	- If the element is added to the front
		- Linear search time complexity is O(1)
		- `__shuffle_right` time complexity is O(N)
		- O(1) + O(N) = O(N)

The rest of the methods follow a similar time complexity to [[List Array - Python Implementation|Array List]]'s
