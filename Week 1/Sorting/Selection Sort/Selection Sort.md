#### Algorithm
[[Selection Sort - Python Code]]
- Start at the leftmost unsorted element, and set it as the current minimum
- Traverse the rest and find the minimum element in the list
- Once we find it, swap it with the leftmost unsorted element
- Repeat until end

![[Pasted image 20240407181137.png]]
#### [[Invariants]]
- Everything to the left of the leftmost unsorted element is sorted, and is in its final position

#### Optimization
- Nope, no optimization here
	- We are unable to detect if the list is already sorted as for each iteration, we are looking for a minimum
		- This tells us nothing about the relative order of the elements

#### Properties

| Algorithm                                        | Stable | Incremental |
| :----------------------------------------------- | ------ | ----------- |
| [[Selection Sort - Python Code\|Selection Sort]] | No     | No          |
#### [[Incremental]]
- Selection sort **has** to redo all the work again in order to sort the list given a new element
	- List - `[3, 6, 10, 14, 18, 20, 13 <- new element]`
	- The list will remain unchanged for the first 3 iteration
		- The algorithm is trying to find 13 as the minimum element
	- After finding the new element, Selection Sort STILL needs to continue its operation, as the new element will swap with the sorted one
		- List - `[3, 6, 10, 13, 18, 20, 14 <- 14 is now in the incorrect place!]`
	- Therefore, our algorithm needs to redo the entire algorithm (not incremental)
#### [[Stable]]
- Unstable, as we are swapping with non-consecutive elements
	- `Original list - [3, 6, 10, 14a, 14b, 13]`
	- When the marker reaches 14a, its going to swap with the minimum that is found (13)
		- `[3, 6, 10, 13, 14b, 14a]`
	- The algorithm will then end without swapping anyone else
		- HOWEVER, the ordering of 14a and 14b has changed!
			- NOT Stable