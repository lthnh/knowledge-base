All design inputs such as
- Device configuration
- Enviroment configuration
- Input data
- Protocol exceptions
- Errors and violations
- Delays
## Device and Enviroment Configuration
The most common reasons for missed bugs in RTL design is not enough different configurations are tried.

You can keep track of all tested combinations using functional coverage to ensure most cases have been covered.
## Input Data
Prepare transaction classes, anticipate any layered protocols and error injection, plus scoreboarding and functional coverage.
## Protocol Exceptions, Errors, and Violations
Try to provoke the hardware with ill-formed stimulus to see if it can handle it. These errors can be caught soon with writing assertions in your testbench and design code.
## Delays and Synchronization
You should pick random delays to help catch protocol bugs. Subtle bugs around boundary conditions are often revealed when realistic delays are chosen.

Certain conditions should be checked like:
- What if the inputs arrive at the fastest possible rate, but the output is being throttled back to a slower rate?
- What if the stimulus arrives at multiple inputs concurrently?
- What if the stimulus is staggered with different delays?

Use functional coverage to measure what combinations have been covered.
## Parallel Random Testing
Different seeds generate different stimulus.

When running multiple simulations in parallel, different seeds should be used to extend coverage. As each simulation results in a different output, you should plan to organize those results to measure coverage effectively (e.g. adding seeds to simulation output directory names).

You should take advantage of different characteristics of simulation enviroments to generate seeds that are unique to each other.
