How it works:
- each file occupies a set of contiguous blocks on disk
- supports [[sequential access]] & [[direct access]]

Directory entry for file with this method contains:
- only starting location (block #)
- length (no. of blocks)

[[Memory address binding||Mapping]] from logical address (*LA*) to physical:

$$Q = LA \div 512, R = LA \mod 512$$

Q = block number
R, = offset address
Example: LA = 1000 is in block 1, offset  = 488

Advantage:
- very fast -> no. of seeks is minimal due to contiguous allocation

Disadvantage:
- Inefficient memory usage -  leads to [[Fragmentation||internal and external fragmentation]]
- hard to increase file size -> depends on available [[Contiguous memory allocation||contiguous memory]] at particular instance
- dynamic storage allocation problem - finding the best space for a new file

![[Pasted image 20230615170542.png]]

Modified contiguous allocation scheme - extent-based systems:
- extents - contiguous blocks of disks
	- allocated for file allocation -> a file consists of 1 or more extents