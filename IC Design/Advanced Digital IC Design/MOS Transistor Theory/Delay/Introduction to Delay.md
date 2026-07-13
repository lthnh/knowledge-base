## Definitions
*Propagation delay time* $t_{pd}$ is the maximum time from the input crossing 50% to the output crossing 50%.
*Contamination delay time* $t_{cd}$ is the minimum time from the input crossing 50% to the output crossing 50%.
*Rise time* $t_r$ is the time for a waveform to rise from 20% to 80% of its steady-state value.
*Fall time* $t_f$ is the time for a waveform to fall from 80% to 20% of its steady-state value.
*Edge rate* $t_{rf}=(t_r+t_f)/2$.

We sometimes differentiate between the delays for the output rising and output falling.
Rise/fall times are also sometimes called *slopes* or *edge rates*.

The gate that charges or discharges a node is called the *driver* and the gates and wire being driven is called the *load*.

Propagation delay is usually the value of interest, often simply called *delay*.

A *timing analyzer* computes the arrival times or the latest time each node in a block of circuit will switch.
The *arrival time* $a_i$ at internal node $i$ depends on the propagation delay of the gate driving $i$ and the arrival times of the inputs to the gate:

$$
a_i = \max_{j \in \mathrm{fanin}(i)} \{ a_j \} + t_{pd_i}
$$

The timing analyzer computes the arrival times at each node and check that the output arrives at their required time.

The *slack* is the difference between the required and arrival time. *Positive slack* means the circuit meets the timing. *Negative slack* means the circuit does not.

![[example-arrival-times.png|400]]

In the graph above, if the output is required at 200 ps, the circuit has 60 ps of slack.

A practical timing analyzer extends this result with a number of effects like
- Arrival times and propagation delays are defined separately for rising and falling transitions.
- The delay of the gate may be different from different inputs.
## Timing Optimization
In real circuits, there are a number of *critical paths* that limit the operating speed of the system.

The critical paths can be affected at four main levels:
- The architectural/microarchitectural level
- The logic level
- The circuit level
- The layout level

Most leverage is achieved in the microarchitectural level. Trade-offs at this stage include the number of pipeline stages, the number of execution units (parallelism), and the size of memories.

Trade-offs at the logic level include types of functional blocks (e.g., ripple carry vs. lookahead adders), the number of stages of gates in the clock cycle, the fan-in and fan-out of the gates.

>[!important]
>No amount of skillful logic design can overcome a poor microarchitecture.

Once the logic is selected, the delay can be tuned at circuit level by changing transistor sizes or using other styles of CMOS logic.

Finally, delay is dependent on layout because wire lengths can dominate delay. Good cell layouts can also reduce parasitic capacitance.
