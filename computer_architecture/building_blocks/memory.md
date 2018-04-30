#Memory Blocks
Registers and register files provide the basic building blocks for
small memories.
The larger amounts of memory are built using either:
* SRAMs (Static random access memories) or
* DRAMs (Dynamic random access memories)

##Static Random Access Memory
SRAMs are simply integrated circuits that are memory arrays
with (usually) a single access port that can provide either a read
or a write.

SRAMs have a fixed access time to any datum, though the read
and write access characteristics often differ.

##Dynamic Random Access Memory
In a dynamic RAM (DRAM), the value kept in a cell is stored as a
charge in a capacitor.

A single transistor is then used to access this stored charge, either
to read the value or to overwrite the charge stored there.

Because DRAMs use only a single transistor per bit of storage,
they are much denser and cheaper per bit.

##Comparison of various memory types
|Type|Category|Erasure|Byte Alterable|Volatile|Typical Use|
|:---:|:---:|:---:|:---:|:---:|:---:|
|SRAM|Read/Write|Electrical|Yes|Yes|Level 2 cache|
|DRAM|Read/Write|Electrical|Yes|Yes|Main memory (old)|
|SDRAM|Read/Write|Electrical|Yes|Yes|Main memory (new)|
|ROM|Read only|Not possible|No|No|Large volume appliance|
|PROM|Read only|Not possible|No|No|Small volume appliance|
|EPROM|Read mostly|UV light|No|No|Device prototyping|
|EEPROM|Read mostly|Electrical|Yes|No|Device prototyping|
|Flash|Read/Write|Electrical|No|No|Digital Cameras etc.|

