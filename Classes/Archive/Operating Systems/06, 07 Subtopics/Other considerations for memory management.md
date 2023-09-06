
|                                          | Considerations for paging system                                                                         |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Page size selection                      | smaller size -> need larger sized page table                                                             |
|                                          | larger size -> waste more on internal fragmentation                                                      |
| I/O point of view on page size selection | larger size -> minimise I/O time per byte and minimise number of page faults                             |
|                                          | smaller size -> fits in more for locality of reference                                                   |
| Prepaging                                | when reloading suspended process, load all working set of pages to prevent many page faults on restart   |
| TLB reach                                | amount of memory accessible from TLB                                                                     |
|                                          | TLB reach = (TLB size) * (page size)                                                                     |
|                                          | working set of each process is stored in TLB. Otherwise there is a high degree of referencing page table |
| Program structure                        | user has control over performance                                                                        |
|                                          | stack: good locality, always accessed at top                                                             |
|                                          | hash table: dynamic array -> poor locality, scattered references                                         |

How to increase [[Associative registers||TLB]] reach size?
- increase page size - may increase [[Fragmentation |internal fragmentation]] as not all apps require a large page size
- provide multiple page sizes - allows apps that need larger page sizes to use them without an increase in fragmentation

IO interlock and addressing:
- Problem of process requesting IO if IO is done to/from user [[Virtual memory|virtual memory]]:
	- [[Processes|process]] issues IO request -> put in queue to access device
	- buffer space (for IO) is swapped out by [[Page replacement algorithm]]
	- when IO runs, it overwrites buffer space (now used by another process)
- Solution:
	- Buffer in OS space -> time consuming
	- Lock buffer pages in memory -> lock bit associated with every frame, if lock bit set than frame cannot be selected for replacement