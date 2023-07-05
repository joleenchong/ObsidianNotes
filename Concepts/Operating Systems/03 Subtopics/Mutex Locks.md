*Definition* - Synchronisation mechanism for enforcing limits on access to resource in an environment when there are many threads of execution
- acquire a lock before entering a critical section and release the lock on exit

**Implementation:**
- calls to acquire() or release() must be *atomic*
- implement with hardware solution (e.g. test and set)
- uses busy waiting (spinlock) -> wastes CPU but does not need context switch
```pseudocode
Repeat
	acquire lock.
		critical section
	release lock.
		remainder section
Until false;

acquire()
{
	while (!available); // busy wait
	available = false
}

release()
{
	available = true
}
```
