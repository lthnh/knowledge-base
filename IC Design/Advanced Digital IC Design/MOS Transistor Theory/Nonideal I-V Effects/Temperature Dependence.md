Carrier mobility decreases with temperature.
An approximation is
$$
\mu(T)=\mu(T_r)\left(\frac{T}{T_r}^{-k_\mu}\right)
$$
Where
- $T$ is the absolute temperature.
- $T_r$ is the room temperature.
- $k_\mu$ is a fitting parameter, typical ~1.5.

$v_{sat}$ also decreases with temperature, dropping about 20% from 300 to 400 K.

$V_t$ also decreases nearly linearly with temperature. It may be approximated by
$$
V_t(T)=V_t(T_r)-k_{vt}(T-T_r)
$$
Where $k_{vt}$ is typically about 1-2 mV/K.

$I_{on}$ at high $V_{DD}$ decreases with temperature.
[[Subthreshold Leakage|Subthreshold leakage]] increases exponentially with temperature.
[[Junction Leakage#^7b13e9|BTBT]] increases slowly with temperature.
[[Gate Leakage|Gate leakage]] is *almost* independent of temperature.

The combined temperature effects are shown in this figure
![[i-v-in-saturation-nmos-diff-temp.png|300]]
At high $V_{gs}$, the current have negative temperature coefficient.
At low $V_{gs}$, the current have positive temperature coefficient.
$\Rightarrow$ OFF current increases with temperature, ON current $I_{dsat}$ normally decreases with temperature like the figure below.
![[idsat-vs-temp.png|300]]
**Figure of $I_{ON} (\mu A)$ vs temperature.**
$\Rightarrow$ The performance of circuit is *worst* at high temperature.

Except for systems operating at low $V_{DD}$ (typically < 0.7 - 1.1 V), $I_{dsat}$ increases with temperature.

>[!tip]
>Performance can also be improved by cooling.

## Advantages of operating at low temperatures
- Reduce subthreshold leakage as it depends exponentially on temperature $\rightarrow$ lower threshold can be used.
- Velocity saturation occurs at higher fields $\rightarrow$ provide more current.
- Higher mobility $\rightarrow$ fields are reached with less power $\rightarrow$ saving power.
- Wider depletion regions $\rightarrow$ less junction capacitance.