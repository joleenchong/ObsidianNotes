Definition:
- allows file I/O to be treated as routine memory access by mapping disk block to page in memory
- a file is initially read using [[Demand paging]]
	- a page sized portion of file is read from file system to physical page
	- subsequent read / write to / from file is treated as ordinary memory accesses

Benefits:
- allows several processes to map same file allowing pages in memory to be shared
- writing to memory mapped file does not require writing to physical file on disk immediately
