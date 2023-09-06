Definition:
- free disk blocks linked together
- a free block contains a pointer to next free block
- block number of very first block is stored at separate location on disk and cached in memory
- last block -> null pointer

Advantage:
- easy to insert new file -> OS can allocate first block in free space list and move head pointer to next free block in list

Disadvantage:
- inefficient
- can't get contiguous space easily