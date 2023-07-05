Definition:
- a modified [[linked list (free space management)||linked list]] approach
- stores address of n free blocks in first free block
- first $n - 1$ of these blocks are free
- last block contains addresses of another n free blocks

Advantage:
- can easily find addresses of group of free disk blocks