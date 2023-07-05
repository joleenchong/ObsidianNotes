Definition:
- the condition of a disk in which files are divided into pieces scattered around disk
- occurs naturally when using a disk frequently to create, delete, and modify files

Types:
- external fragmentation - the various spaced holes generated in either memory or disk space. Total non-contiguous memory space exists to satisfy request
- internal fragmentation - the wasted space within each allocated block due to rounding up from actual requested allocation to allocation granularity
	- allocation granularity - allocated memory slightly larger than requested memory but not being used

How to reduce external fragmentation:
- compaction
	- shuffle memory contents to place all free memory together in one large block
	- only possible if relocation is dynamic and done at execution time
	- must determine cost -> the less size of memory contents that must be moved, the better
	- difficult to find optimal strategy
- [[Paging]]
	- may cause internal fragmentation instead
	- avoids problem of varying sized memory chunks