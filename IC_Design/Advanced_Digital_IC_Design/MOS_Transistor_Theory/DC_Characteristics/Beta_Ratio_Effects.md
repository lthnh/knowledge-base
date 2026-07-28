For $\beta_p=\beta_n$, the inverter threshold voltage $V_{inv}$ is $V_{DD}$/2. This *may* be desirable because it maximizes noise margins.
This also allows a capacitive load to charge and discharge in equal times by providing equal current source and sink capabilities.

Inverters with different ratios$r=\beta_p/\beta_n$ are called *skewed* inverters.
- If $r$ > 1, the inverter is *HI-skewed*.
- If $r$ < 1, the inverter is *LO-skewed*.
- If $r$ = 1, the inverter is *unskewed*.

HI-skewed inverter has a strong pMOS transistor. If the input is $V_{DD}$, we would expect the output is higher than $V_{DD}$/2 $\rightarrow$ the input threshold must be higher than for an unskewed inverter.
The opposite happens for LO-skewed inverter.

![[dc-transfer-curves-for-skewed-inverters.png|300]]

As beta ratios is changed, the switching threshold moves.

>[!note]
>Gates are usually skewed by adjusting the widths of transistors while maintaining minimum length for speed.

Velocity-saturated inverters are more sensitive to skewing because their DC transfer characteristics are not as sharp.

>[!important]
>DC transfer characteristics of other static CMOS gates can be understood by collapsing the gates into an equivalent inverter.

>[!important]
>Series transistors can be viewed as a single transistor of greater length.

>[!important]
>If only one of several parallel transistors is ON, the other transistors can be ignored.
>If several parallel transistors are ON, the collection can be viewed as a single transistor of greater width.


