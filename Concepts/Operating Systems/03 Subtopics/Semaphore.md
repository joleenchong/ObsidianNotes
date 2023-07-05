*Definition* - synchronisation object that controls access by multiple processes to a common resource in a parallel programming environment
- integer variable that can only be accessed via two indivisible (atomic) operations
- used to control access to files & shared memory
- three basic functionalities: set, check, wait

Standard operations:
- wait()
- signal()

| Wait()                                                                                   | Signal()                                                                            |
|:---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| a process performs wait() to tell semaphore it wants exclusive access to shared resource | a process performs signal() to tell semaphore it's finished using shared resource   |
| if value of semaphore not negative, decrement by 1                                       | increments value of semaphore variables by 1                                        |
| if semaphore variable negative, wait is blocked                                          | if pre-increment value was negative, means there are processes waiting for resource |
Types of semaphores:
- binary semaphores - can only be 0 or 1
	- most often used to implement lock that allows only a single thread into a critical section
- counting / general semaphores - can take on any non-negative value
	- used for "counting" tasks such as creating critical region that allows specified number of threads to enter

Implementation:
``` pseudocode
wait (S): S.value = S.value - 1;
	if S.value < 0 then
	begin
		add process to S.list;
		block();
	end;

signal (S): S.value = S.value + 1;
	if S.value <= 0 then
	begin
		remove a process P from S.list;
		wakeup(P);
	end;
```
- block() suspends process that invokes it
- process is put into waiting queue associated with semaphore
- process state is switched from running into waiting queue
- CPU scheduler selects another process from  ready queue
- wakeup() resumes execution of blocked process P in S.list
- P is placed in ready queue
- process state switches from waiting to ready state

**Pros and Cons of Semaphores**
- Pros:
	- *only allows one process into critical section* - follows mutual exclusion principle strictly & much more efficient than other methods of synchronisation
	- *no resource wastage* - processor time not wasted unnecessarily to check if condition is fulfilled to allow process to access critical section
	- *machine independent* - implemented in machine independent code of microkernel
- Cons:
	- *complicated* -> wait and signal operations must be implemented in correct order to prevent deadlocks
	- *impractical for last scale* - wait() and signal() prevents creation of structured layout for system -> loss of modularity
	- *priority inversion* - low priority processes may access critical section first and high priority processes later
	- *timing*
