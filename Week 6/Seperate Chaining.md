- Applies a linked list (or a balanced tree) to represent colliding keys
![[Pasted image 20240409144940.png]]
#### How it works
- Initially, each cell of the table refers to an empty list
- If a key is hashed to h, we push it to the list referred to from that cell
	- This causes addition, deletion and lookup of keys in the table has a complexity
		- Addition - O(n), n is the number of keys in the corresponding list
			- We need to check if the key already exists
		- Deletion - O(n), n is the number of keys in the corresponding list
		- Index - O(n), n is the number of keys in the corresponding list