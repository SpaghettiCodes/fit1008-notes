```python
def insertion_sort(the_list):
	n = len(the_list)
	for mark in range(1, n) :
		temp = the_list[mark]
		i = mark - 1
		while i >= 0 and the_list[i] > temp:
			the_list[i + 1] = the_list[i]
			i -= 1
		the_list[i + 1] = temp
```

#### Analysis
- The outer loop of the algorithm iteratively picks the next unsorted element and then inserts them into the correct position
	- Each iteration of the algorithm extends the sorted part by one item
- Picking a new element is done by the outer loop, which makes it (n - 1) iteration - O(n)
- The insertion operation consists of 2 parts
	- Finding the correct position for the newly selected item and shuffling larger items in the sorted part
		- The collection is already sorted (best case scenario)
			- each newly selected item already sits in its correct position
			- The inner loop stops immediately -- O(1)
			- O(1) * the outer loop O(n) = best case is O(n)
		- Each newly selected item needs to be inserted in position 0 (worst case scenario - the collection is sorted reversely)
			- The inner loop would need to iterate (sorted array length) times and shuffle the sorted items
			- The sorted array length increases as `mark` increases
			- The total iteration to make would be 1 + 2 + ... + (n - 1)
				- $(n - 1) + (n - 2) + ... + 1 = \frac{(n - 1 + 1) \cdot (n- 1)}{2} = \frac{n^2 - n}{2} = O(n^2)$
	- Copying the newly selected item into the position (O(1))
- Best case O(n), Worst case O(n<sup>2</sup>)