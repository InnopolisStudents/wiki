# Sequential Logic

## State element
A memory element that contains a value, the state
of the element.

Clocking is used to update state elements.

The following diagram explains how state elements are updated.
![picture of diagram][clock_state]

The inputs to a combinational logic block come from a state
element, and the outputs are written into a state element.

Edge-triggered methodology is a clocking scheme in which all state changes occur on a clock edge.

## Latch
Latch is a circuit used to store information.
It can retain an input signal until reset by another signal

### SR Latch
![symbol of rs latch][rs_latch_symbol]

SR is for Set-Reset

Stores one bit of state Q, controls what value is being stored with S, R inputs, have invalid state when R=S=1

![picture of sr latch][sr_latch]

There are 4 cases:
R=1 and S=0, then Q=0 and not Q = 1

S=1 and R=0, then Q=1 and not Q = 0
![picture of first two cases][sr_latch_first_cases]

R=S=0, then Q = Q<sub>prev</sub>

R=S=1, then Q=0 and not Q=0. <b>Invalid State</b>
![picture of second two cases][sr_latch_second_cases]


### D Latch
![symbol of D latch][d_latch_symbol]

Improvement over SR Latch, that removes invalid state and adds clock input

Has 2 inputs:
1. CLK: controls when the output changes
2. D: the data input

![picture of d latch][d_latch]

When CLK = 1, D passes through to Q

When CLK = 0, Q holds its previous value

## Flip Flops
Flip flops are fundamental building blocks of digital electronics
systems.

A flip flop stores a single bit (binary digit) of data.

### D Flip Flop
![symbol of d flip flop][d_flip_flop_symbol]

Constructed from two cascaded D-latches, called the
master and the slave. Both are controlled by one CLK signal.

The latch labeled by L1 is called master, and the latch labeled by
L2 is called slave.
![picture of d flip flop][d_flip_flop]

It samples D on rising edge of CLK

When CLK rises from 0 to 1, it is stored
at the internal state of D flip-flop and this
state is propagated to the output Q

Otherwise, Q holds its previous value
Q changes only on rising edge of CLK and therefore called edge-triggered

### Enabled Flip Flop
![picture of enabled flip flop][enabled_flip_flop]

A D Flip Flop with additional input (EN) that control when new data (D) is stored
So if
1. EN = 1: D passes through to Q on the clock edge
2. EN = 0: the flip-flop retains its previous state

It enables signal to change the state of a flip-flop only at desired times and limits the power consumption. 

### Resettable Flip Flop
![picture of resettable flip flop][resettable_flip_flop_symbol]

A D Flip Flop with additional input (Reset) that forces internal value to 0
* Reset = 1: Q is forced to 0
* Reset = 0: flip-flop behaves as ordinary D flip-flop

![picture of resettable flip flop][resettable_flip_flop]

### Settable Flip Flop
![picture of settable flip flop][settable_flip_flop]

A D Flip Flop with additional input (Setet) that forces internal value to 1
* Set = 1: Q is set to 1
* Set = 0: flip-flop behaves as ordinary D flip-flop

## Latches vs Flip Flops
Latches
 * Latches are building blocks of sequential circuits and these can be build from logic gates
 * Latch is level-sensitive. It change the value as input change.
Flip Flops
 * Flip flops are also building blocks of sequential circuits. But, these
can be build from the latches
 * Flip Flop is edge-sensitive and only changes
state when a control signal goes from high to low or low to high

## Registers
An 8-bit register can be constructed from 8 single-bit flip-flops.
![picture of 8 bit register][8_bit_register]

## Register Files
Register file is, basically, an array of registers. It consists of a set of registers that can be read and
written by supplying a register number to be accessed.

A register file can be implemented with a decoder for each read or
write port and an array of registers built from D flip flops.



A register file with two read ports and one write port has five
inputs and two outputs.
![picture of register file][register_file_symbol]

<b>Reading a register in a register file</b>: It does not change any
state, we need only supply a register number as an input, and the
only output will be the data contained in that register.
![picture of reading in register file][register_file_read]

<b>Writing a register in a register file</b>: we will need three inputs:
a register number, the data to write, and a clock that controls the
writing into the register.

![picture of writing in register file][register_file_write]


[register_file_read]: ./images/register_file_read.png
[register_file_write]: ./images/register_file_write.png
[enabled_flip_flop]: ./images/enabled_flip_flops.png
[settable_flip_flop]: images/settable_flip_flop_symbol.png
[resettable_flip_flop]: ./images/resettabe_flip_flop.png
[resettable_flip_flop_symbol]: ./images/resettabe_flip_flop_symbol.png
[8_bit_register]: ./images/8_bit_register.png
[register_file_symbol]: ./images/register_file_symbol.png
[d_flip_flop_symbol]: ./images/d_flip_flop_symbol.png
[d_flip_flop]: ./images/d_flip_flop.png
[rs_latch_symbol]: ./images/sr_latch_symbol.png
[d_latch_symbol]: ./images/d_latch_symbol.png
[d_latch]: ./images/d_latch.png
[clock_state]: ./images/clock_state.png
[sr_latch]: ./images/sr_latch.png
[sr_latch_first_cases]: ./images/sr_latch_first_cases.png
[sr_latch_second_cases]: ./images/sr_latch_second_cases.png