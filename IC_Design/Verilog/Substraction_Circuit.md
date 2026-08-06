---
id: Substraction_Circuit
aliases: []
tags: []
---
Dedicated substraction circuit can be created. But it is much more efficient to reuse existing adder circuits and take advantage of two's complement representation. For the subtrahend, we just need to add additional circuit to complement the number then use 1 as a carry in for the first full adder.

A programmable adder/subtractor can be created with the use of programmar inverter with a control signal. When subtraction enable signal is on, the circuit acts as an inverter and switch the carry in to 1. Otherwise the circuit acts as a buffer with the carry in set to 0. This can be realized with the use of XOR with control line as one of its input, the subtrahend bit for the other input.

Due to the fixed number of bit, if a carry/borrow out is generated, it is ignored. We need additional circuitry to monitor two's complement overflow. Details on situations in which overflow occurs is documented in [[Number_Systems#arithmetic-with-twos-complement]]. Based on those conditions, we can build a circuit with overflow signal line asserted when overflow occurs.

