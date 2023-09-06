Issues:
- more than one process in memory
- if too few then page fault becomes more frequent
- How do we know which frames to allocate to which process?

Constraints:
- cannot allocate more than total frames available unless page sharing
- must allocate a minimum number of frames performance-wise

Allocation schemes:
- Fixed allocation:
	- Equal allocation:
		- *m* frames, *n* processes -> *m* / *n* frames per process
		- put remainder in free frame pool
		- Example: 93 frames, 5 processes -> 18/process, and 3 in free frame pool
	- Proportional allocation - allocate according to size of process
		- s$_i$ = virtual memory required for process p$_i$
		- s = sum of s$_i$
		- m = total number of frames
		- a$_i$ = allocation for p$_i$  $$a_i = \frac{s_i}s \times m$$
- Priority allocation
	- use proportional allocation scheme using priority rather than size
	- if process Pi generates [[Page fault]]:
		- select for replacement:
			- one of its frames
			- a frame from a process with lower priority number
Global vs Local [[Page replacement algorithm]]

| Global                                                                                                            | Local                                                                       |
| ----------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Allows a process to select a frame from set of all frames, even if frame currently allocated to some other prcess | Requires that each process select from only its own set of allocated frames |
| Disadvantage: a process can't control its own page-fault rate                                                     | number of frames allocated to a process does not change                     |
| Larger system throughput                                                                                                                  |                                                                             |
