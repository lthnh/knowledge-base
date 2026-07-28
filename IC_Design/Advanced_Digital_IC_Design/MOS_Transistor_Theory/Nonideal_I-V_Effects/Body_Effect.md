Real transistors have 4 terminals, the extra one is the body.
When $V_{sb}$ is applied between the source and the body. It increases the amount of charge required to create an inversion layer (thus the channel), hence it increases $V_t$.
The threshold voltage is modeled as
$$
V_t = V_{t0} + \gamma\left(\sqrt{\phi_s + V_{sb}} - \sqrt{\phi_s}\right)
$$

^abbc14

Where
- $V_{t0}$ is the threshold voltage when the source is at body potential.
- $\Phi _s$ is the surface potential at threshold.
- $\gamma$ is the body effect coefficient, 0.4 ~ 1 $\mathrm{V}^{1/2}$.
These parameters depend on channel doping level $N_A$.

With
$$
\phi_s = 2 v_T \ln\!\left(\frac{N_A}{n_i}\right)
$$
$$
\gamma
=
\frac{t_{ox}}{\varepsilon_{ox}} \sqrt{2 q \varepsilon_{si} N_A}
=
\frac{\sqrt{2 q \varepsilon_{si} N_A}}{C_{ox}}
$$

The body effect further degrades the performance of passing transistors trying to pass a weak value.

A body bias can be intentionally applied to alter the threshold voltage, permit trade-offs between performance and subthreshold leakage current.

For small voltages applied to the source or body, [[#^abbc14]] can be linearized to
$$
V_t = V_{t0} + k_{\gamma} V_{sb}
$$
Where
$$
k_{\gamma}
=
\frac{\gamma}{2\sqrt{\phi_s}}
=
\frac{1}{2C_{ox}}
\sqrt{\frac{q \varepsilon_{si} N_A}{v_T \ln\!\left(\dfrac{N_A}{n_i}\right)}}
$$


