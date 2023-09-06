A memory management mechanism for efficient memory allocation of objects.

Structure:
- Slab - 1 or more physically contiguous pages
- Cache - consists of 1 or more slabs
	- constructor is used to allocate slab and init memory area to hold objects
	- 1 cache for each unique kernel data structure -> each cache filled with objects
		- 1 cache for PCB, 1 cache for semaphores, etc.

How does it work?
- created cache is filled with objects marked *free*
- when structures stored, objects are marked *used*
- if slab is full of used objects, next object allocated from empty slab
- if no empty slabs, new slab allocated

3 possible states for slabs in Linux:
- full - all objects in slab are used
- empty - all objects in slab are free
- partial - some objects in slab are used, some are empty

Which slab to use first?
![[Slab allocation 2023-06-08 17.31.39.excalidraw]]

Advantages:
- no [[Fragmentation||internal fragmentation]] - memory request is allocated with memory exactly the size of object
- fast memory allocation / deallocation
	- objects are made in advance -> can be allocated immediately
	- memory is released by setting to "free" -> can be used immediately by any later request
