A collection of pages a process is actively using & must prevent from [[Thrashing]]. 

It prevents thrashing by storing all active page frames in a working set for each process. If a process requests additional page frames which cannot be fulfilled, the OS suspends another process in order to free frames for the process requesting additional frames, thus preventing successive page fault activity.

$\bigtriangleup \equiv$ working set window $\equiv$ fixed number of page references
Locality - the set of pages actively used together

Example: 10,000 instructions
- WS$_i$ (working set of process P$_i$) = total number of pages referenced in the most recent $\bigtriangleup$ (varies in time) -> accuracy depends on $\bigtriangleup$
	- if $\bigtriangleup$ is too small -> locality is not completely represented
	- if $\bigtriangleup$ is too large -> will encompass several localities
	- if $\bigtriangleup = \infty$ -> will encompass entire program
- D = sum of WS$_i \equiv$ total demand frames
- when D > m (i.e. total number of available frames) -> thrashing

![[Pasted image 20230605215657.png]]

Use:
- OS monitors working set of each process and allocates process enough frames
- if there are enough extra frames (in free frame pool) -> increase degree of multiprogramming
- if D > M, suspend one of the processes and return frames

How do you keep track of the working set?
- approximate working set model with fixed-interval timer and reference bit
- Example $\bigtriangleup$ = 10,000
	- timer interrupts after every 5,000 time units
	- keep in memory 2 bits for each page
	- whenever a timer interrupts, OS copies bit 1 to bit 2, reference bit to bit 1 and clear values of all reference bits of each other page to 0
	- if a page fault occurs, examine current reference bit and 2 in memory bits
	- if one of the bits = 1 -> page in working set
	- if reference in memory bit = 1, this page was used in last 15,000 references