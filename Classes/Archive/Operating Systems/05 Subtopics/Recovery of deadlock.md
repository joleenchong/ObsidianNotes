Methods:
- Terminate [[Processes]]
	- kills all deadlocked processes one by one until deadlock eliminated
	- Order of termination?
		- lowest priority process
		- length of process runtime, how much longer process has to completion
		- resources used by process
- Pre-empt resource from process
	- roll back process to some safe state and restart from there
		- find safe state through:
			- destroy process & restart
			- use checkpoint during execution
	- starvation - same process may always be picked as victim
		- include number of rollbacks in cost factor to prevent