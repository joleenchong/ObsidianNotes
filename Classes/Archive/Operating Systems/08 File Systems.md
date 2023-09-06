Chapters 11 & 12 of OS textbook

Notes:
1 byte = 8 / 2<sup>3</sup> bits
1 KB = 2<sup>10</sup> = 1024 bytes
1 MB = 2<sup>20</sup> bytes
1 GB = 2<sup>30</sup> bytes
1 TB = 2<sup>40</sup> bytes

----
OS responsibilities for file management: 
- creation & deletion of files
- creation & deletion of directories
- support of primitives for handling files & directories
- mapping files onto secondary storage
- backup of files onto stable (non-volatile) media

File concept and access methods:
- a *file* is a sequence of bits, byte lines, or records
- types:
	- source - sequence of routines, functions, declarations & executable statements
	- object - sequence of bytes organised into blocks understandable by system linker
	- executable - series of code sections that loader can bring into memory & execute
- OS uses an [[open file table]] that contains info abt all open files
- a file system consists of:
	- collection of files - each stores related data
	- directory structure - organises and provides info abt all files in system
	- partitions - used to separate physically or logically large collections of directories
- most systems need a file to be opened explicitly:
	- open (F$_i$) -> search directory on disk for entry F$_i$, copy directory entry (typically a pointer) into open-file table
	- close (F$_i$) -> remove directory entry for F$_i$ from open file table
- an open file needs the following info:
	- file pointer - unique for each process operating on the file
	- file open count - tracks number of processes calling open / close to certain file (if count = 0, entry is removed from open file table)
	- disk location of file - keep in memory, to avoid reading it from disk each operation
- [[File structures]]

| File type      | Usual extension             | Function                                                  |
| -------------- | --------------------------- | --------------------------------------------------------- |
| Executable     | exe, com, bin, no extension | ready-to-run machine language program                     |
| Object         | obj, o                      | compiled, machine language, not lined                     |
| Source code    | c, cc, java, py, asm        | source code in various languages                          |
| Batch          | bat, sh                     | commands to command interpreter                           |
| Markup         | txt, html, xml              | textual data, documents                                   |
| Word processor | docx, rtf, etc.             | various word-processor formats                            |
| library        | lib, a, dll                 | libraries of routines                                     |
| Print or view  | gif, pdf, jpg               | ASCII or binary file for printing / viewing               |
| Archive        | zip, tar                    | related files grouped into one file, sometimes compressed |
| Multimedia     | mpeg, mp3                   | binary file containing audio or A/V info                  |
- access methods:
	- [[sequential access]]
	- [[direct access]]

Directory:
- [[Directory structures]]

File protection:
- file access types:
	- read - view contents
	- write - change contents
	- execute - load file onto CPU and follow instructions
	- append - add to end of existing file
	- delete - remove file from system
	- list - view name and other attributes of file on system
- 3 classes of users:
	- owner
	- group
	- public
- Access Control List - a list of permissions for access that each user has to a system object (e.g. file directory, individual file)

Directory implementation:
- [[Linear list (directory)]]
- [[Hash table (directory)]]

File allocation methods:
- [[contiguous file allocation]]
- [[linked file allocation]]
- [[indexed file allocation]]
note: must know mapping

Free space management:
- [[bit vector (free space management)]]
- [[linked list (free space management)]]
- [[grouping (free space management)]]
- [[counting (free space management)]]
