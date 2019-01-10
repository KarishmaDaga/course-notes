<style>
h1 a {display: none;}
.container-lg {min-width: 200px; max-width:880px; padding:45px;}
</style>

# CISC 342: Operating Systems

## Topics 
- [Lecture 1](#Lecture-1)
- [Lecture 2](#Lecture-2)

### Resources
- [MIT, Operating System Engineering Fall 2012]()
- [Berkeley, CS 162 Operating Systems]()
- [Wisconsin-Madison, CS 537]()
-  [CS 162 Berkeley Lectures on Youtube]()

### Administrative Details
- Office Hours: Monday, 10:30 - 12 Room 241
- TB: Operating Systems Concepts (Dinosaur Book) 

<br></br>

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
	- main memory (dram) 
	- cache memory (sram) 
	- register
	- Note: 
- **I/O Devices**: communicating data to and from devices

#### Von Neumann Architecture
 
