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
