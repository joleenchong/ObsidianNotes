An interrupt is 
1. CPU gets interrupt, stops what it's doing
2. CPU goes to specific location in [[interrupt vector]] table to perform *interrupt service routine (ISR)*
	1. interrupt vector table contains addresses / pointers of all ISRs
	2. each interrupt is known by its interrupt number / vector -> lower numbers = higher priority
	3. CPU computes location by multiplying interrupt number with fixed value
3. CPU resumes execution on completion of ISR
4. CPU saves address of interrupted instruction into program counter
5. CPU resumes interrupted execution using saved processor states

Efficient interrupt handling is needed for good system performance.

Interrupt-controller hardware:
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