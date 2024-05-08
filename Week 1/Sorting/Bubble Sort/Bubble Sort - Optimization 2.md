```python
def swap(the_list, x, y):
	the_list[x], the_list[y] = the_list[y], the_list[x]

def bubble_sort(the_list):
	n = len(the_list)
	for mark in range(n-1, 0, -1):
		swapped = False # set swap to false first
		for i in range(mark):
			if (the_list[i] > the_list[i + 1]):
				swap(the_list, i, i + 1)
				swapped = True # we swapped! set to true
		if not swapped:
			# if no one is swapped, that could only mean one thing
			# the entire list is already sorted
			break
```

### Analysis
- Now we are able to break prematurely, the Big-O is slightly different
	- Best case is O(n)
		- Occurs when the list is already sorted
		- We make **a single iteration** of the outer loop (O(1)), which runs the inner loop for n - 1 times (O(n))
	- Worst case is O(n<sup>2</sup>)
		- The collection is sorted in the opposite order
		- The outer loop iterates n - 1 times
		- The inner loop iterates `mark` times, which is decremented in each iteration of the outside loop
			- the inner loop will iterate (n - 1) + (n - 2) + (n - 3) ... times
			- This adds up into an arithmetic series:
				- $(n - 1) + (n - 2) + ... + 1 = \frac{(n - 1 + 1) \cdot (n- 1)}{2} = \frac{n^2 - n}{2} = O(n^2)$ 
