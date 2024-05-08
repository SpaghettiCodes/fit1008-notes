![[Pasted image 20240422145300.png]]

- Every iterative function can be implemented using recursion
	- Iterations are replaced w/ function calls
	- Base case is the condition for the loop
	- Would require auxiliary function to converge arguments

- Every recursive function can be implemented using iteration
	- Past results are stored in accumulators or a stack (remember how recursive functions are implemented using a run-time stack) (actually, thats just how running a program works, the function to run next is placed into a stack)

- The complexity of a recursive function and a iteration function for the same problem will usually be the same
- Doing recursion is a major flex to newbs

#### Pros and Cons of Recursion
##### Advantages
- Its more natural (Fibonacci)
- Easier to prove correct
- Easier to analyze

##### Disadvantage
- Run-time overhead
	- For tail-recursion, this depends on the compiler
	- Run-time overhead meaning
		- The resources that are used that do not contribute to the intended result, but are required by technology or method used
			- Method call overhead - Each method call require setting up a stack frame, copying parameters and return address, this represents CPU overhead
- Memory overhead
	- Each function calls needs to allocate a stack space, _and stack space is very expensive_
	- This is why stack overflow will happen to bad recursions