Input domain:
- contains all possible inputs for a program
- infinite -> must choose finite sets of values from domain
- Input parameters define input domain's scope:
	- Parameters to a method
	- Data read from a file
	- Global variables
	- User level inputs
- Each input parameter for each domain is partitioned into regions
- one value is chosen from each region

Partitioning domains:
- Partition scheme *q* of domain *D* defines a set of blocks *Bq* = b1, b2, ... bq
- Must satisfy 2 properties:
	- blocks must be pairwise disjoint (no overlap)
		- Example - when partition characteristic is order of file F, and if file is of length 1, then file will overlap into all sorting orders and not satisfy disjointness
		- Solution - each characteristic should address only 1 property
	- together blocks cover the domain *D* (complete)

When using:
- choose value from each partition
- Application:
	- find characteristics in inputs - parameters, semantic descriptions, etc.
	- partition each characteristics
	- choose tests by combining values from characteristics
- Example characteristics:
	- Input X is null
	- Order of input file F (sorted, reverse sorted, arbitrary)
	- Input device (DVD, CD, computer, etc.)

Modelling input domain:
1. [[Identify testable functions & parameters]]
	- individual methods have 1 testable function
	- in a class, each method has same characteristics
2. Find all parameters
	- methods - parameters and state / non-local variables used
	- components - parameters to methods and state variables
	- system - all inputs, including files and databases
3. Model input domain
	- domain is scoped by parameters
4. [[Apply test criterion to choose combinations of values]]
	- a test input has a value for each parameter
	- one block for each characteristic
	- coverage criteria allows subsets to be chosen
5. Refine combinations of blocks into test inputs
	- choose appropriate values from each block

Two approaches to modelling:
- Interface-based approach
	- consider each parameter in isolation
	- ignores relationships among parameters
	- Example - 3 int parameters (TriTyp)
		- Input domain model (IDM) for each parameter is identical
		- Reasonable characteristic - relation of side with zero
- Functionality-based approach
	- identify characteristics that correspond to intended functionality
	- same parameter may appear in multiple characteristics so harder to translate values to test cases
	- Example: 3 int parameters represent a triangle
		- IDM can combine all parameters
		- Reasonable characteristic - type of triangle
Example of interface vs functionality based:
```java
public boolean findElement (List list, Object element)
//Effects: if list or element is null throw NullPointerException
//else, return true if element is in list, false otherwise
```
Interface based:
- two parameters - list, element
- characteristics:
	- list is null (block1 = true, block2 = false)
	- list is empty (block1 = true, block2 = false)
Functionality-based:
- two parameters - list, element
- characteristics:
	- number of occurrences of element in list (0, 1, >1)
	- element occurs first in list
	- element occurs last in list

Constraints:
- infeasible combinations of blocks
- Two types:
	- a block from 1 characteristic cannot be combined with a specific block from another
	- a block from 1 characteristic can only be combined with a specific block to form another characteristic
- Handling with [[Apply test criterion to choose combinations of values ||criteria]]:
	- All Combi, Pair-wise, t-Wise - drop the infeasible pairs
	- Base Choice, Multi Base Choice - change a value to another non-base choice to find a feasible combination

