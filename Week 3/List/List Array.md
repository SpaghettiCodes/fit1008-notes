##### Advantages
- Very fast access O(1)
- Very compact representation if the array is relatively full
##### Disadvantages
- Expensive to resize
	- create a new array and copy all items
- Slow operations if shuffling elements is required
	- Insert
	- Remove
	- delete_at_index
#### [[Invariants]]
- Valid elements between 0 and self.length - 1
- The head is at index 0 