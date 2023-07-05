Definition:
- file system is broken into partitions / volumes
- 1 disk can contain many partitions
- 1 partition can have many disks
- each partition has device directory / volume table of contents

Advantages of organising:
- efficiency -> locate files quickly
- naming -> convenient to users
	- two users can have same name for different files
	- same file can have different names
- grouping -> logical grouping of files by properties

How is a directory viewed?
- symbol table - translates file names into their directory entries
- both directory structure & files reside on disk

Operations performed:
- search / create / delete / rename file
- list a directory and traverse file system

Types of directories:
- [[single level directory]]
- [[two-level directory]]
- [[tree structure directory]]
- [[acyclic-graph directory]]
