- A Cluster is a sequence of full hash table slots
- The tendency for clustering to occur increases as the load factor > 0.5
#### Issues
- Adding a key with hash value N can drastically increase the search time for keys with values other than N
- Deletion can also be time-consuming, as entire cluster needs to be hashed
	- Making our time complexity less of O(1) and more of O(N)

#### Solve
- Taking bigger steps rather than adding 1 during probing (like 2 or 3)

![[Pasted image 20240410162201.png]]