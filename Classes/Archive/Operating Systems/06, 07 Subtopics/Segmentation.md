- An memory management scheme that supports user view of memory.
- memory divided into variable size parts -> known as segments -> can be allocated to a process
- each segment has name and length -> addresses specify both segment name and an offset

A segment is a logical unit such as:
- main program
- procedure / function 
- local variables, global variables
- common block
- stack
- symbol table, arrays
![[Pasted image 20230523120909.png]]

Segmentation architecture:
- two tuple <segment-number, offset>
- segment table -> maps 2d user defined addresses into 1d physical addresses
- each table entry has:
	- base - contains starting physical address where segments reside in memory
	- limit - specifies length of segment
- Segment table base register (STBR) points to segment tables location in memory
- Segment table length register (STLR) indicates number of segments used by program

![[Pasted image 20230523121000.png]]

Protection
- with each entry in segment table associate:
	- validation bit = 0 (illegal)
	- read / write / execute privileges