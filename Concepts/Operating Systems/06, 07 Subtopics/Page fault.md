Definition: 
A type of exception raised when a running program accesses a memory page not currently mapped by [[Memory Management Unit]] into virtual address space of process

When page fault occurs:
- need to restart any instruction after page fault since page fault can occur 
- on instruction fetch - restart by fetching instruction again
- on operand fetch - restart by re-fetch instruction, re-decode, and fetch operand