```python
def swap(the_list, x, y):
	the_list[x], the_list[y] = the_list[y], the_list[x]

def bubble_sort(the_list):
	n = len(the_list)
	for _ in range(n - 1):
		for i in range(n - 1):
			if (the_list[i] > the_list[i + 1]):
				swap(the_list, i, i + 1)
```

#### Analysis
- `for _ in range(n - 1)` is O(n)
- In the inner loop, `for i in range(n - 1)` is another O(n)
- The best/worst time complexity of Bubble sort is O(n<sup>2</sup>)