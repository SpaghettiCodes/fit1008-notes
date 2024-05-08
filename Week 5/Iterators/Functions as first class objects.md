##### First Class objects == being like any other objects
- Functions can be assigned to variables, passed as arguments to functions, as well as returned by a function / method

```python
def my_call(f, x): 
	# f is taken as a function as an argument
	f(x)

def my_function(x):
	print(x)

my_call(my_function, "hello") # prints out hello
```
##### Higher order function
- Takes another function as argument and/or
- Returns another function as argument

```python
def return_f(x):
	def f(y):
		return x + y
	return f

g = return_f(30) # g is now bound to a function that adds 30 to its arguments

g(2) # 32
# you can also call it like return_f(30)(2)
```

We are able to combine the both of them (i mean like yeah no shit right)

```python
def plus_10(x):
	return x + 10

def mult_by2(x):
	return x * 2

def combine(f, a_list):
	def h(g):
		return [f(g(x)) for x in a_list]
	return h

h = combine(plus_10, [1,2,3,4])
h(mult_by2) # [12, 14, 16, 18]

# what is the purpose of this?
```
