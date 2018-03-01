# Software Quality Quiz 2 Notes


[Week 4 - Automatic & Manual Techniques for Generating & Validating Test Data & Testing Process](#Lecture4)
<br>
[Week 5 - Test Driven Development, Static & Dynamic Analysis, Functional Testing](#Lecture5)
<br>

<a name="Lecture4"></a>
## Week 4 - Automatic & Manual Techniques for Generating & Validating Test Data & Testing Process

### Types of Data
- Discrete
  - Whole numbers (discrete variables)
- Continuous
  - Decimal numbers (continuous variables)

### Test Data Management (TDM)
- Well defined TDM strategy can
  - rapidly reduce inefficiencies
  - help extract greater value from expensive data
  - make validated test data available in an organized secured consistent and controlled manner
- **Domain Values**: The full range of valid and meaningful values for a data field
- **Data Ranges & Limits**: Especially those that define our equivalence classes
- **Data Relationships**: Data characteristics including cross-system data mappings and sources for derived or calculated data
- **Upstream & Downstream**: Data dependencies from upstream and downstream systems

- TDM Activities
  - **Initial Setup of Test Data**: This is a one time job which requires initial setup and synchronization of test data
  - **Service Projects for Test Data Requirements**: Provide test data to projects based on the requests received
  - **Continuous Support to Projects for Data Requirements**: Data creation request for change in data requirements
  - **Maintenance of Data**: Scheduled maintenance of test data in defined frequencies (weekly, monthly, quarterly or annually)

### Automatic Test Data Generation
- **Random Test Data Generation**
  - Develops test data at random until useful input is found
  - Easy to implement
  - Also ineffective on realistic program

- **Symbolic Execution-Based Test Data Generation**
  - Allow numeric values to take on symbolic values
  - Basically dont use real values
  - Hard to do for strings

- **Dynamic Test Data Generation**
  - For a condition `y <= 38`
    - Dynamic generation tries to make `y` hold a value smaller than or equal to 38 when it gets to that condition
  - If desired test requirement not met, use the generated data to see how close you were
    - Use the feedback to improve the generation
  - Do not generate test data for strings

### Manual Test Data Generation
- Data generation happens manually
- Time consuming (-)
- Data sets can be created using skills & judgments (+)
  - Ex: Better for Augmented Virtual Reality Testing

### Testing Process
- Planning
- Specification
- Execution
- Recording
- Checking for Test Completion


---

<a name="Lecture5"></a>
## Week 5 - Test Driven Development, Static & Dynamic Analysis, Functional Testing

### Test Driven Development
- Procedure
  - Write tests (that fail)
  - Make that specific test pass with bare minimum code
  - Refactor to make test work better for all cases

### Static Analysis
- Process of examining source code prior to compilation and execution  
- Diagnoses for
  - Quality aspects
    - Maintainability
    - Reliability
    - Understandability
    - Complexity
  - Testing Issues
  - Coding Standard Compliance Issues
  - Best Programming Practices
- **Automated Static Analysis**: Analyzes program without executing

### Static Testing
- Using static analysis as a part of test trajectory
- Static & Dynamic testing are supplementary
  - Static analysis does not replace dynamic testing
- Achieves 100% statement coverage

### Defect Removal Cost
- Cost of defect removal rises exponentially for defects found later in the development cycle
- Static Analysis may reduce defects by a factor of 6
![alt](https://github.com/yenvanio/UOIT-Year-3-Notes/blob/master/Images/defect.png)

### Mechanisms for Static Analysis
- **Syntactic Analysis**
  - Coding standards
  - Ex: Missing statements

- **Data Use Analysis**
  - Identify data flows that do not conform to programming practices
  - Purely symbolic, no specific data values are considered
  - Process involves annotating a program flow graph with each data object definition (D), usage (U) and elimination (E)
  - Ex: Variables are not read before they are written

- **Control Flow Analysis**
  - Identify poorly structured code
  - Process involves translating program into flow graph
  - Ex: Multiple exits from a loop

- **Program Slicing**
  - Focuses on a particular subset of variables within a given program
  - Types
    - **Backward**
      - For a given statement `S`
      - Contains all statements that effect whether control reaches `S`
      - Contains all statements that effect the value of variables that occur in `S`
    - **Forward**
      - For a given statement `S`
      - Contains all statements that are affected by `S`
    - **Static**
      - Calculated symbolically, takes no real values
    - **Dynamic**
      - Calculated based on particular data values

- **Information Flow Analysis**
  - Exploits software annotations
  - Ex: Meta-data that asserts properties that should at certain points during execution

### Use of Static Analysis in Secure Coding
- Security Vulnerabilities
  - Cross-site Scripting (XSS)
  - SQL Injection
  - Command Injection
  - Buffer Overflows
  - Memory Leaks
  - Integer Overflows

### Dynamic Analysis
- Investigation of properties of a running software system over one or more executions
  - Analysis that happens during execution
- Done using...
  - Monitoring
  - Tracing method execution, values of variables, memory usage etc
  - Profiling
- Tools required
  - Monitors
  - Loggers
  - Instrumentation

### Monitors
- A tool used to observe a system
  - Observes performance
  - Collects performance stats
  - Analyzes data
  - Displays results
  - Suggests remedies

- Example Monitor : `gprof` has the following function calls
  - `%time` - percentage of total execution time your program spent on this function
  - `cumulative seconds` - total seconds cpu spend
  - `self seconds` - number of seconds accounted for by this function alone
  - `calls` - total number of times function called
  - `self ms/call` - avg number of ms spent in this function per call
  - `Total ms/call` - avg ms spent in this function and its descendants
  - `name` = name of function

- Classification
  - **Implementation Level**
    - Software, Hardware, Firmware, Hybrid
  - **Trigger Mechanism**
    - Event Driven - low overhead for rare event, higher if event is frequent
    - Sample (Timer Driven) - ideal for frequent events
  - **Display**
    - On-line - provide data continuously
    - Batch - collect data for later analysis

- Triggering monitor to collect data is a challenge
  - **Trap**: Software interrupt at appropriate points, like a subroutine
  - **Trace**: Collect data at every instruction, enormous overhead
  - **Timer Interrupt**: Fixed intervals, need to watch out for overflow

### Instrumentation
- Adding measurement probes to the code to observe execution
- Can be done on several levels
  - Different techniques per level
  - Different overheads and accuracy with each technique

### Profiling
- Recording of summary information during execution
- Reflects performance behavior of program entities
- Implemented through
  - **Sampling**: Periodic OS interrupts
  - **Measurement**: Direct insertion of measurement code

### Black Box Testing
- Attempts to find errors in the external behavior of the code in the following categories
  - Incorrect or missing functionality
  - Interface errors
  - Errors in data structures used by interfaces
  - Behavior or performance errors
  - Initialization and termination errors

### Boundary Testing
- **Boundary Value Analysis**: Testing conditions on bounds between classes of inputs
- Usefulness of testing near boundaries

### Equivalence Partitioning
- Black box test technique to reduce # of required test cases
- Procedure
  - Identify classes of inputs with same behavior
  - Test on at least one member of each equivalence class
  - Assume behavior will be same for all members of class
- Criteria for selecting equivalence classes
  - **Coverage**: Every input is in one class
  - **Disjointedness**: No input in more than one class
  - **Representation**: If error with 1 member of class, will occur with all

---
