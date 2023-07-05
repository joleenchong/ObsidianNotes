Vertices:
- Two sets:
- [[Processes]] and all [[Resources ||resource types]]

Edges:
- directed
- Assignment edge: Resource -> process
- Request edge: process -> resource

Model symbols:
![[Pasted image 20230515221500.png]]

Cycles:
- No cycles - no deadlock
- Has one or more cycles:
	- 1 instance - cycle means deadlock
	- Several instances - cycle is necessary but not sufficient condition for deadlock

Example:
- 3 resources: R, S, T
- 3 processes: A, B, C

| A         | B         | C         |
| --------- | --------- | --------- |
| Request R | Request S | Request T |
| Request S | Request T | Request R |
| Release R | Release S | Release T |
| Release S          | Release T          | Release R          |

Request / release order:
1. A requests R
2. B requests S
3. C requests T
4. A requests S
5. B requests T
6. C requests R

![[Pasted image 20230531213242.png]]
