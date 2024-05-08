- An ADT used to store unordered unique elements // members
	- No duplicates allowed
- Items can be added and removed
- Two sets can be compared (and), merged (or), subtracted (difference)

##### Key Operations
| Name         | Function                                                                                                                   |
| ------------ | -------------------------------------------------------------------------------------------------------------------------- |
| Set          | Creates the set                                                                                                            |
| add          | Adds an element into the set                                                                                               |
| remove       | Remove an element from the set                                                                                             |
| member       | Check if an item is a member of the set                                                                                    |
| union        | union of 2 sets, S<sub>1</sub> U S<sub>2</sub> contains a if a belongs in S<sub>1</sub> **or** S<sub>2</sub>               |
| intersection | intersection of 2 sets, S<sub>1</sub> ∩ S<sub>2</sub> contains a if a belongs in S<sub>1</sub> **and** S<sub>2</sub>       |
| difference   | difference of 2 sets, S<sub>1</sub> \\ S<sub>2</sub> contains a if a belongs in S<sub>1</sub> **but not in** S<sub>2</sub> |
##### Other common operations
| Name      | Function                         |
| --------- | -------------------------------- |
| \_\_len__ | Gets the length of the set       |
| is_empty  | Checks if the set is empty       |
| clear     | Removes all element from the set |

#### Set Application
- Represent an unordered collections of elements with fast membership check
- Artificial Intelligence
	- Represent relations between objects and entities
		- Sets of nodes / Sets of edges in a graph
	- Represent characteristic functions