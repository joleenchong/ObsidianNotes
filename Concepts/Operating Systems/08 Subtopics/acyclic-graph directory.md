A directory that allows directories to have shared subdirectories and files.
- same file / subdirectory may be in two different directories
- acyclic graph - graph with no cycle

Shared file / directory implementation:
- Unix makes new directory entry called *link* - a pointer to another file / subdirectory
- OS ignores these links when traversing directory trees to preserve acyclic structure of system

Problems:
- files can have several absolute path names (distinct file names may refer to same file)
- deletion - if dict deletes list -> dangling pointer
	- solution - entry-hold-count solution (research this)
