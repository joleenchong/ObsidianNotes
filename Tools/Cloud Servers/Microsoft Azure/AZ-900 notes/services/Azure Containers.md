A virtualisation environment. Compared to [[Azure Virtual Machines]], the OS is not managed for the container, making them a more agile method. Containers are lightweight and dynamically created, scaled, and stopped. Containers can be easily restarted in case of crash or hardware interruption. They are a [[Platform as a Service (PaaS)]] offering.

Used for microservice architecture - one app broken into smaller logical sections

- simplest container is an array
- various container types:
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