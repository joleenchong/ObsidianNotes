Used for [[Detection of deadlock]].

Vertices -> [[Processes]]

Edge -> represents one process waiting for another to release resource
- Multiple edges - waiting for multiple resources
	- can be conjunctive or disjunctive set of resources
		- this means they are either connected or not

Example:
Pi->Pj
i.e. Pi waits for Pj to release