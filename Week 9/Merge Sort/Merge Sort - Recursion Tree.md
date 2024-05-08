![[Pasted image 20240507173224.png]]

The depth of the recursion tree is log(N)
- N is the number of elements in the array
- This because each iteration splits the array by half
Each level, we do N constant operations
- The merging cost is N, where N is the total element from first half and second half (i.e. number of elements in the array)