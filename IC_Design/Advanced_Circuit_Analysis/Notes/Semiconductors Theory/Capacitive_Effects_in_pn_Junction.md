## Depletion/Junction Capacitance
The charge stored on either side of the junction is given by [[pn Junction (Open-Circuit)#^7db0cd]].
Rewrite the equation as

$$
Q_J=\alpha\sqrt{V_0+V_R}
$$

^170cc2

with

$$
\alpha=A\sqrt{2\epsilon_s q \frac{N_AN_D}{N_A+N_D}}
$$

^85858a


$Q_J$ is nonlinearly related to $V_R$. So it is hard to find the junction capacitance analytically.

![[C-approx-pn-junction.png|400]]

We can assume the junction operate at the bias point $Q$ and define a capacitance $C_j$ by

$$
C_j = \left.\frac{\mathrm{d}Q_J}{\mathrm{d}V_R}\right|_{V_R = V_Q}
$$

^c9dec8

Combining [[#^170cc2]] with [[#^c9dec8]] yields

$$
C_j = \frac{\alpha}{2\sqrt{V_0 + V_R}}
$$

The value of $C_j$[^1] at zero reverse bias is 

$$
C_{j0}=\frac{\alpha}{2\sqrt{V_0}}=A \sqrt{
\left( \frac{\varepsilon_s q}{2} \right)
\left( \frac{N_A N_D}{N_A + N_D} \right)
\left( \frac{1}{V_0} \right)
}
$$

We can then express $C_j$ as

$$
C_j = \frac{C_{j0}}{\sqrt{1 + \dfrac{V_R}{V_0}}}
$$

The pn junction above is called *abrupt junction*, where the doping concentration is made to change abruptly at the junction boundary.
Another type of pn junction is called *graded junction*. The general formula for junction capacitance is

$$
C_j = \frac{C_{j0}}{\left(1 + \dfrac{V_R}{V_0}\right)^m}
$$

where $m$ is a constant called the *grading coefficient*, whose values ranges from 1/3 to 1/2 depending on the manner in which the concentration changes from the p to the n side.
## Diffusion Capacitance
In forward-biased pn junction, a certain amount of excess minority-carrier charge is stored in each of the p and n bulk regions (outside of the depletion region). These steady state charge distributions are shown in this [[pn Junction (with Applied Voltage)#^e48fa7|image]].

If terminal voltage $V$ changes, these charge distributions will change before a new steady state is achieved $\rightarrow$ gives rise to another capacitive effect.

The excess hole charge stored in the n region can be calculated as

$$
\begin{aligned}
Q_p 
&= A q \times \text{shaded area under the } p_n(x)\text{ curve} \\
&= A q \left[ p_n(x_n) - p_{n0} \right] L_p
\end{aligned}
$$

Notice that the $p_n(x)$ curve is exponential. The shaded area under the curve can be calculated from $AB$ with the exponential curve of the form $A\rm{e}^{-x/B}$.

Substitute for $p_n(x_n)$ from [[pn Junction (with Applied Voltage)#^074083]] and [[pn Junction (with Applied Voltage)#^66e134]], we arrive at

$$
Q_p = \frac{L_p^{2}}{D_p} I_p
$$

with factor $L_p^2/D_p$ a useful device parameter that has the dimension of time (s), denoted as $\tau_p$.

$$
\tau_p = \frac{L_p^{2}}{D_p}
$$

The time constant $\tau_p$ is known as the excess *minority-carrier (hole) lifetime*, which is the average time it tak1es for a hole injected to the n region to recombine with a majority electron.

>[!important]
>This implies that the entire charge $Q_p$ disappears and has to be replenished every $\tau_p$ seconds.
>The current that accomplishes the replenishing is $I_p=Q_p/\tau_p$.

This results in

$$
Q_p=\tau_pI_p
$$

Same for electrons in the p region.

$$
Q_n=\tau_n I_n
$$

where $\tau_n$ is the electron lifetime in the p region.

Combine both $Q_p$ and $Q_n$, we can calculate the total excess minority-carrier charge with

$$
Q=\tau_p I_p + \tau_n I_p
$$

This can also be expressed as diode current $I=I_p+I_n$.

$$
Q=\tau_T I
$$

where $\tau_T$ is the *mean transit time* of the junction. $\tau_T$ is related to $\tau_p$ and $\tau_n$.

>[!note]
In practice, one side is more heavily doped than the other. This means if $N_A \gg N_D$, then $I_p \gg I_n \rightarrow I \simeq I_p$ and $Q_p \gg Q_n \rightarrow Q \simeq Q_p$. Thus $\tau_T \simeq \tau_p$.

For small changes around the bias point, we define a *incremental diffusion capacitance* $C_d$ as

$$
C_d=\dfrac{\mathrm{d}Q}{\mathrm{d}V}=\left(\dfrac{\tau_T}{V_T}\right)I
$$

where $I$ is the forward-biased current.

>[!note]
>As $C_d$ is proportional to forward current $I$. It is negligibly small when the junction is reverse-biased.

>[!important]
>For high-speed/high-frequency applications, $C_d$ must be kept small $\rightarrow$ $\tau_T$ must be made small.


[^1]: $\alpha$ from [[#^85858a]].


