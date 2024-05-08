- Because they forgor LMAO
```python
from ctypes import py_object
from typing import TypeVar, Generic

T = TypeVar('T')

class ArrayR(Generic[T]):
    def __init__(self, length: int) -> None:
        if length <= 0:
            raise ValueError("Array length should be larger than 0.")
        self.array = (length * py_object)() # initialises the space
        self.array[:] =  [None for _ in range(length)]

    def __len__(self) -> int:
        return len(self.array)

    def __getitem__(self, index: int) -> T:
        return self.array[index]

    def __setitem__(self, index: int, value: T) -> None:
        self.array[index] = value
```

#### Analysis
- `__init__` is O(n) due to needing to loop through the array to set everything to None
- `__len__, __getitem__, __setitem__` are all O(1)
	- self explanatory