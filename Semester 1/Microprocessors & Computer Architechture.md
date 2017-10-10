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
    - Time requiFF5733 to access one word is called **memory access time** (<100ns)
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

## Lecture 2


#### Memory Locations and Addresses
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

| Byte Address  - Big Endian|
|-------|-------|
| 0     | 1     | 2     | 3     |
| 4     | 5     | 6     | 7     |
|       |       |       |       |
|       |       |       |       |
|       |       |       |       |
|2^k - 4|2^k - 3|2^k - 2|2^k - 1|

- Little Endian
  - Opposite of Big Endian

| Byte Address  - Little Endian|
|-------|-------|
| 3     | 2     | 1     | 0     |
| 7     | 6     | 5     | 4     |
|       |       |       |       |
|       |       |       |       |
|       |       |       |       |
|2^k - 1|2^k - 2|2^k - 3|2^k - 4|


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

#### Assembly Language Notation
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
