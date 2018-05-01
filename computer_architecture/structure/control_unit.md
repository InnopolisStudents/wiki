# Control Unit

Control Unit is the core of the sequencing of operations
* Picks the new operation to be executed
* Decodes it
* Coordinates its execution

## CPU chips

The logical pinout of a generic CPU. The arrows indicate input
signals and output signals. The short diagonal lines indicate that
multiple pins are used.
![picture of pinouts][cpu_pinout]

### Type of pins
These are the different types of pins that will be found on a CPU

1. <b>Address and Data pins</b>: Sometimes an address line and a data
line are multiplexed into 1 line. Logically they are separate, but
physically they share the same pins on the chip. There may be pins
to indicate the size of the data to write: 8, 16 or 32 bits.
2. <b>Interrupts</b>: There can be different levels of interrupts. The Intel
chip has two levels of interrupts, the Motorola chip has eight.
3. <b>Bus arbitration</b>: Intel chip has Hold (Bus Request) and Hold Acknowledge (Bus Grant). Motorola has Bus Request, Bus Grant,
and Bus Acknowledge. There may be separate pins for a
coprocessor.
4. <b>Bus Control</b>: Pins to indicate if it is a memory or I/O access. It
is also possible to distinguish between code and data. There may
be a pin to indicate if the device has completed the operation.
5. <b>Cache Control</b>: Pins to allow the CPU to communicate with a
cache chip.
6. <b>Status</b>: Pins for indicating the current status of the CPU.
7. <b>Miscellaneous</b>: The RESET pin is an example of a miscellaneous
pin.





[cpu_pinout]: ./images/cpu_pinout.png