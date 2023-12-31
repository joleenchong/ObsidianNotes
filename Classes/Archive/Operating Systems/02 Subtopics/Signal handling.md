A signal is used in Unix to notify [[Processes|process]] that a particular event has occurred.

Types:
- Synchronous signals - delivered to same process that performs operation causing signal
	- operation can be divided by 0, illegal memory access
- Asynchronous signals - generated by event external to running process
	- <\control><c\>, timer expired

Pattern that signals follow:
- signal generation - occurrence of particular event
- delivering signal to a process
- signal handling

Two possible signal handlers:
- default signal handler - every signal has default handler run by the kernel
- user-defined signal handler - override the default

When process has more than one [[Threads||threads]] where should signal be delivered?
- Deliver signal to thread to which signal applies -> for synchronous signals
- Deliver signal to every thread in process -> some asynchronous signals such as </control/><c/>
- Deliver signal to certain threads in process -> options in some versions of UNIX
- Assign specific thread to receive all signals for process -> implemented in Solaris 2
