#### Linked Storage
- Unknown list size (no need to resize by copying)
- Many insertions and deletions needed within, rather at the end
	- No direct access to the positions (no random access)
- Most operation needs traversal of the list from the 1st element

#### Contiguous Storage
- Known number of elements
- Few insertion and deletion needed from within (less shuffling)
- Lots of searches on a sorted list (binary search can be used)
- Access to elements by their positions (constant time) (random access)