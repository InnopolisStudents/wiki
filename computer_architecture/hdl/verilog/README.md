#Verilog
A high-level computer language can model, represent and simulate digital design
 * Hardware concurrency
 * Parallel activity flow
 * Semantics for signal value and time
 
The main element in the Verilog HDL is module.
Every module describes a specific device or its part.
The name of module is written after the “module” word.
The name of module must be the same as the filename.

Verilog is case sensitive.

##Module
Building block in Verilog always start with module followed by circuit name and port list and always terminates with
endmodule
Example of module for 2-1 multiplexer:
```verilog
module mux_2_1(
input x1,
input x2,
input s,
output f
);
    assign f = ( s & x1 ) | ((~ s ) & x2 ) ;
endmodule
```

Signal names in the instance port list can also be matched up with
the signal names in the module definition by name.

The port name in the module definition follows the period, and the
port expression to be connected to it is enclosed in parentheses.

Adwantage: When ports are assigned by name, there is no
ordering consideration.
##Comments
A Single line comment in Verilog starts with //

Multiline comments start with /* and end with */

Always use plenty of comments to make you code more readable

##Monitor
Verilog provides some system functions specifically for generating
input and output to help verification.

$monitor("format string", parameter1, parameter2...);
“format string”, specifies how the parameters will be displayed:
 * %d will print the variable in decimal
 * %b will print the variable in binary
 * %h will print the variable in hexadecimal
 
##Testbench
Testbench is a module which only task is
to test another module

Testbench is for simulation only, not for synthesis

Example of testbench for 2-1 mux preseted earlier:
```
module testbench;
//input and output test signals
    reg a;
    reg b;
    reg sel;
    wire y_comb;
    //creating the instance of the module we want to test
    mux_2_1 mux (a,b, sel, y_comb);
    initial
    begin
        //This will set a to 0, b for byte
        a = 1’b0;
        b = 1’b1;
        #5;
        // pause (5 units of delay )
        sel = 1 ’ b 0;
        // sel change to 0; a -> y
        #10;
        // pause (10 units of delay )
        sel = 1 ’ b 1;
        // sel change to 1; b -> y
        #10;
        b = 1 ’ b 0;
        // b change ; y changes too . sel == 1 ’ b 1
        #5;
        b = 1 ’ b 1;
        #5;
    end
    // print signal values on every change
    initial
        $ monitor ("a=%b, b=%b, sel=%b, y_comb=%b", a, b, sel, y_comb);
    initial
        $ dumpvars ; // iverilog dump init
endmodule
```
###Nets
Nets are the things that connect model components together.

They are usually thought of as wires in a circuit.

Nets should be declared before they are used.

However, if you don’t declare one before it is used in an instance
port list, it will default to a predefined net type, normally a wire.

Each bit in a net can take on one of four values:
1. 0 – represents a logic zero
2. 1 – represents a logic one
3. x – represents an unknown logic value
4. z – represents a high-impedance state

###Wires

Wires are used for connecting different elements. They can be
treated as physical wires.

They can be read or assigned. No values get stored in them.

Inside the module, the signal is written as a wire.

In verilog declared as ``wire``

###Registers
Contrary to their name, regs don’t necessarily correspond to
physical registers. They represent data storage elements in Verilog.

Values are stored in registers in procedural assignment statements.

Registers can be used as the source for a primitive or module
instance (i.e. registers can be connected to input ports)

In verilog declared as ``reg``


###Wire vs Register
reg: can be assigned to a procedural block (a block beginning
with always or initial).

wire: It can be assigned in a continuous assignment (an assign
statement) or as an output of an instantiated submodule.

Therefore, of you plan to assign your output in sequential code, such as
within an always block, declare it as a reg. Otherwise, it should be a wire, which is also the default.

###Vectors
The Verilog word for a multi-bit quantity is a vector(similar to array)

Both nets and registers can be declared as vectors. They are
declared by using a range specifier in the declaration:

``input [msb:lsb] addr;``

or

wire ``[msb:lsb] w1;``

or

reg ``[msb:lsb] r1;``

Both most significant bit (msb) and least significant bit (lsb) must
be constant valued expressions.

The bit order can be either big-endian or little-endian, i.e.
both msb < lsb and msb > lsb are allowed, therefore [3:0] and [0:3] are both legal

##Procedural Blocks
Procedural blocks are the part of the language which represents
sequential behavior.

A module can have as many procedural blocks as necessary. These
blocks are sequences of executable statements.

The statements in each block are executed sequentially, but the
blocks themselves are concurrent and asynchronous to other
blocks.

There are two types of procedural blocks:
initial blocks and always blocks.

There may be many initial and always blocks in a module.
All of them begin execution at time 0.
However, there is no defined order between them.
There is no guarantee that any statement will execute before or
after any other statement which is not in the same block unless
there is a time or event control to establish that relationship.

###Initial
All initial blocks begin at time 0 and execute the initial statement.
Because the statement may be a compound statement, this may
entail executing lots of statements.

When the initial statement finishes execution, the initial block
terminates.

If the initial statement is a compound statement, then the
statement finishes after its last statement finishes.

###Always
Always blocks begins at time 0.

The only difference between an always block and an initial block is
that when the always statement finishes execution, it starts
executing again.

Elements in an always@ block are set/updated in sequentially and
in parallel, depending on the type of assignment used. There are
two types of assignments: <= (non-blocking) and = (blocking)

They are written as follows:
```
always @ ( ... sensitivity list ... ) begin
... statements here ...
end
```
In sensitivity list you can place anything that might change and therefore activate the always block

You also can write always@(*) to activate when anything in input changes

####Non-blocking

Non-blocking assignments happen in parallel.

In other words, if an always@ block contains
multiple <= assignments, which are literally written in Verilog
sequentially, you should think of all of the assignments being set at
exactly the same time.

```
always @ ( ... sensitivity list ... ) begin
B <= A ;
C <= B ;
end
```
In this case B will be set to A's old value and C will be set to B's old value.

####Blocking

Blocking assignments happen sequentially.

In other words, if an always@ block contains multiple =
assignments.

You should think of the assignments being set one after another
```
always @ ( ... sensitivity list ... ) begin
B = A ;
C = B ;
end
```
In this case B and A will be set to A's old value.
