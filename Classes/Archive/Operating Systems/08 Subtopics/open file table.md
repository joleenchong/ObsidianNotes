A table to keep track of details of files opened by corresponding process. Parts of the directory structure are usually cached in memory to speed up directory operations. 

Opening a file returns an index (*file control block*):
- contains info about file

Contains:
- info about currently open files
- file pointer -> records current position in file for next read / write access
- file-open count -> how many times current file has been opened (by different processes at the same time) and not yet closed
- disk location of file
- access rights

Two levels of open-file table:
- pre-process table -> keeps info of all open files for each process
	- example: file pointer for each file for use in read / write calls & pointers to system-wide table)
- system-wide open-file table -> contains info which is process-independent
	- example: file location on disk, access dates, file sizes
