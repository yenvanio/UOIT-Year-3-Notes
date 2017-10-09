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
  - When operands are brought they are stored in registers
  - Registers are high speed storage elements, that store one word of data
  - Access times to registers < cache memory
- Control Unit
  - Operation of all the above units is controlled by the control unit
  - Control circuitry is physically distributed throughout the computer
- All connected by Interconnection Network

##### Processor
- Logic Circuits
- Timing and Control Circuits
- Registers

##### Instructions and Programs
- Instruction specifies operation and location of data operands
- Program is a consecutive sequence of instructions
- Program and Data are stored in main memory
- *32-bit word typically holds one encoded instruction*

###### Three Basic Instructions
- Load
  - Read a data operand from memory/input device into the processor
- Store
  - Write a data operand from a register to memory/output device
- Operate
  - Perform an arithmetic/logic operation on data operands in registers

###### Sample Program
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
##### Processor Components
- Program Counter (**PC**) register holds memory address of next instruction
- Instruction Register (**IR**) holds the current instruction
- General-Purpose Registers hold data and addresses
- Control Circuits and the **ALU** fetch and execute instructions
- Processor-Memory Interface manages transfer of data between main memory and processor

###### Example of Processor Control Circuits
```
Load    R2, LOC
```
- Send address in PC to Memory; Issue Read
- Load instruction from memory to IR
- Increment PC to point to next instruction
- Send address LOC to memory; Issue Read
- Load word from memory into register R2

##### Interrupts
- A device (such as an alarm indicator) can raise an **interrupt signal** to cause a dedicated service program to be executed.
- Interrupt signal causes processor to suspend current program and execute an **interrupt-service routine**

##### Addition of Unsigned Integers
```
1         1         1
1         0         1
------    -----     1
0 (+1)    1         ------
                    1 (+1)
```

##### Addition / Subtraction of Signed Integers
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
##### Floating Point Numbers
- 32-bit signed integer numbers have limited range
- Floating-point #'s created by letting binary point **float** to the left or right

```
1 bit for sign
8 bits for a signed exponent to a base of 2
23 significant bits in the form 1.XX......X

Value: +/- 1.XX....X x 2^exp
```

##### Character Representation
- ASCII (American Standard Code for Information Interchange)
- Uses 7-bit codes
- An 8-bit *byte* is used to represent and store a character.
  - Code occupies the low-order seven bits. High-order bit set to 0
