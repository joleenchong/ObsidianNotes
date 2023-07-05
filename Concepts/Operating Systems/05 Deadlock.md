Chapter 7 of OS textbook

-----

Definition: when 2 or more processes are waiting for each other to release [[Resources ||resources]] in a circular chain

4 conditions for deadlock:
1. [[Mutual Exclusion]]
2. [[Hold & Wait]]
3. [[No pre-emption]]
4. [[Circular Wait]]

Graphs:
- [[System-allocation graph]]
- [[Wait-for graph]]

3 methods to handle:
- [[Prevention of deadlock]]
- [[Detection of deadlock]]
- [[Recovery of deadlock]]
- Optimal approach for each class of resource:
	- sort into hierarchically ordered classes
	- use must appropriate handling technique within each class