# Clock
A clock is simply a free-running signal with a fixed cycle time.

Clocks are needed in sequential logic to decide when an element
that contains state should be updated.
![picture of clock][clock]

A clock signal oscillates between high and low values. The clock
period is the time for one full cycle.

In an edge-triggered design, either the rising or falling edge of the
clock is active and causes state to be changed.

The clock determines the sequencing of events via clock cycles of constant time, aka clock periods, clock ticks or just ticks.

The duration is called cycle time

The clock rate is (tick)<sup>−1</sup>

Clock generator: Generates the signals

Clock rate is also know as clock frequency.

Clock rate (frequency) = cycles per second (1 Hz. = 1 cycle/second)









[clock]: ./images/clock.png