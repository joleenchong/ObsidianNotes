Chapter 5 of OS textbook

 **Main Topics:**
- Concurrent processes
- Critical section problem
- Solutions for critical-section problems using semaphores
- Classical problems of synchronisation
- Monitors
----------------------------

**Cooperating Process vs Independent Process**

| Cooperating Process                                             | Independent Process                            |
| --------------------------------------------------------------- |:---------------------------------------------- |
| can affect / be affected by other processes executing in system | cannot affect / be affected by other processes |
| share logical address space                                     | can stop & restart with no bad effects         |
| share data through files                                        |                                                |

[[Producer-consumer problem]]

Atomic operation - an operation that completes entirely without interruption
- Example: assume initially counter = 5
	- producer executes counter++
	- consumer executers counter--
	- Correct result - counter = 5, if producer and consumer execute separately / each instruction is executed atomically
	- How would these statements be implemented in machine language?
![[Pasted image 20230403104626.png]]

Race condition - a situation where several processes access & manipulate same data concurrently
- outcome of execution depends on particular order in which access takes place

Critical section - a code segment that accesses shared variables & has to be executed as atomic action
- only one process in a group of cooperating processes at a given point of time must be executing critical section
- Critical section problem:
	- how to ensure at most one process executing critical section at a given time?
	- need to make sure when one process executes critical section, no other process allowed to execute in its critical section
- Structure of process with critical section:
``` pseudocode
REPEAT
	Entry section.
		Critical section
	Exit section
		Remainder section
UNTIL false;
```
- requirements to satisfy critical section problem
	- *Mutual exclusion* - if process is in critical section, no other process can execute in their critical section
	- *Progress* - no other process in running outside its critical section may block other processes from entering their critical section
	- *Bounded waiting* - no other process should have to wait forever to enter its critical section
- Simplest solution:
	- Each process disables all interrupts right after entering its critical section & re-enables them right before leaving it -> not advised as enabling / disabling interrupt is privileged instruction
- Kernel mode solution:
	- *Pre-emptive Kernel* - a process can be pre-empted while running in kernel mode
		- process running in kernel can be replaced by another process while in middle of kernel function
		- forced context switch
		- more responsive and suitable for real time system
	- *Non-pre-emptive kernel* - a process can't be pre-empted while run in kerenl mode
		- process in kernel mode allows process to run until exiting kernel mode, blocks, or voluntarily yields CPU
		- planned context switch
		- free from race conditions on kernel data structure
- Algorithm 1 for critical section problem:
``` pseudocode
var turn (0...1); //initially turn = 0, turn = i means Pi can enter its CS

Process Pi
repeat
	while turn != i do no-op;
		Critical section
	turn = j
		Remainder Section
until false;

Process Pj
repeat
	while turn != do no-op;
		Critical section
	turn = i;
		Remainder section
until false;
```
- satisfies mutual exclusion but not progress
- if turn = 0, p1 cannot enter CS even though p0 is in RS
- *busy waiting* - continuously testing a variable waiting for some value to appear -> wastes CPU
- Algorithm 2:
```pseudocode
//initially flag[0] = flag[1] = false; flag[i] = true means Pi wants to enter its CS
var flag array [0...1] of boolean:

Process Pi
repeat
	flag[i] = true;
	while flag[j] do no-op;
		Critical Section;
	flag[i] = false;
		Remainder Section;
until false;

Process Pj
repeat
	flag[j] = true;
	while flag[j] do no-op;
		Critical section;
	flag[j] = false
		Remainder section;
until false;
```
- still does not satisfy progress requirement
- t0: P0 sets `flag[0] = true`
	- t1: P1 sets `flag[1] = true`
- P0 & P1 are looping in their respective whiles
- Peterson's Solution:
	- a concurrent programming algorithm for mutual exclusion that allows 2 or more processes to share single-use resource without conflict using only shared memory to communicate
	- turn - whose turn to enter the critical section
	- flag - indication of whether or not a process is ready to enter critical section
	- satisfies mutual exclusion and progress
```pseudocode
//combine shared variables of Algorithm 1 and 2

Process Pi
repeat
	flag[i] = true;
	turn = j;
	while (flag[j] AND turn == j) do no-op;
		critical section
	flag[i] = false;
		remainder section
until false;

Process Pj
repeat
	flag[j] = true;
	turn = i;
	while (flag[i] AND turn == i) do no-op;
		critical section
	flag[j] = false;
		remainder section
until false;
```
- Bakery algorithm:
	- simplest known solutions to the mutual exclusion problem for general case of N process
	- a critical section solution for N processes
	- algorithm preserves the first come first serve property
	- Concept:
		- Before entering critical section, each process receives a number
		- holder of smallest number enters critical section
		- if processes Pi and Pj receive same number, if i < j, then Pi served first, else Pj served first
		- Notation (ticket# process id#) - first, ticket number is compared. if same then process ID compared next
		- data structures initialised to false and 0