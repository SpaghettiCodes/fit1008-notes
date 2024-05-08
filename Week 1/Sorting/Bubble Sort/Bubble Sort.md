#### Algorithm
[[Bubble Sort - Python Code]]
- Start with the leftmost element X
- Compare X with the element Y to the right
- If X > Y Swap
- Move one position to the right
- Repeat for (length of list - 1) times
#### [[Invariants]]
- After every traversal, the list has the same elements
- In each traversal, **at most n-1 swaps are performed**, n is the length of the list
- **After every traversal**, the largest yet unsorted element **gets to their final place**
	- **After i passes** of the algorithm, the **last i elements** appears in a sorted order
	- The maximum number of traversal needed to sort would be **n - 1**, n is the length of the list
#### Optimization
1. Using the invariant above (after every traversal, the largest unsorted element gets to its final place), we can optimize bubble sort slightly
	- We can avoid comparing the last element moved for each iteration
		- Set a mark to determine the last element sorted
		- [[Bubble Sort - Optimization 1]]

2. We can stop the iteration if the entire algorithm is already sorted
	- [[Bubble Sort - Optimization 2]]

#### Properties

| Algorithm                                        | Stable | Incremental        |
| :----------------------------------------------- | ------ | ------------------ |
| [[Bubble Sort]]                                  | Yes    | No                 |
| [[Bubble Sort - Optimization 2\|Bubble Sort II]] | Yes    | Yes (add to front) |
#### [[Incremental]]
- Adding an element at the end
	- Not incremental
	- The steps to sort an element at the end would depends on the position it's suppose to be in (n - 1)
- Adding an element at the front
	- Very incremental
	- We can guarantee that after 1 iteration it will be sorted
		- Note that this only works for [[Bubble Sort - Optimization 2]], as that variant actually checks if the list is already sorted

#### [[Stable]]
- The only time in which elements can get out of order is when we swap
- The order of the elements is swapped ONLY when `list[i] > list[i + 1]`
	- it will not swap if it is equal
- Therefore, it is stable
	- A small change of the symbol `>` to `>=` will make it unstable
