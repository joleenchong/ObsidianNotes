- small sequence of programmed instructions that tell computer what it has to do to perform a command
- highest level code processor can execute
- managed by a scheduler
- unit of execution within a [[Processes|process]]

States:
- Ready
- Blocked
- Running
- Terminated

Characteristics:
- basic unit of CPU utilization
- share all process memory and other resources
- threads share CPU (one thread at a time running)
- thread within a process executes sequentially
- each thread has own [[program counter]] & stack
- threads within a process are generally invisible from outside process
- threads within a process are scheduled and executed independently in same way as different single-threaded processes

Differences:
- not independent of one another
- all threads can access every address in the task
- no protection between threads within a process

Benefits:
- Responsiveness - when one thread in program is blocked and waiting, a second thread in the same task can run
- Resource sharing - threads share memory and resources within a process
- applications that require sharing a common [[Buffering|buffer]] (e.g. producer-consumer) befit from thread utilisation
- Economy - more economical to create and context switch threads than processes
- Utilisation of multiprocessor architecture - each thread may run in parallel on a different processor

Single vs. Multithreaded process:
- diagram slide 34

Types of threads:
- kernel supported threads
- user-level threads
- Differences:

|                  | User-level threads                                                               | Kernel-supported threads                                                                      |
| ---------------- |:-------------------------------------------------------------------------------- |:--------------------------------------------------------------------------------------------- |
| **Differences**  |                                                                                  |                                                                                               |
|                  | implemented by users                                                             | handled by operating system directly                                                          |
|                  | kernel not aware of the existence of these threads                               | only kind of thread kernel knows about                                                        |
|                  | thread management done by user-level threads library                             | thread management done by kernel                                                              |
|                  | handles them as if they were single-threaded processes                           | don't have their own scheduler                                                                |
|                  | small and much faster than kernel level threads                                  | expensive                                                                                     |
|                  | represented by program counter, stack, registers and small process control block |                                                                                               |
|                  | no kernel involvement in synchronisation for user-level threads                  |                                                                                               |
| **Advantages**   |                                                                                  |                                                                                               |
|                  | easier and faster to create than kernel-level threads                            | multiple threads of same process can be scheduled on different processors                     |
|                  | more easily managed                                                              | kernel routines can also be multithreaded                                                     |
|                  | runs on any OS                                                                   | if kernel-level thread is blocked, another thread of same process can be scheduled by kernel  |
|                  | no kernel mode privileges required for thread switching in user-level threads    |                                                                                               |
| **Disadvantage** |                                                                                  |                                                                                               |
|                  | multithreaded apps in user-level threads can't use multiprocessing to advantage  | mode switch to kernel mode required to transfer control from one thread to another in process |
|                  | entire process is blocked if one user-level thread performs blocking operation   | kernel-level threads slower to create and manage                                              |
|                  | kernel considers set of user-level threads as single thread                      |                                                                                               |
|                  | if any user level threads is blocked then other threads in set cannot run        |                                                                                               |

User to kernel mapping:
- many-to-one model
	- user level threads mapped to one kernel thread
	- multiple threads within process can't run in parallel on multiprocessors
	- used by solaris 2 and thread libraries for systems with no kernel threads
	- diagram slide 39
- one-to-one model
	- each user thread mapped onto a kernel thread
	- allows concurrency -> allows more threads to run when blocked
	- example: windows, linux
	- diagram slide 40
- many-to-many model
	- allows M user-level threads to be mapped to N kernel threads
	- allows OS to create sufficient number of kernel threads
	- many user threads can be made as necessary & corresponding kernel threads can run in parallel on multiprocessors
	- diagram slide 41

Thread cancellation:
- when multiple threads running in process, thread cancellation permits one thread to cancel another thread in that process
- target thread (being cancelled)  can keep cancellation requests pending & perform app-specific cleanup when acting upon cancellation notice
- Scenarios:
	- asynchronous cancellation - one thread immediately terminates target thread
	- deferred cancellation - target thread periodically checks if should terminate
- Problems:
	- if resources allocated to cancelled thread, OS reclaims those system resources (not all of them, asynchronous)
	- thread was cancelled while in the middle of updating data with other threads

Thread pools:
- number of threads created at process start up placed in a pool waiting for work
- Benefits:
	- faster to service a request
	- limits number of threads that may exist at any one point
- Disadvantages of not using thread pools:
	- time consuming to make and destroy thread for each request
	- no limit (bound) on number of threads created -> may exhaust system resources
- How are number of threads in pool set?
	- heuristically - based on system resources such as CPU, memory or number of requests
	- dynamically - adjusted on usage patterns