# Microprocessors and Computer Architecture

## Lecture 1


#### Basic Functional Units of a Computer
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
  - When operands are brought they are stoFF5733 in registers
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

#### Instructions and Programs
- Instruction specifies operation and location of data operands
- Program is a consecutive sequence of instructions
- Program and Data are stoFF5733 in main memory
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
#### Processor Components
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
  R = A - B

  if Sign(R) = Sign(B)
  elseif Sign(R) != Sign(A)
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


## Lecture 2


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
  - Addressing assigns lower addresses to more significant (LMB) bytes of word

| Byte Address  - Big Endian |
|-------|-------|
| 0     | 1     | 2     | 3     |
| 4     | 5     | 6     | 7     |
|       |       |       |       |
|       |       |       |       |
|       |       |       |       |
| 2^k - 4 | 2^k - 3 | 2^k - 2 | 2^k - 1 |

- Little Endian
  - Opposite of Big Endian

| Byte Address  - Little Endian |
|-------|-------|
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
- **Source Program** is code in assembly language
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
- Source Program -> Assembler -> Object Program (Machine Language)
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
      - Moves the Stack Pointer up 4 bytes
    - `Store Rj, (SP)`
      - Stores the new value into stack pointer
  - **Pop** takes out the top element
    - `Load Rj, (SP)`
      - Put stack pointer value into Rj
    - `Add SP, SP, #4`
      - Moves stack pointer down 4 bytes
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
-

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
-
---

## Lecture 3
