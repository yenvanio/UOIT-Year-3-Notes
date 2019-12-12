## Table of Contents

[Chapter 7 - Program Design & Analysis](#Chapter7)
<br>
[Chapter 8 - Memory & Caches](#Chapter8)
<br>
[Chapter 9 - Hardware & Software Interfacing](#Chapter9)
<br>
[Chapter 10 - Verification, Validation & Certification](#Chapter10)
<br>
[Chapter 11 - Software Quality - Performance Analysis of Embedded Systems](#Chapter11)
<br>
[Chapter 12 - Virtualization Technologies](#Chapter12)
<br>
[Chapter 13 - Specification Languages](#Chapter13)
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
  - Unified hardware/software representation
    - Uniform design analysis techniques for HW / SW
    - Easy migration of tasks to either HW / SW
  - Iterative Partitioning Techniques
    - Different HW/SW partitions to be evaluated
  - Integrated Modeling Substrate
    - Intermediate Evaluation throughout the design process
    - Step-wise integration of hardware / software
  - Validation Methodology
    - System meets initial requirements
- **Cross Functionality**
  - Single Language Design
  - Compiler transformations and techniques
    - Dead code elimination
    - Loop unrolling
  - Design Change Management
    - Information Hiding
- **Features**
  - Mutual Influence on HW / SW early on
    - Continual verification throughout design process
  - Tool interoperability and automation of codesign at abstract design levels
  - Key Enabling Technologies (Easier to explore design tradeoffs)
- **Pros / Cons**
  - **Cons**
    - Lack of standardized representation
    - Lack of good validation / evaluation methods
  - **Potential Solutions**
    - Extend HW / SW to use heterogeneous paradigms
    - Extend verification techniques to HW / SW domain
- **Integration**
  - Errors in HW / SW design increase as more commitments are made
  - Hardware first approach compounds cost because SW must compensate for HW

---

<a name="Chapter10"></a>

## Chapter 10 - Verification, Validation & Certification
- **Integrators**: Responsible for setting requirements and validating final product
- **Verification**: Ensuring a subsystem meets the objectives
  - Basically does what we want
- **Validation**: Ensuring entire system meets requirements
  - Basically does what we want
- **Certification**: Convincing an authority that the validation process is correct
  - Process based
  - Follow good process management practices
    - To track requirements and deliverables
  - Expensive
    - Document & Review everything!
- **The Process**
  - Requirements Definition
  - Requirements Validation
  - Allocation of Requirements
  - System Validation
- **Challenges**
  - Interoperability
    - Vendor `X` equipment only works with other vendor `X` equipment
    - Problems
      - Who gets blame when multiple vendor equipment being used
      - Vendors have nothing to gain from doing this
  - Wireless Communication
    - Solve cable mess
    - Interference & Jamming are new problems with wireless
      - Physical layer techniques can help
        - Ultra-Wide Bandwidth, Dynamic Frequency Selection

### Certification Standards
- Organizations
  - **ISO**: International Organization for Standardization founded in 1946
  - **IEC**: International Electrotechnical Commission founded in 1906
  - Both in Geneva
  - Each country gets a vote
- **SIL**: Safety Integrity Level
  - Levels 1 - 4
  - Each level has
    - Probability of Failure / Hour
    - Probability of Failure on Demand
    - Higher Level = Smaller Probability
  - **SIL 1**
    - Integrity required to avoid minor incidents
    - Satisfied by certain degree of fault tolerant design guidelines
  - **SIL 2**
    - Integrity required to avoid more serious incidents
    - May cause injury / death
  - **SIL 3**
    - Integrity required to avoid multiple fatalities
  - **SIL 4**
    - Integrity required to avoid disastrous accidents
  - SIL levels for field instruments are established by two methods
    - **FMEDA**: Failures Modes, Effects and Diagnostic Analysis
      - Reviewed by 3rd party
      - Systematic analysis technique to determine failure rates
    - **Proven In Use**
      - Used by customer
      - Requires lots of operational hours
- **ASIL** Automotive SIL
  - Levels: A -> D
  - `++` highly recommended for the ASIL
  - `+` recommended for the ASIL
  - `o` no recommendation for/against the ASIL

### Hardware Product Development
- Activities and processes for product development at hardware level include
  - Hardware implementation of technical safety concept
  - Analysis of hardware faults and effects
  - Coordination with software development

#### Architectural Design
- Represents all hardware components and their interactions
- Each component inherits the highest ASIL
  - If made up of sub elements with different ASIL's
  - Each treated with highest ASIL
- Traceability between safety requirements and implementation maintained to lowest level of hardware components
- To avoid failures due to high complexity, will follow the principles below
  - Modularity
  - Adequate Level of Granularity
  - Simplicity
- Non Functional causes for failure
  - Temperature, Vibrations, Water, Dust
  - Considered during architectural design

#### Detailed Design
- Level of electrical schematics representing interconnections between hardware parts of a component
- Operating conditions of parts used in design comply with environmental operational limits
- Robust design principles

#### Safety Analysis
- Applies to ASIL B -> D
- Safety Analysis identifies the following for the safety goal
  - Safe Faults
  - Single Point Faults / Residual Faults
  - Multiple Point Faults
- Evidence of safety mechanisms to maintain or switch safely into a safe state shall be made available
  - Diagnostic coverage wrt to residual faults shall be evaluated
- Fault that can occur at anytime
  - If the diagnostic `test interval + fault reaction time > fault tolerant time interval`
- If a fault only occurs at power-up and negligible elsewhere
  - Can run a test at start-up after power-on only
- Analysis like FMEA or FTA can be used to structure rationale

#### Hardware Architectural Metrics
- Evaluates hardware architecture against requirements for fault handling
- Metrics dependent on whole hardware of item
  - Compliance with target figures is achieved for each safety goal in which item is involved
- Need to be precise enough to differentiate between different architectures
- Need to support evaluation of the final design
- Make ASIL Dependent pass/fail criteria
- **Single Point Fault Metric**
  - Reveal if coverage to prevent risk from single point faults is sufficient
- **Latent Fault Metric**
  - Reveal if coverage to prevent risk from latent faults is sufficient
- **Failure rates for hardware parts** are determined by
  - Using hardware part failure rates data from recognized industry source
  - Using statistics based on field tests
  - Use expert judgement founded on an engineering approach
- **Residual Risks**
  - Two methods to evaluate if residual risk of safety goals is low
    - **PMHF**: Probabilistic Metric for random Hardware Faults
      - Compare quantified FTA with target value
    - **Individual Evaluation**
      - Of reisdual / single-point faults
      - Of each dual-point failure leading to the violation of safety goal

### Hazard and Risk Analysis
  - **Hazard**: situation that may lead to risks
  - **Risk Analysis**: Identifying potential hazards and risk of each hazard

### Patient Monitoring System (PMU)

#### Contextual Requirements
- High Level Requirements
- Examples:
  - `Health of immobile patient SHALL be monitored and SHALL be altered in the event it becomes unsatisfactory`
  - `All readings from monitoring equipment of patient SHALL be logged`

#### PMU Requirements
- **External Interfaces**
  - `PMU SHALL provide Acknowledge Button that can be activated via physical contact`
  - `PMU SHALL display its current working state`
- **PMU States**
  - `Active` / `Inactive`
  - `Powered Off` / `Powered On`
- **Routine Maintenance**
  - `Routine maintenance SHOULD not be required more often than once every six months`
- **Dependability Requirements**
  - `The failed state for the PMU shall be to move into the safe state`
  - `Be Compliant with SIL3`
- **Security Requirements**
  - `Any operator SHALL be required to present credentials before PMU operation`
- **Functional Requirements**
  - `PMU SHALL perform sanity check on rules`
- **Non Functional Requirements**
  - `PMU SHALL have an operational life of 20 years`

#### PMU Hardware Requirements
- **Functional**
  - `Hardware SHALL detect complete failure of power to the PMU`
- **Non Functional Requirements**
  - `The PMU SHALL operate at 120V / 240V at 50Hz / 60Hz`

#### PMU - Hardware & Risk Analysis
- **Hazard**: Power Supplies
- **Associated Risk**: External power supply might fail, switching PMU to run on batteries
- **Mitigation**: If external power fails, relay alert to human
- **Residual Risk**: Battery might not be charged enough to allow PMU to handle external power failure

#### PMU - Failure Analysis
- Build fault trees incorporating identified risks to cover
  - Probability of PMU failing to meet functional safety requirements
  - Probability of PMU failing in dangerous manner
    - Not failing gracefully
- Explore opinion to identify risks with each hazard
- **Component Failure Analysis**
  - Assume OS is SIL3
    - Probability of failure in 24 hours: `PFO < 2.4 x 10^-6`
  - Assume hardware is SIL1
    - Probability of failure in 24 hours: `PFH < 2.4 x 10^-6`

### Fault Trees
- **FTA**: Fault Tree Analysis is a top down deductive failure analysis
  - Used to analyze undesired state of system using *Boolean Logic* to combine a series of lower-level events
- Applying
  - Top Event (The Fault)
  - Branch down listing faults that lead to the top fault (working backwards)
    - Consider sequential and parallel or combinations of faults
  - Use boolean algebra to add probabilities fault tree
  - Determine probability of top event

---

<a name="Chapter11"></a>

## Chapter 11 - Chapter 11 - Software Quality - Performance Analysis of Embedded Systems
- **Clustering**
  - Concentrate data points into groups
  - Experiment with group reps instead of each data point
  - Steps
    - Sample, Normalize it, Select metric, Cluster, Analyze results
- **Monitors & Probes**
  - **Probe**: Something inserted into computer to extract information
  - **Probe Effect**: Unintended alteration in system behaviour caused by measuring it
- **Monitors**
  - **Software Monitor**
    - Low input rates, resolution but higher overhead
    - Activiation Trigger
    - Buffer Size
    - Buffer Elements
    - Buffer Overflow
    - Online vs Offline Analysis
  - **Hardware Monitor**
    - Usually separate piece of equipment
    - Probes and Ports
    - Counters
    - Comparators
    - Logic Elements
    - Timer
    - Memory
- **Measurement Scales**
  - Nominal Scale (Categories)
  - Ordinal Scale (Ordered Categories)
  - Interval Scale (Range)
  - Ratio Scale (Ratio)
- **Variables**
  - Qualitative
  - Quantitative
  - Discrete
  - Continuous

### Trade Offs & Common Mistakes
- Tradeoffs occur at every stage of development
  - `Memory` vs `Computation Time`
  - `Computation Time` vs `Power Consumption`
  - `Look` vs `Computation Time`
  - `Look` vs `Durability`
  - `Cost` vs `Safety`
- Requirements: `Features vs Time to Market`
- Design: `Centralization vs Partition vs Integration`
- Coding: `Language of choice vs Training Requirements`
- Manufacturing: `Part Reliability vs Cost`

### Performance Evaluation
- Measures a system with respect to a metric
- Requires Understanding of
  - Measurement techniques and tools
  - Data Analysis with statistics
  - Experimental Design and Analysis
  - Simulation Methods
  - Modeling Methods
- Example: `Computation Time, Memory Consumption, Power Consumption`

### Common Mistakes
- **No Goals**
  - Performance Project needs goals
  - Everything depends on the goal
  - Ex: `Measuring response time requires different setup than measuring interference`
- **Biased Goals**
  - Proper formal approach forbids this
- **Unsystematic Approach**
  - Don't touch setup or experiment during execution
- **Analysis without Understanding**
  - Think First -> Then Do (Saves Time)
- **Incorrect Performance Metrics**
  - Pick correct / comparable metrics
  - Ex: `CISC != RISC`
- **Unrepresentative Workload**
  - Existing workloads might be outdated
  - Be wary of synthetic workloads
- **Assuming no Future Changes**
  - Don't assume workload for analysis will be valid in 24 months
- **Wrong Evaluation Technique**
  - Analytically modeling / simulating / measuring are the correct techniques
- **Overlooking Important Parameters**
  - Renders result useless
  - Ex: `Network-Switch Buffer different size parameter for different cases`
- **Inappropriate Experimental Design**
  - Specifies the number of measurements and parameter settings
    - Improper settings, wastes time
  - Ex: `Full Factorial: trying all combinations (Memoization)`
- **No Analysis**
  - Raw Data without interpretations or conclusions
- **Erroneous Analysis**
  - Errors during data collection
  - Ex: `Short runs`
- **Starting Too Complicated**
  - `Start Simple`
- **Ignoring Variability**
  - Systems have varying performance
- **Improper Presentation of Results**
  - Aim is to inform decision making not make as many graphs as possible
- **Ignoring Social Aspects**
  - Communicating data is more important than flexing
- **Omitting Assumptions and Limitations**
  - Always list assumptions and Limitations
  - When conclusion wont hold etc.

### Systematic Approach
- Steps
  - State Goals & Define System
  - List Services and Outcomes
  - Select Metrics
  - List Parameters
  - Select Factors
  - Select Evaluation Technique
  - Select Workload
  - Design Experiments
  - Analyze Interpret Data
  - Present Results
- Evaluation Types
  - **Analytic Model**
    - Validate through simulation or measurements
  - **Simulation**
    - Validate through analytic model or measurements
  - **Measurements**
    - Validate through analytic model or simulation

### Metrics
- Properties
  - **Global Metrics**
    - Affects whole system
  - **Individual Metrics**
    - Affects only the user
  - **Low Variability**
    - Little difference in measurement values
  - **Non Redundancy**
    - Metrics only convey new information
  - **Completeness**
    - Metrics should cover all service outcomes

#### Performance Metrics
- **Structured Approach to Selecting Performance Metrics**
  - List services, describe service outcomes and classify
    - Done Correctly
    - Done Incorrectly
    - Cannot Do

### Time Rate Resource Metrics
- **Responsiveness**
  - Time delay between two events in the system
- **Productivity**
  - Amount of work a system does
- **Utilization**
  - Unused resources vs Used resources over time
- Resource with the highest utilization is bottleneck

### Error Metrics
- How likely is it to happen?
- Probability of failure modes
  - Distinguish between different modes / sources (error from HW / SW)

### Common Metrics
- **Response Time**
  - Turnaround time: Duration of a job from start to finish
  - Stretch Factor: Describes parameters that affect response time
- **Throughput**
  - Rate at which requests can be services
- **Utilization**
  - Ratio of `resource busy` vs `resource idle`
- **Utility Classification**
  - Higher is better: Higher value is better
  - Lower is better: Lower value is better
  - Nominal is best
    - Tradeoff in system and there exists a best operating point
- **Workloads**
  - Real workload based on observed workloads
  - Synthetic workload based on expected workloads
  - Types
    - **Code Based**:  Cant change source code
    - **Algorithm Based**: Run bubble sort on this data set
    - **Problem Based**: Sort this data set
  - **Timeliness**
    - Workload design for todays system might be invalid for tomorrows system
  - **Loading Level**
    - Design workload with load
    - Ex: `Overloading for stress testing`
  - **Repeatability**
    - Might need to redo experiment
    - Script and keep record of everything
  - **Impact of external components**
    - Ensure external component doesnt become driver for workload
- **Benchmarks**
  - Useful for domain specific applications
  - Results not portable to other domains
  - Evaluation
    - Synthetic load benchmark requires proper justification
    - Real load benchmarks requires citations for the source
    - *Can I use data to make a good decision*
      - Basically how u evaluate a benchmark ^

### Workload Characterization
- Workloads should be created by abstracting observations
  - Comprises workload components
  - Component should be parameterized
- **Measures of Centre**: Mean, Median
- **Dispersion**: Centre doesn't state variability
- **Markov Models**
  - Represents system states with probabilities on transitions
  - Can represent a workload component

---

<a name="Chapter12"></a>

## Chapter 12 - Virtualization Technologies
- To create a virtual version of something
- Including
  - Virtual hardware platform
  - Virtual OS
  - Virtual Storage
  - Virtual Network
- Fundamental part of cloud computing

### Creating Virtualization
- **Host / Guest OS**
  - OS functions as Host
  - Virtual machines are guests
  - Uses *Type 2 Hypervisors*
- **Hypervisor**
  - Description
    - Software that creates and runs virtual machines
    - **Type 1: Native:** Runs directly on hardware
    - **Type 2:** Hosted: Runs on conventional OS
  - Uses Type 1 Hypervisor and custom minimal OS
- **Emulation / Simulation**
  - Creates virtual hardware / software
- **Jails / Linux Containers**
  - Virtual application runs on host OS
  - **Pros**
    - Ease of development & deployment
    - Security isolation
    - Maximizing resource utilization
  - **Performance**
    - Minimal performance overhead
    - Ideal method of process isolation and system virtualization

```
Example

1: Host OS / Guest OS
  - Full blown OS
    - VMWare, Virtual Box etc.

2. Hypervisor
  - Sleek OS customzied for virtualization
    - VMWare Vsphere (specific for VMWare)

3. Emulation
  - Emilates hardware architecture
    - Java VM

4. Containers
  - Virtualizing isolated process
    - Docker, Solaris, Web Hosting

```

---

<a name="Chapter13"></a>

## Chapter 13 - Specification Languages
- **MARTE: Modeling & Analysis of Real-Time Embedded Systems**
  - Support for non-functional property modeling
  - Rich time and resource models to UML
  - Concept definition for SW / HW platform modeling
  - Concept definition for application allocation on platforms
  - Support for Quantitative Analysis
- **AADL: Analysis & Design Language**
  - Core Language Providing Full Support
  - Modeling Application Tasks & Communication Architecture
  - Pre-declared properties to characterize task execution
- **Comparison**
  - Cover same design objectives and real time analysis of real-time embedded system
  - Provide SW / HW design and have semantic equivalencies
  - MARTE is UML based, covers wider modeling range
    - Address multiple abstraction layers
  - AADL optimized and address only needed concepts
    - Addresses specific abstraction layer
- **Subprograms**
  - Represents Entry points in executable code
  - Data subprograms are features of data components
  - Server subprograms are features of threads
  - No static data
    - External data accessed through parameters
  - Called within a process
    - Can be called remotely or locally
- **Process**
  - Visual address space
- **Platform Components**
  - Processor
    - Scheduling and execution abstraction
    - Memory subcomponents
    - Scheduling protocol
  - Memory
    - Size, Access Times, Memory Protocol
  - Bus
    - Latency, Bandwith, Message Size

### AADL
- **Components**
  - Software Components
    - ThreadGroup & Thread
    - Data
    - Subprogram
    - Process
  - Platform Components
    - Processor
    - Memory
    - Bus
    - Device
  - System Components
    - System
- **Component Interfaces**
  - Features
    - External Connections
  - Flows
    - End to End Internal Connections
  - Properties
    - Useful attributes for analysis
- **Component Implementations**
  - Subcomponents are type references
  - Connections conform with flows in the type
  - External features conform with the type
  - Internal features conform with subcomponent types
- **Features & Connections**
  - Communication
    - Ports & Port Groups
    - Port Connections
  - Resource Access
    - Required and provided access
    - Access connections
  - Control   
    - Subprogram features
    - Parameter connections
- **Ports & Port Groups**
  - Ports are typed
    - Data component types
  - Ports are directional
    - Input, Output, Bi-Directional
  - Synchronous or Asynchronous communication
    - Event, Data, Event Data Ports
      - Input event and event data ports have queues
      - Input data ports have status flags for new data
- **Data Components**
  - Data component types
    - Represent data types
    - Can have subprogram features
      - Like access request methods
    - Used as types of data ports and connections
  - Data component implementations can have data subcomponents
    - Representing internal data of object

### Threads
- **Component**
  - Thread represents a sequential flow of control
    - Only data as subcomponents
- **Group**
  - Organization of threads within a process
  - Can be recursive
- **States**
  - Active
    - Member of current mode
  - Inactive
    - Not member of current mode
- **Properties**
  - Dispatch Protocol
    - Periodic, Aperiodic, Sporadic, or Background
  - Period
    - For periodic and sporadic threads
  - Execution Time Range & Deadline
    - Execution states separate
      - Intialize, Compute, Activate ...etc
- **Dispatch**
  - Periodic threads dispatched periodically
    - Event arrivals are in a queue
  - Non periodic threads are dispatched by incoming events
  - Pre declared ports
    - Event IN port `Dispatch`
      - If connected, other events queued
    - Event OUT port `Complete`
      - Can implement precedence

### Port Connections
- Event connections support `n - n` connectivity
- Data connection supports `1 - n` connectivity
- **Semantic Port Connection**
  - Ultimate source to ultimate destination
  - Processor, Thread or Device
- Type Checking
  - Directions and types must match
- **Immediate & Delayed Connections**
  - Data connections between periodic threads
  - `T1 -> T2` vs `T1 -> DELAY -> T2`
- **Component Bindings**
  - Software components are bound to Platform components
  - **Binding Mechanism**: Exploration of design alternatives
    - Properties specify allowed vs actual bindings 


---
