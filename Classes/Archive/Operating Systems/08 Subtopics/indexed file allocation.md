How it works:
- an *index block* contains pointer to all blocks occupied by a file
- each file has own index block
- i<sup>th</sup> entry in index block points to i<sup>th</sup> block of file

Directory entry contains:
- index block address

Mapping:
- in file with maximum size of 64K bytes and block size of 512 bytes:
	- assume each pointer is 4 bytes -> each index block has 128 pointers
	- Q = displacement into index table, R = displacement into block
- in file with unbounded length and block size of 512 bytes:
	- linked scheme
![[Pasted image 20230615210810.png]]
![[Pasted image 20230615210826.png]]
note: this is unfortunately important - appears on exam

Advantages:
- supports [[direct access]] to blocks occupied by file
- faster access to blocks
- no [[Fragmentation||external fragmentation]]

Disadvantages:
- greater pointer overhead than [[linked file allocation]]
	- small index blocks cannot support large files
	- big index blocks can waste space
	- for large files, can use a linked scheme, multilevel index, or combined scheme

![[Pasted image 20230615175749.png]]

Two-level index:
![[Pasted image 20230615210854.png]]
