<style>
h1 a {display: none;}
.container-lg {min-width: 200px; max-width:880px; padding:45px;}
</style>

# CISC 342: Operating Systems

## Topics 
- [Lecture 1](#lecture-1)
- [Lecture 2](#lecture-2)
- [Assignment 1 Notes](cisc-324-assignment-1.md)

### Resources
- [MIT, Operating System Engineering Fall 2012]()
- [Berkeley, CS 162 Operating Systems]()
- [Wisconsin-Madison, CS 537]()
-  [CS 162 Berkeley Lectures on Youtube]()

### Administrative Details
- Office Hours: Monday, 10:30 - 12 Room 241
- TB: Operating Systems Concepts (Dinosaur Book) 
- 6 assignments, 6 labs, 2 midterms, 1 final. 



## Lecture 1
Dfn: An **operating system** is a special layer of software that provides applicationsoftware access to hardware resources 
- Convenient abstraction of complex hardware devices
- Protected access to shared resources
- Security and authentication
- provides and environment in which programs can do useful work

_What does an OS do?_
- Provide abstractions to applications
	- file systems
	- processes, threads
	- virtual machine, containers
	- naming system, etc
- Manage resources
	- memory, cpu, storage, etc
- Achieves the above by implementing specific algorithms and techniques
	- scheduling
	- concurrency
	- transactions
	- security
- User Interface (think Batch, CLI, GUI, etc)
- Program Execution
- I/O operations
- Communication: allows programs to communicate with each other locally or remotely.
- Error Detection: detect and correct errors when they occur during programs execution.
- Protection and Security: for users and processes to preserve privacy

Moore's Law
- Microprocessors have become smaller, denser, and more powerful
- Slowdown in Joy's law of performance


## Lecture 2 

#### Types of Operating Systems

- Multiprogramming Systems: systems that have multiple programs loaded into memory at a time
- Single-tasking systems: only have one program loaded into memory at a time (ex: MSDOS)
- Time-sharing systems: multitasking systems that switch between processes when their time slice is up e.g. modern OSs (linux, mac os x, windows)
- Embedded OS: for embedded devices 
- Real time OS: for critical industrial facilities 
- Distributed OS: designed to handle distributed infrastructure
- Network OS: for network admin + mgmt

_What is a process?_

Dfn: A **process** is an execution stream in the context of a particular process state. A more intuitive definition is that it's just a running piece of code along with all the things that the code can affect or be affceted by.
- Process state is everything that can affect or be affected by the process (code, data values, open files, etc)
- Execution stream is a sequence of instruction performed in a process state
- ONLY one thing happens at a time within a process

Most systems allow more than one process (multiprogramming).

### Computer Systems Architecture
- Hardware and software in computer systems
- Memory unit
- CPU
- Single and multiprocessor systems
- Instruction execution cycle

- A computer system is mainly composed of four components: Hardware|OSs|Apps|Users

#### Hardware Components
- **CPU**: digital logic for performing computation 
- **Central Memory**: hardware components used to store data. They are often classified following their storage capacity, speed (access time), and cost:
	- (in ascending order) mass storage
	- main memory (dynamic ram) 
	- cache memory (static ram) 
	- register
	- Note: 
- **I/O Devices**: communicating data to and from devices

#### Von Neumann Architecture
 

### Jan 17th 

- Dfn: A thread is a lightweight process
- Does not need to allocate additional memory space. They only require dedicated registers and memory stack,
- thread context switching is very fast 

- Similar to processes:
	- threads are identified by a thread identifier
	- each thread is associated to a data structure called a TCB (thread control block)

- Recall: SRAM is the internal cache in the CPU and stores the frequently requested data. 


#### threads vs processes
- assuming you have a process that creates another process (child process) by invoking the system called fork()
- stack segment used for interrupts
- the original pcb and the new pcb are created. the new pcb is pointing to the original pcb, the pc counter of the new process 


(NOTE: assignment. when fork() is called, a new process is created for each iteration of a loop from 1 to n.)

- the child process being changed doesn't change the parent process 

Example: 

```
for (int i = 0, i <= 3, i++) 
{ 
	p = fork()
}
```
p1 -> p2, p3, p4
p2 -> p5, p6
p3 -> p7
p4 -> O
p5 -> p8

### Threads
- single threaded processes
- multithreaded processes = can perform more than one taks at a time
- asynchronous and synchronous threading
- a thread is pointing to a certain data/code segment ????
- full vs partial context switching 

#### Thread levels
- Often implemented in two levels
- User level threads: OS doesn't know you've created multiple threads in a process
	- 

#### Direct Memory Access


### Jan 22 2019
- data races vs race conditions
	- data race: occurs when 2 instructions from different threads access the same memory location, at least one of these accesses is a write and there is o synchronization that is mandating any particular order among these accesses
	- a race condition is a *semantic error*. It is a flaw that occurs in the timing or the ordering of events hat leads to erroneous program behaviour. Many race conditions can be cased by data races, but that's not necessary.
- critical section: program requests to use shared resources on which the access is mutually exclusive
	- typically organized as 
	```
	program()
	{ 
		[remainder section]
		entry section
			critical section
		exit section
		[remainder section]
	}
	```
	- in the entry section, the process places a request to the OS to grant it  access to the critical section 
	- in the exit section, the process informs the OS of leaving the critical section to wake up any waiting processes

##### Example
Let thread 1 and thread 2 be two java threads:
the second line, i = i + 15 and i = i - 15, and v = i / 10 are the critical sections (manipulating variable where more than one thread is currently sharing)

- the **critical section problem** is all about designing a protocol that processes can apply to cooperate. Such protocol must satisfy the following three requirements: 
	- mutual exclusion: at most, one process is executing its critical section at a time
	- progress: a process must leave the crit section once its done with it and *notify other processes about that*
	- bounded waiting: the process waiting in the queue for the critical section must not wait indefinitely 
- Note:
	- a process may be interrupted (context switch) during its critical section
	- there is a queue of PCBs (process control blocks)

#### Synchronization Mechanisms

##### Mutex Locks
Dfn: A mutex lock stands for **mut**ual **ex**clusion, the simplest software based solution for the critical section problem

- a process must acquire the lock before entering its crit section
- two **atomic primitives** are used, the `acquire()` primitive (entry section) and the `release()` primitive (exit section)
- uses a boolean variable `available` to determine whether the lock is available or not

```
acquire() 
{ 
	while(!available);
	available = false;
}

release()
{
	available = true;
}

program() 
{
	acquire();
	Critical Section;
	release();
}
```
- the use of mutex creates **busy waiting** (continuous looping)
- each process acquiring a non available lock spins while waiting 
- no context switch is required when a process must wait on a lock
- used in multiprocessor systems where one process can "spin" on one CPU while another performs its critical section on another CPU
- the primitives are sometimes called `acquire()` -> `lock()` and `release()` -> `unlock()`.

##### Example for Mutex Locks
What is the final value of a shared variable if we use `lock()` and `unlock()`?

#### Semaphores 
Dfn: A semaphore allows two ore more processes or threads to communicate in order to be executed in a correct order

## Feb 5th - Deadlocks Avoidance

If a process requests a resource that is **currently available**, it may still have to wait.

### Banker's Algorithm
An algorithm that allows the avoidance of deadlocks by determining whether a safe sequence S exists or not

- The algorithm uses four data structures
	- **available**: a vector of size *m* (resource types) to express the currently available number of instances for a given resource Rj
		- there are *k* instances of resource type Rj, [Available[j] = k]
	- **max**: a matrix of size nxm to express the max number of resources to be requested by a given process
		- [Max[i,j] = k]: at most k instances of resource type Rj will be requested by process Pi
	- **Need[i,j] = Max[i,j] - Allocation[i,j]**

### Resource Request Algorithm
Let request i be the request vector for process Pi:

- if request i <= Need i, goto 2 else error
- if request i <= available, goto 3, else Pi must wait
- the system pretends to have allocated resources to Pi by updating the data structure

### Banker's Algorithm
- Let work and finish be vectors of len m and n respectively s.t. work = available and for all i, finish[i] = false
- find an index i:
	- finish[i] == false
	- need i <= work
	- else goto 4
- work = work + allocation i
	- finish[i] = true
	- goto 2
- if for all i: finish[1] == true then the system is in a safe state

- Example: a system needs O(m x n^2) operations to execute the banker's alg where n is the # of processess and m is the # of resources

### Example
R1 | R2 | R3
3 | 3 | 2
2 | 0 | 0
**5** | **3** | **2**
2 | 1 | 1
7 | 4 | 3

- when a request is made and it *does not exceed the currently available resources* pretend it has been granted and then see if the resulting state is a safe one.
	- if so, grant the request
	- if not, deny the request


