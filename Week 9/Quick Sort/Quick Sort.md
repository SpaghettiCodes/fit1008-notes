- Splitting the array by partitioning the array into two
	- One with values smaller than pivot P
	- Another with values greater than the pivot P
- Combine by appending the pivot in the middle

![[Pasted image 20240507174507.png]]

#### Complexity
- n is the length of the array
- Best case is O(n log(n))
	- Always pick median as pivot
	- The array is always split in half for every iteration
- Worst case is O(n^2)
	- Always pick min, max as pivot
	- [[Quick Sort - Choosing the pivot#The recursion tree if you choose the first element as the pivot|See the recursion tree]]

