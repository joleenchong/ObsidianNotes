- single-processor system : has only one CPU to do general purpose instructions but also has special purpose processors (e.g. for graphic controllers, keyboard) which don't run user processes
- multiprocessor system: has two or more processors working together. also called parallel / multicore system
	- Advantages:
		- *Increased throughput* - more work gets done in less time
		- *Economy of scale* - shared I/O devices, memory storage, and power supplies
		- *Increased reliability* - if one processor stops working the entire system can still keep going
			- Graceful degradation - system can do operations according to level of operations of working parts of system
			- Fault-tolerant - can continue functioning even if there's component failures
	- Two types:
		- Asymmetric multiprocessing
			- master processor schedules and allocates work to slave processors
			- slave processor waits for master's instructions or have predefined task
			- common in extremely large systems
		- Symmetric multiprocessing
			- each processor runs identical copy of OS with their own registers and cache
				- shares the same memory
			- many processes can be run at once without much effect on performance
			![[Pasted image 20230330091726.png]]
	- Multicore system - multiprocessor system but processors are on single chip
		- on-chip communication faster than inter-chip communication -> more efficient
		- less power / energy
		- ![[Pasted image 20230330091848.png]]
	- Clustered system - multiple CPUs but individual systems
		- share storage and communicate via LAN
		- high-availability service - very reliable?