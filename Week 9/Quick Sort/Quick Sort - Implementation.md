```python
def quick_sort(array: ArrayR) -> None:
	start = 0
	end = len(array) - 1
	quick_sort_aux(array, start, end)

def quick_sort_aux(array: ArrayR, start: int, end: int) -> None:
	if start < end:
		boundary = partition(array, start, end)
		quick_sort_aux(array, start, boundary - 1)
		quick_sort_aux(array, boundary + 1, end)

def partition(array: ArrayR, start: int, end: int) -> int:
	mid = (start + end) // 2
	pivot = array[mid]
	swap(array, start, mid)

	boundary = start

	for k in range(start + 1, end + 1):
		if array[k] < pivot:
			boundary += 1
			swap(array, k, boundary)
	swap(array, start, boundary)
	return boundary
```

Here's the rough diagram on how the partitioning will work
![[Pasted image 20240507175715.png]]
Algorithm
- Select a pivot
- Shift the pivot to the front
- Place the boundary at the 1st element (the pivot)
- Check if the element is smaller than the pivot, if it is, increment boundary and swap with boundary.
- At the end, swap the pivot with the boundary
##### [[Invariants]]
- After the partitioning, the pivot is guaranteed to be **in the correct partition**