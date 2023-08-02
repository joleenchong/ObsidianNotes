Definition:
- A type of swapping where pages of data are not copied from disk to RAM until needed.
- Process resides in secondary memory (like disk)
- brings in only a page, not the entire process, when needed

Advantages:
- Less I/O needed
- Less memory needed
- Faster response
- More users
- Greater multiprogramming levels

Steps:
1. Page is needed & not available in main memory -> generates interrupt indicating memory access fault
2. OS puts interrupted process in blocking state. OS must bring required page into memory to process execution
3. OS will search for required page in logical address space
4. Required page will be brought from logical address space to physical address space
5. Page table updated
6. Signal sent to CPU to continue program execution and process is placed in ready state

Hardware requirements:
- swap space / backing store -> holds page not present in main memory
- page tables to mark entry valid / invalid:
	- Valid bit = 1 -> legal page in memory
	- Valid bit = 0 -> page on disk (valid) / invalid
- [[Page replacement algorithm]] & [[Frame allocation]] algorithm

When a process needs a page:
- if page in memory -> continue as before
- if not (invalid bit set) -> generate [[Page-fault trap]], OS brings page to memory

Pure demand paging:
- never bring in a page into memory until required
- start execution with no pages in memory
- [[Page fault]] occurs until every page needed is in memory

What happens if there is no free frame?
- Do page replacement - find some page in memory not really in use and swap out
	- need [[Page replacement algorithm]]
	- performance - want an algorithm with minimum number of page faults
- during program execution, same page may be brought into memory several times

Performance:
- can have significant effect on performance of computer system
- memory access time (*ma*) = 10 to 200ns
- probability of page fault (page fault rate): $0 \leq p \leq 1$
	- if p = 0 -> no page faults
	- if p = 1 -> every reference is a fault
- Effective Access Time:
$$ EAT = (1 - p)* ma + p*$$

Stages:
1. trap to OS
2. save user registers and process state
3. determine that interrupt was page fault
4. check that page reference was legal and determine location of page on disk
5. issue a read from disk to free frame:
	1. wait in queue for this device until read request serviced
	2. wait for device seek and / or latency time
	3. begin transfer of page to free frame
6. while waiting, allocate CPU to some other user
7. receive interrupt from disk I/O subsystem (I/O completed)
8. save registers and process state for other user
9. determine that interrupt was from disk
10. correct page table and other tables to show page is now in memory
11. wait for CPU to be allocated to this process again
12. restore user registers, process state, and new page table, then resume interrupted instruction

Page fault service time components:
- service page fault interrupt (1-100us)
- read in page (8ms) : average latency = 3ms, seek time = 5ms, transfer time = 0.05ms
- restart process (1-100us)