Types:
- free forms -> text files (sequence of characters organised into lines / pages)
- simple record structure -> lines, fixed length, variable length
- complex structures -> formatted document, relocatable load file

OS must support at least one of structures to load & run programs.

Internal file structures:
- all disk I/O is done in units of one block (physical record) and all blocks are same size
- logical records may vary in size
	- solution - pack some logical records into physical blocks -> can cause [[Fragmentation||internal fragmentation]]