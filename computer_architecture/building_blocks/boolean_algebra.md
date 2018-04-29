#Boolean Algebra
All arithmetic operations performed with Boolean quantities have
one of two possible outcomes: either 1 or 0.

Boolean algebra could be applied to on-and-off circuits, where all
signals are characterized as either “high” (1) or “low” (0).

high = 1 = asserted = active = true

low = 0 = deasserted = inactive = false


Often a non-zero value is considered to “be evaluated” to true (but
still true is represented by 1)

#####Addition
Boolean algebra by adding two numbers together

|Addition|
|:---:|
|0+0=0|
|0+1=1|
|1+0=1|
|1+1=1|

Boolean addition corresponds to the logical function of an “OR”
gate, as well as to parallel switch contacts.
![picture of addition][boolean_function_addition]

#####Subtraction
There is no such thing as subtraction in the realm
of Boolean mathematics. Subtraction implies the existence of
negative numbers: 5 - 3 is the same thing as 5 + (-3), and in
Boolean algebra negative quantities are forbidden.

#####Multiplication
It is the same as in real-number algebra: anything multiplied by 0 is 0,
and anything multiplied by 1 remains unchanged:

|Multiplication|
|:---:|
|0∗0=0|
|0∗1=0|
|1∗0=0|
|1∗1=1|

Boolean multiplication corresponds to the logical function of an
“AND” gate, as well as to series switch contacts:
![picture of multiplication][boolean_function_multiplication]

#####Complement
 Boolean notation uses a bar above the
variable character to denote complementation.

If A = 0 then ¬A = 1 (and vice versa)

Boolean complementation finds equivalency in the form of the
NOT gate, or a normally-closed switch or relay contact.
![picture of complement][boolean_function_complement]
#####Division
There is no such thing as division in Boolean
mathematics, either, since division is really nothing more than
compounded subtraction, in the same way that multiplication is
compounded addition.

## Truth Table
Boolean functions can be fully computed using a truth table
######Example
f = a * b * c

|a|b|c|f|
|:---:|:---:|:---:|:---:|
|0|0|0|0|
|0|0|1|0|
|0|1|0|0|
|0|1|1|0|
|1|0|0|0|
|1|0|1|0|
|1|1|0|0|
|1|1|1|1|

##Boolean algebra laws
![table of boolean algebra laws][boolean_algebra_laws]

##General theorem
Any logical function can be constructed:
 * using AND gates and inverter
 * using OR gates and inverter
 
Therefore any logical function can be made of two levels with a level of or
and a level of and, plus negation

There are two “inverting” gates NOR and NAND and correspond
to inverted OR and inverted AND gates, respectively.

NOR and NAND gates are called universal, since any logic
function can be built using this one gate type

<maybe some images of such occurences>


[boolean_algebra_laws]: ./images/boolean_algebra_laws.png
[boolean_function_addition]: ./images/boolean_function_addition.png
[boolean_function_multiplication]: ./images/boolean_function_multiplication.png
[boolean_function_complement]: ./images/boolean_function_complement.png