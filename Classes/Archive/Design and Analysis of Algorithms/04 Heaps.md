Treat them like binary trees.

i is the parent index.
LEFT_CHILD index = 2 x i
RIGHT_CHILD index = 2 x i + 1

`HEAP_EXTRACT = O(log(n))` 
You're taking out the max value (by replacing root with the last element, then reducing array size) and calling heapify at 1 to fix the heap. Limited by heapify, which is `O(log(n))` 

`Build_heap = O(n)` 
You're calling heapify length/2 times from indexes length/2 to 1 (all the parents. You can ignore calling heapify on leaf nodes because they inherently hold the heap property, given they have no children to compare to). There's a proof in the lecture slides but basically since the height of the node also reflects how many potential swaps there are (it isn't just running an `O(log(n))` operation length/2 times), it converges to `O(n)` 

`Heap_insert = O(log(n))` 
You're increasing the heap size by 1, adding an element to the end of the heap, then using a loop to swap it with its parent if it's larger/smaller (depending on max or min heap). Due to the nature of binary trees this is log2 operations max

`Heap_sort = O(nlog(n))` 
You call build_heap at the start (which is `O(n)`) then effectively keep calling heap_extract (which is `O(log(n))`) n-1 times 

`Heapify = O(log(n))` 
Restores a single violation of the heap property at an index **i**. This assumes **i**'s subtrees are already heaped, so you just worry about trickling down **i** through its children 

`Heap_delete = O(log(n))` 
This isn't covered in the lectures, I don't think, but it should work by replacing the node you want to delete with the last node in the tree, reducing the heap size by 1, then calling heapify at the swapped node's index

Leftist trees:
- the count of nodes in the left tree must be greater or equal to count in right tree
- count = 1 + sum of child counts