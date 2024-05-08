- An ADT that follows the Last In First Out (LIFO) principle
	- Last element added is the first to be removed
- Access to all other element is not allowed

##### Key Operations
| Name  | Function                     |
| ----- | ---------------------------- |
| Stack | Creates a new stack          |
| push  | add an element to the top    |
| pop   | take an element from the top |
##### Other Operations
| Name       | Function                          |
| ---------- | --------------------------------- |
| peek       | look at the item at the top       |
| _\_len\_\_ | gets the length of the stack      |
| is_empty   | check if stack is empty           |
| is_full    | check if stack is full            |
| clear      | removes all elements in the stack |
#### Applications of a Stack
(why the fuck do they ask this)
- Reversing a sequence of items
	- Use a stack ADT to push each item into a stack, then pop and append it to a new array
- Implementing a "History"/"Undo" system
	- When you access a page, the page url is added to a stack
	- When the back button is pressed, the url is popped from the stack
- Parsing
	- Delimiter Matching
	- Reverse polish notation
		- "2 3 + 1 /"
- Run-time Memory Management
	- Stack oriented programming languages (MIPS, WebAssembly)
	- Virtual machines
	- Function calling
- Implement Recursion (?)