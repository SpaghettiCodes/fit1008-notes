```python
def swap(the_list, x, y):
	the_list[x], the_list[y] = the_list[y], the_list[x]

def bubble_sort(the_list):
	n = len(the_list)
	for mark in range(n - 1, 0, -1): 
	# we use mark to iterate through n - 1 instead
	# we set mark to start at the last element, and end at the 2nd element
	# we do not want mark to go to the first element (unnecessary)
		for i in range(mark):
			if (the_list[i] > the_list[i + 1]):
				swap(the_list, i, i + 1)
```

#### Flow Chart
![[Pasted image 20240407165455.png]]

#### Visualization
![[Pasted image 20240407165203.png|250]]