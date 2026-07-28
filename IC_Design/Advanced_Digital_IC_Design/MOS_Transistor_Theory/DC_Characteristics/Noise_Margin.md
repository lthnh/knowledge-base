This parameter allows you to determine how much noise on the input of a gate so that the output will not be corrupted.
Two parameters are most commonly used to describe noise margin are *LOW* noise margin, $NM_L$ and the *HIGH* noise margin, $NM_H$.

![[noise-margin-defs.png|400]]

$$
\begin{aligned}
NM_H&=V_{OH}-V_{IH}\\
NM_L&=V_{IL}-V_{OL}
\end{aligned}
$$

where
- $V_{IH}$ is the minimum HIGH input voltage.
- $V_{IL}$ is the maximum LOW input voltage.
- $V_{OH}$ is the minimum HIGH output voltage.
- $V_{OL}$ is the maximum LOW output voltage.

Inputs between $V_{IH}$ and $V_{IL}$ are said to be *indeterminate region* or *forbidden zone* $\rightarrow$ do not represent legal digital logic levels.

>[!note]
>It is desirable to have $V_{IH}$ as close as possible to $V_{IL}$.

This implies that the transfer characteristic curve should switch abruptly $\rightarrow$ has high gain in the transition region.

## Noise Margins of Inverter

![[cmos-inverter-noise-margins.png|300]]

Logic levels are defined at unity gain points where the slope is -1. This gives conservative bound on the worst static noise margin.

Note that the output is slightly degraded when the input value is at its worst value. This is called *noise feedthrough* or *propagated noise*.

An unskewed gate has equal noise margins $\rightarrow$ more resistance to arbitrary noise. If the gate sees more noise on one side, we can skew it to improve the noise margin at the expense of other side.

If $|V_{tp}|$ = $V_{tn}$, then both noise margins increase as threshold voltages are increases.

Noise margins can be compromised to improve speed.

Noise tend to scale with supply voltage.

DC analysis gives static noise margins. Larger noise pulses may be acceptable, described by *dynamic noise margins*. This parameter is specified by a maximum amplitude as a function of duration. But there is no simple amplitude-duration product that conveniently specifies dynamic noise margins.