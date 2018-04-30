#Verilog
A high-level computer language can model, represent and simulate digital design
 * Hardware concurrency
 * Parallel activity flow
 * Semantics for signal value and time
 
The main element in the Verilog HDL is module.
Every module describes a specific device or its part.
The name of module is written after the “module” word.
The name of module must be the same as the filename.

##Testbench
Testbench is a module which only task is
to test another module

Testbench is for simulation only, not for synthesis

##Monitor

Verilog provides some system functions specifically for generating
input and output to help verification.

$monitor("format string", parameter1, parameter2...);
“format string”, specifies how the parameters will be displayed:
 * %d will print the variable in decimal
 * %b will print the variable in binary
 * %h will print the variable in hexadecimal