[[Stack ADT]]
- Contains 2 attributes
	- An array to store the items
		- length of array == max capacity
	- An integer indicating the first empty space in the array
		- usually reuse length

#### [[Invariants]]
- Valid data appears between 0 to length - 1 position of the array 
- Element at the top of the stack is the element in position length - 1
	- _yes_ the end of the array is the first element's location
		- This is for complexity issue (shuffling is too hard)