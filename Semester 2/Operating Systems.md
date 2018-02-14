# Operating Systems


## Table of Contents

[Lecture 1 - Introduction to OS](#Lecture1)
<br>
[Lecture 2 - Operating-System Structures](#Lecture2)
<br>
[Lecture 3 - ](#Lecture3)
<br>
[Lecture 4 - ](#Lecture4)


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
























---
