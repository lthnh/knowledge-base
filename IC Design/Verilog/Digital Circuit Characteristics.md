## Logic Levels
There are two types of digital assignments.
- Positive Logic: logic HIGH $\rightarrow$ 1, logic LOW $\rightarrow$ 0
- Negative Logic: logic LOW $\rightarrow$ 1, logic HIGH $\rightarrow$ 0
## Output DC Characteristics
The range of output voltages that transmitting circuit guarantees to deliver when outputting 1 or 0: $V_{OH-max}, V_{OH-min}, V_{OL-max}, V_{OL-min}$.
The maximum current the transmitting circuit can deliver is also specified: $I_{OH-max}$. The maximum current the transmitting circuit can sink is $I_{OL-max}$.
## Input DC Characteristics
The same as output characteristics with 6 parameters: $V_{IH-max}, V_{IH-min}, V_{IL-max}, V_{IL-min}, I_{IH-max}, I_{IL-max}$. The last two parameters are current drawn by receiving circuit inputs when its being driven by either HIGH or LOW inputs.
## Noise Margins
The worst case scenario is when transmitting circuit sending HIGH logic at $V_{OH-min}$ or LOW logic at $V_{OL-max}$. These levels represent the furthest away from the ideal voltage that the transmitter can send to the receiver.
If $V_{OH-min}$ is the same as $V_{IH-min}$, even a small amount of signal loss can cause the receiver to misinterpret the signal. $\Rightarrow$ $V_{IH-min}$ must be less than $V_{OH-min}$ to account for loss in interconnect.
The difference between $V_{OH-min}$ and $V_{IH-min}$ is called the noise margin.
$$
NM_H=V_{OH-min}-V_{IH-min}
$$
The same thing is applied for LOW signal.
$$
NM_L = V_{IL-max} - V_{OL-max}
$$
The region lies between $V_{IH-min}$ and $V_{IL-max}$ is called the uncertainty region where the signal can't be interpreted as HIGH or LOW.
## Power Supplies
There are two components of power supply current:
- Quiescent current $I_q$.
- Output current $I_O$
These components change depending on the state of the output pins.
The circuit sources current through $V_{CC}$ pin and sinks current through GND pin.
The quiescent current is often called $I_{CC}$. It usually lies in the range of $\mu A$ to $nA$. This should not be confused with $I_{CC-max}$ which is the maximum current can possibly flow through $V_{CC}$ pin, typically in the $mA$ range.
## Transient Characteristics
Two groups: propagation delay and transition time.

Propagation delay of the gate, normally defined for both LOW to HIGH or HIGH to LOW transition.
It is the time it takes from the point at which the input reaches 50% of its final value to the point at which the output reaches 50% of its final value.

Transition time is the time it takes for the output to transition from 10% to 90% of the output voltage range.
Rise time is the time it takes for transition from LOW to HIGH.
Fall time is the time it takes for transition from HIGH to LOW.