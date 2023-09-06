An abstract model that views protection as a matrix. The *mechanism* for protection.
Row = domain capability list
Column = object access list
Entry = a set of [[access rights]]
- access (*i, j*) - the set of operations in domain *i* can invoke on object *j*

Example:

| domain / object | F1   | F2   | F3      | printer |
| --------------- | ---- | ---- | ------- | ------- |
| D1              | read |      | read    |         |
| D2              |      |      |         | print   |
| D3              |      | read | execute |         |
| D4 | read, write |      | read, write |         |

Rights:
- Copy (denoted by '\*') - access rights are copied within same column
	- copy transfer - a right is copied from access (i, j) to access (k, j); access (i,  j) is removed
	- limited copy - when R* copied from access (i, j) to access (k, j), only right R is made
- The owner of O$_i$ controls access rights in the column / O$_i$
- copy and owner rights do not guarantee info in object to go outside its environment - [[confinement problem]]
- control right - only to domain objects / row
	- if access (i, j) includes control right, then process executing in D$_i$ can modify any access right from D$_j$

Implementation:
- global table - a set of ordered triples <Domain, Object, Rights>
	- drawbacks:
		- large table - can't be in memory thus needing disk IO ([[Virtual memory]] techniques)
		- doesn't take advantage of grouping of objects / domains
- access list for objects - one list per object / column
	- each object O$_j$ has list of <Domain, Right-set>
	- list represents all domains with access rights for O$_j$
	- fast as many operations will not need to search list
- capability list for domains - a list of objects with allowed operations for them
	- a protected object - inaccessible to user to prevent modification
	- capabilities are distinguished from other data by:
		- tag - determines type (capability or accessible data)
		- split address space into 2 parts:
			- part A - address space
			- part B - capability list
			- can use [[Segmentation||segmented]] memory space
- lock-key mechanism - compromise between access list and capability list
	- process in domain D$_i$ can access O$_j$ if key in D$_i$ matches one of locks in O$_j$
Comparison:

| Properties | Access list                                  | Capability list                                        | Lock-key                                 |
| ---------- | -------------------------------------------- | ------------------------------------------------------ | ---------------------------------------- |
| Revocation | Easy - just search list                      | inefficient - capabilities are distributed thru system | revoked by changing some locks of object |
| Access     | determining rights for each domain difficult; access can be time consuming for long list | must present capability to access object               |                                          |

