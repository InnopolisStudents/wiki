# Performance
* Rapidly changing field:
  * Vacuum tube → transistor → IC → VLSI
  * Doubling every 1.5 years (Moore's Law):
    * memory capacity
    * processor speed



## How to define performance?

###The GQM<sup id="a1">[1](#f1)</sup>
* Goal – set the goal why you measure
* Question – set suitable questions you are interested in determining
* Metrics – set up a suitable measurement device

### Performance of the computer system
Goal:
To measure how fast is a computer system

Question:
1. How long does it take for a job to run?
   * Response time
2. How many jobs can the machine run at once?
   * Throughput

Measure:

#### Execution time
Elapsed time - counts everything (disk and memory access, I/O, etc)

CPU time - time spent executing the lines of code that are ”in” our program. Doesnt count I/O or time spent running other programs. Can be broken up into system time and user time

#### Throughput
How many jobs can the machine run at once, what is the average execution rate, how much work is getting done.


* Replacing a processor with a faster yields both improves of response
time and throughput
* Adding a second processor, improves the throughput but NOT the
response time

#### Basic Formulas
Performance:

For some program running on a machine X

![picture of simple formula][performance-simple-formula]

X is n times faster than Y

![picture of performance X being better then performance Y n times][machine-X-better-n-times]

Instead of reporting execution time in seconds, we often use cycles

![picture of cycles instead of seconds][cycles-instead-of-seconds]

For a program (PGM for short here):

![picture of execution time for a program][execution-time-for-program]

Different instructions take different amounts of time. Therefore # cycles != # instructions

We have a vocabulary that relates these quantities:
* cycle time (seconds per cycle)
* clock rate (cycles per second)
* CPI - average cycles per instruction
* MIPS - millions of instructions per second

Finally, classic CPU performance equation:

![picture of the equation][cpu-time-formula]



[1](#a1). GQM Source: Caldiera, V. R. B. G., and H. Dieter Rombach. ”The
goal question metric approach.” Encyclopedia of software engineering
2.1994 (1994): 528-532.

[performance-simple-formula]: ./images/performance_simple_formula.png
[machine-X-better-n-times]: ./images/X_is_better_n_times.png
[cycles-instead-of-seconds]: ./images/cycles_instead_of_seconds.png
[execution-time-for-program]: ./images/program_execution_time.png
[cpu-time-formula]: ./images/cpu_time.png