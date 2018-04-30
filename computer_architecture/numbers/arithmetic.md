# Arithmetic operations on numbers

## Summation

### Integer
#### General summation
Sum in binary notation is performed bit by bit carrying the rest to
next digit

0+0=0

0+1=1

1+0=1

1+1=0 and carry 1

###### Example
![picture of the example][simple_summation_example]


#### Summation in 2's Complement
In 2’s C sum and subtraction are managed in the same way, just
throw away Carry
![picture of the example][2sC_summation_example]

If the two terms have different sign the result is always correct.
If the two terms have the same sign but the result has a different
one we have an ERROR

The sum 100 + 100 using 2 bit representation:
![picture of the example][2sC_summation_example_with_overflow]

### Floating point

#### Summation

To sum (or subtract) floating point numbers it is necessary to
scale mantissa to have the same exponents in all terms

![summation example][floating_point_summation_example]
#### Multiplication

Multiply mantissa and sum exponents

If necessary mantissa is scaled and exponent is
incremented/decremented

![multiplication example][floating_point_multiplication_example]
### Saturation Arithmetic
It is a version of arithmetic in which all operations such as
addition and multiplication are limited to a fixed range between a
minimum and maximum value.

If the result of an operation is greater than the maximum, it is
clamped to the maximum.

If it is below the minimum, it is clamped to the minimum

Saturation arithmetic enables efficient algorithms for many
problems, particularly in digital signal processing.

For example:
* Adjusting the volume level of a sound signal can result in overflow,
and saturation causes significantly less distortion to the sound than
wrap-around.

###### Example of arithmetics
If the range is from -100 to 100

60 + 30 = 90

60 + 43 = 100

(60 + 43) − (75 + 75) = 0

99 × 99 = 100

30 × (5 − 1) = 100














[simple_summation_example]: ./images/simple_summation_example.png
[2sC_summation_example]: ./images/2sC_summation_example.png
[2sC_summation_example_with_overflow]: ./images/2sC_summation_example_with_overflow.png
[floating_point_summation_example]: ./images/floating_point_summation_example.png
[floating_point_multiplication_example]: ./images/floating_point_multiplication_example.png