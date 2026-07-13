In design, transistors have $W_{drawn}$ width and $L_{drawn}$ length.
But during manufacturing process, the actual gate dimensions maybe differ by $X_W$ and $X_L$.
The source and drain tend to diffuse laterally under the gate, hence the effective channel length is shortened by a factor $L_D$.
$W_D$ also accounts for other effects that shrink the transistor width.
The effective channel length and width are
$$
\begin{aligned}
L_{\mathrm{eff}} &= L_{\mathrm{drawn}} + X_L - 2L_D \\
W_{\mathrm{eff}} &= W_{\mathrm{drawn}} + X_W - 2W_D
\end{aligned}
$$

^e30ff9

The factors of 2 comes from lateral diffusion on both sides of the channel.
The length and width from equation [[#^e30ff9]] should be used in current equation in place of the drawn width and length.

>[!important]
>$V_t$ varies with transistor dimensions because of short and narrow channel effects.
>$V_t$, $L_{eff}$, [[Channel Length Modulation|channel length modulation]], [[Velocity Saturation and Mobility Degradation|velocity saturation effects]] make $I_{dsat}$ not scale exactly as $1/L$.

>[!tip]
>Best to use *same width and length* for each device when currents must be precisely matched.
>Current ratios can be produced by tying several identical transistors in parallel.

In process $<0.25\mu m$, the $L_{eff}$ also depends significantly on the orientation of the transistor.

>[!tip]
>Transistors that must match well should have the same orientation.
>Dummy polysilicon wires can be placed nearby to improve etch uniformity.

