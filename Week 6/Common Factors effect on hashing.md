Having a common factors used in multiply / mod will cause details to be ignored

##### EXAMPLE
```python
def hash(string):
	value = 0
	for x in string:
		value = (1024 * value + ord(x)) % 128
	return value 
```

if the word "Aho" is given into the `hash`

value = 0
value = (1024 * 0 + 65) % 128 = 65
value = (1024 * 65 + 104) % 128 = 104
value = (1024 * 104 + 111) % 128 = 111

- Since 1024 = 8 * 128 (128 and 1024 have common factors), anything multiplied by 1024 is cast out when we mod by 128
	- Basically, ((1024 * prev_val) + y) mod 128 ≡ y mod 128
		- Prove:
			((1024 * prev_val) + y) mod 128
			≡ (1024 * prev_val) mod 128 + y mod 128
			≡ 1024 mod 128 * prev_val mod 128 + y mod 128
			≡ 0 mod 128 * prev_val mod 128 + y mod 128
			≡ (0 * prev_val) mod 128 + y mod 128
			≡ y mod 128
	- This would mean that only the last character is kept at each mod step
		- This would mean we lose details in our key