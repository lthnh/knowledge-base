Increasing $V_{ds}$ leads to lowering threshold voltage.
$$
V_t = V_{t0} - \eta V_{ds}
$$
Where $\eta$ is the DIBL coefficient, ~ 0.1 or 100 mV/V.
DIBL causes $I_{ds}$ to increase with $V_{ds}$ in saturation, like [[Channel Length Modulation|channel length modulation]].

> [!important]
> This effect must be taken into consideration in analog designs.
> This effect is pronounced in short-channel transistors.

For most digital circuits, this effect is *negligible*. But DIBL will increase subthreshold leakage at high $V_{ds}$.
