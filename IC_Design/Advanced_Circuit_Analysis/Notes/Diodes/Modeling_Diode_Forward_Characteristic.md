## The Exponential Model
This is the most accurate description but its nonlinear characteristic makes it hard to use.

Assume $V_{DD} > 0$, $I > I_S$. $I$ can be calculated from

$$
I_D=I_S\mathrm{e}^{V_D/V_T}
$$

^11c468

![[simple-circuit-with-diode-forward.png|300]]

From this image we can write another equation based on Kirchhoff's voltage law.

$$
I_D=\dfrac{V_{DD}-V_D}{R}
$$

^2637bd

Assume diode parameter $I_S$ is known. There are only two unknowns left: $V_D$ and $I_D$, which can be solved through by combining the two equations, graphical analysis or iterative analysis.
### Graphical Analysis Using the Exponential Model
Draw the two equations [[#^11c468]] and [[#^2637bd]] on the I-V plane. The straight line is known as the *load line*.

![[graphical-analysis-diode-exp.png|500]]

The intersection point $Q$ is called the *operating point* of the circuit. Its coordinates give the values of $I_D$ and $V_D$.
### Iterative Analysis Using the Exponential Model
==Read the book for details example.==
## The Constant-Voltage-Drop Model

![[constant-v-drop-model-diode.png|500]]

This model is based on the fact that diode voltage drop falls in a narrow range from 0.6 V to 0.8 V. The model assumes the voltage drop to be constant, for example, at 0.7 V.
## The Ideal Diode Model
Useful to assess whenever a diode in multi-diode circuit is on or off.
## The Small-Signal Model
Consider models where $V_{DD}$, $I_D$ and $V_D$ vary slightly. $\Delta V_{DD}$ can be time-varying with $\Delta V_D$ sufficiently small. 

![[small-signal-forward-diode-model.png|500]]

From this figure,

![[small-signal-diode-model.png|400]] ^a584d6

We can expressed voltage across the diode as

$$
v_D(t)=V_D+v_d(t)
$$

^e62aea

The total instantaneous diode current will be

$$
i_D(t)=I_S\mathrm{e}^{v_D/V_T}
$$

Substitute $v_D$ from [[#^e62aea]], we have

$$
i_D(t)=I_S\mathrm{e}^{(V_D+v_d)/V_T}=I_S \mathrm{e}^{V_D/V_T} \mathrm{e}^{v_d/V_T}=I_D\mathrm{e}^{v_d/V_T}
$$

with $I_D$ the current when time-varying $v_d$ is absent.
If $V_D$ is kept sufficiently small such that

$$
\dfrac{v_d}{V_T}\ll1
$$

Then we can apply Taylor's series and take the first two terms.

$$
i_D(t) \simeq I_D \left( 1 + \frac{v_d}{V_T} \right)
$$

This is valid for signals < ~5 mV as $V_T$ $\simeq$ 25 mV.
We can say that the current $I_D$ has another current component *superimposed* on it.

$$
i_D=I_D+i_d
$$

with

$$
i_d=\dfrac{I_D}{V_T}v_d
$$

The quantity $I_D/V_T$ have the dimensions of conductance, mhos ($\mho$). It is called *diode small-signal conductance*. Its inverse is *diode small-signal resistance*, or *incremental resistance*, $r_d$.

$$
r_d=\dfrac{V_T}{I_D}
$$

The value of $r_d$ is inversely proportional to the bias current $I_D$.

Another interpretation of this is based on this [[#^a584d6|graph]]. The use of small-signal approximation assumes that the signal varies along the I-V curve is limited to a short almost-linear segment.
The slope of this segment = slope of the tangent to the I-V curve at the operating point $Q$ = small-signal conductance.

$$
r_d=1 / \left [ \dfrac{\partial i_D}{\partial v_D} \right ]_{i_D=I_D}
$$

The quantities $V_D$ and $I_D$ define *dc bias point*, or *quiescent point*.

Small-signal analysis can be done separately from dc bias analysis due to inherent linearization of diode characteristics in the method of said analysis.

After dc analysis, the small-signal equivalent circuit can be obtained by eliminating all dc sources (short voltage sources and open current sources) and replacing the diode by its small-signal resistance.

>[!note]
$r_d$ models the small-signal operation at low frequencies, its dynamic operation is modeled by capacitances $C_j$ and $C_d$ (also small-signal parameters).

>[!note]
>A complete model of the diode includes $C_j$ and $C_d$ in parallel with $r_d$.


