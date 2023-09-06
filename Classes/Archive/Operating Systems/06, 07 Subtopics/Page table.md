A table containing the base address of each page in physical memory.

Implementation of page table:
- each page table is kept in main memory
	- page table base register (PTBR) points to page table
	- page table length register (PTLR) points to size of page table
- every data / instruction access requires 2 memory accesses:
	- Page table access
	- Data / instruction access
- two memory access problems can be solved with special fast-lookup hardware cache AKA [[Associative registers ||associative registers]] (AKA translation look-aside buffers)

Techniques for structuring page table types:
- Hierarchical paging
- hashed page tables
- inverted page tables

Hierarchical paging:
- page table can become too big to fit in contiguous space -> have hierarchy with several levels
- break logical address space into multiple page tables
- simple technique-> two-level page table
	- page the page table
- Two-level paging example:
	- logical address on 32 bit machine with 4k size
		- page number is 20 bits
		- page offset 12 bits
	- page table is paged -> page number is further divided:
		- 10 bit page number
		- 10 bit page offset
	- p1 -> outer page table index, p2 -> displacement within page of inner page table
![[Pasted image 20230523113950.png]]
![[Pasted image 20230523114004.png]]
- Performance:
	- each level stored in separate table in memory
		- converting logical address to physical may take 4 memory accesses (4 level paging system)
		- even though time needed for one memory access is quintupled, caching permits performance to remain reasonable

Hashed Page table:
- virtual page number is hashed into page table
- page table contains chain of elements hashing to same location
- each element has
	- virtual page number
	- value of page frame
	- pointer to next element
- search through chain for virtual page number. if match is found, corresponding physical frame is extracted
- used when address spaces > 32 bits
![[Pasted image 20230523120731.png]]

Why use inverted page table?
- uses one table that has one entry for each real page of memory
- decreases memory needed to store each page table, but increases time needed to search table when page reference occurs ( can use hash table to limit search to one - or at most a few page table entry)

Inverted page:
- entry consists of virtual address of page stored in real memory location, with info about process (e.g. PID) that owns that page

![[Pasted image 20230523120815.png]]

Benefits:
- can share common code (re-entrant code AKA pure code)
	- re-entrant code is non-self-modifying code -> never changes during execution (several processes can execute @ same time)
	- Shared code: one copy of read-only (re-entrant) code shared among processes
	- Private code & data: each process keeps separate copy of code & data
		- pages for private code & data can appear anywhere in logical address space