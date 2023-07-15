- if you can't avoid it you have to find it
- leads to [[Recovery of deadlock]]
- examines state to determine occurrence of deadlock

Methods:
- maintain [[Wait-for graph]]
- periodically looks for cycle in graph using algorithm
	- algo requires O(N^2) operations where N = number of vertices in graph

When to use algo?
- depends on frequency of deadlock occurrence
- number of processes will be affected by deadlock occurrence

Risks of using algo:
- expensive when called every time process makes requests -> but useful for finding what processes caused deadlock
- invoked at less frequent intervals

