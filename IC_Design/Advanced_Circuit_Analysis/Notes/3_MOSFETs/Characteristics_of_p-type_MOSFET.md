![[pmos-iv-characteristic.png|500]]

Conventionally, $v_{OV}$ and $V_{tp}$ are negative. If we take their absolute values and use physics intuition on the circuit in the graph above. You will see that the p-type MOSFET behavior is basically identical to n-type MOSFET.

The $i_D$ saturation-region expression is

$$
\begin{aligned}
i_D &= \frac{1}{2} k_p' \left( \frac{W}{L} \right) (v_{SG} - |V_{tp}|)^2 \left( 1 + |\lambda| v_{SD} \right) \\
&= \frac{1}{2} k_p' \left( \frac{W}{L} \right) (v_{SG} - |V_{tp}|)^2 \left( 1 + \frac{v_{SD}}{|V_A|} \right)
\end{aligned}
$$
where
- $\lambda$ is a device parameter, [[I-V Characteristic#^53796d|as it is for n-type MOSFET]]. [[I-V Characteristic#^53796d|]]
- $V_A$ is the Early voltage. See more [[I-V Characteristic#^7296dc|here]].
Both of these parameter are conventionally negative. Hence the use of absolute sign $|a|$.

>[!important]
>For a given CMOS fabrication process:
>$\lambda _n \neq |\lambda _p|$
>$V_{An} \neq V_{Ap}$


