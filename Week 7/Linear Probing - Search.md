#### Algorithm
- Search for an item with the hash value of N
- Perform a linear search from array[N] until either the item or an empty space is found (or we loop though the entire array)
	- if empty space is found, we immediately raise an KeyError exception