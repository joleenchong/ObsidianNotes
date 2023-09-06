Definition:
- a memory management capability of an OS that uses hardware & software to allow computer to compensate for physical memory shortages by temporarily transferring data from RAM to disk storage
- separation of user's logical memory from physical memory
- allows execution of program that is only partially in memory
- much larger logical address space than physical address space

Advantages:
- a program is not constrained by amount of available physical memory
- with the available physical memory more programs can be run at same time
- less I/O needed to load / swap user program into memory -> program runs faster

Implementation:
- [[Demand paging]]
- [[Demand segmentation]] - this is not elaborated on

Benefits during process creation:
- [[Copy-on-Write]]
- [[Memory-mapped files]]