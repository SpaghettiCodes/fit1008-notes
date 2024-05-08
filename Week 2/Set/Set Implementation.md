##### [[Set Array - Python Implementation|Set Array]]
- Set implemented using a ArrayR
##### [[Set BitVector - Python Implementation|Set BitVector]]
- Only allows positive integers as items (or negative integers, no combination)
- The set is represented using a vector of bits
	- Item _i_ belongs to the set if the bit is 1 in the position _i_ - 1
	- This allows us to use bit manipulation techniques

![[Pasted image 20240413172650.png]]
##### [[Invariants]]
- valid data will only appear from 0 to size - 1

##### Arrays vs Bit Vectors

| Array                                                  |           Aspect           | Bit Vectors                                                                   |
| ------------------------------------------------------ |:--------------------------:| ----------------------------------------------------------------------------- |
| Any                                                    |     Item Type to Store     | Only Integers                                                                 |
| O(1) (we can just access size)                         |    \_\_len__ complexity    | O(\|elem\|) (we need to count bit by bit)                                     |
| Quite (ok very) expensive                              | Other operation complexity | O(1)                                                                          |
| Supports arbitrary sets of arbitrary size <sub>1</sub> |        Size of Set         | Limited by the number of bits in bitvectors (which is an integer)<sub>2</sub> |
<sub>1</sub> Have fun with memory allocation tho
<sub>2</sub> Except Python, Python integer can support any arbitrary size
