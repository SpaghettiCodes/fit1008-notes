- Split the original problem into subproblems
- Solve each problem independently
- Combine their solutions to yield the final solution

- Such algorithm can be very efficient, **especially if the subproblems have roughly the same size**

![[Pasted image 20240507111359.png]]
![[Pasted image 20240507111350.png]]

#### Sorting array by Divide and Conquer
- The general pseudocode is usually
```python
def sort(array) -> None:
	if len(array) > 1 # if len is <= 1, the array is already sorted
		split(array, first_part, second_part)
		sort(first_part)
		sort(second_part)
		combine(first_part)
```

- Merge sort - simple split, complex combine
- Quick Sort - complex split, simple combine