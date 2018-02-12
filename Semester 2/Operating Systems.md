# Operating Systems


## Table of Contents

[Lecture 1 - Introduction to OS](#Lecture1)
<br>
[Lecture 2 - ](#Lecture2)
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
- 













---
