- Goal : increase CPU utilisation -> keep it as busy as possible
- many jobs kept in main memory at same time and CPU constantly switches between them
	- Job scheduling - OS chooses jobs from job pool and puts into memory
	- Memory management - OS allocates memory for each job
	- CPU scheduling - OS chooses one process (job in memory) that is ready to run
	- I/O allocation
- *Time-sharing / Multitasking system:*
	- Goal : provide interactive use of computer at reasonable cost (one computer - several users / jobs)
	- like multiprogramming but user input is from on-line terminal and switches based on time period
	- CPU switches between jobs frequently so user can interact with their running program
		- on-line communication between users and systems - after finishing one command it seeks next *control statement* from user's keyboard
		- on-line file system for users to access data and code