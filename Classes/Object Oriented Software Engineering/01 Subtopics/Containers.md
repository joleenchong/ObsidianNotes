The simplest container is an array.

 Container types:
- list - ordered, lineared sequences of values / objects
	- In Java, they are ArrayList and LinkedList
	- Python - array-based list and tuple
	- C++ - std::vector (array-based), std::list (linked-list)
- set - non-repeating collections of unique values / objects
	- binary-tree set - sorted order
	- hashtable set - unordered but faster
	- in java, objects inside sets must:
		- be immutable
		- define equals()
		- define hashCode() for hash sets
		- implement Comparable for tree sets
- map - collection of objects accessibly via a key
	- key-value pairs
	- hash and tree maps
	- keys must be immutable, define equals(), etc.