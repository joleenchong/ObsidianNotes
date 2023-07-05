- Chapters 3 and 4 of OS textbook

**Main Topics:**
- Process concept
- Operations of processes
- Inter-process communication
- Threads
---------------------
Processes:
[[Processes]]
[[Process Scheduling]]
[[Context switch]]

Shared memory vs. message passing:

| Shared Memory                                                                                           | Message Passing                                                 |
|:------------------------------------------------------------------------------------------------------- |:--------------------------------------------------------------- |
| process uses [[System call]] to create shared memory region                                                 | uses system call to exchange message between processes          |
| other process that wants to communicate via memory region must attach its address space to it           | more time consuming                                             |
| once established, all accesses to shared memory are like assessing normal memory area -> no system call | OS handles synchronisation between processes                    |
| suffers from cache coherency issues                                                                     | Good for distributed system with small amount of data exchanged |
| note: all accesses must be synchronised                                                                 |                                                                 |

[[Message-passing operations]]
Types of message passing:
- Blocking (Synchronous)
	- send: sender is blocked until message is received
	- receive: receiver blocks until message is available
- Nonblocking (Asynchronous)
	- send: sender resumes operation after sending message
	- receive: receiver retrieves either valid message or a NULL
[[Producer-consumer problem]] (Example of concurrent processes)

- Exception conditions and recovery steps:
	- cause: error may happen during process communication. Failure occurs in a centralised / distributed machine recovery must take place after
	- *Problem:* Process terminates e.g. Process P is waiting for a message from a terminated process Q
		- *Solution:* OS terminates P or notify P that Q has terminated
	- *Problem:* Lost messages e.g. message from P to Q become lost due to hardware error (most common lost detection is timeout)
		- *Solution:* OS detects it and resends message; sender detects it and resends; OS detects it and lets sender know
	- *Problem:* Scrambled message, message is received but in error (detected by parity checking)
		- *Solution:* resend it

[[Buffering]]

[[Threads]]

[[Signal handling]]
