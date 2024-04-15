Each process gets a small unit of CPU time (AKA time quantum) abt 10-100ms. After this time passes, the process is pre-empted and added to the ready queue. Higher avg turnaround than SRTF, better response time.

For ready queue with n processes, time quantum of q:
- each process gets 1/n CPU time in chunks of max q time units at once
- no process waits more than (n-1) q time unit

Performance depends on time quantum's size:
- large quantum - FCFS
- small quantum - must be large with respect to [[Context switch]]
	- overhead  may be too high
- turnaround time improves if 80% of processes finish next CPU burst within quantum
