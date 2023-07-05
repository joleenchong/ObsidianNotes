Schemes:
- [[Contiguous memory allocation]]
- Multiple partition allocation:
	- memory is divided into fixed-size partitions that contain exactly one process
	- can also be divided into variable partitions:
		- OS maintains info about allocated and free partitions (AKA block of available memory AKA hole)
		- when process arrives, it is allocated memory from large enough hole to accommodate it

![[Pasted image 20230522122814.png]]
- three available holes of size 100K, 300K, and 260K
	- process of size 400k cannot run although system has total of 660k available memory
	- this is [[Fragmentation ||external fragmentation]]

How to satisfy a request of size n from a list of free holes? (Dynamic storage allocation problem)
- First-fit - allocate first hole that is big enough
- Best-fit - allocate smallest hole that is big enough.
	- must search entire list unless ordered by size
	- produces smallest leftover
- Worst-fit - allocate largest hole
	- must search entire list
	- produces largest leftover hole
- First and best fit are better than worst-fit -> by speed and storage utilisation
