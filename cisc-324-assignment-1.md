# Notes for Assignment 1 

### Terms

- address bus:
- data bus:
- memory data register: 
- memory address register:
- current instruction register:
- instruction pointer:
- uniprocessor computer:
- parallelism:
- multiprogramming: 
- multitasking OS: 
- single-tasking OS:
- clustered computing system:
- distributed computing system:
- system call:

### Terminology for Processes, Interrupts, and Context Switching
- thread: single unique execution context: fully describes program state
	- program counter, registers, execution flags, stack
- address space: programs execute in an address space that is distinct from the memory space of the physical machine
	- the set of accessible addresses and state associated with them
	- Ex: for a 32 bit processor there at 2^32 = 4 billion addresses
	- | stack | ... | heap | static data | code (i.e. instructions |
- process: an instance of the executing program is a *process* consisting of an adress space and one or more threads of control
- dual mode operation/protection: only the system has thr ability to access certain resources 
	- the os and the hardware are protected from user programs and user programs are isolated from one another by controlling the translation from program virtual addresses to machine physical addresses
- virtual address:
- process control block:
- 'Zombie' state of a process:
- orphan process:
- context switching:
- interrupt:
- fork() function: 
- program counter:
- pooling:
- software interrupts:
- hardware interrupts:
-  

### Assembly Code (x86)
- recall fetch/decode/execute cycle:
	- fetch instruction at program counter
	- decode
	- execute (possibly with registers)
	- write results to registers/memory 
	- program counter = next instruction (PC)
	- repeat


### Assembly to C
