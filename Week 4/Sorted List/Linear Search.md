- Going through each element one by one until the element that we want is found
- If an element larger than the element we want is found in the list, that means the element cannot be found (in a sorted list)

```python
def index(self, item: T) -> int:
	for i in range(len(self)):
		if item == self.array[i]:
			return i
		elif item < self.array[i]:
			raise ValueError("item not in list")
	raise ValueError("item not in list")
```

#### Time Complexity
##### Best Case
- Loop stops in the first iteration
	- The item we are looking for is at the start of the list
- O(1)
##### Worst case
- Loop goes all the way to the length of the array
	- The item we are looking for is at the end of the list
- O(N)
