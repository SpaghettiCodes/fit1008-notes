An algorithm is incremental if it does not need to re-compute everything after a small change
- Able to reuse most of its work that is already done to handle the change

A sorting algorithm is considered incremental if
- Given a sorted list and one new element
- Use one (or a few) iteration of the algorithm to return a sorted list that has the new element
	- The number of iteration has to be a small constant (no variables)