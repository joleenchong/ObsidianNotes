Buffer overflow attacks occur when a program writes too much data into a [[Buffering|buffer]] and makes it overflow into adjacent memory. This allows attackers to overwrite data, change program behaviour or inject malicious code -> unauthorised access / system compromise

CPU registers:
- 16 int registers - 64 bits wide
	- rdx - full 64 bit register
	- edx - lower 32 bits
	- dx - lower 16bits
	- dl - lower 8 bits
	- dh - value in bits 8-15
![[Pasted image 20230820224514.png]]
- RSP - register stack pointer (current location in stack, growing downwards)
- RBP - register base pointer (start of stack)
- RSI - register source index (source for data copies)
- RDI - register destination index (destination for data copies)
- RIP - holds current instruction being executed at any one time

Assembly:
- uses directives / commands to define segments within program so assembler knows how to organise program sections in memory -> process memory layout
- directives:
	- .data - defines block where initialised static / global variables are stored
	- .bss - defines block where uninitialised static / global variables are stored
	- .text - defines block where executable instructions are placed
	- .heap - defines block for dynamic memory allocation
	- .stack - defines block to store local variables defined in functions + data related to function calls (return address, arguments, etc.)
https://cs.brown.edu/courses/cs033/docs/guides/x64_cheatsheet.pdf


Stack overflow:
![[Pasted image 20230820225233.png]]
- when it becomes an attack:
![[Pasted image 20230820225309.png]]
- two folded:
	- first fold - when CPU executes over stack, malicious code is considered as value for variables / arguments
	- second fold - when redirected by new return address, code should execute as commands

Unsafe C functions (could lead to buffer overflow)
- printf
- sprintf
- strcat
- strcpy
- gets

Steps:
- identify unsafe functions
- fill stack with a repeated character
- get memory address of where buffer has started
- use memory address to get the number of characters to fill the buffer
- pad malicious code front and back to inject into adjacent memory spaces
	- use '\\x90' - 'no operation' to make CPU keep executing to reach the shellcode
[[Vulprog attack example]]

Big endian - the biggest byte is ordered first.
Little endian - the smallest byte is ordered first

1 byte = 8 bits
1 word = 2 bytes / 16 bits
1 double word = 4 bytes / 32 bits
1 giant word / quad-word = 8 bytes / 64 bits

Mitigation:
- stack canaries - special values placed before return address on stack -> checked before a function returns to see if stack was tampered with
- Address Space Layout Randomizer (ASLR) - randomises memory addresses where program components are loaded to make it harder for attackers to predict memory location
- use safe programming languages (e.g Rust / Swift) - strict memory management rules prevent vulnerabilities
- use secure APIs and libraries 
- boundary checking and validation - user inputs properly validated & sanitised
- least privilege principle

Notes: read through book_sample_bufferOverflow.pdf