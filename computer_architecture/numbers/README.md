# Numbers

Number - abstract entity

Numeral - string of symbols that represent a number in a given
system

Thus, any number can be represented by different numerals in
different numeric systems

There are two types of numeric systems:

1. Non Positional Numeric System: the value of digits in the number
is position independent (For example, Roman Numeric System)
2. Positional Numeric System: digit value depends on its position
within the number (weight)
    * Each digit represents the coefficient of a power of the base
    * Exponent is given by the position of the digit within the number

In this example:

Base: b, used symbols: 0 <= a <sub>i</sub> <= b-1
![example of number representation][example_of_positional_number_representation]

## Finite precision numbers
That is number with a finite numbers of digits. Because of this property several others are lost:
* Operators closure
* Distributive and associative properties
* Holes in the representation of real numbers

#### Examples
Let's consider rational numbers numbers with two decimal
digit after the comma

Represented interval: [-0.99, +0.99]
1. Lost closure with respect to operator +: 0.76 + 0.30 = ??? (number is out of interval)
2. Lost associativity: 0.25 + (0.90-0.30) != (0.25 + 0.90) - 0.30
3. We can't represent any additional number between 0.01 and 0.02

## Represented Interval
By representing positive integers in binary notation, n digits
(bits), cover the interval [0, 2<sup>n</sup>-1]

Therefore, to represent number X in binary we need Int(log<sub>2</sub>X + 1) bits

## Representation of positive and negative numbers
To represent Integer Relative Numbers, if the same number of
digits is used, the interval of absolute is halved

There are several notations can be used

#### Sign and magnitude
The first bit is used to denote sign 0:+, 1:-

n - 1 bits are used for magnitude

Represented interval: Represented interval: [-2<sup>n-1</sup>+1, 2<sup>n-1</sup>-1]

###### Examples

Using n=4 interval [-7, 7] is completely represented

5 0101

-5 1101

Note that 0 has two possible representations (1000 and 0000) therefore we lose 1 number (only 2<sup>n</sup>-1 numbers can be represented)

#### One's Complement
A 0 is added on left of positive numbers

To change sign the numeral is complemented bit by bit (change 0 to 1 and 1  to 0)

Positive numerals start with 0, negative ones with 1

n-1 bits are used for the magnitude

Represented interval: [-2<sup>n-1</sup>+1, 2<sup>n-1</sup>-1]

###### Example
Using n=4 interval [-7, 7] is completely represented

5 0101
 
-5 1010

Note that 0 has two possible representations (1111 and 0000) therefore we lose 1 number (only 2<sup>n</sup>-1 numbers can be represented)
#### Two's Complement
A 0 is added on left of positive numbers

Negative numbers are obtained by complementing bit by bit the
corresponding positive a and then adding 1

Positive numerals start with 0, negative ones with 1

n-1 bits are used for the magnitude

Represented interval:[-2<sup>n-1</sup>, 2<sup>n-1</sup>-1]

###### Example
Using n=4 interval [-8, 7] is completely represented

5 0101

-5 1011

Note that here we <b>don't</b> lose any number: 0 has only one representation (0000)
#### Excess Notation
Numbers are represented as a sum of the number with a power of 2
and deducing an "excess"

In practice, if we use n bits, we start counting not from 0 but from
the “excess": -2<sup>n−1</sup>

Represented interval: [-2<sup>n−1</sup> , 2<sup>n−1</sup>-1]

Practical rule: numerals are obtained by complementing the highest
digit in 2’s complement notation

###### Example
Using n=4 interval [-8, 7] excess = 2<sup>n−1</sup> = 2<sup>3</sup> = 8

5 5+8 = 13 → 1101

-6 -6+8 = 2 → 0010

Note that here we <b>don't</b> lose any number: 0 has only one representation (1000)

## Floating point representation
###### Example in base 10
Using numerals with 5 digits of the kind ± .XXX ±EE

Mantissa = ± .XXX three signed digits 0.1 ≤ m < 1

Exponent = ±EE two signed digits -99 ≤ e ≤ 99

Bias = 127 (single precision) or 1023 (double precision)

So, standart representation will be: 
`(1)^s * (1 + Mantissa) * 2^(Exponent - Bias)`

Represented numbers are:
![represented numbers][floating_point_number_representations_base_10]

Represented interval is
-.999·10<sup>-99</sup> ≤ N ≤ -.001·10 <sup>-99</sup>; .001·10<sup>99</sup> ≤ N ≤ .999·10<sup>99</sup>

### IEEE 754 Standard 
Simple precision (uses 32 bits to represent sign, exponent and mantissa)

Note that exponent is written in excess notation

|Simple precision|
|:-------------:|
|+/- (1 bit)|
|Exponent (8 bits)|
|Mantissa (23 bits)|

Double precision (uses 64 bits)

|Double Precision|
|:-------------:|
|+/- (1 bit)|
|Exponent (11 bits)|
|Mantissa (52 bits)|

There are notation using normalized mantissa or not

Some configurations of the exponent are reserved (i.e. not
standardized)


[example_of_positional_number_representation]: ./images/example_of_positional_number_representation.png
[floating_point_number_representations_base_10]: ./images/floating_point_number_representations_base_10.png
