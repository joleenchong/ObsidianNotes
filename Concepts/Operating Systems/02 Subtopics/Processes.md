*Process* - a program in execution
- program (executable file containing list of instructions) is passive unless instructions are executed
- requires counter to specify next instruction to execute
- needs resources (CPU time, memory, files, I/O devices) to accomplish task
- Includes:
	- Text section - program code
	- [[program counter]] - pointer to next instruction to execute
	- Contents of process registers
	- Stack - has temporary data (temp variables, return addresses, etc.)
	- Data section - global variables
	- Heap - memory dynamically allocated during run time

Responsibilities of the Process Management of OS:
- Creation and deletion of user and system processes
- Suspension and resumption of processes
- Provision of mechanisms for process synchronisation (coordinate  process that uses shared data)
- provision of mechanisms for process communications
- provision of mechanisms for [[05 Deadlock ||deadlock]] handling

Two types:
- User level
- Kernel level

States a process can be in:
- *New* - process is being created
- *Running* - instructions are being done
- *Waiting* - process waiting for an event to occur
- *Ready* - process waiting to be assigned to a processor
- *Terminated* - process has finished execution
- look at diagram for this later (slide 7)

Data structures that represent a process:
- [[Process Control Block]] (PCB)
- Task Control Block - ??

Process hierarchy:
- Parent - a process that created another process
- Children - a process created by a parent
- Siblings - children with the same parent

Types of process operations:
- Process creation - parent process creates child process, which in turn can create other processes and form a tree of process
- process termination

How is each process identified:
- process ID (an integer value)
- init process has PID 1 as it's the root parent process for all other user processes
- a process requires resources (CPU, memory, files, I/O)

What happens when process creates a sub-process:
- Resources:
	- Parent & child may share all resources
	- child processes may share subset of parents' resources
	- parent & child process may share no resources
- Execution:
	- Parent & child may execute concurrently (linux)
	- parent may wait until child terminates (parent calls wait() to move itself out of the way)
- Address Space:
	- child address space is duplicate of parent
	- child has program loaded into it

Program termination:
- occurs when program executes last statement and / or calls exit()
- OS will deallocate child's resources
- child can return its status value to parent that calls pid = wait (&status)

If parent does not call wait():
- OS will not remove child from process table -> child becomes *zombie*
- when parent terminates, child becomes an *orphan* and init will automatically be its parent (init periodically calls wait() to remove orphans from process table)

Reasons for parent terminating execution of child process (abort):
- child exceeded allocated resources
- task assigned to child is no longer required
- parent is exiting (some OS don't allow child to run if parent terminates)

Types of concurrent processes executing in OS:
- Independent processes - cannot affect or be affected by execution of another process
- Cooperating processes - can affect or be affected by the execution of another process
	- Advantages:
		- Information sharing - several users may need same piece of information
		- Computation speed - breaks task into subtasks and execute in parallel
		- Modularity - divide system function into separate processes
		- Convenience - a user may want to do editing, printing in parallel
	- communicate via shared-memory or message passing