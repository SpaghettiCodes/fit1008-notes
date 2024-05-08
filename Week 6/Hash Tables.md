- A Container that is optimized for **searching, adding and deleting** a specific object
	- A Hash table is able to do **O(1)** operations
		- Worst case can be **O(N)**, hash table need to be constructed properly
	- We do not need to traverse them in any order or sort them

##### Design choices
 - We use an array for constant time access to a position
	 - This would mean that each item must have an assigned position
 - Each item must have a unique key which is symbolic
 - Basic Operations for a Hash Table
	 - Hash Function: maps a unique key to an array position
	 - Add
	 - Search
	 - Delete

![[Pasted image 20240408145617.png|450]]
##### Why not use Unsorted / Sorted List?
- Unsorted List Complexity
	- Search = `O(N)` worst in linked list and array
	- Add = `O(1)` best in linked list (added to first) and arrays (added to last)
		- `O(N)` worst
	- Delete = `O(N)` worst in linked list and array
- Sorted List Complexity
	- Search = `O(N)` in linked list, `O(log N)` in array
	- Add = `O(N)` in both linked list and arrays
	- Delete = `O(N)` in linked list and arrays
- We are trying to achieve `O(1)` for adding, searching and deleting