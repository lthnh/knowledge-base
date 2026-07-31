---
id: Finite State Machine
aliases: []
tags: []
---
## What is a Finite State Machine (FSM)?
A FSM, or state machine, is a circuit that contains a pre-defined, finite number of states. The machine can only exist in one state at a time. The circuit transitions between states based on (a) triggering event(s). All possible transitions are also pre-defined.
## State Diagrams and State Transitions Table
A state diagram is a graphical way of describe the functionality of a FSM. A state diagram is a directed graph with each vertex represents a state and each edge represents a valid transition. A state transitions table is an table form equivalent to state diagram, this makes logic synthesis straight forward.

>[!info] For a FSM implemented using sequential logic storage, an evaluation of state transition occurs when the storage devices update their output values.

>[!info] Example: A system is implemented using rising edge-triggered D-flip-flop, an evaluation of state transition occurs on every rising edge of the clock.

## Types of FSM
There are two different types:
- Outputs only depends on the current state of the machine: Moore Machine. Each state will have its own output value.
- Outputs depend on both the current state and the system inputs: Mealy Machine. Outputs will associate with state transitions corresponding to the appropriate input values.jj
## Logic Synthesis for an FSM
There are three main components for a FSM:
- The state memory
- The next-state logic
- The output logic

The next-state logic block is a combinational circuit that produces the next-state signals based on the current state and any system inputs. The state memory holds the current state of the system and is updated with the next state every time a triggering event occurs. This behaviour can be modelled by D-flip-flops. The output logic block is a combinational block that creates the outputs of the system. Depending on the type of FSM, it can depend either only on current state of the machine or both the current state and current inputs to the machine.
### State Memory
The state memory is simply one or more D-flip-flops. The number of D-flip-flops required depends on how the state is encoded. Any state can be assigned an arbitrary binary value. This can be taken advantage of to minimize the circuitry needed.

There are three main *styles* of state encoding:
- Binary encoding
- Gray code encoding
- One-hot encoding

For binary encoding, with n D-flip-flops we can encode $2^n$ state.

For gray encoding, each gray code is one bit different from any of its neighbors. It's useful for a machine with linear transition sequence as it reduces the number of bit transitions. Therefore, if a machine has highly-nonlinear code transitions this approach doesn't provide any benefit. We can create n-bit gray code pattern by writing all the gray codes in a vertical axis. Then mirror them across a horizontal axis. The upper part is padded with leading 0s while the lower part is padded with leading 1s.

For one-hot encoding, each separate D-flip-flop represents a state of the machine. For example, if a machine has 3 states, it will be '001', '010' and '100'. This has two advantages. The first is the next state circuit will be simple. The second one is there will be less chances of propagation delays through the next state circuit will cause an inadvertent state to be entered.

Once the codes have been assigned to state names, each of the bits within the codes must be given a unique name. These individual signal names are called state variables. Unique variable names are needed for both current state and next-state signals. The current state variables are the outputs Q of D-flip-flops. The next-state variables are the output of the combinational next state logic circuit and are connected to the D inputs of D-flip-flops.
### Next-State Logic
The next-state logic will compute the next values for state variables. The results depend on both the current state and the inputs to the system. Note that a combinational logic function drives only one output. So dedicated combinational circuits are necessary for each state variable.
### Output Logic
The output logic will compute the output values based on the current state. And in the case of Mealy machine, it's also based on system inputs. Each output signal requires a dedicated combination circuit, as shown in the section above.
## FSM Design Process
Word Desc. -> State Diagram -> State Transition Table -> State Memory Synthesis -> Next State Logic Synthesis -> Output Logic Synthesis -> Final Logic Diagram.
## FSM Reset's Condition
It is important to has some sort of reset mechanisms to set the initial state for the FSM. Since the state memory is made up of D-flip-flops, we can use the reset lines of the D-flip-flops to set its initial condition. But this is not enough if the system have a none zero binary code initial state. To deal with this, preset lines must be include to set the D-flip-flops to one if necessary. 

Resets are often asynchronous to immediately alter the state of FSM. This is beneficial in case of clock failure.
## Determine the Maximum Clock Frequency of an FSM
Many sources of delay can determine the maximum frequency an FSM can reliably operate. They are listed below:
- $t_{CQ}$: the delay between when an input appears on the D pin of D-flip-flop to the output Q pin.
- $t_{cmb}$: the delay when signals are passing through combinational circuit.
- $t_{int}$: the delay of interconnect.
- $t_{setup}$: the minimum time in which the input signals need to be ready before the clock rising edge for D-flip-flop to not go metastable.
- $t_{margin}$: the extra padding time to ensure the system is stable when there is an extra delay in the circuit, typical 10% in modern systems.

The sum of all these delay sources constitutes the period of the clock. It is also called the period of signal. The inverse of it is frequency.

For modern D-flip-flops, $t_{CQ}$ is often larger than $t_{hold}$. This means $t_{hold}$ is inherently satisfied. But if in rare cases, $t_{hold}$ is larger than $t_{CQ}$ then it is used in place of $t_{CQ}$.

