# Operating Systems


## Table of Contents

[Lecture 1 - Introduction to OS](#Lecture1)
<br>
[Lecture 2 - Operating-System Structures](#Lecture2)
<br>
[Lecture 3 - Processes](#Lecture3)
<br>
[Lecture 4 - Threads](#Lecture4)
<br>
[Lecture 5 - Process Synchronization](#Lecture5)


<a name="Lecture1"></a>
## Lecture 1 - Introduction to OS
- **Operating System** : Intermediary between user and computer hardware
  - Executes user programs
  - Make computer system convenient to use
  - User computer hardware efficiently
- Common Definition
  - **Kernel**: Program that runs at all times
  - System Program (Ships with OS)
  - Application Program

### Computer System Structure
- Hardware: Provides basic computing resources
  - CPU, Memory, I/O
- Operating System
  - Controls and coordinates hardware among applications and users
- Application Programs
  - Define ways to use system resources to solve computing problems of the user
- Users
  - People, Machines, Other Computers

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Computer_Structure.png)

- **User View**
  - Want convenience, ease of use and good performance
  - Do not care about resource utilization or optimization

- **System View**
  - OS is the program that is most involved with hardware
  - View OS as a
    - Resource Allocator
      - Manage resources
      - Decide who uses what and when
    - Control Program
      - Controls program execution
      - Prevents errors and improper usage

### Computer System Operation

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Computer_Structure2.png)

- I/O devices and CPU can execute concurrently
- Each device controller is in charge of a device type
  - Each controller has a local buffer
  - Controller informs CPU that operation is done by using interrupt
- CPU moves data between main memory and local buffers
- I/O is from device to local buffer


- Computer Startup Process
  - Needs an initial program to run
    - **Bootstrap Program** is loaded at power-up / reboot
  - Stored in ROM or EEPROM
  - Initializes all aspects of System
  - Loads OS Kernel and starts execution
    - Kernel provides services to system and users
  - Some services not provided by kernel
    - **Systems Processes / System Daemons**
    - These are programs that run with kernel and are loaded during boot time

### Common Functions of Interrupts
- An event is signaled by an *interrupt* from hardware or software
  - Hardware trigger an interrupt by sending a **signal to the CPU**
  - Software trigger an interrupt by executing a **system call**
- Interrupt gives control to the ISR (Interrupt Service Routine)
  - Uses the Interrupt Vector which contains the addresses of all the service routines
- Must save the address of the interrupted instruction to return back to it after
- **Trap** / **Exception** : Software generated interrupt caused by an error or user request
- OS is *Interrupt Driven*

### Interrupt Handling
- OS preserves CPU State by storing registers and the PC (program counter)
- Determines type of interrupt
  - Polling
  - Vectored Interrupt System

### Storage Structure
- **Main Memory**: Only large storage media that CPU can directly access
  - Random Access
  - Volatile
- **Secondary Storage**: Extension of main memory that provides large nonvolatile storage
- **Hard Disks**: Rigid metal or glass platters covered with magnetic recording material
  - Divided into tracks, subdivided into sectors
  - Disk controller determines logical interaction between device and computer
- **Solid State Disks**: Faster than hard disks, nonvolatile

### Storage Hierarchy

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Storage_Hierarchy.png)

### Caching
- Copies info that needs to be used from slower to faster storage temporarily
  - First checks if info already there
  - If not copy
- Cache management is important because it is smaller in size

### I/O Structure
- OS's have *device driver* for each device controller to manage I/O
- Interrupt driven I/O is good for moving small data
  - Device driver loads registers within device controller
  - Device controller determines the action
  - Device controller transfer data to local buffer
  - Device controller informs driver via interrupt that its done
  - Device driver gives control back to OS
- This produces **High Overhead** when using it for bulk data
  - To solve this, use DMA

### Direct Memory Access (DMA)
- Used for high speed I/O Devices
- Transfer blocks of data from buffer to main memory without CPU
- 1 Interrupt per block instead of byte
  - Used for moving bulk data

### Single Processor System
- Most systems use a single-general-purpose processor
  - Also have special-purpose processors
  - Used for keyboards and disks

### Multiprocessor System
- Parallel / Multicore
- 2+ processors that share resources
- Pros
  - **Increased Throughput**: More work in less time
  - **Economy of Scale**: Cost less than equivalent single-processor systems
  - **Increased Reliability**: Graceful degradation or fault tolerance
- Two Types
  - Asymmetric Multiprocessing:
    - Each processor assigned a task
    - **Boss Worker** Relationship
    - Boss schedules work to the worker processors
  - Symmetric Multiprocessing:
    - Most common
    - All processors are peers, each processor performs all tasks

### Multi-Core CPUs:
- More efficient than multiple single-core chips
  - On-chip communication > chip-to-chip communication
- Uses less power than multiple single-core chips

### Clustered Systems
- Like multiprocessor systems, but its multiple systems working together
- Use **Storage Area Network (SAN)** to share storage
- High-Availability service that survives failures
  - **Asymmetric Clustering**: One machine in hot-standby mode
  - **Symmetric Clustering**: Multiple nodes running apps, monitoring each other
- Some clusters are **High Performance Computing (HPC)**
  - Apps use parallelization
- Some clusters have **Distributed Lock Manager (DLM)**
  - Avoids conflicting operations

### Important Aspects of OS
- **Multiprogramming (Batch System)**
  - Needed for efficiency
  - Single user cant keep CPU / I/O busy all the time
  - Organizes jobs so CPU always has one to execute
  - Jobs are selected and run via **Job Scheduling**
  - Instead of waiting, switches to another job


- **Timesharing (Multitasking)**
  - CPU switches jobs frequently so that users can interact with jobs while they are running
  - Response time < 1s
  - Each user has at least one process running
  - Several jobs ready to run, handled by CPU Scheduling
  - If processes exceed memory space, swap them in and out
  - Virtual memory allows processes > physical memory to execute

### Dual-Mode & Multi-Mode Operations
- OS can know when a user is executing code and when kernel is
  - **Mode Bit**: provided by hardware (kernel(0), user(1))
- Switch between user and kernel mode
  - System calls go from user mode to kernel mode, then back to user after executing system call
  - **Timer** is used to make sure user doesn't hog resources or no infinite loop
  - After timer expires control goes back to OS
- Can be applied to multiple modes
  - **Virtual Machine Manager** is another mode
  - Has more privileges than user but less than kernel
  - Will have a bit to identify when VMM is in control

### Process Management
- **Process**: A program in execution. (Unit of work)
  - Program is passive, process is active
- **Single Threaded**: Process that has one program counter specifying location of next instruction to execute
  - Process executes sequentially
- **Multi Threaded**: Process has one program counter per thread

### Memory Management
- To execute program, must be in memory (at least a part of it)
- Memory management determines what is in memory and when
  - Needs to keep track of which parts of memory are being used and who's using it
  - Decide which processes to move in and out of memory
  - Allocate/Deallocate memory space as needed

### Storage Management
- OS provides uniform, logical view of info storage
- File System Management
  - Files organized into directories
  - Access control to determine level of accessibility
  - Activities include
    - Create/Delete files/directories
    - Backup onto non-volatile storage

### Mass Storage Management
- Disks used to store data that can't fit on main memory
  - Long storage periods
- OS responsible for
  - Free-space management
  - Disk Scheduling
  - Storage allocation

### Cache Coherency
- Data might show up multiple times in the hierarchical storage structure
- Cache coherency is making sure all levels of data have the most recent value in their cache

### I/O Systems
- Subsystem consists of
  - Memory Management of I/O
    - Buffering - Storing data temporarily while being transferred
    - Caching - Storing parts of data in faster storage for performance
    - Spooling - Overlapping output of one job with input of others

### Protection & Security
- **Protection**: Controlling access of resources to processes and users
- **Security**: Defense of system against attacks (Internal / External)
- Systems first distinguish among users (Who can do what)
  - User ID's - Associated with files, processes, determine access
  - Group ID's - Define the above to a group of users
  - **Privilege Escalation** - Allows users to change effective ID with more rights

### Kernel Data Structures
- Array
- List
- Linked List
  - Singly
  - Doubly
  - Circularly
- Stack (LIFO)
- Queue (FIFO)
- Trees
  - Binary
  - Binary Search Tree - O(N) performance
  - Balanced Binary Search Tree - O(log(2)n) performance
- Hash Functions & Maps
  - Hash collision control - Secondary Hash Function, Linear Probing, Linked List
- Bitmaps
  - String of `n` binary digits that represent status of `n` items
  - `001011101`
    - Resources: 2,4,5,6,8 are unavailable because 0 and rest are available

### Computing Environments
- Traditional Computing
- Mobile Computing
- Distributed Computing
  - LAN / WAN / MAN / PAN
- Client Server
- Peer to Peer
- Virtualization
  - Allows OS's to run as applications inside other OS's
  - Emulation (Running android on laptop for testing)
- Cloud Computing
  - Types
    - Public Cloud
    - Private Cloud
    - Hybrid Cloud
  - Services
    - SaaS = Software as a Service
    - PaaS = Platform as a Service
    - IaaS = Infrastructure as a Service
---

<a name="Lecture2"></a>
## Lecture 2 - Operating-System Structures

### Operating System Services
- User Interface - All systems have a UI
  - Command Line Interpreter (CLI)
  - Graphics User Interface (GUI)
  - Batch Interface
- Program Execution
- I/O operations
- File-System Manipulation
- Communications
- Error Detection
- Resource Allocation
- Accounting
- Protection & Security

### Command Interpreters
- CLI allows direct command entry
- Fetches command from user and executes
- Examples
  - BASH
  - C Shell
  - Korn Shell
  - Bourne Shell

### System Calls
- Provide interface to the services of the OS
- Written in high level language
  - C / C++
- Accessed via API (Application Programming Interface)
  - Another High level language

### System Call Implementation
- Number associated with each system call
  - System Call Interface (SCI) maintains table with these numbers
- SCI invokes system call in OS kernel
  - Returns status of system call

### System Call Parameter Passing
- 3 Methods used
  - Passing parameters in registers
  - Passing parameters in a block / table
  - Parameters placed/pushed onto stack by program and popped off by OS
**Block and stack methods DO NOT limit number/length of parameters being passed**

### Types of System Calls
- **Process Control**
  - Create / Terminate Processes
  - Wait / Signal Events
  - Allocate / Free Memory
  - Debugger
  - Locks
  - Example
    - `fork()` to start new process, `exec()` to load system call, `exit()` to end


- **File Management**
  - Create / Delete / Open / Close / Read / Write Files


- **Device Management**
  - Request / Release Devices
  - Read / Write / Reposition
  - Get / Set Device Attributes


- **Information Maintenance**
  - Get / Set Time & Date
  - Get / Set System Data
  - Get / Set process, file, attributes


- **Communications**
  - Create / Delete Communication connections
  - Transfer status info
  - Interprocess communication
    - Message-Passing Model: exchange small data from client to server
    - Shared-Memory Model: inter-computer communication


- **Protection**
  - Get / Set Permissions
  - Allow / Deny user access


### System Programs
- File Management
- Status Information
- File Modification
- Programming-Language Support
- Program Loading & Execution
- Communications
- Background Services
- Application Programs

### OS Design & Implementation
- Highly creative task of software engineering
- Principles of designing OS
  - **Design Goals**
    - Define specifications (hardware, type of system)
    - User Goals: Convenient to use
    - Designers Goals: Easy to design and implement
  - **Separation of mechanism and policies**
    - Policy: What will be done?
    - Mechanism: How to do it?
  - **Implementation**
    - Used to use assembly (Now its a mix)
    - High level languages are easier to port to other hardware

### Simple Structure -- MS-DOS (OS Structure)
- Most functionality in the least space
- Not divided into modules
  - Not well separated
  - More vulnerable to malicious programs

### Traditional UNIX (OS Structure)
- Not simple but not fully layered
- Limited by hardware functionality
- Two parts
  - System Programs
  - Kernel

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/UNIX.png)

### Layered Approach
- Divided into layers (levels)
  - Each layer built on top of lower layers
  - Layer 0 = Hardware
  - Layer N = UI

### Microkernel System Structure
- Kernel keeps core stuff (essential stuff)
  - Non-essential stuff becomes system and user-level programs
- Communication happens via Message Passing Model
- Pros
  - Easy to extend Microkernel
  - Easy to port
  - More reliables (less code in kernel)
  - More secure
- Cons
  - Performance overhead of user space to kernel space communication

### Modules
- Lots of OS implement *Loadable Kernel Modules*
  - Uses OOP
  - Each core component separate
  - Each is loadable as needed
  - Each talks to others over known interfaces


- **Solaris Modular Approach**
  - Organized around a core kernel with seven types of loadable kernel modules

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Solaris.png)

### Hybrid Systems
- Combines multiple approaches to address
  - Performance
  - Security
  - Usability

### OS Debugging
- Finding / Fixing Bugs or Errors
- OS generates log files
- Failure of application generates core dump
  - Core dump captures memory of process
- OS failure generates crash dump
  - Crash Dump contains kernel memory

### Performance Tuning
- Improves performance by removing bottlenecks
- OS provides way to compute and display measures of system behavior

### Dtrace Tool
- Dynamically adds probes to a running system
- Probes are fired when code is executed within a provider
  - Captures state data and sending it to consumer of probes

### OS Generation
- `SYSGEN` = Program that obtains info about config of hardware system

---

<a name="Lecture3"></a>
## Lecture 3 - Processes
- A program in execution
- Process has multiple parts (not all code)
  - Text Section (Code)
  - Program Counter
  - Stack
    - Function parameters, return addressees, local variables
  - Data Section
    - Global variables
  - Heap
    - Contains dynamically allocated memory
- Program becomes process when the executable file is loaded into memory

### Process State
- As a process executes, changes state
- Types of States
  - New
  - Running
  - Waiting
  - Ready
  - Terminated

### Process Control Block (PCB)
- Each process represented in the OS by a PCB
- PCB contains
  - Process State
    - Ready, Running, Waiting
  - Program Counter
    - Location of Next Instruction
  - CPU Registers
    - Contents of all process-centric registers
  - CPU Scheduling Information
    - Priorities, Scheduling & Queue Pointers
  - Memory-Management Information
    - Memory allocated to the process
  - Accounting Information
    - Amount of CPU used, Clock time elapsed, process numbers
  - I/O Status Information
    - list of I/O devices allocated to the process

### CPU Switch from Process to Process


### Threads
- Process performs a single thread of execution
- OS's allow for multiple threads
- PCB can be expanded to include info about each thread

### Process Scheduling
- Objective of Multiprogramming is to have some process running at all times
  - Maximizes CPU utilization
- Objective of Time sharing is to switch CPU among processes
- Scheduler
  - Selects among available processes for next execution
  - Maintains scheduling queues of processes
  - Types of Queues
    - Job Queue: All processes in the system
    - Ready Queue: All processes in main memory that are waiting to execute
    - Device Queue: Set of processes waiting for I/O Device

### Queueing Diagram
- Representation of Process Scheduling
- Legend
  - Rectangle = Queue
  - Circle = Resources serving the queue
  - Arrow = Flow of processes
- Process
  - New process put in ready queue
  - Waits until selected for execution
  - While waiting process can
    - Issue I/O Request and move to I/O Queue
    - Create new child process & wait for its termination
    - Be removed from CPU due to interrupt


![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Queue_Diagram.png)

### Schedulers
- Short Term ( CPU Scheduler )
  - Selects which process to execute next from the ready queue
  - Invoked frequently (milliseconds)
- Long Term ( Job Scheduler )
  - Selects which processes should be brought into ready queue
  - Invoked infrequently (minutes)
  - Controls degree of multiprogramming
- Either...
  - I/O Bound Process
    - Spends more time doing I/O
  - CPU Bound Process
    - Spends more time doing computations
- **Long term scheduler should select a good process mix of I/O and CPU bound**
- Some times intermediate level of scheduling
  - Medium Term Scheduler
    - Added if degree of multiple programming needs to decrease
    - Remove process from memory, store it to disk and bring it back
    - Swapping is necessary to improve the process mix

### Context Switch
- When CPU switches processes
  - System saves the state of old process and loads saved state for new process via **Context Switch**
- Context of a process is represented by PCB
- Context-switch time is an overhead, cannot do useful work while switching
- Time increases as the complexity of context-switch increases

### Process Creation
- Parent process create children processes
  - Children create other processes, forms a tree of processes
  - Node is parent, leaves are children
- Process identified and managed via PID (Process Identifier)
- `fork()` returns  0 for child and nonzero for parent

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Tree.png)

- **Resource Sharing Options**
  - Child process may get it from OS
  - Can also share subset of parent's resources
    - This prevents overloading


- **Execution Options**
  - Parent continues to execute with children
  - OR Parent waits until children terminate

- **Address Space Options**
  - Child process is duplicate of parent
  - Child process loads a new program

### Process Termination
- `exit()` deletes process
  - Returns status data from child to parent (via `wait()`)
- Parent can use `abort()` to end child without waiting if
  - Exceeds resources
  - Not needed
  - Need to terminate so parent can terminate
- **Cascading Termination**
  - Terminate all childs when parent is terminated
- When process terminates, resources are deallocated by OS
  - But entry in process table there until parent calls wait()
- If parent does not `wait()`
  - Zombie Process
- If parent terminates without `wait()`
  - Orphan Process
  - Init becomes parent and issues `wait()` to clear orphans

### Interprocess Communication
- Independent processes are not affected by the execution of another
- Cooperating processes can be affected though

### Shared Memory Systems
- Area of memory shared among processes that want to communicate
- Under control of user
  - Need System call too establish shared memory regions
- **Produce Consumer Problem**
  - Producer process produces info that is consumed by consumer process
  - Need a buffer that can be filled by producer and emptied by consumer
  - 2 Types of Buffers
    - **Unbounded**: No Limit on Buffer Size
      - May have to wait for new items, but can always add more
    - **Bounded**: Fixed Buffer Size
      - Customer needs to wait if buffer empty and producer wait if buffer full
      - Implemented as a circular array (ends are marked as *in* and *out*)
      - *in*  = next free position in buffer
      - *out* = first full position in buffer

### Message Passing Systems
- Provided by OS for processes to communicate and sync actions without sharing same address space
- Good for distributed system (chat system)
- Process
  - If P & Q (processes) want to communicated
  - Need to establish communication link
  - Exchange messages via send/receive operations
- Implementation
  - Physical
    - Shared Memory
    - Hardware Bus
    - Network
  - Logical Issues
    - Direct or Indirect communication
    - Synchronous or Asynchronous communication
    - Automatic or Explicit Buffering


- **To solves the issues, OS needs mechanism for naming processes, synching actions and buffering**
  - Naming: Processes need to refer to each other
  - Direct Communication: Processes name each other explicitly
    - Links are established automatically
    - Only need ID to communicate
  - Indirect Communication: Messages are sent and received from mailboxes/ports
    - Processes need common mailbox
    - Can be associated with many processes

#### Indirect Communication (In Depth)
- OS needs to allow creating/deleting of mailbox
- Sending and Receiving messages through it
- Mailbox Sharing
  - If P1 sends message and P2/P3 both share mailbox, who gets it?
  - 3 options
      - Round Robin
      - Allow link to max out at connecting 2 processes
      - Allow only one process to receive at a time

#### Synchronization
- Can be blocking or non-blocking
- Blocking = Synchronous
  - Sender blocked until message received
  - Receiver blocked until message available
- Non-Blocking = Asynchronous
  - Send message and continue
  - Receiver gets valid/null message

#### Buffering
- 3 ways
  - **Zero Capacity:** No messages are queued on a link
    - Sender must wait for receiver to get message
  - **Bounded Capacity**: Queue has finite length of n messages
    - Sender must wait if link is full
  - **Unbounded Capacity**: Queue with infinite length
    - Sender never waits

### Sockets
- Endpoint for communication
- Identified by IP Address + Port
- Ports below 1024 are well known, used for standard services
  - Ports > 1024 are used for sockets and stuff
- Client-Server Architecture
  - Listen on port for client requests

### Remote Procedure Calls (RPC)
- Allows client to invoke procedure on remote host as it would do it locally
- Hides details about communication and provides client side with stub
  - When remote procedure is invoked, RPC calls the appropriate stub
  - Client Side stub locates server and *marshalls* parameters
  - Server Side stub receives the message, unpacks it and performs procedure

### Pipes
- Allows two processes to communicate
- 4 Issues
  - Unidirectional or Bidirectional
  - Half or Full Duplex
  - Need of parent-child relationship?
  - Can pipes be used over network?
- 2 Common Types
  - Ordinary: Cannot be accessed from outside the process that created it
  - Named: Accessed without parent-child relationship

#### Ordinary Pipes
- Producer-Consumer Style
  - Produces writes to one end (write end)
  - Consumer reads from other end (read end)
- Unidirectional
- For two way communication need 2 pipes
- Need Parent-Child relationship

#### Named Pipes
- Bidirectional
- No parent-child relationship
- **ON UNIX**
  - Called FIFOs
  - Exist until explicitly deleted
  - Only communicate with same machine
- **ON WINDOWS**
  - Full Duplex
  - Can communicate with same or other machines
----

<a name="Lecture4"></a>
## Lecture 4 - Threads
- Basic unit of CPU utilization
- Consists of
  - Thread ID
  - Program Counter
  - Register set
  - Stack
- Shares the following with other threads belonging to same process
  - Code Section
  - Data Section

### Process vs Thread
|Process|Thread|
|-------|------|
|Process is heavy weight or resource intensive.|Thread is light weight taking lesser resources than a process.|
|Generally, more than one process cannot share the same memory. Sharing memory among processes requires additional memory management schemes.| Threads of the same process can share the same memory unless they are specially allotted separate memory locations.|
|Process creation, process execution, and process switch are time consuming.| Thread creation, thread execution, and thread switch are much faster in comparison.|
|Processes are generally loosely coupled and so a lesser amount of resource sharing is possible.| As the threads of a process are tightly coupled; a greater amount of resource sharing is possible.|
|Communication between processes is difficult and requires system calls.| Communication between threads is much easier and more efficient.|


### Multithreaded Server Architecture
- Single application might need to perform several similar tasks from different clients requests
  - Can use multithreading to create a thread to listen to requests
  - When request received, create threat to handle it rather than a process
- Pros
  - Responsiveness
    - Might still allow thread to run even if part of process is blocked
  - Resource Sharing
    - Easier to share resource from one process instead of between processes
  - Economy
    - Cheaper than process creation, less overhead
  - Scalability
    - Can take advantage of multiprocessor
    - Threads can run in parallel

### Concurrency vs Parallelism
- Concurrency
  - Uses time sharing to allow more than one task to make progress
  - Seems like parallelism, but not really cause just switching between processes really fast
- Parallelism
  - Threads run in parallel
  - Types
    - Data Parallelism
      - Distributes subsets of data across multiple cores, and doing same operation on each core
      - Example: Sum half of array on each core
    - Task Parallelism
      - Distributing threads across cores, each one doing different operation
      - Example: Sum elements on one, find max on another

### Amdahl's Law
- S = Serial Portion %
- N = Number of processing cores

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Amdahl.png)

- If application is 75% serial, 25% serial moving from 1 core to 2 will speedup the results by 1.6 times


### User Threads & Kernel Threads
- User
  - Management done by user-level threads library
  - 3 Libraries: POSIX Pthreads, Windows threads, Java threads
  - Pros
    - Thread switching does not need Kernel mode privileges
    - User level thread can run on any OS
    - Faster to create and manage
  - Cons
    - Most system calls are blocking
    - Cannot take advantage of multiprocessing


- Kernel
  - OS Managed Threads
  - Supported by most OS's
  - Pros
    - Schedule multiple threads from same process on multiple processors at the same time
    - If one thread blocked, can schedule another
    - Kernel routines can be multithreaded
  - Cons
    - Slower to create and manage
    - Transfer of thread control requires mode switch

### Many to One Model
- Many user-level threads mapped to a single kernel thread
- One thread blocking, blocks all
- Cant run in parallel because only one may be in kernel at a time


### One to One Model
- Each user-level thread maps to one kernel thread
- Supports running threads in parallel
- Bad because creating a user-level thread needs kernel thread to be created
  - Overhead of creating kernel threads


### Many to Many Model
- Allows many user-level threads to be multiplexed to a smaller or equal amount of kernel threads
- OS can create sufficient number of kernel threads
- Developers can create s many user threads as necessary and the kernel threads can run in parallels

### Two Level Model
- Same as Many to Many, but
  - Allows user thread to be bound to kernel thread

### Thread Library
- Gives developers API for managing threads


- 2 Primary ways to implement thread library
  - Provide a library without kernel support
    - Everything exists in user space
    - No system calls for access
  - Implement kernel-level library supported by OS
    - Everything in kernel space
    - Need system calls for access


- 3 Main Libraries
  - POSIX Pthreads
    - Can be user or kernel
  - Windows threads
    - Kernel Library
  - Java threads
    - Managed in java programs
**For POSIX and Windows, global variables are shared among threads in same process**


- 2 Main strategies for creating multiple threads
  - Asynchronous Threading
    - Once parent creates child thread, parent does own stuff and doesnt care when child terminates
  - Synchronous Threading
    - Parent creates one or more children and wait for child termination to continue
    - Fork-Join strategy

### Pthreads
- User-level or Kernel-level
- POSIX API for thread creation and synchronization

### Java Threads
- Managed by JVM (Java Virtual Machine)
- Created by
  - Extending Thread class and overriding `run()`
  - Define class implementing Runnable

### Implicit Threading
- Transfer management of threads to compilers and run-time libraries instead of programmers
- 3 Methods
  - Thread Pool
  - OpenMP
  - Grand Central Dispatch

### Thread Pools
- Create a bunch of threads at start-up and put them in a pool
- When a request comes in, get a thread from the pool and use it
- When done put it back in the pool

### Semantics of fork() and exec()
- Will `fork()` duplicate one thread or all
- 2 options
  - If `exec()` is called after forking then duplicate only the calling thread
  - If process does not call `exec()` after forking then should duplicate all threads

### Signal Handling
- Signal generated by event
- Delivered to a process
- Handled by one of the following
  - Default Signal Handler
  - User-Defined Signal Handler
- For single thread, signal delivered to process
- For multi-threaded process
  - Send to the thread where it applies
  - Divide by 0 goes to thread that caused it
  - Ctrl C goes to all

### Thread Cancellation
- Terminating before completion
- Asynchronous terminates immediately
- Deferred cancellation allows thread to check a flag if it should be cancelled and only cancel if flag is true

### Thread-Local Storage
- Threads belonging to process share process data
- TLS (Thread Local Storage) allows each thread to have own copy of data
  - Different from local variables
  - Similar to static data
---

<a name="Lecture5"></a>
## Lecture 5 - Process Synchronization









---
