- Ensures there can never be [[Circular Wait]]

Resource allocation state defined by:
- the number of available & allocated resources
- the maximum demands of the processes

Safe state:
- when system can allocate all resources requested by all processes without entering deadlock
- when process requests available resource, system checks if its allocation keeps system in safe state -> process may have to wait

Bankers' Algorithm:
- tests for safety by simulating allocation for predetermined maximum possible amounts of all resources
- How it works:
	- each process must claim maximum number of instances of each resource type that it may need presumptively
	- when requesting, process may have to wait until other process releases enough resources
	- when process gets all its resources, must return them in finite amount of time
- Algorithm:
	- let n = number of processes and m = number of resource types
	- Data structures:
		- Available - Vector of length m
			- available\[j] = k; means k instances of resource type Rj are available
		- Max - n x m matrix
			- Max \[i, j] = k; means process Pi may request at most k instances of resource type Rj
		- Allocation - n x m matrix
			- Allocation \[i,j] = k; means process Pi is currently allocated k instances of resource type Rj
		- Need - n x m matrix
			- Need \[i,j] = k; means process Pi may need k more instances of resource type Rj to complete task
			- Need\[i,j] = max\[i,j] - allocation\[i,j]

go over slide 27+