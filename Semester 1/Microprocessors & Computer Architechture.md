# Microprocessors and Computer Architecture

## Table of Contents

[Lecture 1 - Basic Structure of Computers ](#Lecture1)
<br>
[Lecture 2 - Instruction Set Architecture ](#Lecture2)
<br>
[Lecture 3 - Basic Input & Output ](#Lecture3)
<br>
[Lecture 4 - Software](#Lecture4)
<br>
[Lecture 5 - Basic Processing Unit](#Lecture5)
<br>
[Lecture 6 - Pipelining](#Lecture6)
<br>
[Lecture 7 - The Memory System](#Lecture7)
<br>
[Lecture 8](#Lecture8)
<br>
[Lecture 9](#Lecture9)
<br>
[Dictionary](#Dictionary)



<a name="Lecture1"></a>
## Lecture 1 - Basic Structure of Computers


### Basic Functional Units of a Computer
- Input Output
- Memory

  - Main Memory
    - Large # of Semi-Conductor Storage Cells
    - Each Cell stores one bit of info
    - Cells are in fixed group sizes => **words**
    - Each word has a **word length**, 16, 32, 64 which is the number of bits in each word.
    - Each word has a distinct **address** associated with it's location. (Consecutive #'s, start from 0)
    - A **word** is accessed by specifying address and issuing a control command.

  - Random-access memory (RAM)
    - A memory where any location can be accessed in a short and fixed time after specifying address.
    - Time required to access one word is called **memory access time** (<100ns)

  - Cash Memory
    - Supplementary to main memory.
    - Facilitates high instruction execution rate
    - Smaller and faster than RAM
    - Holds sections of program that are currently being executed (+ any extra data)
    - Cache is usually on the same integrated circuit chip as the processor

  - Secondary Memory
    - Primary Memory is expensive, doesn't retain info when turned off.
    - So, we use less expensive, permanent secondary storage to hold large amounts of data.
    - Access time for secondary storage > primary memory

- Arithmetic and Logic Unit (ALU):
  - Most computer operations are executed by this processor
  - Arithmetic/Logic operations are initiated by bringing operands to the processor where ALU performs operation
  - When operands are brought they are stored in registers
  - Registers are high speed storage elements, that store one word of data
  - Access times to registers < cache memory

- Control Unit
  - Operation of all the above units is controlled by the control unit
  - Control circuitry is physically distributed throughout the computer
- All connected by Interconnection Network

#### Processor
- Logic Circuits
- Timing and Control Circuits
- Registers

### Instructions and Programs
- Instruction specifies operation and location of data operands
- Program is a consecutive sequence of instructions
- Program and Data are stored in main memory
- *32-bit word typically holds one encoded instruction*

##### Three Basic Instructions
- Load
  - Read a data operand from memory/input device into the processor
- Store
  - Write a data operand from a register to memory/output device
- Operate
  - Perform an arithmetic/logic operation on data operands in registers

##### Sample Program
- C = A + B
- Given that...


| Word Address  | Values        |
| ------------- |:-------------:|
| A             | 23            |
| B             | 10            |
| C             | 15            |

```
Load    R2, A       Puts A in R2
Load    R3, B       Puts B in R3
Add     R4, R2, R3  Adds R2 and R3 into R4
Store   R4, C       Stores R4 into C
```
### Processor Components
- Program Counter (**PC**) register holds memory address of next instruction
- Instruction Register (**IR**) holds the current instruction
- General-Purpose Registers hold data and addresses
- Control Circuits and the **ALU** fetch and execute instructions
- Processor-Memory Interface manages transfer of data between main memory and processor

##### Example of Processor Control Circuits
```
Load    R2, LOC
```
- Send address in PC to Memory; Issue Read
- Load instruction from memory to IR
- Increment PC to point to next instruction
- Send address LOC to memory; Issue Read
- Load word from memory into register R2

#### Interrupts
- A device (such as an alarm indicator) can raise an **interrupt signal** to cause a dedicated service program to be executed.
- Interrupt signal causes processor to suspend current program and execute an **interrupt-service routine**

#### Addition of Unsigned Integers
```
1         1         1
1         0         1
------    -----     1
0 (+1)    1         ------
                    1 (+1)
```

#### Addition / Subtraction of Signed Integers
```
Same as Signed, but if Subtraction take the 2's complement of the number being subtracted

1's Complement = Flip all 1's to 0's and 0's to 1's
2's Complement = Take 1's Complement and add '1' to the RMB
```
- Sign Extension
  - Padding the LMB with 0's (for positive) and 1's (for negative) to go from 4-bit signed to 8-bit signed etc.

- Overflow
  - When adding (in 2's complement), if the result has a different sign then there is an overflow
  - When subtracting, if the result has a different sign than the number being subtracted from or the same sign as the subtracting number then there is an overflow

  ```
  A - B = R

  IF Sign(R) = Sign(B) OR Sign(R) != Sign(A)
  then OVERFLOW
  ```
#### Floating Point Numbers
- 32-bit signed integer numbers have limited range
- Floating-point #'s created by letting binary point **float** to the left or right

```
1 bit for sign
8 bits for a signed exponent to a base of 2
23 significant bits in the form 1.XX......X

Value: +/- 1.XX....X x 2^exp
```

#### Character Representation
- ASCII (American Standard Code for Information Interchange)
- Uses 7-bit codes
- An 8-bit *byte* is used to represent and store a character.
  - Code occupies the low-order seven bits. High-order bit set to 0

---

<a name="Lecture2"></a>
## Lecture 2 - Instruction Set Architecture


### Memory Locations and Addresses
- Memory consists of millions of cells
- **Cell** holds a bit ( 0 or 1 )
- **Word** is a group of *n* bits ( 16 - 64 )
- **Memory** is a collection of consecutive words defined by word length
- Each memory byte has a distinct **address**
- 0 -> 2^k - 1 are used as addresses for successive locations in memory
- **Address Space** is a collection of the 2^k locations
- **Memory Size** is set by k

#### Word
- Common word length is 32-bits
  - Can store 32-bit signed integer or four 8-bit bytes (ASCII Characters)
- Words in memory store data or machine instructions for a program
  - Machine instructions can require consecutive words for encoding
- Significance of a word is that most instructions operate on entire words
  - 32-bit machine has 32-bit registers and instructions for manipulating 32-bit words
  - 64 bit machine is the same ^

#### Byte Addressability
- Byte (octet) = 8bits but word length may range from 16-64 bits
- Instead of assigning address to each bit, we assign an address to each byte

| Word Address                        | Values        |
| ------------------------------------|:-------------:|
| <span style="color:#FF5733">0</span>| 23            |
| <span style="color:#FF5733">1</span>| 10            |
| <span style="color:#FF5733">2</span>| 15            |
| <span style="color:#FF5733">3</span>| 11            |
| <span style="color:#33B7FF">4</span>| 02            |
| <span style="color:#33B7FF">5</span>| 03            |
| <span style="color:#33B7FF">6</span>| 55            |
| <span style="color:#33B7FF">7</span>| 23            |
| <span style="color:#3CFF33">8</span>| 22            |

#### Endian Addressing
- Big Endian
  - Addressing assigns lower addresses to more significant bits
  - **Note** Basically puts more significant bits in LSB (Right Side)

| Byte Address  - Big Endian    |  |  |  |
|-------|-------|-------|-------|
| 0     | 1     | 2     | 3     |
| 4     | 5     | 6     | 7     |
|       |       |       |       |
|       |       |       |       |
|       |       |       |       |
| 2^k - 4 | 2^k - 3 | 2^k - 2 | 2^k - 1 |

- Little Endian
  - Opposite of Big Endian
  - **Note** Basically puts less significant bits in LSB (Right Side)

| Byte Address  - Little Endian    |  |  |  |
|-------|-------|-------|-------|
| 3     | 2     | 1     | 0     |
| 7     | 6     | 5     | 4     |
|       |       |       |       |
|       |       |       |       |
|       |       |       |       |
| 2^k - 1 | 2^k - 2 | 2^k - 3 | 2^k - 4 |


#### Word Alignment
- Number of bytes per word = power of 2
- If the word beings at a byte address that is a multiple of the number of bytes in a word, the word location has an aligned address
  - 4 bytes per word, the 4th byte, 8th byte, etc...

| Example |
|---------|
|  <span style="color:#33B7FF">0000</span>   |
|  0001   |
|  0010   |
|  0011   |   This location is an aligned address (4 bytes per word)|
|  <span style="color:#33B7FF">0100</span>   |
|  0101   |
|  0110   |
|  0111   |
|  <span style="color:#33B7FF">1000</span>  |

#### Memory Operations
- To execute instructions, word(s) must be transferred from memory to the processor
- Results must also be moved between memory and processor
- 2 basic memory operations
  - Read
    - Copies contents of memory location to the processor
      - 1.) Address loaded into Memory Address Register ( **MAR** )
      - 2.) A read signal ( read('0') ) issued by CPU
      - 3.) After memory delay, word is loaded into Memory Data Register ( **MDR** )

  - Write
    - Transfers a word from the processor to a memory location (overwrites)
      - 1.) New word loaded by CPU into MDR, desired address loaded by CPU into MAR
      - 2.) A write signal ( write('1') ) issued by CPU
      - 3.) After memory delay, word stored from MDR into desired location

#### Register Transfer Notation ( RTN )
- RTN describes hardware-level data transfers and operations
- Possible locations for transfers
  - Memory Locations
  - Processor Register
  - Registers in the I/O Subsystem
- Identify these locations symbolically with...
  - LOC, PLACE, A, VAR2 -> names that represent addresses of mem location
  - Predefined processor registers -> R0, R5 ..etc
  - Registers in the I/O Subsystem -> DATAIN, OUTSTATUS ..etc

```
' [ ] '  = contents of a location
' <-  '  = transfer to a destination

Ex: R2 <- [LOC]
- Transfers contents of LOC into memory register R2

Ex: R4 <- [R2] + [R3]
- Transfers the sum of registers R2, R3 and put it in R4

**Note**
- Right hand side is always value
- Left hand side is the location where value is to be placed
- Only contents of destination change

```

### Assembly Language Notation
- Needed to represent machine instructions and programs

```
Load    R2, LOC     =>    R2 <- [LOC]
Add     R4, R2, R3  =>    R4 <- [R2] + [R3]
```
- Commercial processors use mnemonics (LD, ST, ADD ..etc)

#### RISC
- RISC = Reduced Instruction Set Computers
- Each instruction occupies exactly 1 word
- Require Arithmetic/Logic operands to be stored in registers
- Instructions are directly executed by hardware (no interpretation)
- Only **Load** and **Store** instructions are used to access memory operands
- At the start of execution, all instructions/data stored in memory
  - Processor register contents are initially invalid
  - RISC requires register operands, data transfers required before arithmetic
    - Load source into destination
    - Load operand from memory location into processor register
  - **Addressing Mode** specifies memory location; Gives flexibility on how to access operands.

```
  C = A + B in RISC

  Load    R2, A       
  Load    R3, B       
  Add     R4, R2, R3  
  Store   R4, C     

**Note**
- Load puts the second argument into the first
- Store puts the first argument into the second

```
#### CISC
- CISC = Complex Instruction Set Computers
- Have multi-word instructions
- Allow arithmetic operands to be accessed directly from memory

#### Instruction Execution and Straight-Line Sequencing
- A 32-bit word length, byte-addressable (Each byte assigned an address) program.
- First RISC instruction at address *i* and then each consecutive instruction will be at *i*+4, *i*+8, *i*+12...etc
- Program Execution Steps
  - Processor has program counter ( **PC** ) register
  - Address *i* for first instruction is place in **PC**
  - Control circuits fetch and execute instructions one after the other
  ( **Straight Line Sequencing** )
  - During execution of instructions, **PC** is incremented by 4
  - **PC** contents are *i*+16 after Store is executed (at the end)
- Executing an Instruction is a 2-step process
  - Fetch
    - Read operation using **PC** value
    - Place data in **IR**
  - Execute
    - Control circuits examine encoded machine instructions in **IR**
    - Specified operation is performed
    - **PC** is incremented to point to the next instruction (ready for fetch)

#### Branching
- Used to repeat instructions (Loops)

```
Ex:

N is a location that holds 'n' which is the size of a list
The size is loaded into R2 and then decremented until all element
have been added to R3 (Conditional Branch goes back to Loop)

Load                  R2, N
Clear                 R3

--------LOOP----------
Determine address of "Next" number
Load it into R5
Add it to R3
--------LOOP----------

Subtract              R2, R2, #1
Branch_if_[R2]>0      LOOP
Store                 R3, SUM

```

### Addressing Modes
- Information involved in any operation performed by CPU needs to be addressed
- Any instruction issued by processor has **at least** two types of info
  - Operation to be performed (**op-code**)
  - Address info of the operand on which operation is to be performed
  (**Address Field**)
- **Addressing Mode** = different ways that specify location of operands
- Instructions can be classified on the # of operands
  - 3-address, 2-address, 1-address, 0-address instructions
- Effective Address (**EA**) is the actual address of the location containing the referenced operand in either memory or register address

#### RISC-Type Addressing Modes

| Name              | Assembler Syntax | Addressing Function |
|-------------------|------------------|---------------------|
| Immediate         | #Value           | Operand = Value     |
| Register          | Ri               | EA = Ri             |        
| Absolute          | LOC              | EA = LOC            |        
| Register Indirect | (Ri)             | EA = [Ri]           |         
| Index             | X(Ri)            | EA = [Ri] + X       |             
| Base with Index   | (Ri,Rj)          | EA = [Ri] + [Rj]    |                  

EA = Effective Address
<br>
Value = A Signed Number
<br>
X = Index Value

#### Immediate Mode
- Value of operand is *immediately* available in the instruction itself
- Ex: Load Decimal Value 1000 into register Ri
  - `Load Ri, #1000` OR `Loadi Ri, 1000`
  - The `Loadi` OR the `#1000` indicates that 1000 is the value to be loaded and not the address to be loaded from.
- **This mode basically puts a number into register directly**

#### Direct (Absolute) Mode
- Address of the memory location that contains the operand is included in the instruction
- Ex: Load the value of the operand stored in memory location 1000 into register Ri
  - Load Ri, 1000
**This mode basically references an address to get the number into register**

#### Indirect Mode
- Two types
  - Memory Indirect Addressing (*ONLY IN CISC Style*)
    - `Load   Ri 1000` Where the address 1000 points to address 10002
  - Register Indirect Addressing
    - `Load   R2,(R5)` Loads the contents of R5 directly into R2

#### Index Mode
- Add values to an **Index Register** to access other values
- The index register contains an address and by moving up or down (+- bytes) we can generate different addresses which hold different values
- Ex: Operand address is 1020, start of array is 1000
  - If start address is stored in R5
  - Can access operand by `Load     R2, 20(R5)`
  - Where the effective address is `EA=[R5]+20`

#### Relative Mode
- Same as Index mode but instead of an index register we use a **PC**
  - `Load     Ri, X(PC)`

#### Auto-increment Mode
- Similar to register-indirect addressing `Load Ri,(R2)` Where the contents of R2 are loaded into Ri
- However for auto-increment `Load Ri,(Rauto)+` The register is incremented after the operand is accessed
- **Basically a post increment**

#### Auto-decrement Mode
- Similar to Auto-increment Mode
- However for auto-decrement `Load Ri,-(Rauto)` The register is decremented before the operand is accessed
- **Basically a pre-decrement**

### Assembly Language
- Mnemonics that represent the operation codes
  - Regular: Load, Store
  - Assembly: ldw, stw
- Assembly language needs an assembler to translate to machine language
- **Source Program** is code in high-level language
- **Object Program** is code in machine language

#### Assembler Directives
- **ORIGIN** defines instruction start position
- **RESERVE** declares that a memory block is to be reserved for data
- **DATAWORD** informs assembler to assign values to certain words
- **EQU** associates name with constant value
  - `TWENTY EQU 20`
  - Not a part of the instructions but whenever `TWENTY` appears will be replaced with `20`
- **END** tells the assembler it has reach the end of the source program

#### Program Assembly and Execution
- Source Program -> Compiler = Assembly Language -> Assembler -> Object Program (Machine Language)
- Uses Directives to determine address locations
- Computes *+-offset* from present address (in **PC**) to branch target
- **Loader** places object program in memory
- **Debugger** used to track execution

#### Number Notation
- *Decimal* Numbers are used as immediate values
  - ADDI R2,R3,93 (i, replaces need for #)
- *Binary* Numbers are represented below
  - ADDI R2, R3, %01011101
- *Hexadecimal* Numbers are represented below
  - ADDI R2, R3, 0x5D

### Stacks
- Last in First Out (LIFO)
  - **Push** puts a new element at the top
    - `Subtract SP, SP, #4`
      - Moves the Stack Pointer up 4 bits
    - `Store Rj, (SP)`
      - Stores the new value into stack pointer
  - **Pop** takes out the top element
    - `Load Rj, (SP)`
      - Put stack pointer value into Rj
    - `Add SP, SP, #4`
      - Moves stack pointer down 4 bits
- Processor has a stack pointer ( **SP** )
  - Always points to the top of the processor stack

### Subroutines
- Subroutine is a block of instructions that can be called multiple times with different values (like a method in a class)
- **Call** instructions is a special type of branch
- Subroutine must return to calling program after
  - Done using a **Return** instruction
- Subroutine can be called from multiple places in the program
  - Use Subroutine Linkage Method to return to correct place
- Simplest Subroutine Linkage method is to save return address in a register ( **LR** ), Link Register

#### Subroutine Linkage
- **Call** Instruction performs two operations
  - Store **PC** contents in link register
  - Update **PC** to hold subroutine address
- **Return** Instruction returns to the program by branching indirectly to the address in the link register

- When a **Call** is executed to go to a subroutine the program counter is updated to the subroutine address and not the next instruction address
- It also saves the next instruction address in a Link Register for the **Return** instruction to use
- The **Return** call indirectly branches to the address in the link register

#### Subroutine Nesting
- Subroutines can make nested calls
  - BUT... Link Register gets overwritten each time
  - SO ... cannot trace back to the first call
- To overcome this, each consecutive sub routine call should be saved on the processor stack
- After each subroutine is finished the link-register can be updated by popping the stack

#### Parameter Passing
- Exchanging information with the subroutine
- Registers / Stacks can be used to pass info
- Load up Registers / Stacks before subroutine CALL
- Can Load / Store Multiple Registers
  - `StoreMultiple R2-R5, -(SP)`
    - Range of registers = R2, R3, R4, R5
    - -(SP) decrements the stack pointer by 4 before contents of registered are pushed
  - `LoadMultiple R2-R5, (SP)+`
    - Range of registers = R2, R3, R4, R5
    - (SP)+ increments the stack pointer by 4 as each registered is loaded
    - *This happens in reverse order because of popping a stack*

#### Stack Frame
- Locations at the top of the processor stack reserved for private work space by subroutines
- **Stack Frame** allocated on subroutine entry and deallocated on subroutine exit
- Frame Pointer ( **FP** ) register enables access to private work space for current subroutine
- In subroutine nesting, stack frame saves return address and **FP** of each caller

### Additional Instructions
- Logic Operations -> **And**, **Or**, **Not**
- First operand comes from register/memory
- Second operand can come from immediate value as well (#value)

#### AND
- Matches bits with operands and if both are 1, return 1 otherwise 0

```
Ex:   Operand 1: 0101
      Operand 2: 0011

And   Op1, Op2

Result -> Op1 -> 0001 (Because only 1 pair of matching 1 bits)

```

#### OR
- Matches bits with operands and if either/or are 1, return 1 otherwise 0

```
Ex:   Operand 1: 0101
      Operand 2: 0011

Or   Op1, Op2

Result -> Op1 -> 0111 (Because only 1 pair where both bits 0, so rest is 1)

```

#### NOT
- Returns the reverse (switches 1's and 0's)

```
Ex:   Operand 1: 0101

Not   Op1

Result -> Op1 -> 1010 (Reversed)
```

#### Shift Instructions
- Some operations need bits of an operand to be shifted left or right
- For general operands, **Logical Shift** -> **LshiftL** and **LShiftR**
  - `LShiftL Ri, Rj, count`
  - Shifts contents of Rj but number of bit positons specified in count
    - Shift Binary Left/Right = multiply/divide by 2
    - Basically moves numbers and any empty positions after shift are filled with 0's
  - Stores shifted content in Ri, Rj remains unnaffected
  - *Note* Count can be #value or register
- For signed number, **Arithmetic Shift** -> **AShiftR** and **AShiftL**
  - Preserves the sign in the MSB

```
Logical Shift: LShiftL R3, R3, #2

Before: 0     0 1 1 1 0 . . . 0 1 1
After:  1     1 1 0 . . . 0 1 1 0 0

*Shifted all bits to the left twice, so 2 placeholder 0's to fill vacant positions


Arithmetic Shift: AShiftR R3, R3, #2

Before: 1 0 0 1 1 . . . 0 1 0       0
After:  1 1 1 0 0 1 1 . . . 0       1

*Shifted all bits to the right twice, but have to perserve the sign so filled vacant positions with 1
*If the Arithmetic Shift is to the left it is the same as a logical shift because it wouldn't make sense to pad with 1's

```

#### Rotate Instructions
- Copies bits from one end to the other end (may include carry bit)
  - `RotateL R3, R3, #2` OR `RotateLC R3, R3, #2`
- Rotate amount can be in register or #value

```
Rotate Left without carry: RotateL R3, R3, #2

Before: 0     0 1 1 1 0 . . . 0 1 1
After:  1     1 1 0 . . . 0 1 1 0 1

*Shifted all bits to the left twice(ignore carry), the bits at the end are shifted back to the beginning and the last remaining bit (after rotate) is pushed to carry.

Rotate Left with carry: RotateLC R3, R3, #2

Before: 0     0 1 1 1 0 . . . 0 1 1
After:  1     1 1 0 . . . 0 1 1 0 0

*Shifted all bits to the left twice (including carry), the bits are pushed into carry and the carry bits are shifted back to the beginning

```

#### Digit Packing Example
- someone contribute from tuorial plsss

#### Multiplication and Division
- Signed integer multiplication of n-bits
  - Result can be up to 2^n bits
- `Multiply Rk, Ri, Rj    (Rk <- [Ri]x[Rj])`
- `Divide Rk, Ri, Rj      (Rk <- [Rj]/[Ri])``

#### Immediate Values with 32-bits
- Cannot load 32-bit values in one instruction
- Seperate it into 2 instructions
  - `OrHigh   R2, R0, #0x2000`
  - `Or       R2, R2, #0x4ff0`
- Result in R2 = `0x20004FF0`

#### RISC Summary
- Simple address modes
- All instructions fit in a single word
- Operations can only be performed on register operands
- Load/Store Architechture
  - Cannot transfer directly from one mem location to another
- Fast execution
- Larger Size because more instructions but simple instructions

#### CISC Summary
- Complex address modes
- Complex instructions, can span multiple words
- Operations can be performed on memory operands and register operands
- Transfer from memory location to another memory location
- Smaller Size because less instructions ubt complex instructions


---
<a name="Lecture3"></a>
## Lecture 3 - Basic Input & Output


### Accessing I/O Devices
- I/O Devices must have some kind of address
  - Referred to as **I/O** registers
- I/O devices share same address space as meomry
  - Called *Memory-Mapped I/O*
- `Load R2, DATAIN`
  - Reads data from **DATAIN** register and loads into processor register **R2**
- `Store R2, DATAOUT`
  - Sends contents of **R2** to location **DATAOUT** which is a register in an output device

#### I/O Device Interface
- Circuit between device and Interconnection network
  - Allows for data transfer
- This interface has 3 registers that the processor can access
  - **Buffer Register** -> Holds data during transfers
  - **Status Register** -> Holds information about status of device
  - **Control Register** -> Stores information that controls operations of device
- The *Memory-Mapped I/O* makes it seem like I/O registers are a part of memory
  - They are also accessed as if they were memory locations

#### Keyboard
- **KBD_DATA** = holds the character pressed by the keyboard in 8-bit register
- **KIN** = a flag that is set to 1 when a key has been pressed
  - **KIN** is part of an 8 bit register = **KBD_STATUS**
- Processor checks for **KIN** flag and if 1, processor reads **KBD_DATA** register

#### Display
- **DISP_DATA** = 8 bit register to recieve characters from processor
- **DOUT** = a flag that is set to 1 when it is ready to recieve next character
  - **DOUT** is part of an 8 bit register = **DISP_STATUS**

#### Wait Loop
- A wait loop is used to read status from keyboard

```

READWAIT:   LoadByte            R4, KBD_STATUS
            And                 R4, R4, #2
            Branch_if_[R4]=0    READWAIT
            LoadByte            R5, KBD_DATA

* Reads the KIN Flag, if 0 (nothing pressed) loop back to READWAIT,
if 1 transfer data to R5

```

#### General RISC Style I/O Programs
1. Waits for character to be entered
2. Checks KIN Flag (until 1)
3. Reads Data from KBD_DATA (Clears KIN to 0)
4. Writes into meomry
5. Wait for display to be ready
6. Check DOUT Flag (unti 1)
7. Move character read to buffer register (clears DOUT to 0)
8. If not carriage return keep going

### Interrupts
- Problems with using a wait loop is that the processor is always busy
  - waiting for status updates (KIN flag, DOUT flag)
 - Instead we can let the I/O device alert the processor when it's ready
  - Device can send an **Interrupt Request Signal** to the processor
  - Processor is not occupied with waiting anymore
- Ex: A task with lots of computation and must display results periodically
  - Can use timer circuit to send interrupts
  - Program will compute until interrupt then display then go back to computing

#### Interrupt Service Routine
- **DISPLAY** is an interrupt service routine
- NOT the same as a subroutine because an interrupt can occur at any time unlike a subroutine which has to be called
- When an interrupt occurs, the current instruction (*i*) is completed then PC is saved before switching to **DISPLAY**
- **DISPLAY** has a *Return-From-Interrupt* instruction with the address *i+1*

#### Issues for Handling Requests
- Return address must be saved in stack or register
- *Interrupt-Acknowledge Signal* must be sent from the processor to tell the device that interrupt has been recognized, which removes the interrupt request.
  - Otherwise interrupt will keep appearing even if the service routine is done

#### Enabling & Disabling Interrupts
- Processor cannot always respond immediately
- Some tasks need to be completed without interruption
- In these cases we need ways to enable and disable interrupts
  Ex: Task A cannot be interrupted, so disable when running task A and enable later

#### Event Sequence for an Interrupt
- Processor Status Register ( **PS** ) has an interrupt enable/disable bit ( **IE** )
  - Set to 1 to enable and 0 to disable interrupts
- Procedure is as follows:
1. Device sends interrupt request
2. Processor interrupts program and saves contents of **PC** and **PS** registers
3. Interrupts disabled by setting **IE** to 0 (One interrupt at a time)
4. Interrupt service routine happens, lets device known that its been acknowledged
5. Saved contents of PC and PS are restored, **IE** is set to 1 to allow interrupts

### Handling Multiple Devices

#### Polling Scheme
- idk if we even need this tbh
- but if someone wanna essplain das cooo

#### Vectored Interrupts
- A method to handle multiple device interrupts
- Reduces delay
- Each device identifeis itself with a signal or binary code
- Have a place in memory for **Interrupt Vector Table**
  - This will hold **Interrupt Vectors**
  - These vectors contain address of the interrupt service routines
- Processor will use the table to find the right interrupt routine for the given device

#### Interrupt Nesting
- Can reduce delay even more by allowing nesting
- Works by setting the **IE** bit to 0
  - Make sure to acknowledge the current request before allowing other to interrupt otherwise infinite loop
- Use priority levels to control better
- If ISR1 (Interrupt Service Routine 1) has less priority than an interrupt that occurs after it (ISR2) then ISR2 will complete before ISR1

#### Simultaneous Requests
- 2 or more requests at the same time
- if someone wanna essplain dis too das coooo

#### Controlling I/O Device Behavior
- teacher i dun know

### Processor Control Registers
- IPS
  - This is where processor status register (**PS**) is saved during an interrupt
- IENABLE
  - Has one bit per device to recognize the source its coming from
- IPENDING
  - Has one bit per device to indicate if interrupt request has been serviced or not

#### Accessing Control Registers
- Cant be accessed by Load/Store or arithmetic/logic instructions
- Can ONLY use `MoveControl`
- Ex: `MoveControl    R4, IPENDING`
  - Transfer pending interrupt request to R4
- Ex: `MoveControl    R2, PS`
  - Transfer Current processor IE setting to R2
- Ex: `MoveControl    IENABLE, R3`
  - Transfer desired bit pattern in R3 to IENABLE

#### Interrupt Process Example
- When an interrupt request goes to the processor and processor interrupts are enabled
  1. Save the contents of **PC** in register or stack
  2. Transfer contents of **PS** to **IPS** (temporarily save) and clear **IE** bit in **PS** (to allow other interrupts)
  3. Load address ILOC into program counter
- The main program intializes the interrupt process (shown below)
  1. Load address LINE into mem location PNTR
    - Interrupt service routine will use this location as a pointer to store input characters
  2. Enable interrupts in keyboard interface by setting **KIE** bit to 1
  3. Enable interrupts in processor by setting **IENABLE** bit to 1
  4. Enable processor to respond to interrupts in general by setting **IE** bit to 1 in **PS**

#### Multiple Interrupt Sources
- To use interrupts for both keyboard/display call subroutines from ILOC service routine
- Service routine reads IPENDING register
- Check which device bit is in the IPENDING
- Service routine must save/restore Link register
- Need pointer variable to indicate output character for next display

#### Exceptions
- An exception is any type of interruption during execution
- Other types of exception (other than I/O) = Recovery from errors
  - division by 0, invalid OP codes
- Steps for errors in execution
  1. After saving state, service routine executed
  2. Routine can attempt to recover, if not inform the user and end the execution
  3. Because the instruction is the cause of exception, cannot fully complete and interrupt routine will execute right away

### Bus Structure
- Single Bus Systems
  - Processor, Memory, I/O Device 1...N
- An I/O interface responds when it recognizes the address of the input device
- Interface needs to know when to
  - check address information
  - Send Input
  - Receive Output
- Two approaches for bus transfer timings
  - Synchronous
  - Asynchronous

#### Synchronous Bus
-


---

<a name="Lecture4"></a>
## Lecture 4 - Software

### The Assembly Process
- *Assembler* translates source file to object code
  - source file = code written in an IDE or text editor (Java/C++..etc)
  - object code = machine code
- Interprets addressing modes for operands
- Recognizes directives that define constants and allocate memory for that data
- Assembler uses a symbol table to store names and labels
  - When a name appears it refers to the table to replace it with a value
- **Two Pass Assembler**
  - You cant immediately know the value of all the branches when you start because you have to take the starting address and offset it
  - First Pass
    - Generate machine instructions
    - Generate Symbol Table (load names and labels in)
  - Second Pass
    - Calculate unknown branches and address using offset and replace anything that is found in symbol table

### Loading and Executing
- *Loader* performs the following operations
  - Loads object file from disk into memory
  - Address of first instruction loaded into PC
  - Starts execution of instructions

### Linker
- Using a linker you can combined multiple program files and run it as a single program
- Subroutines defined by one file can be used in another
- Linker combines all object files into an object program

### Libraries
- Can use a library and reference it in object files and use a linker to combine the library once for all times it needs to be used
- Can make library of custom subroutines in object files using *archiver*

### Compiler
- Compiler generates assembly-language file then tells assembler to make the object file
- Linker combines everything (object files, libraries) to create the final object program

#### Compiler Optimizations
- Lots of the execution time is spent in loops
- To speed it up compiler can use register to hold index values rather than accessing from memory
  - Load before loop to place initial register value
  - Store after to place final register value

#### Multiple Languages
- Once object files are created, source language is not relevant
- Linker combines object files, libraries..etc of any language

### Debugger
- Syntax errors in the source file are detected by assembler / compiler / linker

- Programming errors and bugs that lead to wrongful output can be found using a debugger
- A debugger can stop execution at points of interest
  - It displays values in registers and memory so you can maybe see what went wrong

#### Trace Mode Debugger
- Go through the code line by line to see what's happening to the values

#### Breakpoints Mode
- Stops only where breakpoints are placed, after breakpoint resumes regular execution

### Operating System
- There is a spot in memory that permanently holds an instruction needed for loading the OS.

#### Boot-Strapping Process
- Loads Memory-Resident part, gives OS control over resources
- Processor fetches first instruction from predetermined location
- Larger and larger programs transfer OS into memory to prepare for user input

#### Managing Execution of Programs
1. User enters command
2. Loader transfer code and data in object file to memory
3. Request is made to OS to read data from file
4. OS and I/O activity occur while program waits

#### Interrupts in OS
- Interrupts are used by the OS for I/O operations
- Also assign execution priorities and switch between programs
- Service routine for I/O devices is a part of the OS
- I/O makes a request through library routine that raises a software interrupt to enter the OS
- OS starts I/O activity and makes program wait
- Hardware signals the OS upon completion using an interrupt
- OS and program pass control back and forth this way

#### Multitasking
- OS uses hardware timer for *time slicing* to manage execution of multiple programs
  - Fair allocation of processor usage

```
Example of Multitasking

Programs A and B are initiated

A is executing when time slice expires, SCHEDULER is entered and registers are saved

OS then selects B, restores its values and return-from-interrupt to resume B

^ That was a switch ^

This time A calls I/O for interrupt

OS calls IOINIT (Initialize I/O) and KBDINIT (Initialize Keyboard)
Device interrupts are enabled for transfer

SCHEDULER routine in OS then selects B

Keyboard interrupt invokes IODATA routine which finds interrupt source

A made runnable, OS lets B resume

After switch, A executes again


```
---

<a name="Lecture5"></a>
## Lecture 5 - Basic Processing Unit
- Processor reads program instructions and executes them
  1. PC has address of next instruction
  2. Gets stored into IR
  3. PC gets updated by "Instruction Address Generator"
  4. Control circuit generates control signals to perform actions

**Instruction Fetch Phase** - Fetching an instruction and loading it into the IR

**Instruction Execution Phase** - Performed the operation in the instruction

### Digital Processing System
- Suppose contents of R1 are processed and being deposited in R2
- Clock signal must be used to control timing of data transfers
- Period (time between two successive rising edges) must be long enough for circuit to produce correct result

#### Multi-Stage
- A digital processing system can be broken down into simpler steps
  - Each step is a sub circuit
  - Circuits can be combined into multi-stage structure
  - n stages = n clock cycles
  - Shorter clock cycles for each step
- Multi-Stage system = Pipeline
  - Pipeline lets next instruction start before first one finished
  - Run concurrently (overlap)

#### Hardware Stages
- Some processors have set hardware stages (Lets say 5)
- Ex: `Fetch instruction AND increment PC`
- By combining two instructions into one step we can meet the 5 stage requirement
- Pipelined organizations work best when all instructions take same number of steps
  - (Each step is carried out in a separate stage)

#### Splitting Instruction Execution - 5 stages
- ALU Instructions
  - *Add R3, R4, R5*
    1. Fetch the instruction and increment the PC
    2. Decode and read contents of R4 R5
    3. Compute the sum [R4] + [R5]
    4. **No Action**
    5. Load result into R3
- Store Instructions
  - *Store R6, X(R8)*
    1. Fetch instruction and increment the PC
    2. Decode instruction and read R6 R8
    3. Compute address X + [R8]
    4. Store contents of R6 into EA from Step3
    5. **No Action**
- Summary of Actions
  - *Sample Instruction*
    1. Fetch instruction and increment PC
    2. Decode and read registers
    3. Perform ALU operation
    4. Read/Write memory data if needed
    5. Write result into register if needed

### Hardware Components

#### Register File
- Lets 2 registers be read at the same time
  - 2 separate outputs, A & B
- Has 2 address inputs to select which two registers that will be read
- Has 1 data input + address input to select the register to write the data

#### ALU
- Register File reads and passes values of registers to ALU
- Computed value is sent back and stored in register C

#### Datapath
- Instruction processing has two phases
  1. Fetch Phase
    - Decodes
    - Generates control signals for actions to take place in execution section
  2. Execution Phase    
    - Reads data operands
    - Performs operation
    - Stores result


- Hardware can be split into a five stage structure just like the instruction execution

1. Instruction Fetch
2. Decoded & Source Registers Read
3. Computation in the ALU
4. Memory Access (if needed)
5. Result is stored in destination register

**Note**  IR generates the control signals for all subsequent steps. So it must hold current instruction until execution completes **Note**

**Note** Registers need to be inserted between stages. To pass values between stages **Note**

- The hardware from stages 2-5 is known as the **DataPath**

```
Example with Datapath

Add R3, R4, R5

1.  [PC] loaded into Memory Address
    Read Memory
    Memory Data loaded into IR
    [PC] += 4

2.  Decode.
    [R4] loaded into RA
    [R5] loaded into RB

3.  ALU Computation.
    [RA] + [RB] is loaded into RZ

4.  Memory Access.
    [RZ] is loaded into RY

5.  Store Result.
    [RY] is stored in R3

```

#### Branching
- Unconditional Branch
  - Stage 3:
    - PC += Branch Offset
- Conditional Branch
  - Stage 3:
    - Compare [RA] & [RB]
    - if == then PC += Branch Offset

#### Sub Routine Calls
- Store Sub Routine Address in RA
- Store [PC] in temp
- PC = [RA]
- Return address is stored in general-purpose register LINK
  - Moves from LINK to RA then to PC

#### Memory Function Completed (MFC)
- When reading/writing to/from memory the processor generates a signal called MFC
- Basically MFC says that the read/write operations is complete
- Stage 1 must wait for MFC then proceed to next step


### Hardwired Control
- A method to implement circuitry that will generate control signals so that actions take place in correct sequence and at the correct time
  - Another method is microprogramming
- Hardwired control involves circuitry that considers *Step Counter*, *IR*, *ALU*, *Result*, *External Inputs*
  - Step Counter tracks execution progress (one clock cycle for each step)
  - Unless memory access takes longer than one cycle
- Control signal generation depends on
  - [Step Counter]
  - [IR]
  - Result of computation / comparison operation
  - External input signals (interrupt signals)
---

<a name="Lecture6"></a>
## Lecture 6 - Pipelining
- Arranging hardware to perform multiple operations simultaneously
- Same total time for each item, but *overlapped*
- **If all stages take same amount of time and there is enough work to do, then the speed up due to pipelining is equal to the number of stages in the pipeline**

### Pipeline Organization
- PC to fetch instructions
- New instruction every cycle
- Interstage buffers hold instruction specific information

### Pipelining Issues
- First instruction updates R1
- Second instruction updates R2
- Third instruction uses R1, R2 to do something BUT must wait till R1 R2 done
  - Called a hazard and needs pipelining to stall in order to produce correct output

### Data Dependencies
- `Add R2, R3, #100`
- `Subtract R9, R2, #30`
- Destination R2 in ADD is source for SUBTRACT, this is a data dependency because it needs to be carried over from add -> subtract
- Old value of R2 will be there when subtract gets to decoding (stage 2), need to stall for 3 cycles now

```
F = Fetch
D = Decode
C = Compute
M = Memory
W = Write

Clock Cycle:            1       2       3       4       5       6
Add R2, R3, #100        F       D       C       M       W
Sub R9, R2, #30                 F       D       D       D       D (Now available in Decoding)
```

### Stalling Pipeline
- Interstage buffers have information about source/destination registers for each instruction
- During Cycle 3
  - Take Destination Register in Compute Stage (Add)
  - Take Source Register in Decode Stage (Subtract)
  - See if same, is yes need to stall until Add done
- Hold interstage buffer B1 steady until Add done and then resume
- After add finishes compute, creates bubbles (idle time) in each later stage

### Operand Forwarding
- Forwards the value from first instruction compute stage to second instruction compute stage as soon as it finishes
  - Doesnt have to wait to finish all stages
  - No stalling

### Memory Delays
- Usual time to access memory (cache) is one cycle
- When we have a cache *miss* it causes a delay which delays subsequent instructions
- Even with cache *hit*, load instruction may cause short delay due to data dependency
  - One-Cycle stall is needed for the correct value to be forwarded to the next instruction
- To optimize the one-cycle-stall by inserting a useful instruction in between the two
  - If it cant find one, then automatically one-cycle-stall
  - If the processor hardware doesn't deal with dependencies then must insert an explicit NOP (no operation) instruction

### Branch Delays

#### Unconditional Branches
- If the first instruction branches to 3 instructions down the line it wont be known until the 4th cycle (after compute using PC)
- By this time, the next 2 instruction would have been loaded and then they need to be dropped (2 cycle penalty)
- To fix this we have a separate adder for branches
  - Problem occurs when computing with PC b/c it increments every cycle
  - If we have separate adder, it can be placed in decoding and only incur 1 cycle penalty

#### Conditional Branches
- Conditional branches also need a comparator in the decode stage to incur 1 cycle penalty
- Will incur 0 penalty when conditional branch is not taken

#### Branch Delay Slot
- Instead of risking the conditional discarding of an instruction
- The branch delay slot (appears right after branch) can hold the instruction BEFORE the branch
- The compiler must find the instruction before the branch and put it in the data slot, if data dependencies allow
  - If not insert explicit NOP
- That way it is always executed and no problem because needed to be executed anyway
- This is called *Delayed Branching* due to reordering - penalty is 0

#### Branch Prediction
- Assume Branch *not* taken
  - Get penalty if disproved during decode stage
  - 50% chance
- If it is a backward branch (branches to earlier line of instruction)
  - Predict that it is taken (usually in loops and is taken all but last time)

#### Dynamic Branch Prediction
- Teacher idunkno?

### Resource Limitations
- Pipeline stalls due to insufficient hardware resources to allow actions to proceed concurrently
- When two instructions want to access same cache memory, also stalls
  - Provide 2 cache memories, one for instruction, one for data

### Performance Evaluation

```
- T = Execution Time
- S = Average # of Clock Cycles it takes to fetch/execute one instruction
- R = Clock rate in cycles per second
- N = Dynamic Instruction Count
```

- Non Pipeline -> T = (N x S) / R *(Basic Performance Equation for Execution Time)*
- Non Pipeline -> Pnp = R/S *(Number of instructions executed per second)*

- Pipeline -> Pp = R *(Given S = 1 (Absence of Stalls))*
- Ideal value of S = 1
- Real value looks something like -> S = 1 + stallValue + branchPenaltyValue + cacheMissValue
  - cache miss is the most dominant
- N value shouldn't be too high because deep pipelining can cause more harm

### Superscalar Operation
- Has *fetch unit* to bring in 2 instructions every cycle
- Has *dispatch unit* to decode and send 2 instructions to execution every cycle
- Has *completion unit* to write results to registers
- Results of instructions should not be committed until prediction confirmed - **Speculative Execution**
  - Cant have instructions writing to same register at the same time now
- Data dependencies between instructions the execution units have **Reservation Stations**
- If there are no dependencies, there is no real order -> causes **Out of Order Exception**
  - Leads to *imprecise exceptions*
  - For *percise exceptions* commit results strictly in original order
- To commit in original order, can use
  - **Register Renaming**
    - Use temp registers to hold new data before safe for final update
  - **Reorder Buffer**
    - Ensure correct order by reordering
---

<a name="Lecture7"></a>
## Lecture 7 - The Memory System
- Need memory access times to be slow
- Need fast, large and inexpensive memory (cant meet all 3 at the same time)

### Basic Concepts
- Maximum Memory Size for any computer = 2^k
  - K = # of bits  
  - For 16 bit -> 2^16 = 64k
  - For 32 bit -> 2^32 = 4G
- Memory is designed to store/retrieve data in word-length quantities
- **Memory Access Time** -> Time from start to finish of a word or byte transfer
- **Memory Cycle Time** -> Min. Time delay between the start of successive transfers
- For **RAM** the access time is same, independent of location

#### Processor - Memory Interface
- The connection between processor and memory
- *Address Lines* specify memory location
- *Data Lines* transfer data
- *Control Lines* carry Read/Write and whether byte/word is being transferred

#### Cache and Virtual Memory
- Main Memory slower than processor
- **Cache Memory** is smaller but faster memory, reduces access time
  - Sometimes the cache cant hold entire programs due to capacity
  - **Virtual Memory** provides larger apparent size
    - Sections of the programs are transferred between main memory and secondary storage
    - Application program does not see this
  - Need efficient block transfers for virtual memory
    - Data always transferred in blocks that have 10/100/1000's of words

### Semiconductor RAM Memory
- Cycle Times range from 100ns to less than 10ns

#### Static RAMs and CMOS Cell
- Static memories need power to retain state
  - short access time
- Static *RAM Cell* in a chip has two cross-connected inverters to form a latch
- Chip implementation uses CMOS
  - Complementary Metal Oxide Semi-Conductor = CMOS
- Two transistors controlled by word line act as switches between cell and bit lines
- To write, bit lines are driven with desired data

#### Dynamic RAMs
- Simple for high density and lower cost
- Longer access times (outweighed by density/cost advantages)
- Consists of transistor, capacitor
- Needs to be refreshed as charge leaves capacitor
- For Read *Sense Amplifiers* check charge from cells in the selected row on bit lines
  - 1/0 if charge is above/below threshold
  - Action of sensing the bit lines also causes refresh in selected row
- For write access row and drive bit lines to change charge in cells
  - Refresh periodically to maintain charge

```
Example Questions for Memory

Type 1

32M x 8 DRAM with 16K x 16K array

16K x 2048 = 32M -> 2048 Bits
16K = 2^4 + 2^10 -> 14 bits for selector so 2^14 rows


Type 2

4M x 8bits
256K x 1bit

256K x 16 = 4M
1bit x 8 = 8bits

16 rows x 8 bit columns

```

#### Dynamic RAM (cont'd)
- Fast Page Mode
  - Transfer consecutive data faster
  - page = large block of data

#### Synchronous DRAMs
- Operations synchronized with clock signal
- Chips include data registers and address latches
- New access operations can be initiated while data being transferred
- Memory controller initializes mode register
  - Specifies burst length fir block transfer
  - Able to set delays for timing control

#### Efficient Block Transfers
- Asynchronous = longer delay from CAS for each column
- Synchronous = reduce delay by having CAS once for initial column
- Burst length determines # of transfers

#### Double Data Rate SDRAM
- Transfer on rising and falling edges
- Doubles rate after RAS/CAS
- Needs complex circuitry

#### Address Decoder
- 2M word-addressable memory needs 21 bits
- Each chip has 19 address bits(0-18) ((512K) 2^10 = K, 2^9 = 512)
- Bits 19 & 20 are used for 2 bit decoder to select one of 4 groups (rows)

#### Dynamic Memory Systems
- SIMMs = Single In Line Memory Modules
- DIMMs = Dual In Line Memory Modules

#### Memory Controller
- Handles multiplexing and proper timing of control signals for DRAM

### Read Only Memory
- Non Volatile storage (retains info on power off)

#### Basic ROM Cell
- ROM only has its contents written once (during manufacturing)
- Contains a single transistor switch for bit line
  - If transistor is connected to ground, bit line voltage ~= 0
  - Else it is high ~= 1

#### PROM
- Programmable ROM can be written after manufacturing
  - A fuse (point P) is burned out with a high current pulse

#### EPROM
- Erasable Programmable ROM
  - Uses transistor instead of fuse at point P
  - Transistor is off (open circuit)
  - Turns on when charge is injected at point P
  - Uses UV light to remove charge and erase ROM

#### EEPROM
- Electrically Erasable ROM
  - Erase individual cells
  - programmed, erased, reprogrammed
  - Different voltages for each operation

#### Flash Memory
- Based on EERPROM
- Higher Density, Lower Cost
- Writing a cell must first
  - read block
  - erase block
  - write block again

### Direct Memory Access (DMA)
- Manages transfer of larger blocks of data between memory and I/O

#### DMA Controller
- Shared by many I/O devices
- Performs memory access instead of processor
- Tracks progress with address counter
- Processor interrupt used to signal completion

### Memory Hierarchy
- Memory should be fast, large, expensive
- Cannot have all
  - Use memory hierarchy to make it seem like its fast and large
- Key is to bring data that is going to be used as close to the processor as possible to reduce access time
- Processor
- Registers (on Processor)
- Primary Cache (L1 on Processor)
- Secondary Cache (L2 on Processor)
- Main Memory
- Secondary Memory

### Cache Memory
- Between main memory and processor
- Makes main memory seem faster to the processor
  - Achieved by *locality of reference*
- Temporal Locality
  - Data that has been accessed recently are likely to be accessed again very soon
- Spatial Locality
  - Nearby data is likely to be accessed soon after current access
  - To exploit this, transfer cache block with multiple words from memory
    - Later accesses to nearby words are fast
- Mapping Function determine where a block in memory is to be put in the cache
- When cache is full, replacement algo determine which block to remove

#### Cache Operation
- Processor issues Read/Write as if accessing main memory
- First Cache is checked
  - If resent then read/write *hit* occurs
  - If read hit, cache provides info
  - If write hit
    - **Write-Through Protocol**
      - Update Cache and memory
    - **Write-Back Protocol**
      - Only update Cache, Memory is updated when block replaced
  - Need *Dirty Bit* to mark blocks that are updated in cache

#### Cache Misses
- Read Miss
  - Block with desired word is transferred from mem to cache
- Write Miss
  - With *Write Through Protocol*, info is written to mem
  - With *Write Back Protocol*, transfer block with word to cache
    - Overwrite cached block with new word
- To avoid pipeline stalling use separate caches for instruction and data so we can run LOAD and STORE in parallel

#### Mapping Functions
- Block of words must be transferred from mem to cache after miss
- Mapping function determines location of placement
  - Direct Mapping
  - Associative Mapping
  - Set-Associative Mapping

#### Direct Mapping
- To find # of bits for word
  - 2^x = # of words cache can hold
  - Ex: 2^3 = 8 (Cache capable of holding 8 32bit words)
    - Bits for word = 3
- To find # of bits for block
  - #of blocks = Total Capacity Word / # of Words in block
  - Ex: Capable of holding 8 32bit words, Each block has 2 32bit words
  - #of Blocks = 8/2 = 4
  - #of bits for Block = 2^2 = 4
    - = 2 bits
- After finding all the bits for Block, Word, rest of bits are for Tag
- Convert all hex addresses to binary and split by Tag, Block, Word

Example:

|Hex Address|Tag|Block|Word|
|-----------|---|-----|----|
|208|0010000|01|000|
|20C|0010000|01|100|
|2F0|0010111|10|000|
|2F4|0010111|10|100|
|200|0010000|00|000|
|204|0010000|00|100|
|208|0010000|01|000|
|20C|0010000|01|100|
|218|0010000|11|000|
|21C|0010000|11|100|
|248|0010010|01|000|
|24C|0010010|01|100|

- Place the Values in the correct block and if it is already in the cache add a hit marker and if not add a miss marker

|Block Position|Contents|
|--------------|--------|
| 0 = 00 | 200 |
| 0 = 00 | 204 |
| 1 = 01 | 208 -> 248 |
| 1 = 01 | 20C -> 24C |
| 2 = 10 | 2F0 |
| 2 = 10 | 2F4 |
| 3 = 11 | 218 |
| 3 = 11 | 21C |

- When doing a second pass use the initial values and repeat

#### Associative Mapping
- Same thing as before but now there is a counter
- Increment counter on each cache entry
- Counter is set to 0 and everything else is incremented by 1 on a **Hit**
- When cache is full and you need to replace, find the highest counter and set it to 0 and increment the rest

|Block Position|Contents|Counter|
|--------------|--------|-------|
| 0 = 00 | 200 |0-1-2-0-1-2|
|| 204 ||
| 1 = 01 | 208 -> 248 |0-1-2-3-0|
|| 20C -> 24C ||
| 2 = 10 | 2F0 |0-1-2-3|
|| 2F4 ||
| 3 = 11 | 218 |0-1|
|| 21C ||

#### Set-Associative Mapping
- Same as associative mapping but split into sets
- Find Sets and Bits for Set
  - #of Blocks / #-way associative (2way 4way etc) = #of Sets
  - 2^1 = 2
    - 1 Bit for 2 way set associative mapping

|Set|Block Position|Contents|Counter|
|---|--------------|--------|-------|
|Set 0| 0 = 00 | 200 |0-1-2-0-1-2|
||| 204 ||
||| 1 = 01 | 208 -> 248 |0-1-2-3-0|
||| 20C -> 24C ||
|Set 1| 2 = 10 | 2F0 |0-1-2-3|
||| 2F4 ||
||| 3 = 11 | 218 |0-1|
||| 21C ||

#### Stale Data
- Valid Bit = 1 when placed in cache
- Cache may contain stale data from memory
  - Cleared to 0 for those blocks

#### LRU Algorithm
- Least Recently Used Replacement Algorithm
- Basically when cache is full and you need to replace
  - Take the one with the highest counter and replace it

#### Virtual Memory
- A large program may not be entirely in main memory
- Parts of the program that are needed are automatically loaded into memory
  - This replaces other parts of the program using *virtual memory*
- Binary addresses issued by the processor are called *virtual*
  - Gets translated into physical address
- Need **Memory Management Unit (MMU)** to keep track of which parts of virtual address space are in physical memory
- MMU manages virtual to physical address mapping
  - When no physics address exist, transfer from disk to mem with DMA

#### Address Translation
- Assume all programs are compost of pages (fixed length units)
- Split virtual address into 2 fields
  - Lower bits = Offset to word within page
  - Upper bits = Virtual Page # (VPN)
- VPN replaced with page-frame bits (a space in memory that holds a page)
- Page table stored in main memory
  - Provides info to perform address translation

#### Page Table
- MMU needs to know where the page table is to do the address translations
- Page table base register has starting address of page table
- Adding VPN to the base gives location of page

#### Translation Lookaside Buffer (TLB)
- Holds recently accessed entries of page table
- Searches are performed on TLB first, if no match pull up the full table and search

#### Page Faults
- Occurs when virtual address has no corresponding physical address

### Secondary Storage

#### Magnetic Hard Disks
- Computers often use magnetic hard disks for large secondary storage devices
- Two components involved in time delay between disk receiving address and beginning of data transfer
  - Seek Time
    - Time required to move the read/write head to the correct track
  - Rotational Delay
    - Time taken to reach addressed sector after read/write head positioned correctly
- Access Time = Seek Time + Rotational Delay
---

<a name="Lecture8"></a>
## Lecture 8
---

<a name="Lecture9"></a>
## Lecture 9
---

<a name="Dictionary"></a>
## Dictionary
| Term | Definition |
|------|------------|
| RAM  | Random access memory. Temporarily saves stuff in memory. |
| ROM  | Read only memory. Retains memory even after power off. |
| DMA  | Direct memory access, allows computers to access main system memory, independent of CPU |
| OS | Operating System |
| Cell | Holds a bit (0 or 1)|
| Word | Group of n bits (16-64) |
| Memory | Collection of words |
| Load |  Load R2, R3 = Loads R3 into R2; Loads from memory to register |
| Store | Store R2, R3 = Stores R2 in R3; Stores from register to memory |
| Move | Move R2, R3 = Copies R3 into R2; Copies from memory to register |
| PC | Program Counter = holds memory address of next instruction |
| IR | Instruction Register = holds current instruction |
| Byte Addressability | Assign addresses to each byte instead of each bit |
| Big Endian | Assign lower address to more significant bits = puts significant bits on the right side |
| Little Endian | Assign lower address to less significant bits = puts less significant bits on the right side |
| Word Alignment | If the address is multiple of number of bytes it is aligned = 4byte word so every 4th byte location |
| MAR | Memory Address Register |
| MDR | Memory Data Register |
| RTN | Register Transfer Notation |
| RISC | Reduced Instruction Set Computers |
| CISC | Complex Instruction Set Computers |
| Straight Line Sequencing | Executing instructions one after the other |
| Op-Code | Operation to be performed |
| Address Field | Address Information of the operand on which an operation will be perfomed |
| EA | Effective Address = Address of the location containing the referenced operand |
| Immediate Mode | Puts a number directly into register = Load R2, #1000 OR Loadi R2, 1000 |
| Direct Mode | References an address to get number into register = Load R2 1000 |
| Indirect Mode | Points to an address which points to another address |
| Index Mode | Add values to index register and access by adding bytes = 4(R2) = contents of address in R2 + 4 bits|
| Relative Mode | Same as index but use program counter |
| Auto-increment | Loads into register then increments the value by amount specified, if not specified its 4 bits|
| Auto-decrement | Decrements and then loads into register |
| Source Program | High-level language code |
| Object Program | Machine language code |
| Compiler | Turns source program into assembly language |
| Assembler | Turns assembly language into machine code |
| ORIGIN | Defines instruction start position |
| RESERVE | Declares a memory block that is to be reserved for data |
| DATAWORD | Informs assembler to assign values to certain words |
| EQU | Sets a keyword to a value -> TWENTY EQU 20, whenever TWENTY called it will be 20 |
| END | Tells assembler that it's the end of the program |
| Loader | Places Object program in memory |
| Debugger | Tracks execution |
| LR | Link Register = stores address to return to after sub routine call |
| Stack Frame | Allocated space for subroutine to use (only when subroutine called) |
| FP | Frame Pointer  = register that lets you access private workspace for current subroutine |
| AND | If two binary numbers both have 1's in the same position it returns 1 for that position otherwise 0 |
| OR | If two binary numbers have at least one 1 in the same position it returns 1 for that position otherwise 0 |
| NOT | returns the inverse of the binary number |
| LShiftL | Logical shift to the left, just shifts numbers to the left and fills empty spots on the right with 0's |
| LShiftR | Logical shift to the right, just shifts numbers to the right and fills empty spots on the left with 0's |
| AShiftL | Same as LShiftL |
| AShiftR | Arithmetic Shift to the right, just shifts numbers to the right and fills empty spots on the left with the MSB(Sign) |
| RotateL | Similar to shift but bits do not get lost, the bits that get pushed off rotate around to the other end |
| RotateR | Same as RotateL just different direction |
| RotateLC | Rotates but includes the carry in the rotation |
| RotateRC | Same as RotateLC just different direction |
| DATAIN | Loads data from I/O into register |
| DATAOUT | Outputs from register to output device |
| Buffer Register | Holds data during transfers |
| Status Register | Holds info about status of device |
| Control Register | Holds info about control operations |
| KBD_DATA | Holds character pressed by keyboard in 8bit register |
| KIN | Flag that sets to 1 when key pressed |
| KBD_STATUS | 8 bit register that holds KIN |
| DISP_DATA | 8 bit register to receive characters from processor |
| DOUT | Flag that is set to 1 when its ready to receive next character |
| DISP_STATUS | 8 bit register that contains DOUT |
| Interrupt Request Signal | Sends Signal to the processor when device has stuff to send |
| Interrupt Acknowledge Signal | Sent from processor to tell device that the interrupt signal was received |
| PS | Processor Status Register |
| IE | Interrupt Enable/Disable Bit |
| Interrupt Vector | Contain address of interrupt service routines |
| Interrupt Vector Table | Place in memory for Interrupt Vectors |
| IPS | Processor Status Register is saved here during an interrupt |
| IENABLE | Has one bit per device to recognize where its coming from |
| IPENDING | Has one bit per device to indicate if interrupt request has been serviced |
| MoveControl | Command to transfer between control registers and regular registers |
| Assembler | Assembler translates source file to object code |
