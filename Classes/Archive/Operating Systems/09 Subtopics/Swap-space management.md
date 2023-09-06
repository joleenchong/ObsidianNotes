Goal: to provide best [[throughput]] for [[Virtual memory]] system

Swap-space - virtual memory uses disk-space as an extension of main memory

Usage:
- can hold entire process image (e.g, code & data segments)
- store pages pushed out of main memory

The size of swap-space varies:
- safer to overestimate size -> if underestimated, may result in aborted processes or system crash 

Two locations swap-space can reside:
- a large file within file system - easy to implement but inefficient
- a separate disk partition
	- use algorithms to optimise speed (not storage efficiency)
	- may cause [[Fragmentation||internal fragmentation]]

The [[Kernel]] uses a swap-map to track swap-space use.