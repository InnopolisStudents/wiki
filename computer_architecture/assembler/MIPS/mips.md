# MIPS
Microprocessor without Interlocked Pipeline Stages is a reduced
instruction set computer (RISC) instruction set architecture (ISA)
developed by MIPS Computer Systems (now MIPS Technologies).

MIPS is currently used in many embedded systems:
* Android supports MIPS hardware platforms
* DVD, Digital TV, Set-Top Box
* Nintendo 64, Sony Playstation and Playstation 2
* Cisco routers
Check out the MIPS web page for more information: www.mips.com

## Translation
* The assembly language level differs in a significant respect from
the Microarchitecture, Instruction set architecture, and Operating
system machine levels – it is implemented by translation rather
than by interpretation.
* Programs that convert a user’s program written in some language
to another language are called translators.
* The language in which the original program is written is called the
source language.
* The language to which it is converted is called the target
language.

### What is translation

* In translation, the original program in the source language is not
directly executed. Instead, it is converted to an equivalent
program called an object program or executable binary
program whose execution is carried out only after the translation
has been completed.
* In translation, there are two distinct steps:
   * Generation of an equivalent program in the target language.
   * Execution of the newly generated program.
* In translation, these two steps do not occur simultaneously. The
second step does not begin until the first has been completed.
* In interpretation, there is only one step: executing the original
source program.

### Types of tranlastion

* Translators can be roughly divided into two groups, depending on
the relation between the source language and the target language.
* When the source language is essentially a symbolic representation
for a numerical machine language, the translator is called an
assembler and the source language is called an assembly
language.
* When the source language is a high-level language such as Java or
C and the target language is either a numerical machine language
or a symbolic representation for one, the translator is called a
compiler.

*In machine language, all instructions have the same length.
*In MIPS instructions are 32 bits long.
*MIPS instructions have three different formats:

### Assembly versus Machine Language
Assembly language is easier to use than machine language
(hexadecimal). The use of symbolic names and symbolic addresses
instead of binary or octal ones makes an enormous difference.
The assembly language programmer need only remember the
symbolic names because the assembler translates them to the
machine instructions.
The assembly language programmer can give symbolic names to
memory locations and have the assembler worry about supplying
the correct numerical values.
The machine language programmer must always work with the
numerical values of the addresses. As a consequence, no one
programs in machine language today, although people did so
decades ago, before assemblers had been invented.

###Assembly versus High-level Language
The assembly programmer has access to all the features and
instructions available on the target machine. The high-level
language programmer does not.
Everything that can be done in machine language can be done in
assembly language, but many instructions, registers, and similar
features are not available for the high-level language programmer
to use.
An assembly language program can only run on one family of
machines, whereas a program written in a high-level language can
potentially run on many machines. For some applications, this
ability to move software from one machine to another is of great
practical importance.

### Why Use Assembly Language?
Writing a program in assembly language takes much longer than
writing the same program in a high-level language.
It also takes much longer to debug and is much harder to maintain.
However, there are two reasons for using assembly language:
performance and access to the machine.

###Performance versus Machine Access

Performance:
An expert assembly language programmer can often produce code
that is much smaller and much faster than a high-level language
programmer can.
For some applications, speed and size are critical. For example,
smart cards, embedded applications, device drivers etc.
Access to the machine:
Some procedures need complete access to the hardware, something
usually impossible in high-level languages.
For example, the low-level interrupt and trap handlers in an
operating system, and the device controllers in many embedded
realtime systems fall into this category