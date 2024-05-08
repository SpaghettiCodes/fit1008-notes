- We would need 
	- a temporary array to store the merged solution
	- markers for the part of the array we are looking at

Slides implementation
```python
def merge_arrays(a: ArrayR, start: int, mid: int, end: int, tmp: T) -> None:
	ia = start
	ib = mid + 1
	for k in range(start, end + 1):
		if ia > mid: 
			# half1 finish, copy half2
			tmp[k] = a[ib]
			ib += 1
		elif ib > end: 
			# half2 finish, copy half1 over
			tmp[k] = a[ia]
			ia += 1
		elif a[ia] <= a[ib] 
			# the left side value is lesser than the right side value
			# the <= symbol gurantees the merge array is stable
			# as if there is 2 of the same value, the value that comes first
			# (which would be at the first end), will be added in the front
			tmp[k] = a[ia]
			ia += 1
		else: 
			# the right side value is lesser than the left side value
			tmp[k] = a[ib]
			ib += 1

def merge_sort_aux(array: ArrayR, start: int, end: int, tmp: T) -> None:
	if not start == end: # 2 or more still need to sort
		mid = (start + end) // 2
		# split into two halves
		merge_sort_aux(array, start, mid, tmp)
		merge_sort_aux(array, mid + 1, end, ,tmp)
		# merge
		merge_arrays(array, start, mid, end, tmp)
		# copy tmp back into the original
		for i in range(start, end + 1):
			array[i] = tmp[i]


def merge_sort(array: ArrayR) -> None:
	tmp = ArrayR(len(array)) # stores the merged sorted array
	start = 0
	end = len(array) - 1

	merge_sort_aux(array, start, end, tmp)
```


My Implementation

```python
def merge_array(array1, array2):
	tmp = []
	i = 0
	j = 0

	while i < len(array1) or j < len(array2):
		if i >= len(array1): 
			# 1st array done, copy array2 values over
			tmp.append(array2[j])
			j += 1
		elif j >= len(array2):
			# 2nd array is done, copy array1 values over
			tmp.append(array1[i])
			i += 1
		elif array1[i] <= array2[j]
			# value in array1 is lesser than array2
			# we add that value in first
			# <= ensures that merge array is stable
			# same reasoning as above, because array1 is guranteed
			# to be at the front of array2
			# if 2 values are equal, we add the value that comes first
			tmp.append(array1[i])
			i += 1
		else
			# value in array2 is lesser than array1
			tmp.append(array2[j])
			j += 1
	return tmp

def merge_sort(array):
	if len(array) <= 1:
		# array is less than one
		# nothing to sort here
		# just return immediately
		return array
	mid = len(array) // 2
	# split to two arrays
	array1 = merge_sort(array[:mid]) # first end
	array2 = merge_sort(array[mid:]) # second end
	# merge them back into one
	# please ensure the first end is at the front (or else not stable)
	return merge_array(array1, array2)
```
