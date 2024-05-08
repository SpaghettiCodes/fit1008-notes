- Mapping of a set of Keys K to a set of Hash Values H
#### Properties
- The key is type dependent (it depends on the type of item's key)
- Returns a value within the array's range (0, TABLESIZE - 1)
##### Desirable
- Fast
	- should not have too many arithmetic operations
- Minimize collisions (two keys mapped to the same hash value)
	- Distribute keys by hash values uniformly
	- Perfect hashing - maps every key into a different hash
		- Almost impossible to achieve in real practice

#### Universal hashing
- Apply a family of hash functions F
	- the family is designed to minimize probability of collisions, regardless of distribution of keys
- Given a key, picks a random hash function from F
- Guarantees the chance of a collision to be `<= k / TABLESIZE`
- Good Hash functions aim to emulate universal hashing
	- Emulate a random function's behavior
	- Reduce the chance of a collision through distributing keys by hashes uniformly

#### Defining a Hash Function
- Do not use non-data, modify the key until all bits count
- The more elements in the key is used, the better the hash function (less collisions)
	- Do not use too much as it may be slow
- Using all elements is not enough to guarantee a good spread of possible hashes
	- We would need something that uses all elements as well as taking into account of its position
- We would need something in the range of the TABLESIZE
	- % TABLESIZE if its too big
	- convert to \[0, 1\] and then * TABLESIZE if its too small
	- [[Horner's method]] - mod/multiply at each step
- If the key is random, the simple formula of `position = key % TABLESIZE` is enough
- If the key is not random, use a prime table size
	- If many values and TABLESIZE share a common factor, they will hash to the same position
		- Example: a TABLESIZE of 10, will cause every key that ends with a 0 to be hashed to 0
- If we are multiplying or modding with a constant, ensure that they are relatively prime / co-prime (no common factors)
	- Having common factors results in keys with close hash values (clustering) and same values (collisions)
	- [[Common Factors effect on hashing]]
- We can also choose the coefficients in a pseudo-random fashion
	- Use a different coefficient for each key position
	- Example:
```python
def hash(word: str, TABLESIZE: int) -> int:
	value = 0
	a = 31415
	b = 27183
	# A and B should be prime to reduce the chances of getting into a problem of zero divisors
	# zero devisors are  A * B = 0 (mod TABLESIZE - 1), neither A nor B are divisors of TABLESIZE - 1
	for char in word:
		value = (ord(char) + a * value) % TABLESIZE
		a = a * b % (TABLESIZE - 1) # the base change for each position pseudorandomly
	return value
```

#### Example of a Hash Function
```python
def hash(word: str, TABLESIZE: int) -> int:
	value = 0
	for char in word:
		value = (value * 31 + ord(char)) % TABLESIZE
	return value

# with pseudorandom coefficients
def hash(word: str, TABLESIZE: int) -> int:
	value = 0
	a = 31415
	b = 27183
	for char in word:
		value = (value * a + ord(char)) % TABLESIZE
		a = a * b % (TABLESIZE - 1)
	return value
```
