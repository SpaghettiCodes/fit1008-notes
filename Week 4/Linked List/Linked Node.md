- A Collection of Nodes
- Each node contains
	- One or more data items
	- One or more links to other nodes

```python
from typing import TypeVar, Generic

T = TypeVar('T')

class Node(Generic[T]):
	def __init__(self, item: T = None) -> None:
		self.data: item
		self.link: Node
```

