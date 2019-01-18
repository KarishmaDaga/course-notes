<style> h1 a {display:none;} .container-lg {min-width:200px; max-width:880px; padding:45px}
</style>

[CISC 324 Notes](cisc-342.md) // [All Notes](http://karishmadaga.com/course-notes) // [About](http://karishmadaga.com)


# Notes for Assignment 1 

### General Terms

-**address bus**: determines the location in memory that the processor will read data from or write data to
-**data bus**: this contains the contents that have been read from the memory location or are to be written into the memory location
- **control bus**: manages the information flow between the components indicating whether the operation is a read or write and ensuring that the operation happens at the right time
- **memory data register**: the cpu register that stores the data being transferred to and from the immediate access storage (i.e. the data value being fetched or stored). It contains the copy of designated memory locations specified by the memmory address register. 
- **memory address register**: the cpu register that either stores the memory address from which the data will be fetched from the cpu or the address to which the data will be sent and stored (i.e. it holds the memory location of data that needs to be accessed)
- **current instruction register**: holds the instruction currently being executed
- **instruction pointer**: the instruction pointer is incremented after fetching an instruction, and holds the memory address of ("points to") the next instruction that would be executed (in a processor where the incrementation precedes the fetch, the IP points to the current instruction being executed.)
- **uniprocessor system**: a computer system that had a single cpu that is used to execute computer tasks
- **multiprocessor system**: a computer system having two or more CPUs within a single computer system and the ability to allocate tasks between them
- **parallelism**: concerned with utilizing processors/cores to improve the performance of a computation
- **concurrency**: concerned with managing access to shared state from different threads
- **multiprogramming**: 
- **multitasking OS**: 
- **single-tasking OS**:
- **clustered computing system**:
- **distributed computing system**:
- **system call**:

### Terminology for Processes, Interrupts, and Context Switching
- **thread (also referred to as lightweight process)**: single unique execution context: fully describes program state.
	- It's a sequence of instructions withing a process and it behaves like "a process within a process".
	- It differs from a process because it does not have its own PCB (process control block).
	- Usually multiple threads are created withing a process
	- Contains a program counter, registers, execution flags, stack, and thread ID
- **address space**: programs execute in an address space that is distinct from the memory space of the physical machine
	- the set of accessible addresses and state associated with them
	- Ex: for a 32 bit processor there at 2^32 = 4 billion addresses
	- stack | ... | heap | static data | code (i.e. instructions
- **process**: an instance of the executing program is a *process* consisting of an address space and one or more threads of control. The OS holds most of its information about active processes in data structures called process control blocks (PCB).
- **dual mode operation/protection**: only the system has thr ability to access certain resources 
	- the os and the hardware are protected from user programs and user programs are isolated from one another by controlling the translation from program virtual addresses to machine physical addresses
- **virtual address**:
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

Example: When we launch a python shell or executing a python script, we start a process that runs our python shell or our python script. The operating system creates a process in response to us starting the python shell or python script 
### Assembly Code (x86)
- recall fetch/decode/execute cycle:
	- fetch instruction at program counter
	- decode
	- execute (possibly with registers)
	- write results to registers/memory 
	- program counter = next instruction (PC)
	- repeat


### Assembly to C
