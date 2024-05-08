#### Algorithm
- we use the search function to find the item
- Then, we _will need to reinsert every item from N + 1 to the first empty position_
	- Due to how linear probing works, any key may not be on its actual hashed location
	- Simply changing the delete element to None will cause `___linear_probe` to think no one is there 
		- Even though there WOULD be an element there, but its inserted somewhere else due to the deleted element once occupying the space
	- Simply shuffling all elements may also cause issue
		- Some elements may ALREADY be in it's actual hashed location
	- Therefore, we need to reinsert everything in that cluster

- Another position implementation of delete is to use a special symbol to denote delete
	- we can then modify add and search to take that symbol into account
		- for example, we can just keep on looking if we found a sentinel, then we can move the pair into the sentinel's spot. (search)
		- we can just add in the first deleted spot (add)
			- only for new keys (good luck for existing keys)

![[Pasted image 20240410154057.png]]
Since we are removing Kruse, we would need to reinsert Horowitz, Aho, Standish and Langsam

![[Pasted image 20240410154143.png]]
Here is the final table after deletion, notice how Langsam takes the 6th spot and Horowitz takes the 5th spot now, as Kruse (which occupies the 5th spot) is gone, Horowitz is able to occupy that spot and since the 6th spot is empty, Langsam is able to occupy that spot