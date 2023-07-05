What?
- a system that allocates memory from a fixed size segment consisting of physically contiguous pages
- size of memory is allocated from this segment using power of 2 allocator
- requests rounded up to next power of 2
- Example:
	- a request for 21 KB of memory is allocated with memory of size 32 KB
- Segment is sequentially divided into two *buddies* of same size until it finds a buddy that closely satisfies the request
- Example:
	- a system has a block of size 256 KB and requests 21 KB of memory
	- Block is divided until a buddy C$_L$ = 32 KB -> big enough for the request (21 KB)
![[Pasted image 20230608170643.png]]

Advantages:
- easy to implement
- finding free memory block simple
- merging adjacent memory buddies into 1 big segment is fast
- allocates block of correct size
- easy to merge adjacent holes
- fast to allocate and de-allocate memory

Disadvantage:
- needs all allocation to be powers of 2
- can cause [[Fragmentation||internal fragmentation]]
- memory waste is close to 50% possible