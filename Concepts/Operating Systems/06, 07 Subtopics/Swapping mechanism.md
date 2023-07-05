A mechanism where process can be temporarily swapped out of main memory to [[Backing store||backing store]] and memory is availed to other processes. 

![[Pasted image 20230522121315.png]]

Constraints:
- [[Context switch]] time can be very high
	- if next process put in CPU is not in memory, need o swap out a process and swap in target process
- can't swap out in middle of I/O as I/O would occur to wrong process
	- Solution:
		- latch job in memory while it is involved in I/O
		- do I/O only into OS buffers