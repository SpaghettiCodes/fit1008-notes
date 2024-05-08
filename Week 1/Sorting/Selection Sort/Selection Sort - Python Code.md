```python
def find_min(the_list, start):
	pos_min = mark
	n = len(the_list)
	for i in range(mark + 1, n):
		if the_list[i] < the_list[pos_min]:
			pos_min = i
	return i

def swap(the_list, x, y):
	the_list[x], the_list[y] = the_list[y], the_list[x]

def selection_sort(the_list):
	n = len(the_list):
	for mark in range(n - 1):
		min_index = find_min(the_list, mark) 
		swap(the_list, mark, min_index)
```

#### Analysis
- `find_min` has a Big-O of O(N)
- `for mark in range(n - 1)` has a Big-O of O(N)
- Therefore, the best/worst time complexity is O(N<sup>2</sup>)
	- Find min will iterate a varying number of times, depending on the iteration of the main loop (`for mark in range(n - 1))`)
		- It will iterate (n - 1) + (n - 2) + (n - 3) + ... + 1 times
		- This results in the arithmetic series
			- $(n - 1) + (n - 2) + ... + 1 = \frac{(n - 1 + 1) \cdot (n- 1)}{2} = \frac{n^2 - n}{2} = O(n^2)$