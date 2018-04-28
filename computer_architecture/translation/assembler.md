# Assembler


The assembler converts assembly language instruction into themachine language equivalent.
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