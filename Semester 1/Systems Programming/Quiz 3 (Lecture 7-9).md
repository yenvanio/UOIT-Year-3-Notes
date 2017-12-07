# Systems Quiz 3

## Lecture 7

### OS Vs System Program
- A system program provides a convenient environment for program **development and execution**

- Operating system also provides convenient environment to **execute user programs** but also acts as intermediary between user and computer hardware and makes computer system easy to use.


### Linking and Loading
- Linking combines programs along with libraries to create a *loadable image*
  - Resolves symbols within the set
  - Lists symbols that loader needs to resolve


- Loading copies the *loadable image* into memory and connects it with already loaded programs and updates memory address
  - In UNIX interpreting file to initialize the process address space
  - In all systems kernel image is in it's own format

- Workflow
  1. Source File (.c file) goes through compiler becomes a compiled object (.o file)

  2. After compiled, goes to linker and it links static libraries and other objects to the object file and it becomes an executable file

  3. `gcc a.c b.c -o a.out` This command basically does the above two steps.

  4. Then goes to loader which connects it with dynamic libraries and creates a image

**Note** In class Akramul said something like "The executable file has all the static libraries in it but does not have the dynamic libraries because those are connected externally" **Note**

- Linker is located inside of the gcc comand (compiler command)

- Loader is part of the *exec* sytem call

- Executable image contains *all* object and library modules needed by program

- Entire image loaded at once

### Absolute Loader
- Object program loaded at the specified address
- No relocation or linking needed

### Bootstrap Loader
- Workflow
  1. Computer turned on
  2. Absolute loader is executed
  3. Bootstrap loader loads the OS
  4. Jumps to loaded program and executes
  5. The loaded program is a loader itself (and small size)
  6. The loader that was just loaded, will load another larger loader
  7. Jumps to new loader (bigger)
  8. Process Repeats until entire OS is loaded

### Relocating Loader
- Two methods to describe where in the object program to modify the address (i.e where to add the program starting address)
  - Modification Records  for small changes
  - Relocation Bit Mask for large changes

### Program Linking
- Program composed of many control sections
  - These can be assembled separately
  - Can be loaded at different addresses in memory
  - They must be loaded into memory before resolving external references to symbols defined in other sections

### Implementing Linking Loader
- Data Structures and Algorithms
- Machine Independent Features
- Loader Design Options

#### Data Structures and Algorithms

##### Definitons
- Passes
  - A linking loader makes two passes over the input
    1. Assign addresses to external references
    2. Perform loading, relocation and linking


##### Data Structures
  - ESTAB - External Symbol Tables
    - Stores name and address of external symbols in control sections
    - Needs to specify which control section the symbol is defined in
  - PROGADDR
    - Beginning Address in memory where the linked program is loaded
  - CSADDR
    - Contains starting address assigned to control section that is being scanned by loader
    - This value is added to all relative addresses within control sections

##### Algorithm
- Pass 1 (Loader only concerned with HEADER and DEFINE to build ESTAB)
  1. PROGADDR obtained from OS

  2. This is now the starting address for first control section (CSADDR)

  3. Control Section name is put in ESTAB and value is the CSADDR

  4. All external symbols in DEFINE for that control section also added to ESTAB, address values are obtained by adding the value in DEFINE (offset) to the CSADDR

**Note** In the end, ESTAB should have all external symbols defined with the address of each **Note**

- Pass 2 (Loader performs loading, relocation and linking)
  1. CSADDR still contains starting address of control sections
  2. Each text record is read
  3. Object code is moved to (address + CSADDR)
  4. When a modification record is encountered, ESTAB is referenced
  5. Value is added or subtracted from indicated memory location

**Note** Can make linking loader algorithm faster by using reference #, this would be used instead of symbol name and if it is searched once can store in array and look up using ref # instead of making multiple searches in the ESTAB **Note**

### Machine Independent Features
- Most linking loaders automatically add routines from a subprogram library into the program being loaded.
  - Automatically fetched from library, linked with main program and loaded
  - No extra work for programmer
- In this case the linking loader only keeps track of external symbols that are referred to and not defined.
- At the end of the first pass, the loader searches libraries for these symbols
- One search result might come with a reference to another library and so it must be repeated until all external references are resolved
  - If not resolved = error!
- If symbol defined in both source and library, source is used

### Loader Options
- Allows modification of standard processing
- Examples
  - `Include program-name`
    - Directs loader to read object program from a library
  - `Delete csect-name`
    - Tells loader to delete the name control sections
  - `Change name1, name2`
    - Cause external symbol name1 to change to name2 everywhere in program

### Linkage Editor
- Produces a linked version of the program written to a file for later execution (basically skips loading step)
- To run it later, use relocating loader to load program into memory
- All items that need to be modified have values relative to start of linked program so no ESTAB needed
- Useful for executing a program many times

### Dynamic Linking
- Postpones the linking function until execution time, unlike linkage editor that does it before and linking loaders that do it at the same time.
- Advantages
  1. Good for loading one library then loading all programs that need it so they share one copy instead of each having their own
  2. Good for OOP as well
  3. Saves space and time
- Implementation
  1. Subroutines are called via a OS service request
  2. OS examines its tables to make sure its not there already
  3. Control is passed from OS to subroutine
  4. After processing control back to OS
  5. After completed the memory it was using is released (usually at the end cause same subroutine might be called multiple times)

```
Creating a Static Library using gcc

$ gcc -c foo.c

$ ar rcs libfoo.a foo.o  // Creates the Library libfoo.a

$ gcc bar.c -L. -lfoo

$ ./a.out



Creating a Dynamic Library using gcc

$ gcc -c -fPIC foo.c

$ gcc -shared -WI, -soname, libfoo.so.1 -o libfoo.so.1 foo.o

$ gcc bar.c -L. -lfoo

$ export LD_LibRARY_PATH=.

$ ./a.out

```

## Lecture 8

### Tracing
  - `strace` on Linux
  - `-T` for time spent in each system call
  - `-t` prints timestamp for each strace output line
  - `-o nameofFile` prints output to specified file
  - `top` shows top consumers of CPU and Memory

### Debugging
  - Used to find errors that are not found by compiler/linker
  - Classification
    - Runtime Error
    - Not run as intended
  - Usage
    - Analyze main memory after program crash (Post Mortem)
    - Run program step by step (Dynamic)

#### Post Mortem Debugging
- Program crashes, writes contents of main memory to a file (core dump)
- Use debugger to go through it
- Will show info about machine code, functions, parameters, variables, constants etc
- Shows which line the error occurred and a backtrace
- Values of parameters and variables

#### Dynamic Debugging
- Can set several break points
- Start at one point and go step by step
- Takes lots of time, better to check post mortem first and think about possible errors and it narrows the area of dynamic search

## Lecture 9

### GBD Debugger
- GNU Debugger, also called GBD is most popular debugger for linux to debug c and c++
  - Helps you find, which statement caused crash
  - Which line and what parameters involved
  - Value of variables at that point
  - Result of expression at that point
- Lets you run the program up a point then stop and print variables or continue line by line and print variables after each line execution

### Debugging Symbol Table
- Maps instructions in the compiled program to the corresponding variable, function or line in the source code
- Example: `Program Instruction => itemName, itemType, file, lineNumber`
- Can be embedded or stored as separate file
- Need it to debug a program
- If program changes symbol table must too
- Debug Builds are larger and slower cause more stuff needed to debug
- `gcc -g hello.c -o hello` compile with g flag for symbol table

### Starting and Stopping GDB
- 3 ways to Run
  - **r** (Run Directly)
  - **r arg1 arg2** (Pass arguments)
  - **r < file1** (Feed in a file)
- **q** to quite GDB
- **help**, **h breakpoints** (gives help on breakpoints)

### Stepping Through Code
- `l` list 10 lines of code from current line
- `l 50` list line 50
- `l functionName` lists code from specified function
- `step` executes the next instruction, NOT line
- `finish` like a step out, exits the current function after execution and pauses

### Breakpoints
- Pause the program when it reaches the breakpoint
- Examine and change variables / resume execution
- `break 45` puts a breakpoint at line 45
- `break functionName` puts a breakpoint at functionName

### Watchpoints
- Pauses the program when a condition changes
  - `watch x==3` When x changes it will pause
- Good for null checking

### Scheduling in Linux
- 3 Categories
  - Real Time
    - Extremely high scheduling requirement
    - Needs guarantee on how often it will run
    - highest priority process in a system
  - IO Bound
    - Processes that spend most the time waiting for data going to or coming from the disk
  - CPU Bound
    - Processes that consume large amounts of CPU
- Time Slice - Amount of time a process can run on CPU
- Preemption - When execution is interrupted to run higher priority

#### Schedule() Function
- Runs when a new process needs to be selected for scheduling
- Called when process is blocked, waiting for a resource
- Each process can call function itself
- Device drives may call schedule as well

#### Real-Time Scheduling
- Linux has soft real-time scheduling
  - No hard real-time guarantees
- Real time processors always have higher priority than regular
- Priorities [0-99] are real time
  - saved in *rt_priority* in the *task_struct*
- Can make a process real time via system call
  - `sched_setscheduler`

#### Real-Time Policies
- First in First out (SCHED_FIFO)
  - Static Priority
  - Preempted for higher priority process
  - Runs until blocks or stops by itself, no time constraints
  - RR within same priority level
- Round-Robin (SCHED_RR)
  - Same as FIFO but time constraint of 800ms
- Normal Processes (SCHED_OTHER)

#### Multiprocessor Scheduling
- Each processor has separate run queue
- Only selects process from its own queue to run
- One processor can be idle while others have jobs, but to each their own queue
- Periodically if one processor queue is too long it might get balanced with another

### Compilers
- Translates high-level language to low-level instructions
  - High Level = Source code
  - Machine Level = Object Code
- Changes to code require recompiling

### Programming Language Components
- Lexicon
  - All legal *words* in the language
  - Meaning and type
- Syntax
  - Grammer Rules
- Semantics
  - Meaning of command

### Parsing Process
- Lexical analysis
  - Also known as csanning
  - Divides string of input characters into single elements, tokens, based on **strict** computer punctuation
- Syntactic analysis
  - Check for errors in grammar rules
- Semantic Parsing
  - Determines meaning of the string

### Optmization
- Compiler analyzes code in order to
  - Reduce amount of code
  - Remove repeated code
  - Reorganize for faster execution
  - Use resources more effectively
- Example
  - If an operation is repeated inside a for loop, but the values in the operation aren't affected by the for loop, it can be moved outside to do the same calculation

### Compiling Source Files
- `gcc -o newFileName sourceFileName.c`
  - Ex: `gcc -o a.out source.c`
  - This will take the source.c file and compile it and output it as a.out
  - adding `-g` will provide debug info
  - adding `-Wall` will provide all warnings
- `g++ -c file1.cpp` && `g++ -c file2.cpp`
  - These two commands will produce file1.o and file2.o (object files)
  - To combine them and compile we must do `g++ -o result file1.o file2.o`
    - This creates an executable file called result
- Link libraries using `-lnameofLibrary`
  - Ex: `-lm` links the math library

### Make Files
- Can declare all the files you need to compile, so dont have to re compile every file indivdually every time
- If the final output is **sum (exe)** and it contains
  - main.o
    - main.c
    - sum.h
  - sum.o
    - sum.c
    - sum.h
- We can make a *makeFile* like the following (each point+subpoint = rule for makeFile)
  - `sum: main.o sum.o`
    - `gcc -o sum main.o sum.o`
  - `main.o: main.c sum.h`
    - `gcc -c main.c`
  - `sum.o: sum.c sum.h`
    - `gcc -c sum.c`

### Organization of Compilers
- Frontend
  - Depends on Source Language
  - Lexical Analysis
  - Parsing
  - Semantic Analysis
- Optimizer
  - Independent part of compiler
  - Different optimizations are possible
  - IR to IR translation (?)
  - Very computational intensive
- Backend
  - Depends on target processor
  - Code selection
  - Code scheduling
  - Register allocation
  - Peephole optimization

### Parsing using LEX and YACC
- YACC (Yet Another Compiler Compiler)
  - LookAhead-Left-to-Right (LALR) grammar
  - YACC is a tool where you can define your own grammar rules and upon recognizing the custom defined rules it will replace them with the correct code and output a C file
- LEX is a scanner generator
  - Input is description of patterns/actions
  - Outputs a C program with function yylex() that matches patterns and performs actions per input
- Usually you get the tokens from LEX and send to YACC to parse

### Recursive Descent Parsing
- Constructs parse tree from the top and input is read left to right
- Recursively parses input to make parse tree (may require backtrack)
- If it doesn't need backtracking = predictive parsing
