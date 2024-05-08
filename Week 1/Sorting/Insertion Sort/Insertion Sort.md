Basically [[Selection Sort]], but better (and [[Stable|stable]])
#### Algorithm
[[Insertion Sort - Python Code]]
- Split the list into 2 parts
	- Already sorted part (with one element)
	- Part that is unsorted
- Extend the sorted part by taking any element from the unsorted part and inserting it into the sorted part, maintaining the order
	- For every iteration
		- Store the first unsorted value (X) in a temporary buffer
		- Shift all sorted element bigger than X one position to the right
		- Copy X into the new empty space

![[Pasted image 20240407233715.png]]
#### [[Invariants]]
- Elements in the Sorted Part are always sorted and grows by 1 in each iteration
	- Number of iteration would be n - 1
	- Elements in the sorted part **might not be in their final position**

#### Properties
| Algorithm                                        | Stable | Incremental       |
| :----------------------------------------------- | ------ | ----------------- |
| [[Insertion Sort - Python Code\|Insertion Sort]] | Yes    | Yes (add to back) 
#### [[Incremental]]
- Is Incremental by appending the new element at the end
	- Since we need to split the list into 2 parts, we can just split the already sorted part, and the new element
		- We can then just insert the new element within the sorted part
		- This takes 1 iteration
	- We can split the sorted part by just setting `mark` at the last sorted
		- due to the invariant above, everything to the left of the mark is already sorted

#### [[Stable]]
- The algorithm is stable
	- The only time in which elements can get out of order is when
		- Elements are shuffled to the right
			- Shuffled elements are kept in relative order, so this does not break stability ( we used > instead of >= )
			- if we changed the comparison to >=, it makes it non stable
		- We re-insert the element from the temp
	- Temp element jumps over those shuffled, but none of the shuffled elements are **equal and before the temp elemen**t , so those do not break stability
 