To calculate transient response, we typically start with physical modeling. First we derive differential equation from physical modeling. Then we solve this equation and the result is the *transient response*. The delay is the amount of time it takes for output to reach $V_{DD}$/2.

The differential equation is based on charging and discharging of the capacitances in the circuit.

In an integrated circuit, capacitance usually consists of the gate capacitance of the load along with the diffusion capacitance of the driver's own transistors. Wires that connect transistors together often contribute to a majority of the capacitance.

The transistor's current depends on both the input (gate) and output (source/drain) voltages. (As transistor has capacitance that related by this equation $I=C\mathrm{d}V/\mathrm{d}t$.


