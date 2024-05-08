- An object that help us traverse through a data structure
	- Without accessing the implementation of the data structure (abstraction)
- Traverses the data structure until the end, then raises **StopIteration**

##### Implementation
- We would need a way of creating an iterator object to start the iterations
	- An object other than the list as
		- It would need to move through the list w/o changing the list
		- We might require several iterators on the same list
	- Iterator objects are returned by the method \_\_iter\_\_
- We would need an iterator class to create the object
	- The \_\_init\_\_ method performs the "beginning-of-iteration" initialization
- The class would need a way to return the next element
	- `__next__` method

```python
x = "abc"
it1 = iter(x)
next(it1) # 'a'
next(it2) # 'b'
next(it3) # 'c'
next(it4) # StopIteration
```

##### Using Iterators
```python
def positive(a_list: LinkList[T]) -> bool:
	for item in a_list: # implicitly calls iter and next for you
		if item <= 0:
			return False
	return True
```

Alternative method:

```python
def positvive(a_list: LinkList[T]) -> bool:
	return [] == [e for e in a_list if e <= 0]
```