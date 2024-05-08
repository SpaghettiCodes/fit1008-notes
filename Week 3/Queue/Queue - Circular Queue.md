The solution to [[Queue - Linear Queue - Python Implementation#Problem|the problem]] found in linear queues can be remedied by using a Circular Queue instead

![[Pasted image 20240413223259.png]]
We warp the rear around to the front so that elements can be added to the front, when the end of the queue is full

#### [[Invariants]]
- If front <= rear, element is stored from front to rear - 1, in that order
- If front > rear, element is stored from the front to the end of array and from 0 to rear - 1, in that order