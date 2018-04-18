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
<br>
[Lecture 6 - CPU Scheduling](#Lecture6)
<br>
[Lecture 7 - Deadlocks](#Lecture7)
<br>
[Lecture 8 - Main Memory](#Lecture8)
<br>
[Lecture 9 - Virtual Memory](#Lecture9)
<br>
[Lecture 10 - File System Interface](#Lecture10)
<br>
[Lecture 11 - File System Implementation](#Lecture11)


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
- **Cooperating Process**: Can affect or be affected by other processes in the system
- Processes can execute concurrently or in parallel
  - Might be interrupted: ending in partial execution
  - Concurrent data sharing may cause inconsistencies

### Race Condition
- Two processes try to change the value of the data at the same time
- Can not know for sure which one changed first because scheduler keeps swapping processes

### Critical Section
- Each process has a critical section of code
  - During this stage, no other processes are allowed to be in its critical section
  - Example: When changing common variables, updating table, writing file
- Design a protocol to solve this issue s
  - Each process needs to request to enter its critical section

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Critical.png)

- **Solution must satisfy the following**
- `Mutual Exclusion`
  - No other processes can execute critical section while one already is
- `Progress`
  - If nobody executing critical section then processes that are not in remainder stage can participate in the decision on which one will do the critical section next
- `Bounded Waiting`
  - Bound must exist on number of time other processes can enter critical sections after a process has made a request to enter critical section

- **Critical Section Handling in OS**
- 2 approaches
  - `Preemptive Kernel`
    - Allows preemption of process when running in kernel mode
  - `Non-Preemptive Kernel`
    - Process runs until it exits kernel mode, blocks, voluntarily yields
- Preemptive kernel is more responsive, less risk

### Peterson's Solution
- Software based solution to the critical-section problem
- Restricted to two processes that alternate execution between critical sections
- Have `turn` and `flag[]` variables
  - P(i) has a turn value i
  - If flag[turn] is true then P(i) is ready

![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/Peterson.png)

### Synchronization Hardware
- Hardware support for the critical section code is provided via locks
- The critical-section problem is easily solved in a single-processor system
  - Single processor can disable interrupt after entering critical section
- For multi-processor, because message has to be sent to ALL processors it is not efficient
- **Atomic Hardware Instructions**: Non-interruptible.
  - If two executed same time, will end up in sequential order (arbitrary)
  - This will help avoid the critical section problem
- Instructions
  - `Test & Set` the content of a memory word
  - `Compare & Swap` the contents of two memory words atomically

#### Test & Set
- Executed atomically
- Returns original value of passed parameter
- Sets new value of passed parameter to true
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/defSet.png)
- After critical section passed, set `lock` variable to false to satisfy mutual exclusion
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/teste.png)

#### Compare & Swap
- Executed atomically
- Returns original value of passed parameter
- IF expected value is received, THEN set new value of passed parameter
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/defSwap.png)
- `lock` variable set to 0
  - Satisfies mutual exclusion because sets `lock = 1` to prevent entry to critical section
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/swape.png)

#### Bounded-Waiting & Mutual Exclusion
- The above examples do not satisfy the bounded-waiting requirement
- The following algorithm uses the `test_and_set()` instruction that satisfies all the critical-section requirements
- To meet the bounded waiting requirement, there is a waiting array so that processes waiting will enter the critical section within `n-1` turns
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/bounD.png)

### Mutex Locks
- The previous solutions are complicated and inaccessible to application programmers
- A better solution is **Mutex Lock** (Mutual Exclusion Lock)
  - Lock has a boolean variable
  - Used to protect critical regions and prevent race conditions
  - A process must `acquire()` lock before critical and `release()` after critical
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/muteX.png)  
- `acquire()` and `release()` need to be atomic so are implemented as hardware mechanisms mostly
- It is called a **Spinlock** due to busy waiting times while trying to acquire the lock

### Semaphores
- Synchronization tool that provides better ways (> Mutex Locks) for process to sync activities
- It is an `int` variable that can be accessed via 2 atomic operations
  - `wait()`
  - `signal()`
- One process modifies semaphore at a time
- **Counting Semaphore**
  - Initialized to No. of Resources
  - Want to use resource? = `wait()` = `count --;`
  - Done using resource? = `signal()` = `count ++;`
  - `if count(==0)` wait until `count > 0` because all resources being used
- **Binary Semaphore**
  - Domain is between 0 and 1
  - Used like a mutex lock for mutual exclusion
- **Synchronization**
  - To ensure one statement executed after another can do the following
  - S2 only executed after because have to wait for `signal(synch)` to be invoked
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/synch.png)

#### Semaphore without Busy Waiting
- Every semaphore has an integer value and a waiting queue
- If Semaphore value less than 0, add the process trying to access it in the queue
- If Semaphore value greater than 0, remove it from the waiting queue and put it in the ready queue
- Implemented using
  - `block()`: places process in waiting queue
  - `wakeup()`: removes from waiting queue and puts in ready queue
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/semasem.png)

#### Deadlock & Starvation
- **Deadlock**: >=2 processes are waiting indefinitely for an event from the other processes
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/deadass.png)

- **Starvation** (Indefinite Blocking): A process may never be removed from the semaphore queue
  - Another problem with deadlocks

#### Priority Inversion
- Lower priority process holds a lock needed by a higher priority process
- Solved by **priority-inheritance protocol**
  - A process that is using a resource needed by a higher-priority process will inherit its priority until it is finished with the resource

### Bounded Buffer Problem
- Variables
  - `int n` buffers
  - `semaphore mutex = 1` mutual exclusion
  - `semaphore empty = n` n empty buffers
  - `semaphore full = 0` 0 full buffers
- The problem is if we have a producer and a consumer we don't want the producer producing items to a full buffer and customer consuming items from an empty buffer
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/proco.png)

### Readers-Writer Problem
- A common database with a reading specific process and writing specific process
  - When both accessed at the same time may lead to unexpected results

- **First Problem - Readers Preference**
  - No readers should be kept waiting unless a writer has permission to modify the database
  - No point in Reader1 waiting for Reader2
  - Readers may starve
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/read1.png)
- `rw_mutex` used by first or last reader that enters/exits the critical section
- If a writer is in critical and `n` readers waiting then one reader is put on `rw_mutex` and rest on `mutex` (mutual exclusion ^)

- **Second Problem - Writers Preference**
  - No writers should be kept waiting longer than necessary once added to the queue
  - Reader2 shouldn't jump ahead of Writer while it is waiting
  - Writers may starve

### Dining Philosophers Problem
- One bowl of rice
- One chopstick between each philosopher
- Taking chopsticks should be the critical section
- Avoid Deadlocks
  - Allow at max 4 (for the diagram below)
  - Only pickup if both chopsticks available
  - `Odd #` picks up left > right
  - `Even #` picks up right > left

### Semaphore Summary
- Correct oder is `wait(mutex)` *critical section* `signal(mutex)`
- Deadlock caused by `wait(mutex)` *critical section* `wait(mutex)`

### Monitors
- Monitor type is an ADT used process synchronization
- One process active within a monitor at a time
- Not powerful enough to model all synchronization schemes
  - Need to define synchronization mechanisms provided by **Condition Construct**

#### Condition Construct
- Variables of type condition `condition x, y;`
- Only `wait()` & `signal()` are allowed on condition variables
- `x.wait()` waits until `x.signal()` invoked and when it is invoked, it resumes exactly one process that was suspended by `x.wait()`.
- If `x.signal()` called and no suspended process then nothing happens

#### Condition Variable Choices
- Process P1 invokes `x.signal()` and Process P2 is suspended in the `x.wait()`
  - They cannot run in parallel
- SO one of the processes have to either
  - Leave the monitor
  - Wait for another condition

#### Dining Philosophers Solution w/ Monitors
- 3 States
  - Thinking
  - Hungry
  - Eating
- Can only pickup chopsticks if both available so
  - Can only pickup if neighbors are not in eating state
- If hungry and cannot eat, add delay and put in queue
- Each philosopher needs to `pickup()` eat then `putdown()`

#### Resuming Processes within a Monitor
- If lots of suspended processes, which one should be resumed first?
  - **FCFC** First come First server is not enough in most cases
- Implement **Conditional-Wait** by doing `x.wait(c)`
  - `c` is a priority number (low num = high priority)
- Highest priority comes back first

#### Single Resource Allocation
- Allocate single resource using max-time limitations
  - Specify max-time a process plans to use a resource

### Linux Synchronization
- Version 2.6 and later fully preemptive kernel
  - **Preemptive**: Temporarily interrupting a task without cooperation & with intent to resume it at a later time
- Atomic Integers
```
atomic_t counter;
int value;
atomic_set(&counter,5); /* counter = 5 */
atomic_add(10, &counter); /* counter = counter + 10 */
atomic_sub(4, &counter); /* counter = counter - 4 */
atomic_inc(&counter); /* counter = counter + 1 */
value = atomic_read(&counter); /* value = 12 */
```

- Mutex Locks
  - `mutex_lock()`
  - `mutex_unlock()`

- Semaphores, Spinlocks (replaced by enable/disable kernel preemption)
  - `preempt_disable()`
  - `preempt_enable()`
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/linuxEE.png)
---


<a name="Lecture6"></a>
## Lecture 6 - CPU Scheduling
- Maximum CPU Utilization obtained with multiprogramming
  - Lots of processes kept in memory at the same time
  - When one process is waiting, another process will use the CPU
- **CPU-I/O** Burst Cycle
  - CPU Execution (CPU Burst)
  - I/O Wait (I/O Burst)
- CPU Burst distribution is the main concern
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/burstC.png)

- I/O Bound program has many short CPU bursts
- CPU Bound program might have a few long CPU bursts

### CPU Scheduler
- **Short Term Scheduler**: Selects processes from ready queue and allocates CPU to one of them, while CPU is idle

### Preemptive Scheduling
- Scheduling decisions happen in the following situations
  1. When a process switches from running to waiting state (**Cooperative**)
    - Waiting for I/O request or during `wait()` for child process termination

  2. When a process switches from running to ready state (**Preemptive**)
    - Due to an interrupt

  3. When a process switches from waiting to ready (**Preemptive**)
    - When it finishes an I/O operation

  4. When a process terminates (**Cooperative**)

- **Preemptive Scheduling**
  - There is a choice in scheduling
  - Can cause race conditions if a processes served is preempted (not completely finished)
- **Cooperative Scheduling**
  - There is no choice in scheduling
  - Once CPU has been allocated to process, process will keep until switch to waiting state or terminated
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/schedSit.png)


### Dispatcher
- Gives control of CPU to process selected by short-term scheduler, this involves:
  - Switching context
  - Switching to user mode
  - Jumping to the proper location in user program to restart that program
- Dispatcher needs to be really fast because used for EVERY process switch
  - **Dispatch Latency**: Time it takes for the dispatcher to stop one process and start running another

### Scheduling Criteria
- **CPU Utilization**: Keep CPU as busy as possible (irl 40%-90%)
- **Throughput**: Number of processes that complete their execution per unit time
- **Turnaround Time**: Time taken to execute a process
  - Sum of periods spent (Getting into Memory + Waiting in the ready queue)
- **Waiting Time**: Time a process spends waiting in the ready queue
- **Response Time**: Time from request submission to first response
- To optimize Scheduling Algorithms want to
  - `Max` CPU Utilization
  - `Max` Throughput
  - `Min` Turnaround Time
  - `Min` Waiting Time
  - `Min` Response Time
- Basically
  - **Maximize CPU usage and number of processes being executed while minimizing execution, wait and response times**

### First-Come, First-Served (FCFS) Scheduling
- First process to request the CPU gets allocated the CPU first
- Implemented with a FIFO queue
- Waiting time on average is pretty long
- Example

|Process|Burst Time (ms)|
|-------|---------------|
| P<sub>1</sub>| 24 |
| P<sub>2</sub>| 3 |
| P<sub>3</sub>| 3 |

- Gantt Chart looks like the following
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/gantTC.png)
- Average waiting time is longer because shorter processes are queued up behind a long process, if it was the opposite, waiting time would be a lot shorter
- **Convoy Effect**: When short processes are waiting behind long processes

### Shortest-Job-First (SJF) Scheduling
- Dependent on length of **next CPU burst**
- FCFS is tie breaker for processes with same length
- Minimum Average waiting time
- Complex part is getting the length of next CPU request
  - Can estimate by using previous CPU burst lengths
    1. t<sub>n</sub> = actual length of n<sup>th</sup> CPU burst
    2. τ<sub>n+1</sub> = predicted value for the next CPU burst
    3. α, 0 <= α <= 1 *(Commonly set to 1/2)*
      - If α = 0, Recent history does not count, So τ<sub>n+1</sub> = τ<sub>n+</sub>
      - If α = 1, Only the actual last CPU burst counts, So τ<sub>n+1</sub> = ατ<sub>n</sub>
    4. τ<sub>n+1</sub> = αt<sub>n</sub> + (1-α)t<sub>n</sub>
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/predIk.png)  
- **Preemptive**
  - Shortest-Remaining-Time-First
  - If a new process comes with a burst length less than remaining time of current process then preempt it
- **Non-Preemptive**
  - Once CPU is given to process, can't be preempted until burst complete
- **Preemptive vs Non-Preemptive**
  - Example

|Process|Arrival Time (ms)| Burst Time (ms)|
|-------|-----------------|----------------|
| P<sub>1</sub>| 0 | 8 |
| P<sub>2</sub>| 1 | 4 |
| P<sub>3</sub>| 2 | 9 |
| P<sub>4</sub>| 3 | 5 |

- Gantt Chart for Preemptive
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/preeG.png)
- Gantt Chart for Non-Preemptive
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/NpreeG.png)


### Priority Scheduling
- Priority number associated with each process
- CPU allocated to process with highest priority
  - Smallest integer = highest priority
- Priorities can be defined internally or externally
  - **Internally**: Set by OS
    - Time limits
    - Memory Requirements
    - Number of open files
  - **Externally**: Set by criteria outside OS
    - Importance of process
    - Political factors
- Can also be preemptive or non-preemptive
  - Will be preempt if priority of newly arriving process is higher
- May lead to starvation (low priority process may never execute)
  - **Aging**: Gradually increase the priority of waiting processes
- Example ( All of them arrived at time 0)

|Process|Burst Time (ms)|Priority|
|-------|---------------|-------|
| P<sub>1</sub>| 10 | 3 |
| P<sub>2</sub>| 1 | 1 |
| P<sub>3</sub>| 2 | 4 |
| P<sub>4</sub>| 1 | 5 |
| P<sub>4</sub>| 5 | 2 |

- Gantt Chart is as follows
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/PSG.png)

### Round Robin
- Designed especially for time sharing systems
- Each process gets a small amount of CPU time (time quantum `q`)
  - For `n` processes, each process gets `1/n` of the CPU time in chunks of `q` time units at most
- If `q` is large: FCFS
- If `q` is small: high overhead (too many context switches)

- Example with Time Quantum = 4

|Process|Burst Time (ms)|
|-------|---------------|
| P<sub>1</sub>| 24 |
| P<sub>2</sub>| 3 |
| P<sub>3</sub>| 3 |
- Gantt Chart is as follows
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/RRP.png)

### Multilevel Queue Scheduling
- Used when processes can be classified into different groups
- Ready queue is separated into
  - **Foreground** (Interactive Processes)
    - Round Robin Scheduling
  - **Background** (Batch Processes)
    - FCFS Scheduling
- Processes are permanently assigned to one of the two queues
  - Based on properties of the process
  - Memory Size, Priority, Type etc
- **Fixed Priority Scheduling**
  - Server all from foreground queue then background
  - Starvation because low priority queue wont server until higher is empty
- **Time Slice**
  - Each queue gets a chunk of CPU time which it can schedule amongst processes
  - 80% Foreground in RR
  - 20% Background in FCFS

### Multilevel Feedback Queue Scheduling
- Allows process to move between queues
  - Allows for aging processes
- This scheduler defined by the following parameters
  - Number of queues
  - Scheduling algorithm for each queue
  - Method to upgrade process to higher queue
  - Method to demote a process to lower queue
  - Method to determine which queue a process will enter
- Example
  - `Q0` - RR with quantum 8 ms
  - `Q1` - RR with quantum 16 ms
  - `Q2` - FCFS
- When a new process comes it gets 8ms with RR in Q0
- If it doesn't finish in that time, move to Q1 with RR 16ms
- If it doesn't finish in that time either, move to Q2 with FCFS so it can finish

### Thread Scheduling
- Can be **user-level** or **kernel-level**
- **Process Contention Scope (PCS)**
  - Schedule user-level threads to run on available Lightweight Processes (LWP)
  - Competition for CPU takes place among threads from same process
  - Done by priority (set by programmer)
- **System Contention Scope (SCS)**
  - Decides which kernel-level thread to schedule
  - Competition among all threads in system

### Pthread Scheduling
- `PTHREAD_SCOPE_PROCESS`
  - Schedules threads using PCS
- `PTHREAD_SCOPE_SYSTEM`
  - Schedules threads using SCS
- Pthread Scheduling API
  - Determines existing contention scope and sets it to `PTHREAD_SCOPE_SYSTEM`
  - Creates 5 different threads that run using SCS

```C
#include <pthread.h>
#include <stdio.h>
#define NUM_THREADS 5

int main(int argc, char *argv[]) {
  int i, scope;
  pthread_t tid[NUM_THREADS];
  pthread_attr_t attr;

  /* get the default attributes */
  pthread_attr_init(&attr);

  /* first inquire on the current scope */
  if (pthread_attr_getscope(&attr, &scope) != 0)
    fprintf(stderr, "Unable to get scheduling scope\n");
  else {
    if (scope == PTHREAD_SCOPE_PROCESS)
      printf("PTHREAD_SCOPE_PROCESS");
    else if (scope == PTHREAD_SCOPE_SYSTEM)
      printf("PTHREAD_SCOPE_SYSTEM");
  else
    fprintf(stderr, "Illegal scope value.\n");
  }

  /* set the scheduling algorithm to PCS or SCS */
  pthread_attr_setscope(&attr, PTHREAD_SCOPE_SYSTEM);

  /* create the threads */
  for (i = 0; i < NUM_THREADS; i++)
    pthread_create(&tid[i],&attr, runner, NULL);

  /* now join on each thread */
  for (i = 0; i < NUM_THREADS; i++)
    pthread_join(tid[i], NULL);
}

/* Each thread will begin control in this function */
void *runner(void *param) {
  /* do some work ... */
  pthread_exit(0);
}
```

**

### Multiple-Processor Scheduling
- CPU scheduling complexity increases when there are more CPUs
- Even if processors are homogeneous
  - A system with an I/O device attached to a private bus of one process
  - Other processes that want to use it must be scheduled to run on that processor
- **Asymmetric Multiprocessing**
  - All scheduling handled by a single processor
- **Symmetric Multiprocessing (SMP)**
  - Each processor is self-scheduling
  - Can have common ready queue or private ready queue per processor

### Issues with Multiple-Processor Scheduling
- **Processor Affinity**: Keeps a process running on the same processor that it was before
  - A process has an affinity for the processor it is in running on
  - If it needs to migrate then old cache needs to be cleared and new one repopulated which has a high cost
  - 2 types of Affinity
    - **Soft Affinity**
      - OS tries to keep a process on the same processor bu no guarantee to keep it this way
    - **hard Affinity**
      - OS allows a process to specify a subset of processor on which it can run
      - `sched_setaffinity()`

- **NUMA & CPU Scheduling**
  - Non-Uniform Memory Access
  - Faster access to some memory vs others
  - More memory boards

- **Load Balancing**
  - If Symmetric Multiprocessing is used all the CPUs need to be loaded for efficiency
  - Load Balancing tries to distribute workload across processors
  - Only necessary when private ready queues are being used
  - **Push Migration**
    - Checks load on all processors and if there is imbalance, push process from busy to less busy processors
  - **Pull Migration**
    - Idle processor pulls a waiting task from a busy processor
  - **Push and Pull are often implemented in parallel**

- **Multicore Processors**
  - Recent trend is to place multiple processors on same chip
  - Faster and consumes less power than multiple processors
- Takes advantage of memory stall to make progress on another thread while memory is being retrieved
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/mmPP.png)

### Algorithm Evaluation
- **Deterministic Modeling**
  - Takes predetermined workload and defines performance of each algorithm for that workload

- **Queueing Network Analysis**
  - `n` average queue length
  - `W` average waiting time in queue
  - `λ` average arrival rate into queue
  - Littles Law - Processes leaving queue must equal processes arriving
    - `n = λW`
    - *If on average 7 processes arrive per second, and normally 14 processes in queue then average wait time per process is 2 seconds*

- **Simulations**
  - More accurate than Queueing Models
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/simEval.png)

- **Implementation**
  - Implement new scheduler and test in real systems
    - High Cost, High Risk
    - Environments may vary

----

<a name="Lecture7"></a>
## Lecture 7 - Deadlocks



----



<a name="Lecture8"></a>
## Lecture 8 - Main Memory



----



<a name="Lecture9"></a>
## Lecture 9 - Virtual Memory



----



<a name="Lecture10"></a>
## Lecture 10 - File System Interface
- **File System**: Mechanism for storage and access to both data and programs
  - **Files**: Each storing related data
    - Data Files: Numeric, Character, Binary
    - Program Files: Source, Object, Executable
  - **Directory Structure**: Organize and provide information about all the files in the system
    - Stores file name and identifier which is used to locate rest of attributes

### File Attributes
- **Name**: The only human-readable information (text)
- **Identifier**: Unique tag (number)
- **Type**: Needed for systems that support different types of files
- **Location**: Pointer to the file location on device
- **Size**: Current file size in bytes/words/blocks
- **Protection**: Controls determine who can read, write, execute
- **Time, Date, User Identification**: Info may be kept for creation/modification date

### File Operations
- **Create**
- **Write**
  - Start writing at the write pointer
- **Read**
  - Start reading at the read pointer (same pointer for read/write)
- **Reposition**
  - Current file position pointer is given a new value
- **Delete**
  - Erases file, release file space
- **Truncate**
  - Keep file attributes, set size to 0, release file space
- `Open(Fi)`
  - Search directory for entry Fi and move content to memory (open-file table)
- `Close(Fi)`
  - Move content from memory (open-file table) to directory on disk

- First time a file is opened by a process
- Puts into system-wide table and then each process that uses it gets a pointer to it in its own open-file table

#### Open Files
- **Open File Table**
  - One table for each process to track its opened files
  - Pointer to system-wide table
  - Current File Position Pointer to the last read/write location
- **File Open Count**: Counter, for how many times file is opened
- **Disk Location of the file**: Data needed to locate file, ease of memory access  
- **Access Rights**: Access mode information per process

#### Locking
- **Shared Lock**: Several processes can acquire it concurrently (reading)
- **Exclusive Lock**: Only one process at a time (writing)
- **Mandatory Locking**: Access denied to a resource if process already acquired its advisory lock
- **Advisory Locking**: Process can find status of locks and then decide what to do

### Linux Commands

``` sh
mkdir dirname       # Create directory
rmdir dirname       # Remove directory
mv data newdata/    # Move data to new directory and delete old one
cp data newdata/    # Copy data to new directory
ls                  # Lists files
pwd                 # Print working directory
cd                  # Changes directories
rm data             # Deletes file within current directory
find                # Finds
whereis             # Locates stuff like binary source files
grep                # Filters text
touch               # Update last modified date, create if not exists
tar                 # Combine files/directories

```

### File Types
- `name.extension`
- Uses extension to indicate type of file
  - Lets OS know what operations can be done on it
- Files have `creator` attributes
  - Name of program that created it

### File Structure
- UNIX considers files to a be a sequence of 8-bit bytes
  - Each application needs to have code to interpret input files of appropriate structures
- All OS's must support executable files

### Access Methods
- **Sequential Access**
  - **Tape Drive Model**
  - Records are processed one after the other
  - `Read_next`: Reads next portion and advance pointer
  - `Write_next`: Appends to end of file and advance pointer to end of newly written text
  - `Reset`: Reset file to the beginning

- **Direct Access**
  - **Disk Model**
  - File is made of a numbered sequence of fixed length logical records
  - `read(n)`: Read block `n`
  - `write(n)`: Write block `n`
  - `n`: Relative block number from start of file
  - Keep a `cp` variable for current position

- **Other Methods**
  - Most other techniques involve creation of an index for the file
  - Keep index in memory to determine location faster
  - If index file too large, index the index file

### Disk Structure
- Disks can be subdivided into partitions
  - Partitions a.k.a minidisks, slices
- Disks can be RAID protected against failure
- Disk can be used raw without a file system
  - Or formatted with a file system
- Entities containing file system is known as a volume
- Volumes contain information about device directory
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/fileZ.png)

### Types of File Systems
- We usually look at general-purpose file systems
- **Solaris has many**
  - `tmpfs`: Temp memory-based volatile file system for fast I/O
  - `objfs`: Virtual file system which is an interface to the kernel memory to get kernel symbols for debugging
  - `ctfs`:  Contract File System for managing daemons
  - `lofs`: Loopback file system allows one file system to be accessed in place of another
  - `procfs`: Kernel interface to process structure
  - `ufs`, `zfs`: General purpose file systems

### Directory
- Collection of nodes with info about all files
- Organized to obtain
  - **Efficiency**: Locate file quickly
  - **Naming**: Convenient Naming
    - Same file, different names
    - Different users, same name for different files
  - **Grouping**
    - Group by properties

#### Single Level Directory
- All files in the same directory
- Single directory for all users
  - Limitation when No. of files increase or users increase
- Since only 1 directory, must have unique names

### Two Level Directory
- Each user gets their own single level directory
- **User File Directory (UFD)**
  - Separate directory per user
- **Master File Directory (MFD)**
  - Indexed by user's name
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/MUFD.png)

### Tree Structured Directory
- Users are able to create their own subdirectories to organize their files
- All directories have same internal format
  - One bit in each directory defines the entry type as
    - `file(0)`
    - `subdirectory(1)`
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/treeDP.png)





----



<a name="Lecture11"></a>
## Lecture 11 - File System Implementation



----
