# Embedded Systems


## Table of Contents

[Chapter 7 - Program Design & Analysis](#Chapter7)
<br>
[Chapter 8 - Memory & Caches](#Chapter8)
<br>
[Chapter 9 - Hardware & Software Interfacing](#Chapter9)
<br>

<a name="Chapter7"></a>

## Chapter 7 - Program Design & Analysis

### Representation of Programs
- Source code not always good representation
- Compilers derive *Intermediate Representations*
  - Used to **Manipulate** and **Optimize** the program
- Data Flow Graph (**DFG**)
  - Describes minimal ordering requirements on operations
    - It is not about control, just basic blocks of code
  - Each Operator is a Node `+`
    - Input is the expression `A + B`
    - Output is the evaluated variable `A + B = X`
  - Partial Orders
    - Can perform pairs of operations in any order
    - `A + B, C - D;` `B + D, X * Y`
- Control Data Flow Graph (**CDFG**)
  - Node can be
    - Decision
    - Data Flow
  - Can simplify nodes by joining simple statements
    - Assignments
    - Print Statements

### Compiler Optimization
  - **Loop Transformations**
    - Reduce loop overhead
    - Increase pipelining opportunities
    - Improve memory performance
  - **Loop Unrolling**
    - Ex: `for i = 0 -> 4; a[i] = b[i] * c[i]`
    - If we substitute loop with individual statements, reduces loop overhead
      - No iteration, No Extra Variable, No Tests
      - This expands the amount of code and interferes with cache
      - `a[0] = b[0]*c[0]; ...` and so on
    - If we unroll it twice instead
      - Have for loop but reduce iterations
      - i = 0 -> 2 instead of 4
      - `a[i*2] = b[i*2] * c[i*2]; a[i*2+1] = b[i*2+1] * c[i*2+1];`

### Assembly & Linking
- Last steps in compilation
- Programs can be composed of multiple files, addresses become more specific during processing
  - **Relative Addresses**
    - Measured relative to start of module
    - **Generation**
      - Some labels not known at assembly time
  - **Absolute Addresses**
    - Measured relative to start of CPU Address Space

#### Assemblers
- Major Tasks
  - Generate binary for symbolic instructions
    - Two Passes: Generate Symbol Table -> Generate Binary Instructions
    - Need Symbol table first for lookup
  - Translate labels into addresses
  - Handle pseudo-ops (data)
- One to One translation

#### Linking
- Combines several object modules into a single executable model
- Jobs
  - Put modules in order
    - Core modules placed in absolute positions in memory
    - **Load Map** controls the order of modules
  - Resolve labels across modules
- Dynamic Linking
  - Some OS's link modules dynamically at run time
    - Share one copy of library among all programs
    - Programs get updated with new lib versions

### Static Analysis
- Process of examining code before compilation / execution
- Diagnoses
  - Quality Aspects
    - Maintainability
    - Understandability
    - Complexity
  - Testing Issues
  - Coding Compliance Issues
  - Best Programming Practices
  - Unsafe Programming Constructs / Coding Defects
- **Program Slicing**
  - Focuses on parts of code relevant to subset of variables in the slice
  - Backward
    - For statement `S` get all lines that effect `S` and variables in `S`
  - Forward
    - For statement `S` get all lines affected by `S`
  - Static
    - Symbolic, no concrete data values
  - Dynamic
    - Sliced based on particular data values

### Dynamic Analysis
- Investigation of properties of software over one or more executions
- **Instrumentation**
  - Adding probes to code to observe execution
  - Can be done on multiple levels
    - Each level has different techniques applied
    - Different overheads and accuracy for each technique

---


<a name="Chapter8"></a>

## Chapter 8 - Memory & Caches
- **Memory Wall Problem**
  - `CPU Speed / Number of Cores` increases faster than memory bandwidth
  - Memory elements causes unpredictability when shared amongst multiple cores
  - Cache is hard to analyze for a single task
- **Timing Interference**
  - Depends on
    - Caches
    - Interconnects
    - Main Memory
  - **Arbitration**: Order in which cores access a resource will effect next resource in the chain
  - **Latency**: Access latency for a slower resource can hide the latency for access to a faster resource
- **Cache Challenges**
  - Need to determine worst-case to establish a safe bound
  - Worst Case is hard to determine
    - Ex: Direct-Mapped Cache
      - Multiple `<dynamic>[size]`
      - They all have same indexes in cache, huge # of conflict misses
- **Memory Controllers**
  - Main Memory consists of multiple parallel components (**Banks**)
  - Most commonly used memory is Dynamic Random Access Memory (**DRAM**)

### DRAM
- Each device is composed of multiple banks
  - Each bank has a row buffer
- DRAM row must be loaded before read/write operations
  - Closed after operation so we can load another page
- Banks operate in parallel
  - However there is a shared command bus and data bus
- DRAM Module consists of multiple DRAM devices

#### How a Page Works
- Latency for initial request is long
  - Successive requests to same page are more efficient

```
Steps

Part A (Latency of Request 1 (Closed Page))
  1. Request 1 Arrives @ Page
  2. Close Previous Page
  3. Load New Page

  PRE -> ACT -> READ -> DATA

Part B (Latency of Request 2 (Open Page))
  1. Request 1 Completes
  2. Request 2 Arrives
  3. Request 2 Completes

```

#### Contention
- Depends on which rank and bank is accessed by each core
- If all cores access same rank & bank
  - `N` requests for one cache block at the same time
  - Must close / open page `N` times
- Different Ranks can operate in parallel
  - Do not need to close before opening because each rank/bank has a different page
  - Open all pages in parallel even
    - (in this ex: limited to 4 to avoid command bus conflicts)
- Same Rank, Different Banks
  - Can also run pages in parallel
  - However more read and write constraints within same rank
    - IO / gating adds these read/write constraints

### Interconnection
- Need scalable communication between cores
- Delay on interconnection compounds memory access delay
- Types
  - **Shared Bus**
    - Single Resource
    - Each transaction interferes with every other one
    - Not scalable
  - **Crossbar**
    - N inputs, M outputs
    - Each input connected to each output
    - Employs virtual input buffers
    - Still scales poorly, delay increases with N, M ^
  - **Network On Chip**
    - Interconnect comprises on-chip switches connected by links
    - Topologies: Linear, Ring, Tree, 2D Mesh

#### Off-Chip vs On-Chip Networks
- **Synchronization**
  - Easier with On-Chip routers
- **Link Width**
  - Wires are inexpensive On-Chip, so fairly wide
  - However, many Off-Chip moved to serial connection
- **Buffers**
  - Inexpensive on Off-Chip
  - Buffers are main cost for On-Chip
- **Wormhole Routing**
  - Buffer parts of packet
  - Break into blocks (**Flits**) equal to link width
  - Propagates in sequence through network
- **Virtual Channels**
  - *Problem*: packet occupies multiple flit switches
    - If packet blocked, all switches blocked
  - *Solution*: Multiple flit buffers in each router
    - Assign packets to different flit buffers (virtual channels)

### Shared Memory Issues
- Case Study
  - Fixed Priority Scheduler
  - 2 Processes with different low / high priorities
    - Low Priority: (5ms, 10ms) & (10ms, 20ms)
    - High Priority: (1ms, 2ms), (2ms, 4ms) & (5ms, 10ms)
  - Low Priority task utilization increased due to interference from high priority task
- **Cache Interference**
  - Reloading cache directly affects execution time
  - If it takes `655 us` to reload L2 cache and partition size `2ms`
  - Execution time increment = `655us / 2ms ~ 33% ^`
  - Cache Interference proportional to
    - Cache Size
    - CPU Clock Frequency
    - (Inversely Proportional to) Memory Bus Speed
- **Storage (Shared Cache) Interference**
  - Multiple cores compete for cache space
  - A core can evict cache lines belonging to another core
    - **Cache Line**: Cache entry holding certain number of words, a line is read and cached at once.
- **Shared Timing Interference**
  - Multiple cores want access simultaneously
  - Other cores wait for the selected core to finish
  - Each core can delay the others

### Solutions to Interference

#### Allocation Interference
- **Cache Partitioning**
  - Partitioning amongst multiple tasks / cores
    - Pro: No Allocation Interference
    - Con: Each task / core gets smaller portion of cache
  - How to do?
    - **Compiler Based**
      - Modify linkage so different cores occupy different cache lines
    - **OS Based**
      - Modify page allocation so different cores occupy different cache lines
    - **HW Based**
      - Partition cache n-ways among cores
  - For shared cache it is harder because
    - Need to know which tasks running on which core
    - If schedule of all cores not scheduled then tough
- **Scratchpad**
  - A programmable cache
    - Software responsible for loading and unloading the Scratchpad
  - What it do?
    - Divide memory access into two categories
      - Scratchpad
      - Main Memory
  - How it do?
    - Determine what to load by algorithm
    - Scratchpad contents can be updated while tasks are running

#### Timing Interference
- **Modify Arbitration**
  - Works better when different contenders have different requirements
    - Different latency / bandwidth
  - Access is given to high priority cores
    - Reads > Writes (Higher Priority)
- **Schedule Resource Access**
  - Schedule the contenders so no competing for access

---

<a name="Chapter9"></a>

## Chapter 9 - Hardware & Software Interfacing
- **Characteristics of an OS**
  - Real-time operation
  - Reactive operation
  - Configurability
  - I/O device flexibility
  - Streamlined protection mechanisms
  - Direct use of interrupts
- Using OS for Embedded Systems
  - Adapt an Existing OS
    - Slower than a special purpose OS
    - Familiar interface though
    - Usually need to add specialized functionality
  - Purpose Built OS
    - Faster, Smaller
    - Scheduling in real-time
    - Interrupt response time is quicker and less latency

### Embedded Linux
- **Advantages**
  - Vendor Independence / Open Source
  - Supports wide range of processor architectures and peripheral devices
  - Minimal cost for dev / training
- **Kernel Architecture**
  - Modular
  - Single process with one address and memory space
  - Each application protected with own user memory
    - Invalid access will only crash that process
  - `User Space > Kernel Space > Architecture`
- **Structure**
  - Kernel Modules export functions that can be called by other modules
  - If kernel has invalid memory reference then kernel + all processes crash
- **Booting Process**

```
Bootloader
  1. Reset Microcontroller
  2. First Stage Bootloader (in small ROM) initializes CPU, MMU, on-chip devices and memory map
  3. ROM bootloader loads second stage bootloader from flash -> RAM
  4. Second Stage Bootlader loads Kernel and RAMDisk
  5. Manual Interrupt (ctrl + c) to use tftp and load Linux Kernel from Server
    - Trivial File Transfer Protocol
  6. After linux starts running, bootloader not in RAM anymore
  7. Bootloader config saved in high address space (only for dev/tesing)
  8. During development, Bootloader runs start_kernel()

Kernel
  1. Kernel initializes cache, hardware devices, mounts root file system
    - Without root file system, kernel hangs
  2. Kernel executes init() -> startup scripts
    - Run Level: Diff processes started by scripts to activate resources
      - Run Level 5 - GUI
      - Run Level 3 - System Console Window

Root File System
  1. RAMDisk used for file system (No Hard Disk in Embedded System)
  2. Compressed file before loaded, supports multiple file systems
  3. Mounted in RAM, stays there till reboot
```

### QNX
- **Micro Kernel**
  - **Inter Process Communication (IPC)**
    - Micro Kernel Supervises routing of messages
    - Micro Kernel Supports 3 Types of IPC
      - **Messages**: Fundamental form of IPC
        - Synchronous communication, requires proof of receipt
      - **Proxies**: Special form of message
        - Good when process doesn't interact with recipient
      - **Signals**: Traditional form of IPC
        - Supports Asynchronous IPC
  - **Low Level Network Communication**
    - Micro Kernel Delivers all messages destined for other nodes
  - **Process Scheduling**
    - Micro Kernel Scheduler decides which process executes next
  - **First Level Interrupt Handling**
    - Micro Kernel Supervises routing of hardware interrupts / faults

#### Process Manager
- Responsible for creating new processes and managing resources of a process
- QNX Supports 3 process-creation functions
  - `fork()`
    - Creates a new process that is duplicate of the calling process image
  - `exec()`
    - Replaces calling process image with new process image
  - `spawn()`
    - Creates new process - child of calling process
- Lifecycle
  - Creation
    - Allocating process ID for new process
    - Environment definitions for new process
  - Loading
    - Loading process images
    - Loading thread runs under ID of new process
  - Execution
    - Compete with other process for CPU resources
  - Termination
    - Can be terminated in 2 ways
      - Process invoked `exit()` manually or returning from `main()`
      - Signal whose action is to terminate process
- Process States
  - Ready
    - Can use CPU
  - Blocked
    - Cannot use CPU
  - Held
    - Received `SIGSTOP` cannot use CPU until removed from `HELD` state
  - Wait-Blocked
    - `wait()` or `waitpid()` was called, waiting for status from child processes
  - Dead
    - Process ended, cannot send exit status to parent because no `wait()` called
    - Zombie Process


#### File System Manager
- **Fys** provides standardized storing / accessing of data on disk subsystems
- QNX implements 6 types, 5 are managed by Fsys
  - **Regular Files**
    - Randomly accessible sequences of bytes
    - No predefined structure
  - **Directories**
    - Information to locate regular files
    - Status / Attribute info of regular files as well
  - **Symbolic Links**
    - Pathname to file / directory to be linked in place of symbolic link
    - Provide multiple paths to a single file
  - **Pipes & FIFO's**
    - I/O channels between processes
  - **Block Special Files**
    - Devices, disk drives, partitions
    - Accessed in a way that hides characteristics from applications
- 6th type is **Character Special File**
  - Managed by Device Manager (**Dev**)
    - Interface between process and terminal devices
    - Located in I/O space, names starting with `/dev`
    - Manages flow of data between processes

#### Network Manager
- (**Net**) gives user a seamless extension of OS messaging
- Responsible for propagating QNX messaging across LAN
- TCP / IP
  - QNX implements LAN that relies on its own protocol to provide fast seamless interface between QNX computers
  - To communicate with non-QNX systems uses TCP/IP


### Design Process
- **Outline**
  - Partitioned into hardware / software components
  - Developed separately
  - Usually hardware first approach
- **Assumptions**
  - Hardware / Software can be acquired separately and easily integrated
  - Hardware problems can be fixed with software modifications
  - Software doesn't need maintenance
- **Cons**
  - Impact of hardware and software on each other is hard to assess
  - Poor quality designs
  - Expensive modifications

### Co-Design Environment
- **Requirements**
- **Cross Functionality**
- **Process**
- **Features**
- **Issues**









---
