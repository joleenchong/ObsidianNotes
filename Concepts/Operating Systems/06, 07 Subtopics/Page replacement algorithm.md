Resources:
https://nicomedes.assistedcoding.eu/#/app/os/page_replacement

-------
Definition:
- decides which memory pages to swap out or write to disk when page of memory needs to be allocated
- needed to decide which page needs to be replaced when new page comes in
- target for all algorithms is to reduce number of [[Page fault]]s
- used together with [[Page buffering algorithm]]

How does it work?
1. Find a location of desired page on disk
2. Find free frame -> if free, use frame
3. Otherwise, use page replacement algorithm to select victim frame
4. Write victim page on disk -> update page & frame tables
5. Read desired page into new frame -> update page & frame table
6. Restart user process

FIFO page replacement algorithm:
- simplest algorithm
- FIFO [[03 Stacks and Queues ||queue]] to replace page at head of queue & insert new page at tail
- suffers from Belady's Anomaly-> more frames result in more page faults

Optimal page replacement algorithm:
- replaces page that will not be used for longest period
- for fixed number of frames, it has lowest page fault rate of all algorithms
- never suffers from Belady's Anomaly
- Problem: difficult to implement -> needs future knowledge of reference string

Least Recently Used Algorithm:
- replaces page that *has* not been used for longest period
	- associates each page with its last use
	- good performance and often used
	- doesn't sufffer from Belady's Anomaly

Second Chance Algorithm:
- candidate pages for removal are considered in round robin matter
- a page accessed between consecutive considerations will not be replaced
- uses a reference bit
	- if 1, decrement and leave in memory
	- if 0, replace next page

Enhanced Second Chance Algorithm:
- include modify bit to reduce number of I/O needed
- use modify and reference bits as pair 
	- (0,0) - neither used or modified
	- (0,1) - not used recently but modified
	- (1,0) - used recently but not modified
	- (1,1) - used recently and modified
- replace (0,0) first
- Use FIFO if all pages have same pair of values

Counting Algorithm:
- keep counter of number of references made to each page
- Expensive implementation:
	- Least Frequently Used - replaces page with smallest count
	- Most Frequently Used - page with smallest count was likely just brought in and has yet to be used
