# The Bus
Common electrical pathway between multiple devices.

Internal to the CPU to transport data to and from the ALU

External to the CPU to connect it to main memory and I/O
controllers

The bus protocol is a well-defined set of rules governing how the
bus works
* All attached devices must obey these rules
* Makes it possible for boards designed by third parties to be attached

A computer system with multiple buses:
![picture of this computer system][computer_system_with_buses]
## Concept of slaves and masters
Active devices attached to the bus that can initiate bus transfers
are called masters

Passive devices that wait for requests are called slaves

Some devices may act as slaves at some times and masters at
others

Memory can never be a master device.

|Master|Slave|Example|
|:---:|:---:|:---:|
|CPU|Memory| Fetchig instructions and data|
|CPU|I/O Device|Initiating data transfer|
|CPU|Coprocessor|CPU handling instruction of to coprocessor
|I/O Device|Memory| DMA (Direct Memory Access)
|Coprocessor|CPU| Coprocessor fetching operands from processor

## Address Lines
The more address lines a bus has, the more memory the CPU can
address directly.

If a bus has n address lines, then the CPU can use it to address 2<sup>n</sup>
different memory locations.

Wider buses are more expensive:
1. Need more wires
2. Need larger connectors
3. Take up more space on the motherboard

The number of data lines needed also tends to increase over time.

There are different ways to increase throughput of the bus:

1. decrease the bus cycle time
2. increase the data bus width
3. decrease bus transaction latency (number of cycles necessary to
transmit address and data)

Speeding up the bus can result in problems of “bus skew” since
data on individual lines travel at slightly different speeds, therefore it is better to increase the data width

We could use a multiplexed bus
1. Breaks up the bus operation into multiple steps
2. Same lines used for both data and addressing
3. Slows down bus performance

For Example: modern AXI bus
* It can transfer 128, 256 or even 512 bits in one clock cycle to
transfer to memory the whole cache line.
* On-chip buses can be very wide - 256 bits or wider

## Bus synchronization
Buses can be divided up into two categories, depending on their
synchronization:
1. Synchronous bus
   * All bus activities take an integral number of cycles, called bus cycles
1. Asynchronous bus
   * Bus cycles can be of any length required and need not all be the
same
###Synchronous bus
Example of read timings of synchronous bus:
![picture of timings][bus_reading_timings]
A synchronous bus with a 40-MHz clock, gives a clock cycle of 25 nsec.

Assume reading from memory takes 40 nsec from the time the address is stable.

It takes three bus cycles to read a word.
* MREQ indicates that memory is being accessed.
* RD is asserted for reads and negated for writes.
* WAIT inserts wait states (extra bus cycles) until the memory is
finished.

Specification of some critical times (Al in nanoseconds)

|Symbol|Parameter|Min|Max|
|:---:|:---:|:---:|:---:|
|T<sub>AD</sub>|Address output delay| |4
|T<sub>ML</sub>|Address stable prior to MREQ|2| |
|T<sub>M</sub>| MREQ delay from failing edge of φ in T<sub>1</sub>| |3|
|T<sub>RL</sub>|RD delay from failing edge of φ in T<sub>1</sub>| |3|
|T<sub>DS</sub>|Data setup time prior to failing edge of φ|2| |
|T<sub>MH</sub>|MREQ delay from failing edge of φ in T<sub>3</sub>| |3|
|T<sub>RH</sub>|RD delay from failing edge of φ in T<sub>3</sub>| |3|
|T<sub>DH</sub>|Data hold time from negation of RD|0| |

Although synchronous buses are easy to work with due to their
discrete time intervals, they also have some problems.

* Everything works in multiples of the bus cycle.
   * If the CPU and memory can complete a transfer in 3.1 cycles they
have to stretch it to 4.0 because fractional cycles are impossible.

Once a bus cycle has been chosen, and memory and I/O cards
have been built for it, it is difficult to take advantage of future
improvements in technology. The bus has to be geared to the
slowest (“legacy”) devices on the bus.

<b>The system goes at the speed of the slowest device.</b>

### Asynchronous bus

In asynchronous bus there are additional signals:
1. MSYN: Master SYNchronization
2. SSYN : Slave SYNchronization

The process of read can be described as follows:
1. The master starts as usual asserting MREQ, RD, etc.
2. Then the master asserts MSYN 
3. Seeing this, the slave device starts its work
4. When it is finished it asserts SSYN
5. Seeing this, the master reads the data from the slave
6. When it is done, it negates MREQ, RD, the address lines,
MSYN and SSYN

This completes the read, with all signals back to their original
state

Operation of an asynchronous bus.
![picture of operation][operations_asynchronous_bus]

The essential operation consists of four events:
1. MSYN is asserted
2. SSYN is asserted in response to MSYN
3. MSYN is negated in response to SSYN
4. SSYN is negated in response to the negation of MSYN

A set of signals that interlocks in this way is called a full
handshake

###### Conclusion
Despite the advantages of asynchronous buses, most buses are
synchronous since it is easier to build a synchronous system.

The CPU just asserts its signals, and the memory just reacts.
 * There is no feedback (cause and effect), but if the components have
been chosen properly, everything will work without handshaking.

###### Buses example
On-chip Buses
* Advanced eXtensible Interface (AXI) Bus: Used to connect
CPU core with GPU and L2 cache

Off-chip Buses
* Peripheral Component Interconnect Express
(PCI-Express) Bus: Used to connect toperipherals outside CPU
* Serial Peripheral Interface (SPI), Inter-Integrated Circuit
(I 2 c), Universal asynchronous receiver-transmitter(UART)
Buses: Used to connect devices like sensors and serial terminals





[operations_asynchronous_bus]: ./images/operations_asynchronous_bus.png
[bus_reading_timings]: ./images/bus_reading_timings.png
[computer_system_with_buses]: ./images/computer_system_with_buses.png
