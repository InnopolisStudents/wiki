# Assembler

* A pure assembly language is a language in which each statement
produces exactly one machine instruction.
* There is a one-to-one correspondence between machine
instructions and statements in the assembly program.

The assembler converts assembly language instruction into the
machine language equivalent.
* The assembler can also treat common variations of machine
language instructions.
* The hardware do not need to implement these instructions;
however, their appearance in assembly language simplifies
translation and programming.
* Such instructions are called pseudoinstructions
* Assemblers keep track of labels used in branches and data transfer
instructions in a symbol table.
* The table contains pairs of symbols and addresses.
* **Symbol Table** - A table that matches names of labels to the
addresses of the memory words that instructions occupy.

During this course we are going to use [MIPS](./mips) assembly language