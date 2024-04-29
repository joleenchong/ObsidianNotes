Chapter 6 of OS textbook
**Main topics:**
- Scheduling concepts
- CPU scheduling algorithms
- CPU scheduling evaluations
--------------
Note: very incomplete, I'll return to it later

[[Processes|Process]] execution is a cycle of CPU and I/O burst. The processes alternate between these 2 activities until the last CPU burst -> terminates.
- CPU-bound process - very long CPU burst, spends more time on computation
- I/O-bound process - many short CPU bursts, spends more time on I/O

CPU schedulers:
- Short term scheduler (STS) - selects one process in memory ready for execution and allocates CPU to it
	- ready queue - FIFO, priority, tree or unordered linked list -> contains [[Process Control Block]]s of processes
	- schedules processes more frequently than other schedulers
- Medium term scheduler (MTS) - swaps jobs in and out of memory to reduce competition for CPU
	- removes processes from memory and puts them in secondary memory
- Long term scheduler - determines which jobs are put into ready queue
	- executes less frequently -> only when a job finishes
	- controls degree of [[Multiprogramming]] (number of processes in memory)

| Preemptive scheduling                                                    | Non-preemptive scheduling                                                                                           |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| highest priority process should always be the process currently utilised | Once CPU is allocated to process, process keeps it until it releases through termination or switching to wait state |
| needs special hardware (e.g. timer)                                      | no overhead of switching process from running to ready state                                                        |
| can result in race condition                                             | if CPU is allocated to processes with bigger burst time then processes with smaller burst times may starve          |
<<<<<<< HEAD
=======
|                                                                          |                                                                                                                     |
>>>>>>> d48770f836e1c92806f65151aec7df40503c7db2

Types of scheduling algorithms:
- [[First Come First Serve (FCFS)]]
- [[Shortest Job First (SJF)]]
- [[Priority Scheduling]]
- [[Round Robin (RR)]]
- [[Multilevel Queue Scheduling]]
- Multilevel Feedback Queue Scheduling
- Guaranteed Scheduling
- Multi-processor Scheduling
- Real-time Scheduling
- Thread Scheduling (User-level and Kernel-level)

Criteria for determining which is better:
- CPU utilisation - % usage of CPU -> higher is better
- throughput - num of processes that complete execution per time unit -> higher is better
- turnaround time - sum of periods spent waiting to get into memory, waiting in ready queue, executing on CPU, doing I/O -> shorter is better
- waiting time - sum of periods process waits in ready queue -> shorter is better
- response time - time taken from when request is first submitted until first response is produced -> for time sharing environment
- others:
	- for interactive systems:
		- minimise variance in response time (more predictable)
		- minimise maximum response time / average response time
	- each process gets fair share of CPU time

Calculator for scheduling algorithms:
- https://nicomedes.assistedcoding.eu/app/os/process_scheduling
- https://process-scheduling-solver.boonsuen.com/