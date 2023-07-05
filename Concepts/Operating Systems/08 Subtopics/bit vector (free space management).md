Definition:
- a collection of bits where each bit corresponds to a disk block
- bits can take 2 values - 0 & 1
	- 0 - allocated block
	- 1 - free block
- can be represented by a bitmap of 16 bits (e.g. 0000111000000110)

Advantage:
- simple to understand
- finding first free block is efficient

Disadvantage:
- bitmap needs extra space