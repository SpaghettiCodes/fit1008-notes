```python
from abstract_set import Set, T	

class Set(ABC, Generic[T]):
	def __init__(self, dummy_capcity: int = 1) -> None:
		# integers have arbitrary size, so capacity is not needed
		Set.__init__(self)

	def __len__(self) -> int:
		# uh oh stinky complexity

		# there is no way we can calculate number of elements using bitwise operations
		# so would actually need to count one by one
		# .bit_length returns the total length of bits for our bitVector
		size = 0
		for item in range(1, self.elems.bit_length() + 1):
			if item in self:
				size += 1
		return size
		# well i mean, this could be easily mitigated by
		# - checking if element does not exist, then only + 1 to count
		#    - checking if an element exist takes O(1) time
		# - we already have to check if element exist to remove, just - 1 to count
		# but yeah, wedonttalkaboutthat

	def is_empty(self) -> bool:
		# if every bit is 0, the set is empty (and the value is 0)
		return self.elems == 0

	def is_full(self) -> bool:
		# integers have arbitray size and can never be full
		return False

	def clear(self) -> None:
		self.elems = 0

	def __contains__(self, item: T) -> bool:
		# we first move the target bit to position 0, then we check if it has the value 1
		# to move a n bit to position 0, we need to left shit (n - 1) times
		return (self.elems >> (item - 1)) & 1

	def add(self, item: T) -> None:
		# we first construct a bit vector that only has the item as the element
		# then, we use the or operation to add that item into our own bit vector
		self.elems |= 1 << (item - 1)

	def remove(self, item: T) -> None:
		# same with add, except now we use the XOR operation to remove the element
		# remember that XOR returns 0 if both values are 0 or both values are 1
		# we need to check if the item is in the bit vector first, as if the element does not exist, it will be added (0 XOR 1 = 1)
        if item in self:
            self.elems ^= 1 << (item - 1)

	# an alternate implementation of remove
	def remove(self, item: T) -> None:
		self.elems &= ~(1 << (item - 1))

	def union(self, other: Set[T]) -> Set[T]:
		result = BVSet()
		result.elems = self.elems | other.elems
		return result

	def intersection(self, other: Set[T]) -> Set[T]:
		result = BVSet():
		result.elems = self.elems & other.elems
		return result

	def difference(self, other: Set[T]) -> Set[T]:
		result = BVSet():
		result.elems = self.elems & ~other.elems
		return result	
```

#### Analysis
- `__len__` would require O(|elems|) <- |elems| is the largest element in the bit vector
	- This is because a set w/ a single element ({1000}) will cause len to iterate from bit 0 all the way to bit 999
- Other than that, everything else is O(1)

#### Picture explanation
`__contains__`
![[Pasted image 20240413175838.png|350]]

`__add__`
![[Pasted image 20240413181144.png|350]]

`__remove__`
![[Pasted image 20240413182920.png|350]]
alternate implementation:
![[Pasted image 20240413182643.png|350]]

`union`
![[Pasted image 20240413184411.png|350]]

`intersection`
![[Pasted image 20240413184420.png|350]]

`difference`
![[Pasted image 20240413184433.png|350]]