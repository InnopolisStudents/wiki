# Assembly Language
A pure assembly language is a language in which each statement
produces exactly one machine instruction.

To command a computer, you must understand its language
* Instructions: words in a computer’s language
* Instruction set: the vocabulary of a computer’s language

Instructions indicate the operation to perform and the operands to
use
   * Assembly language: human-readable format of instructions
   * Machine language: computer-readable format (1’s and 0’s)

Because of the close relationship between machine and assembly
languages, each different machine architecture usually has its own
assembly language (in fact, each architecture may have several), and
each is unique.


## Translation
The assembly language level differs in a significant respect from
the Microarchitecture, Instruction set architecture, and Operating
system machine levels – it is implemented by translation rather
than by interpretation.

Programs that convert a user’s program written in some language
to another language are called translators.

The language in which the original program is written is called the
source language and the language to which it is converted is called the target
language

In translation, the original program in the source language is not
directly executed. Instead, it is converted to an equivalent
program called an object program or executable binary
program whose execution is carried out only after the translation
has been completed.

In translation, there are two distinct steps:
   * Generation of an equivalent program in the target language.
   * Execution of the newly generated program.

These two steps do not occur simultaneously. The second step does not begin until the first has been completed.

In interpretation, there is only one step: executing the original
source program.
### Types of Translators

#### Assembler

When the source language is essentially a symbolic representation
for a numerical machine language, the translator is called an
assembler and the source language is called an assembly
language.

#### Compiler

When the source language is a high-level language such as Java or
C and the target language is either a numerical machine language
or a symbolic representation for one, the translator is called a
compiler.

## Assembly versus Machine Language
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

##Assembler vs High-level Languages
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

However, writing a program in assembly language takes much longer than
writing the same program in a high-level language.

It also takes much longer to debug and is much harder to maintain.
However, there are two reasons for using assembly language:
performance and access to the machine.

### Performance

An expert assembly language programmer can often produce code
that is much smaller and much faster than a high-level language
programmer can.

For some applications, speed and size are critical. For example,
smart cards, embedded applications, device drivers etc.

### Access to the machine

Some procedures need complete access to the hardware, something
usually impossible in high-level languages.

For example, the low-level interrupt and trap handlers in an
operating system, and the device controllers in many embedded
realtime systems fall into this category