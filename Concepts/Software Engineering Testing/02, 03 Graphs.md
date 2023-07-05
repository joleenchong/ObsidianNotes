**Outcomes:**
- create control flow graphs from source code
- identify test requirements for
	- Node & Edge Coverage
	- Prime Path Coverage
	- All-DU-Paths, All-Uses, All-defs coverage
- identify test paths for above
---------------
Terminology
- *Graph* - made up of non-empty sets of nodes, initial nodes, final nodes, edges
- *Path* - a sequence of nodes
- *Length* - number of edges in a path
- *Subpath* - a path that is part of a larger path
- *Test path* - a path that starts at initial node and ends at final node
- *Visit* - If node / edge exists on test path, test visits that node / edge
- *Tour* - a subpath part of a test path is toured by that test path

Set notation:
- lowercase - element of set
- uppercase - entire set
- Path (**t**) - a test path executed by test **t**
- Path (**T**) - a set of test paths executed by test set **T**

Testing:
- Test criterion - the rules by which tests are designed
- Test requirements (TR) - a set of paths that test paths should cover based on criterion

Coverage:
- node coverage - ensure TR contains all reachable nodes for a given graph
- edge coverage - TR contains each reachable path of length up to 1, inclusive, in given graph
- edge-pair coverage - TR contains reachable path of length up to 2, inclusive, in G
- complete path coverage - TR contains all paths in G
- specified path coverage - TR contains a set S of test paths where S is supplied as parameter
- prime path coverage - TR contains each prime path in G
	- covers node, edge, and edge-pair coverage
- simple round trip coverage - TR contains at least one round-trip path for each reachable node in G that begins and ends a round-trip path
- complete round trip coverage - TR contains all round-trip paths for each reachable node in G
![[Pasted image 20230418122327.png]]

Paths:
- simple path - a path with no duplicate nodes except possibly for the first and last nodes
- prime path - a simple path that is not a subpath of any other simple path
	- don't need to be test paths as they can start and end anywhere
- round trip - a prime path that starts and ends at the same node

# Data flow coverage criteria
- def - a location where variable is given in value (i.e. stored in memory)
- use - a location where a variable is accessed
- def(n) / def(e) - the set of variables that are defined by node n or edge e
- use(n) / use(e) - the set of variables that are used by node n or edge e
![[Pasted image 20230418114026.png]]

- DU pair - a pair of locations; one def and one use
- Def-clear - a path from one location to another with no other defs between them
- reach - when there is a def-clear path between a def and use
- du-path - a simple subpath that is def-clear with respect to a DU pair
- du-tour - a test path p du-tours subpath d with respect to variable if p tours d and subpath is def-clear
- Notation:
	- du(ni, nj , v) - the set of du-paths from one location to another
	- du(ni, v) - the set of du-paths that start at one location
- Coverages:
	- All-defs coverage - ensure test requirements include all defs
	- All-uses coverage - for each def, ensure there is a path to all uses / variable
	- All-du-paths coverage - for each def, explore every du-path to every use
![[Pasted image 20230418120940.png]]
