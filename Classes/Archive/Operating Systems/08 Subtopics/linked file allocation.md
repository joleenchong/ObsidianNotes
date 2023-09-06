How it works:
- each file is a linked list of disk blocks
- blocks can be scattered anywhere -> solves external fragmentation and size declaration problem in [[contiguous file allocation]]

Directory entry contains:
- pointer to starting and ending file block
	- each block points to next block occupied by file
Mapping from logical address to physical address:
$$Q = LA \div 508, R = LA \mod 508$$

Advantage:
- flexible file sizes
- no [[Fragmentation||external fragmentation]] -> better memory usage

Disadvantage:
- file blocks distributed randomly -> accessing every individual block needs large number of seeks
	- inefficient to use [[direct access]]
- if pointer is lost / damaged, potential reliability issue
- pointers incur extra overhead:
	- solution - allocate clusters of blocks instead of just blocks
	- problem - leads to internal fragmentation

![[Pasted image 20230615173936.png]]