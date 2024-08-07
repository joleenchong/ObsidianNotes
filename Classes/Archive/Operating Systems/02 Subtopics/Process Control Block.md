Contains information needed to manage scheduling of a particular [[Processes ||process]], found in operating system [[Kernel]]

PCB characteristics:
- process number (pid)
- process state - new, ready, running, etc.
- [[program counter]]: - shows address of next instruction to do
- CPU registers - vary in number and type (based on computer architecture)
- CPU scheduling information - process priority, pointers to schedule queues, etc.
- memory management information - [[base register]] and [[limit register]]s
- accounting information - amt of CPU and time used
- I/O status information - list of I/O devices allocated to process, list of open files, etc.