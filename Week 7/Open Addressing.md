- Each array position contains a single item
- Upon collision, either update (same key) or use an empty space to store the new item (which empty space depends on technique)
	- This means we would need an array of at least x 2 the size of the number of elements

#### Terminology
- Load Factor - Total number of items / TABLESIZE
- [[Clustering|Cluster]] - sequence of full hash table slots

- The load factor should be under 2/3
	- The probe length (number of items visited before an element is found) would be too high
	- It would be better if it is below 0.5

![[Pasted image 20240410164337.png]]