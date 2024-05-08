- Must be an element in the array
- Ideally, this value is the median of all values
	- The pivot would perfectly split the array in half

- How to pick the median element
	- We could pick a small sample of elements and then choose the median between all these
- However, its just better (and more efficient), to choose a random element

- First element is usually a bad idea
	- The input is somewhat sorted // presorted\
- Below is the recursion tree if the pivot is at the first

##### The recursion tree if you choose the first element as the pivot
![[Pasted image 20240507182845.png]]
- As seen above, the depth would be N, instead of log N
	- This is because only one element is seperated from the array per iteration