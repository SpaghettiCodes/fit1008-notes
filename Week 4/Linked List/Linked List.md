#### Attributes
- A reference to a head node
- (optional) length

List Object
\[head\] -> \[Node A\] -> \[Node B\] -> \[Node C\] -> \[Node D\]
\[length\]

-> : linked via the [[Linked Node|node.link]]
##### Advantages
- Fast deletion // addition of an item
	- No reshuffling
		- Accessing values is _way_ faster than copying elements from one place to another
- Easily resizable: just create/delete a node
- Less memory used than an array if the array is relatively empty 
	- As soon as the array is fuller than half, the array will use less memory than the list
		- i.e. an array of size 7, when filled with 3 elements, uses more memory than a list (size 7 vs size 6). However, if an element is added to the array, it will use less memory (size 7 vs size 8)
###### Disadvantages
- More memory used than an array if the array is relatively full 
	- Every data item has an associated link
	- For an array of 5 size, Linked list will have 10
		- Linked list can be thought of having a "data" array and a "link" array
- Some operation may be more time consuming 
	- no random access

#### [[Invariants]]
- The number of valid elements is `self.length`, and are found via the node links starting from the head