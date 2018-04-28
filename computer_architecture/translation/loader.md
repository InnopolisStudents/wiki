# Loader

Now that the executable file is on disk, the operating system reads
it to memory and starts it.
The loader follows these steps in UNIX systems:
1. Reads the executable file header to determine size of the text
and data segments.
2. Creates an address space large enough for the text and data.
3. Copies the instructions and data from the executable file into
memory.
4. Copies the parameters (if any) to the main program onto the
stack.
5. Initializes the machine registers and sets the stack pointer to
the first free location.
6. Jumps to a start-up routine that copies the parameters into the
argument registers and calls the main routine of the program.
When the main routine returns, the start-up routine terminates
the program with an exit system call.