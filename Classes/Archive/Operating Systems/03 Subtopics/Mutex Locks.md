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

C implementation - they legit do not teach you this :clown emoji: 
```C
/* Built-in C library for multithreading */
#include <pthread.h>

/* It's recommended to have one for each file that's being changed by multiple threads. */
pthread_mutex_t mutexLock;

void multithreadedFunction()
{
	...
	pthread_mutex_lock( &mutexLock );
	/* critical section */ ...
	pthread_mutex_unlock( &mutexLock );
	...
}
```

https://www.geeksforgeeks.org/mutex-lock-for-linux-thread-synchronization/
https://docs.oracle.com/cd/E19455-01/806-5257/sync-12/index.html