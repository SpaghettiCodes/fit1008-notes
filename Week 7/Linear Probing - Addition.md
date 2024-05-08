- A [[Open Addressing]] method
#### Algorithm
- Adding an item with hash value N
- If `Array[N]` is empty, we place the item there
- If there is already another item there
	- A Different key - do a linear search from N for a empty slot:
		- Search for the first empty space in the array from N + 1
			- if there are no empty spot, we would need to rehash
				- can only be done once we traverse the whole table
				- Create a bigger array and reinsert all items
		- add the item there
	- Same Key - just update the data

#### Example:
![[Pasted image 20240410150522.png]]
Kruse already occupies spot 5, so we place Horowitz at 6 instead

![[Pasted image 20240410150642.png]]
Kruse already occupies spot 5 (collision), so we try to insert in place 6
Horowitz already occupies spot 6 (conflict), so we probe for empty space
We place Langsam at space 2
- it is only possible to have one conflict (wtf), everything other than that is just probing

##### Probe Chain
- a list of index that was accessed
- in the above example, the probe chain is 6 -> 0 -> 1 -> 2

