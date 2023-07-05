Von Neumann Architecture
- it basically stores programs and data in memory -> CPU can only do instructions from memory
- Cycle:
	- Fetch instruction from memory and stores in [[instruction register (IR)]]
	- pointer to next instruction to fetch/do stored in CPU's [[program counter]] (PC)
	- decode instruction
	- if instruction needs operands, get operands from memory and store in internal registers
	- do instruction and store results in memory
	- repeat