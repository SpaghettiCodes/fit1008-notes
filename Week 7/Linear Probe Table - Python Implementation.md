```python
from typing import TypeVar, Generic
T = TypeVar('T')

class LinearProbeTable(Generic[T]):
	def __init__(self, size: int = 7919) -> None: # default value is a prime
		self.count = 0 # how many elements
		self.table = ArrayR(size)

	def __len__(self) -> int:
		return self.count

	def hash(self, key: str) -> int:
		value = 0
		a = 31415
		b = 27183
		for char in key:
			value = (value * a + ord(char)) % len(self.table)
			a = a * b % (len(self.table) - 1)
		return value

	def __setitem__(self, key: str, data: T) -> None:
		try:
			position = self.__linear_probe(key, False)
		except KeyError:
			# whoops, no more empty space, time to rehash
			self.rehash()
			self.__setitem__(key, data)
		else:
			# if we return None, it means we found a new data
			# if we returned an instance, it means there is already an existing key
			if self.table[position] is None:
				self.count += 1
			self.table[position] = (key, data)

	def __getitem__(self, key: str) -> T:
		position = self.__linear_probe(key, True)
		return self.table[position][1]

	def __delitem__(self, key: str) -> None:
		pos = self.__linear_probe(key, False)
		self.table[pos] = None
		self.count -= 1

		pos = (pos + 1) % len(self.table) # start with the next element
		while self.table[pos] is not None:
			item = self.table[pos] # grab the item at that position
			self.table[pos] = None # set that position as None
			self.count -= 1 # remove one from count (we will increment when we reinsert it back)
			self[item[0]] = item[1] # reinsert the element
			pos = (pos + 1) % len(self.table) # go to the next position

	def __linear_probe(self, key: str, is_search: bool) -> int:
		position = self.hash(key)

		for _ in range(len(self.table)):
			if self.table[position] is None:
				if is_search:
					# we are searching and found nothing
					raise KeyError(key)
				else:
					# we are trying to add a value and found an empty space
					return position
			elif self.table[position][0] == key: 
				# found the key
				return position
			else:
				position = (position + 1) % len(self.table)

		# we looped through the entire thing and got nothing
		raise KeyError(key)

	# it took python to version 3 to implement this
	def __str__(self) -> str:
		result = ""
		for item in self.array:
			if item is not None:
				(key, value) = item
				result += " (" + str(key) + "," + str(value) + ")\n"
		return result
```