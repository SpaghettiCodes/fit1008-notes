```python
from abc import ABC, abstractmethod
from typing import TypeVar, Generic # POV no templates
T = TypeVar('T')

class Stack(Generic[T]):
	def __init__(self) -> None:
		self.length = 0

	@abstractmethod
	def push(self, item: T) -> None:
		pass

	@abstractmethod
	def pop(self) -> T:
		pass

	@abstractmethod
	def peek(self) -> T:
		pass

	def __len__(self) -> int:
		return self.length

	def is_empty(self) -> bool:
		return len(self) == 0

	@abstractmethod
	def is_full(self) -> bool:
		pass

	def clear(self) -> None:
		self.length = 0
```
- yeah, theres no implementation, its an adt what do you expect?

#### Analysis
- All methods in this abstract class is O(1)