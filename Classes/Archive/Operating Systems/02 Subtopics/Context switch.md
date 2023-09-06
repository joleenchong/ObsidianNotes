- The process of storing the state of a [[Processes ||process]] or thread so that it can be restored and execution resumed from the same point later -> allows multiple processes to share a single CPU -> essential feature for multitasking OS
- Disadvantages:
	- Overhead - system does no useful work while switching -> performance bottleneck
	- Dependent on hardware support
- When to switch CPU:
	- job voluntarily waits (system calls)
	- [[Interrupts||interrupt]]: higher priority event / job needs attention
	- interrupt: timer ([[program counter]])
slide 16 diagram