# The Von Neumann Model/Architecture

Also called a stored program computer (instructions in memory).
There are two key properties:
1. Stored Program
   * Instructions stored in linear memory array and directly addressable
   * Memory is unified with instructions and data
      * The interpretation of a stored vale depends on the control signals
2. Sequential instruction processing
   * One instruction processed (fetched, executed, and completed) at a time
   * Program counter (instruction pointer) identifies the current instruction.
   * Program counter is advanced sequentially except for control transfer
instructions

##### Examples
All major instruction set architectures today use The
Von-Neumann Model (with minor variations, such as separate
instruction and data caches, and multi-core clusters). For
example: x86, ARM, MIPS, SPARC, Alpha, POWER,
