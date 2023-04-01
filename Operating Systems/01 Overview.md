- Chapter 1-2 and Section 13.1-13.2 of OS textbook

**Main Topics**
- Overview of an OS, development, purposes, components, services
- basic hardware structure and operations
- OS structures

should refactor longer notes into new notes

------------
**Definitions:**
- *Operating System (OS)* : a program that acts as interface between a user and the computer hardware
- *Kernel* : a program that is part of an OS and is running at all times on computer
- *Bootstrap* : initial program to run when computer is powered on or rebooted
	- stored in a *firmware* (such as ROM or EEPROM)
	- initialises everything, locates, loads and runs OS kernel

**Purposes (Slide 8):**
- provides environment for user to execute programs conveniently and efficiently
	- users can be people / machines / other computers
- simulates features not available on hardware
	- virtual disks, virtual memory, virtual machines, etc.
- controls all computer resources and provides base at which application programs can be written and run

**Kernels (Slide 14 & 58):**
- System programs are loaded and start running at boot time
	- called *system processes / daemon* when they run when kernel is running
		- example: init in Linux (runs other daemons)
- once fully booted waits for events to happen -> *interrupt-driven*
	- system knows event happened through interrupts from hardware or software (traps or exceptions)
		- hardware interrupt -> sends signal to CPU by bus
		- software interrupt -> *system call / monitor call*
- Consists of everything below system-call interface and above physical hardware - file system, CPU scheduling, memory management, other operating system functions -> difficult to implement and maintain as everything in one level
- *Layered System (Slide 59):*
	- OS divided into layers - bottom layer is hardware and highest layer is user interface
	- each layer uses functions and services of only lower-level layers -> modularity -> easy to debug
	- less efficient and hard to define level functionality
- *Microkernel (Slide 60):*
	- smaller-sized kernel -> provides minimal services like process, memory management, communication
	- non-essential services become system / user programs
	- function: a communication facility ebtween a client and OS services using message passing
	- Pros:
		- easier to extend OS
		- more portable
		- more security and reliability
	- Cons:
		- message passing increases system function overhead -> reduced performance
- Modular kernel - set of core components that can add additional modules during boot / run time
	- more flexible than layered system -> module can call other module
	- more efficient than microkernel -> no message passing needed

**Interrupts (Slide 15):**
1. CPU gets interrupt, stops what it's doing
2. CPU goes to specific location in *interrupt vector table* to perform *interrupt service routine (ISR)*
	1. interrupt vector table contains addresses / pointers of all ISRs
	2. each interrupt is known by its interrupt number / vector -> lower numbers = higher priority
	3. CPU computes location by multiplying interrupt number with fixed value
3. CPU resumes execution on completion of ISR
4. CPU saves address of interrupted instruction into program counter
5. CPU resumes interrupted execution using saved processor states
- efficient interrupt handling is needed for good system performance
- Interrupt-controller hardware:
	- defers interrupt handling during critical processing
	- provides efficient dispatch to interrupt handler
	- supports multi-level interrupts with priority
- CPU defers low priority interrupt when higher priority interrupt is being served
- At boot time: OS probes hardware buses for present devices and installs their interrupt-handlers into interrupt vector
- During I/O: devices raise interrupts to signal they're ready to provide service, completed output, input data are available, or a failure was detected
- Interrupt I/O mechanism (Slide 32):
	- device controller raises interrupt - asserts signal on CPU's interrupt request line
	- CPU catches interrupt and dispatches to ISR or interrupt handler
	- interrupt handler clears interrupt by servicing device

**Von Neumann Architecture (Slide 21):**
- it basically stores programs and data in memory -> CPU can only do instructions from memory
- Cycle:
	- Fetch instruction from memory and stores in *instruction register (IR)*
	- pointer to next instruction to fetch/do stored in CPU's *program counter (PC)*
	- decode instruction
	- if instruction needs operands, get operands from memory and store in internal registers
	- do instruction and store results in memory
	- repeat

**Direct memory access (DMA) (Slide 34):**
- improve performance for large data transfers
	- bypasses CPU to transfer data directly between I/O device and memory -> CPU freed for other work
- CPU gives command to DMA controller with information on pointer of source of data transferred, pointer of destination of transfer, count of number of bytes to transfer
- Handshaking tween DMA controller & device controller uses *DMA-request line* & *DMA-acknowledge line* - handshaking is process for negotiating setting up comm channel tween 2 entities
	- device controller puts signal on DMA-request line when data is available for transfer
	- DMA controller senses signal -> seizes memory bus -> sets intended address on address bus  -> sends signal on DMA-acknowledge line
	- device controller receives DMA-acknowledge signal -> transfers data to memory -> removes DMA-request signal
- after finishing entire transfer DMA controller interrupts CPU:
	- OS sets DMA controller registers to set source and destination addresses, read/write request, transfer length
	- DMA controller transfers blocks of data from buffer storage directly to main memory -> no CPU intervention frees CPU for other tasks
	- DMA controller interrupts CPU after transfer completed - one interrupt generated per block
**Computer-System Architecture (Slide 37):**
- single-processor system : has only one CPU to do general purpose instructions but also has special purpose processors (e.g. for graphic controllers, keyboard) which don't run user processes
- multiprocessor system: has two or more processors working together. also called parallel / multicore system
	- Advantages:
		- *Increased throughput* - more work gets done in less time
		- *Economy of scale* - shared I/O devices, memory storage, and power supplies
		- *Increased reliability* - if one processor stops working the entire system can still keep going
			- Graceful degradation - system can do operations according to level of operations of working parts of system
			- Fault-tolerant - can continue functioning even if there's component failures
	- Two types:
		- Asymmetric multiprocessing
			- master processor schedules and allocates work to slave processors
			- slave processor waits for master's instructions or have predefined task
			- common in extremely large systems
		- Symmetric multiprocessing
			- each processor runs identical copy of OS with their own registers and cache
				- shares the same memory
			- many processes can be run at once without much effect on performance
			![[Pasted image 20230330091726.png]]
	- Multicore system - multiprocessor system but processors are on single chip
		- on-chip communication faster than inter-chip communication -> more efficient
		- less power / energy
		- ![[Pasted image 20230330091848.png]]
	- Clustered system - multiple CPUs but individual systems
		- share storage and communicate via LAN
		- high-availability service - very reliable?

**Multiprogramming (Slide 43):**
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

**OS operation (Slide 47)**:
- Dual-mode operation:
	- two modes of operation:
		- *user mode* - runs user programs
		- *monitor / privileged mode* - loads OS at system boot-time, runs privileged instructions, is switched to when interrupt or fault happens
	- hardware provides *mode bit* to indicate current mode : monitor (0) or user (1)
	- *Privileged instruction* - machine structions that may cause harm and can only be done in monitor mode
	- OS switches from monitor mode to user mode to start user processes -> user process can never gain control of computer in monitor mode
- I/O:
	- all I/O instructions are privileged -> user program must use system call to do I/O
- Memory:
	- must protect memory for interrupt vector and ISR
	- uses two registers to define range of legal addresses program can access:
		- *Base register* - holds smallest legal physical memory address
		- *Limit register* - holds size of range
		- instructions to load these registers are privileged
	- memory outside range is protected
	- OS is unrestricted for monitor and user memory
- CPU:
	- uses timer interrupt after certain period to prevent a single program from using CPU all the time
		- timer is decremented every clock tick -> upon reaching value 0, interrupt happens
	- used for time sharing
	- loading timer value -> privileged instruction

**System calls (Slide 52):**
- a user interface to OS services available in assembly-language instructions / high level languages for systems programming (like C)
- *Application Program Interface (API)* - set of functions available to application programmer
	- does the system calls for app programmers
	- more portable and easier to use
- has a number in a vector table that stores pointers to system call routines
- Result / termination:
	- normal termination (exit / return) : exits current program and returns to command interpreter
	- abnormal termination (trap) : program error
- Types of system calls:
	- Process control
	- File management
	- Device management
	- Information maintenance
	- Communications
	- Protection

-------------------
# Compiled questions from workshop and past year tests

### Workshop
1. What are the **three main purposes** of an Operating System?
2. What is **multiprogramming**? What is the main **advantage** of multiprogramming?
3. What is **time-sharing or multitasking system**? What is the main **advantage** of timeshared system? Is multitasking possible without **timer interrupts**?
4. In a multiprogramming and time-sharing environment, **several users share the system simultaneously**. This situation can result in various security problems.
	1. What are the **problems**? (Name at least two problems)
	2. Can we ensure the same degree of **security** in time-shared machine as we have in a dedicated machine? Explain your answer.
5. Describe how typically a **computer hardware** and an **operating system** support the implementation of **privilege instruction**. What would the hardware do if a process that runs in a **user mode** tries to execute a privilege instruction?
6. What is a **privileged instruction**? Which of the following instructions should be privileged? (i'm not gonna put the list down)
7. What is the purpose of **system calls**? Describe **three methods** to pass parameters to the OS.

### Mid-sem tests
1. Describe the folllowing terms:
	1. System call
	2. Timesharing system
	3. Privilege instruction
2. One of the main purposes of OS is to simulate features not available on hardware. List two such features, and describe one of the two listed features.
3. Explain difference between instruction register (IR) and program counter (PC)
4. Setting the program counter register is a privileged operation. True or False?
5. Why is using direct access memory (DMA) more effective than using intterupt to communicate with I/O controller?
6. Explain 1 main advantage and disadvantage of the microkernel design
7. An operating system is interrupt driven. Briefly explain the statement.
8. Which of the two modes, kernel or user mode, is a computer in when first powered on? Justify why the computer must be in a kernel or user mode
9. (repeat of workshop question 5)
10. How does an operating system obtain the address of an interrupt service routine. Where does the system store the address of an interrupted instruction?
11. For the following events, state if it's a hardware or software generated interrupt (combined two questions)
	1. Completing an I/O operation
	2. Recovery from error (e.g. division by zero)
	3. Invalid memory access
	4. System call
12. An operating system that uses microkernel offers good system security. True or False?
	1. Same statement but replacing security with reliability
13. (repeat of workshop question 3)
14. Discuss differences between main goals of desktop operating systems and main frame systems
15. An interrupt vector table is an array of pointers to the PCBs of processes that are generating interrupts. True or False?
16. Setting the base and limit registers are privileged operations. True or False?
17. A layered operating system has slower performance than a monolithic operating system. True or False?