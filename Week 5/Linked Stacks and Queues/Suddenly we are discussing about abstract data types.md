Any data types provides a storage for a collection of data items, as well as a set of operations to interact with the data

A Data structure is a particular way in which the data is organized (structured) in memory
- it also the way a given data type is implemented
- IT IS NOT a DATA TYPE

An Abstract Data type **does not provide any info on how**
- User can only interact with the data through the provided operations

This can be seen from the Stack ADT
- A Stack ADT must have push, pop, is_empty, reset
	- However, the implementation is not known, and could be an array, linked list, or something else completely (Data Structure)
	- As a user, **only the operation needs to be known**

#### Pros and Cons of Abstract Data Types
##### Main advantage: maintainance
- Changing implementation of ADT != changing user's code

##### Main disadvantage: efficiency
- Having access to the implementation might allow good programmers to improve time/space performance