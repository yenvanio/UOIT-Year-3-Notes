# Embedded Systems


## Table of Contents

[Chapter 7 - Program Design & Analysis](#Chapter7)
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
