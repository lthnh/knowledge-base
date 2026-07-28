![[pass-transistor-threshold-drop-1.png|300]]

The transistor above is an nMOS with both drain and gate tied to $V_{DD}$. 
Assume that $V_S$ is 0 at first. This means the nMOS is on as $V_{GS}$ > $V_{tn}$. As the voltage at the source rises to $V_{DD}-V{tn}$[^1]. $V_{GS}$ returns to $V_{tn}$ and the nMOS stops conducting.
$\rightarrow$ This means the nMOS can never pull the source above $V_{DD}-V_{tn}$.
$\Rightarrow$ The phenomenon is called a *threshold drop*.

As $V_S$ increases, another effect comes into play is the body effect. This effect increases the threshold voltage, thus further reduce the performance of passing transistors.

Similarly, pMOS transistors pass 1s well but 0s poorly. If the pMOS source drop below $|V_{tp}|$, the transistor cuts off. Hence pMOS transistors will pull down to a certain threshold above GND.

![[pass-transistor-threshold-drop-2.png|299]]

As the source can rise to value close to threshold voltage, the output of several transistors in series is no more degraded than that of a single transistor.

![[pass-transistor-threshold-drop-3.png|300]]

However, if the degraded output drives the gate of another transistor, the second transistor can produce an even more degraded output.

![[pass-transistor-threshold-drop-4.png|300]]

In old processes, switch where $V_{DD}$ is high and $V_t$ is only a small fraction of it $\rightarrow$ negligible.
Now, $V_t$ is closer to 1/3 of $V_{DD}$ $\rightarrow$ CMOS switches are built using transmission gates.

[^1]: Technically, $V_S$ can rise very slowly by means of subthreshold leakage.
