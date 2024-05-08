From [[01, 02 Introduction]]:
- define a cost (money, time, etc.)
- sort items by best impact on cost
- choose the best result at the current stage until problem solved
- result may not be optimal

Activity Selection problem (p.415 of textbook):
- basically select activities with the shortest finish time

| activity | start | finish |
| -------- | ----- | ------ |
| 1        | 1     | 4      |
| 2        | 3     | 5      |
| 3        | 3     | 8      |
| 4        | 5     | 9      |
| 5        | 8     | 12     |
| 6        | 0     | 14     |
| 7        | 12    | 14     |
| 8        | 0     | 6      |
| 9        | 5     | 7      |
| 10       | 6     | 10     |
| 11       | 8     | 11     |
- Activity 1 will be selected first
	- this renders 2 and 3 incompatible as they start before 1 finishes
- Activity 4 is selected - 5, 6 incompatible 
- Activity 7 is selected - 8, 9, 10, 11 incompatible
Final set will be A = {1, 4, 7}

0/1 or Fractional Knapsack (p.425):
- Select a set of items with max total profit but total weight cannot exceed certain weight limit
- Solution choice:
	- optimise weight
	- optimise profit
	- optimise profit-per-weight
![[Pasted image 20240501222857.png]]

Minimum-Cost Spanning Tree (p.625):
```pseudocode
A = []
while there are more candidate edges:
	get edge with least weight
	if selected edge doesn't make a cycle, add to A
```
- Algorithms:
	- Kruskal's
	- Prim's

Single-source Shortest Path (p.644):
