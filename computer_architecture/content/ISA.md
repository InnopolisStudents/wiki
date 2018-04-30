# Instruction Set Architecture
Interface between hardware and low-level software. Standardizes instructions, machine language bit patterns, etc.
* Advantage: different implementations of the same architecture
* Disadvantage: sometimes prevents using new innovations

## Classification of Instruction Sets
The instruction sets can be classified by
* Number of addresses (1,2,3...)
* Operand internal storage inside the CPU;
* Number of explicit operands per instruction;
* Operand location;
* Operations;
* Type and size of operands.

### Based on internal storage

The type of internal storage in the CPU is the most basic
differentiation. The major choices are
1. Stack-based architecture
2. Accumulator-based architecture
3. Register-Set based architecture

#### Stack-based architecture
A stack machine has a stack as a part of the processor state. No registers, No explicit operands in ALU

Typical operations: push, pop, +, *, ...

Instructions like + implicitly specify the top 2 elements of the
stack as operands.

###### Advantages
* Short instruction
* Easy to write compiler
* Simple model of expression evaluation
* Good code density
###### Disadvantages
* Stack is a bottleneck
* A stack can’t be randomly accessed. It makes it difficult to
generate efficient code.

###### Example
The code segment for C = A + B 
```
Push A
Push B
Add
Pop C
```

#### Accumulator-based architecture
Single register A

One explicit operand per instruction

Two instruction types: op (A := A op *M) and store (*M := A)

###### Advantages
* Short instructions possible
* Minimal internal state

###### Disadvantages
* High memory traffic – many loads and stores
* Since accumulator is only temporary storage, memory
traffic is high.

###### Example
The code segment for C = A + B
```
Load A
Add B
Store C
```

#### Register-based architecture
All operands are explicit either registers or memory locations

General purpose registers (GPR)

###### Advantages
* Allows fast access to temporary values
* Permits clever compiler optimization
* Reduced traffic to memory
* Most general model for code generation
###### Disadvantages
* All operands must be named, leading to longer instructions

###### Example
The code segment for C = A + B
```mips
load $t0, A
load $t1, B
add $s0, $t0, $t1
```
### Based on Complexity metric
An ISA may be classified by architectural complexity.
#### Complex Instruction Set Computer (CISC)
It has many specialized instructions, some of which may only be
rarely used in practical programs.
#### Reduced Instruction Set Computer (RISC)
It simplifies the processor by efficiently implementing only the
instructions that are frequently used in programs, while the less
common operations are implemented as subroutines.
#### CISC vs RISC

|CISC|RISC|
|:---:|:---:|
|Multiple instruction sizes and format|Instruction of same set with few formats|
|More addressing modes|Fewer addressing modes|
|Complexity lies in microprogram|Complexity lies in compiler|
|Pipelining is difficult|Pipelining is easy|
|Emphasis on hardware|Emphasis on software|

