# MIPS
Microprocessor without Interlocked Pipeline Stages is a reduced
instruction set computer (RISC) instruction set architecture (ISA)
developed by MIPS Computer Systems (now MIPS Technologies).

## Operations on the hardware
Every computer must be able to perform arithmetic

Add and subtract consists of three operands

Two sources and one destination
```
add a, b, c #a gets b + c
```
All arithmetic operations have this form. Arithmetic instructions use register operands

MIPS has a 32 × 32-bit register file, that a numbered from 0 to 31

Any 32-bit data is called a “word”

###### Example
C code
```C
f = (g + h) − (i + j);
```
f, . . . , j in $s0, . . . , $s4

Compiled MIPS code
```mips
add $t0, $s1, $s2# t0=g+h
add $t1, $s3, $s4# t1=i+j
sub $s0, $t0, $t1# s0=f
```

## Memory Operands
Main memory used for composite data
 * Arrays, structures, dynamic data

To apply arithmetic operations
* Load values from memory into registers
* Store result from register to memory

Memory is byte addressed
* Each address identifies an 8-bit byte

Words are aligned in memory

* Accessing word should be a multiple of 4 bytes align
* Accessing the half-word should be 2 bytes align

MIPS architecture processors can be configured to run either in
big or in little endian mode.
* Big Endian: Least significant byte has highest address
* Little Endian: Least significant byte has lowest address
###### Example
Word x value 0x01234567, with address &x is 0x100

Big Endian

|0x100 |0x101| 0x102| 0x103
|:---:|:---:|:---:|:---:|
|01|23|45|67|

Little Endian

|0x100 |0x101| 0x102| 0x103
|:---:|:---:|:---:|:---:|
|67|45|23|01|

###### Another example

C code
```C
g = h + A[8];
```
g in $s1, h in $s2, base address of A in $s3

Compiled MIPS code
```mips
lw $t0, 32($s3)
add $s1, $s2, $t0
```
Index 8 requires offset of 32. This is because in MIPS, words must start at addresses that are multiples of 4. This requirement is called an alignment restriction.
Alignment leads to faster data transfers

### Registers vs Memory
Registers are faster to access than memory
* Operating on memory data requires loads and stores which lead to more instructions to be executed

Compiler must use registers for variables as much as possible
* Only spill to memory for less frequently used variables
* Register optimization is important

## Immediate operands
Constant data specified in an instruction
```mips
addi $s3, $s3, 4
```
No subtract immediate instruction. Just use a negative constant
```mips
addi $s2, $s1, −1
```
MIPS register 0 ($zero) is the constant 0. It cannot be overwritten and i iuseful for common operations

For Example: move between registers
```mips
add $s2, $s1, $zero
```
## Representing Instructions
Instructions are encoded in binary called machine code. In particular, MIPS instructions are encoded as 32-bit instruction words

## MIPS register names and conventions
![picture of registers][mips_register_name]

## MIPS R-format instructions
|op|rs|rt|rd|shamt|funct|
|:---:|:---:|:---:|:---:|:---:|:---:|
|6 bits|5 bits|5 bits|5 bits|5 bits|6 bits|

Instruction fields
* op: operation code (opcode)
* rs: first source register number
* rt: second source register number
* rd: destination register number
* shamt: shift amount only for shift instructions
* funct: function code (extends opcode)


###### Encoding example
```mips
add $t0, $s1, $s2
```
|Special|$s1|$s2|$t0|0|add|
|:---:|:---:|:---:|:---:|:---:|:---:|
|0|17|18|8|0|32|
|000000|10001|10010|01000|00000|100000|
Final encoded instruction: 00000010001100100100000000100000<sub>2</sub> = 02324020<sub>6</sub>


### Logical operations
Instructions for bitwise manipulation:
![picture of instructions][logical_operations]
#### Shifts
Shift left logical
* Shift left and fill with 0 bits
* sll by i bits multiplies by 2<sup>i</sup>

Shift right logical
* Shift right and fill with 0 bits
* srl by i bits divides by 2<sup>i</sup> (unsigned only)

Shift arithmetical
* Left shift close to be identical (except exceptions)
* Shift right different in sign bit which is used as filler (sra operation)

###### Examples
Shift left logical

* Original pattern 10100111
* Resulting pattern 01001110

Shifted left by 1
```mips
sll d, s, shft
# $d gets the bits in $s
# shifted left logical
# by shft position
```

Shift right logical
* Original pattern 1010 0111
* Resulting pattern 01010 011
* Resulting pattern if shift is arithmetical 11010 011
```mips
srl d, s, shft
# $d gets the bits in $s
# shifted right logical
# by shft positions

# for arithmetic use sra
# in this case sign at the msb is extended 
```
#### Others
###### Example of and operation
```mips
and $t0, $t1, $t2
```
* $t2 0000 0000 0000 0000 0000 1101 1100 0000
* $t1 0000 0000 0000 0000 0011 1100 0000 0000
* $t0 0000 0000 0000 0000 0000 1100 0000 0000

###### Example of or operation
```mips
or $t0, $t1, $t2
```
$t2 0000 0000 0000 0000 0000 1101 1100 0000
$t1 0000 0000 0000 0000 0011 1100 0000 0000
$t0 0000 0000 0000 0000 0011 1101 1100 0000

###### Not
Just inverts every 1 to 0 and every 0 to 1
###### Example of nor operation
```mips
nor $t0, $t1, $zero
```
$t1 0000 0000 0000 0000 0011 1100 0000 0000
$t0 1111 1111 1111 1111 1100 0011 1111 1111
## MIPS I-format instructions
|op|rs|rt|address or constant|
|:---:|:---:|:---:|:---:|
|6 bits|5 bits|5 bits|16 bits|

Instuctions fields
* op: operation code (opcode)
* rs: first source register number
* rt: destination or source register number
* Constant: –2<sup>15</sup> to +2<sup>15</sup>-1
* Address: offset added to base address in rs


## MIPS J-format instructions
|op|address|
|:---:|:---:|
|6 bits|26 bits|
Jump (j and jal) targets could be anywhere in text segment, therefore we need to encode full address in instruction

(Pseudo) Direct jump addressing
* It takes the upper four bits of the program counter, concatenated
with the 26 bits of the direct address from the instruction,
concatenated with two bits of 00


## Making decisions

Branch to a labeled instruction if a condition is true, otherwise, continue sequentially

* beq rs, rt, L1
   * if (rs == rt) branch to instruction labeled L1
* bne rs, rt, L1
   * if (rs != rt) branch to instruction labeled L1
* j L1
   * unconditional jump to instruction labeled L1

Branch instructions specify: opcode, two registers, target address

Most branch targets are near branch, goes forward or backward

PC(program counter)-relative addressing
* This mode can be used to load a register with a value stored in
program memory
* Target address = PC + offset × 4
* PC already incremented by 4 by this time

###### Example
C Code
```c
if ( i == j )
    f = g + h;
else
    f = g - h;
```
MIPS Code
```mips
bne $s3, $s4, Else # go to Else if i!=j
add $s0, $s1, $s2 # f = g + h (skipped if i!=j)
j Exit #go to exit
Else: sub $s0, $s1, $s2 #f = g - h (skipped if i=j)
Exit:
```








[logical_operations]: ./images/logical_operations.png
[mips_register_name]: ./images/mips_register_names.png