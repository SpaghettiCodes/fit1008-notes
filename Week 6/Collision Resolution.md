- Collision - A situation where `hash(key1) == hash(key2)`
	- Conflict - a position in the hash table we attempt to use for a given key is already occupied by a different key (you will see in [[Open Addressing]])
- Collisions are bound to happen
- Since we cant put two different keys in the same slot of the hash table, we need to apply a collision resolution mechanism

# IMPORTANT!
Collision = A situation where the hash function returns the same position for two different keys

Conflict = A position in the hash table we attempted to use for a given key is already occupied by another key
##### Ways to handle collisions
- [[Open Addressing]]
- [[Seperate Chaining]]