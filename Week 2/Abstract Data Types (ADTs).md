- [[Data Types]] that we do not know the implementation of
	- Data abstraction
- Provides information on
	- The possible values of the type and their meaning
	- The operation that can be done on them
- DOES NOT provide information on the implementation
	- like how the values are stored, how are the operation implemented
- Users only interact with data w/ the provided operation


#### Advantages
- Simplicity
	- Build programs w/o knowing their implementation
		- for babies
- Maintenance
	- Implementation can change w/o affecting you
		- The implementation of the adt and your program are abstracted and seperated
- Flexibility and reusability
	- If several ADTs are available, its easy to switch
- Portability
	- Different compilers can use different implementation of the ADT