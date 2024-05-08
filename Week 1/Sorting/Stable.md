- A sorting algorithm is table if it maintains the relative order among elements

#### Example
```
[8, 3, 8, 6, 3]
[a, b, c, d, e]

there are 2 8s (8a and 8c)
there are 2 3s (3b and 3e)

A stable sort will always obtain 
[3, 3, 6, 8, 8]
[b, e, d, a, c]
- The relative order is preserved
- b is before e, and a is before c

A unstable sort will instead obtain
[3, 3, 6, 8, 8]
[e, b, d, a, c]
- notice how e is behind b now, even though e should be after b
- the sorting algorithm isnt stable as the relative order isnt preserved
```
