Chapter 10 & 13 of OS textbook

---
Disk structure:
![[Pasted image 20230620192609.png]]

OS responsibilities:
- free-space allocation
- storage allocation
- disk scheduling - must have fast [[access time]] and [[disk bandwidth]]

A process request for disk I/O requires the following info:
- if request is input or output
- disk address for transfer
- memory address for transfer
- number of sectors to be transferred

The OS uses a [[disk scheduling algorithm]] for [[Multiprogramming||multiprogramming]] disk requests.

Swap-space management:
[[Swap-space management]]

Disk reliability:
[[RAID structure]]

IO devices characteristics:

| Aspect             | Variation                                                       | Example                          |
| ------------------ | --------------------------------------------------------------- | -------------------------------- |
| data-transfer mode | character, block                                                | terminal, disk                   |
| access method      | sequential, random                                              | modem, CD-ROM                    |
| transfer schedule  | synchronous, asynchronous                                       | tape, keyboard                   |
| sharing            | dedicated, sharable                                             | tape, keyboard                   |
| device speed       | latency, [[seek time]], transfer rate, delay between operations |                                  |
| IO direction       | read only, write only, read-write                               | CD-ROM, graphic controller, disk |

A [[System call]] for IO can be blocking or non-blocking.
- blocking - suspends process until IO completes
	- easy to use and understand but insufficient for some needs (e.g. keyboard and mouse)
- non-blocking - IO call returns as much data as available without waiting for IO completion
	- implemented using [[multithreading]]
	- returns quickly with count of bytes read or written
- asynchronous IO - process runs while IO executes
	- an alternative to non-blocking IO
	- IO subsystem signals process when IO completes

[[Kernel]] services for IO:
- IO scheduling:
	- improves overall system performance 
	- shares device access fairly among processes
	- reduces average waiting time for IO to complete
- [[Buffering]]
- [[Caching]]
- [[Spooling]]
- device reservation
	- provides exclusive access to device
	- uses [[System call]]s for device allocation and de-allocation
	- OS must handle possible [[05 Deadlock||deadlock]]
- error handling
	- OS can recover from the following failures: disk read, device unavailable, transient failures
	- most OS returns an error number / code when IO request fails

Improving IO performance:
- reduce total number of [[Context switch]]es
- reduce number of times data must be copied in memory while passing between device and app
- reduce frequency of [[Interrupts]] by using large transfers, smart controllers, polling (if busy waiting can be minimised) 
- increase concurrency by DMA controllers or channels to offload simple data copying from CPU