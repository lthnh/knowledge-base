MOS gate sits above the channel and may partially overlap the source and diffusion areas.
$\Rightarrow$ The gate capacitance has two components: the intrinsic capacitance $C_{gc}$ (over the channel) and the overlap capacitances $C_{gol}$ (to the source and drain).

The bottom plate of gate capacitance depends on the mode of operation of the transistor. The intrinsic capacitance has three components representing the different terminals connected to the bottom plate: $C_{gb}$ (gate to body), $C_{gs}$ (gate to source) and $C_{gd}$ (gate to drain).

![[intrinsic-gate-capacitance.png|300]]

Above is the graph of intrinsic gate capacitance $C_{gc}=C_{gs}+C_{gd}+C_{gb}$ as a function of a) $V_{gs}$ and b) $V_{ds}$.

**In the Cutoff Region**
When the transistor is OFF, the channel is not inverted and charge on the gate is matched with opposite charge from the body. This is $C_{gb}$.
For negative $V_{gs}$, the transistor is in accumulation and $C_{gb}$ = $C_0$.
As $V_{gs}$ increases but remains below $V_t$, a depletion region is formed *pushing* the bottom plate downward from the oxide $\rightarrow$ reduces $C_{gb}$.

**In the Linear Region**
When $V_{gs}$ > $V_t$, the channel inverts and serves as a bottom plate. The channel is connected to the source and drain, but not the body $\rightarrow$ $C_{gb}$ drops to 0.
At low $V_{ds}$, the channel charge is roughly shared between the source and drain $\rightarrow$ $C_{gs}$ = $C_{gd}$ = $C_0$/2.
As $V_{ds}$ increases, the region near the drain becomes less inverted $\rightarrow$ greater fraction of capacitance is attributed to the source and smaller fraction to the drain.

**In the Saturation Region**
As $V_{ds}$ > $V_{dsat}$, the transistor saturates and the channel pinches off $\rightarrow$ all the capacitance is attributed to the source.
Due to pinchoff, the capacitance reduces to $C_{gs}$ = 2/3 $C_0$.

![[approx-intrinsic-gate-capacitance.png]]

In reality, the gate overlaps the source and drain $\rightarrow$ additional overlap capacitances $\rightarrow$ fringe fields terminating on the source and drain.

![[overlap-gate-capacitance.png|300]]

These capacitances are proportional to the width of the transistor.

These should be added to the intrinsic gate capacitance to find the total.

$$
\begin{aligned}
C_{gsol(overlap)}&=C_{gsol}W\\
C_{gdol(overlap)}&=C_{gdol}W
\end{aligned}
$$

The source and drain form second terminals $\rightarrow$ the effective gate capacitance varies with the switching activity of the source and drain.

![[data-dependent-gate-capacitance.png|300]]

The graph above is an example of data dependent gate capacitance in 0.35 $\micro$m process. It demonstrates the effective gate capacitance for seven different combinations of source and drain behavior.

More accurate modeling can be achieved with charge based model.

For hand calculation of delay in digital circuits, we approximate

$$
C_g=C_{gs}+C_{gd}+C_{gb}\approx C_0+2C_{gol}W
$$

or use effective capacitance extracted from stimulation.

>[!important]
>The model above significantly overestimates the capacitance of transistors operating just below threshold.

