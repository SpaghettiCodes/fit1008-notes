```python
from abc import ABC, abstractmethod
from typing import TypeVar, Generic

T = TypeVar('T')
class Set(ABC, Generic[T]):
	def __init__(self) -> None:
		self.clear()

	@abstractmethod
	def __len__(self) -> int:
		pass

	@abstractmethod
	def is_empty(self) -> bool:
		pass

	@abstractmethod
	def clear(self) -> None:
		pass

	@abstractmethod
	def __contains__(self, item: T) -> bool:
		pass

	@abstractmethod
	def add(self, item: T) -> None:
		pass

	@abstractmethod
	def remove(self, item: T) -> None:
		pass

	@abstractmethod
	def union(self, other: Set[T]) -> Set[T]:
		pass

	@abstractmethod
	def intersection(self, other: Set[T]) -> Set[T]:
		pass

	@abstractmethod
	def difference(self, other: Set[T]) -> Set[T]:
		pass
```