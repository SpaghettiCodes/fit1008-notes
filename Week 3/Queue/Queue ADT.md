- An ADT used to store items and its operation follows a First In First Out (FIFO) principle
	- The first element to be added is the first element to be deleted
- Access to any other element is unnecessary and not allowed

##### Key operations
| Name   | Function                    |
| ------ | --------------------------- |
| Queue  | Creates a queue             |
| append | adds an item to the back    |
| serve  | takes an item off the front |
##### Common operations
| Key       | Function                            |
| --------- | ----------------------------------- |
| __len\_\_ | gets the length                     |
| is_empty  | check if the queue is empty         |
| is_full   | check if the queue is full          |
| clear     | removes all elements from the queue |

#### Applications
- Scheduling and buffering
	- Printers
	- Keyboards
	- Executing Asynchronous procedure calls
	- message buffers between programs
		- Amazon Simple Queue Service (SQS) (im just kidding this isnt in the slides)
