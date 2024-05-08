A divide and conquer algorithm to search an element, by dividing the array into half every time the element is not found
- can only be used on a **sorted** array
	- Or else we cannot guarantee that the item we are looking for is at **not** at the half that we discarded

```python
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
```

#### Time Complexity
##### Best Case
- The item to find is in the middle
	- Loop stops immediately
	- O(1)
##### Worst Case
- The item is at one of the extremes
	- Since we break down the array into half every iteration, the running time for the algorithm grows faster than constant time, but slower than quadratic time (log n) 
	- Therefore, the worst case time complexity is O(log N)

```
1st iteration - n   = n/2^0 items
2nd iteration - n/2 = n/2^1 items
3rd iteration - n/4 = n/2^2 items
4th iteration - n/8 = n/2^3 items
  ...
bth iteration - n/2^(b - 1) = 1 item

   b = log2(n) + 1
O(b) = O(log n)
```

