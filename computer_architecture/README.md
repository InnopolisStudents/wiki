# Computer Architecture
>I think it’s fair to say that personal computers have become the most
>empowering tool we’ve ever created. They’re tools of communication,
>they’re tools of creativity, and they can be shaped by their user.
>>Bill Gates, February 24, 2004

The science and the art of **designing**, selecting, and interconnecting
**hardware components** and designing the hardware/software **interface**
to create a computing system that meets function, performance, energy consumption

##Why is architecture important?
* For the world
   * Computer architecture provides the engines that power all of
computing
* For You
   * As computer scientists, software engineers, and sophisticated users,
understanding how computers work is essential
   * The processor is the most important piece of this story
   * Many performance (and efficiency) problems have their roots in
architecture.

## Topics
1. [Assembler](./assembler)
2. [Building block of the hardware](./building_blocks)
3. [Hardware description language](./hdl)
4. [Performance of the computer](./performance)
5. [Structure of the comuter](./structure)
6. [Process of translation](./translation)
7. [Number systems](./numbers)
8. [Various topics](./content)

### Problem Solution stack in the modern world
||
|:-------------:|
|Problem|
|Algorithm|
|Data Structure|
|User Programs|
|System Programs|
|Architecture/ISA|
|[Microarchitecture](./content/microarchitecture.md)|
|Circuits|
|Electrons|

### Architecture vs Microarchitecture
* Architecture:
   * Programmer’s view of computer
   * Defined by instructions and operand locations
* Microarchitecture
   * How to implement an architecture in hardware

##5 components of any Computer
![picture of the components][5_components_of_the_computer]


[5_components_of_the_computer]: ./images/5_compinents_of_computer.png
## Organization of the computer 
Each computing system consists of the following types of
components:
* Computational devices: one or many CPU cores, DSP, GPU
* Memory hierarchy: caches, memory controllers
* I/O devices, with memory-mapped registers
* Interconnect bus fabric that connects all computational and I/O
devices to the system memory via regular read and write requests
and DMA access from I/O device to the system memory