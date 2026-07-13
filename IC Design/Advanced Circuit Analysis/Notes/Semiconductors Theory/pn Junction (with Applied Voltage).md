## Qualitative Description
![[pn-junction-with-applied-voltage.png|500]] ^a5082f
### Reverse Bias
In this case, the external voltage applied adds to the barrier voltage, thus increase its effective barrier voltage to $(V_0+V_R)$.
This will limits the diffusion current $I_{D}$, a reverse bias voltage of ~1 V is sufficient to cause $I_D\simeq0$.
Only drift current $I_S$ remains, but it's very small and almost-constant.
Also the depletion region widens, it can be shown by using this analytical expression
$$
W = x_n + x_p
=
\sqrt{
\frac{2 \varepsilon_s}{q}
\left(
\frac{1}{N_A} + \frac{1}{N_D}
\right)
\left( V_0 + V_R \right)
}
$$
With the magnitude of charge stored in this region
$$
Q_J
=
A
\sqrt{
2 \varepsilon_s q
\left(
\frac{N_A N_D}{N_A + N_D}
\right)
\left( V_0 + V_R \right)
}
$$

### Forward Bias
The applied voltage $V_F$ will subtract from the built-in voltage $V_0$, resulting in a reduced barrier voltage $(V_0-V_F)$ across the depletion region. Pretty evident in this [[#^a5082f|image]] above.
The reduced barrier voltage $\rightarrow$ reduced depletion region $\rightarrow$ more diffusion current.
More holes will diffuse from p to n. More electrons will diffusion from n to p.
$\Rightarrow$ Substantially large diffuse current, orders of magnitude larger than drift current $I_S$.
$$
I=I_D-I_S
$$
$I$ flows from p to n, determined by the forward-bias voltage $V_F$.
## I-V Characteristic
![[minority-carriers-distribution-in-forward-bias.png|500]] ^e48fa7

From device physics, the steady-state concentration of holes at the edge of depletion region will be
$$
p_n(x_n)=p_{n0}{\rm e}^{V/V_T}
$$

^074083

Applying the forward-bias voltage $V$ results in excess concentration of minority holes at $x=x_n$
$$
\begin{aligned}
\rm{Excess \space concentration}&=p_{n0}{\rm e}^{V/V_T}-p_{n0}\\
&=p_{n0}\left({\rm e}^{V/V_T}-1\right)
\end{aligned}
$$
As injected holes diffuse into n material and recombine, the excess concentration will decay exponentially with distance.
The total hole concentration in n material is
$$
\begin{aligned}
p_n(x)&=p_{n0}+(\rm{Excess \space concentration}){\rm e}^{-(x-x_n)/L_p} \\
&=p_{n0}
+
p_{n0}\!\left(\mathrm{e}^{V/V_T}-1\right)
\mathrm{e}^{-(x-x_n)/L_p}
\end{aligned}
$$
Where
- $L_p$ is the *diffusion length* of holes in n material. The smaller the faster holes recombine with electrons in n material.

From the hole concentration, the diffusion can be determined by [[Current Flow in Semiconductors#^7c2386]].

$$
J_p(x)
=
q\left(\frac{D_p}{L_p}\right)
p_{n0}
\left(\mathrm{e}^{V/V_T}-1\right)
\mathrm{e}^{-(x-x_n)/L_p}
$$

$J_p$ is highest at $x_n$, as in

$$
J_p(x_n)
=
q\left(\frac{D_p}{L_p}\right)
p_{n0}
\left(\mathrm{e}^{V/V_T}-1\right)
$$

^66e134

The same thing with electrons in p material,

$$
J_n(-x_p)
=
q\left(\frac{D_n}{L_n}\right)
n_{p0}
\left(\mathrm{e}^{V/V_T}-1\right)
$$

However, since minority holes combine with majority electrons, the electrons must be supplied from the the external circuit to the n region to compensate. This current have the same direction as the diffusion current of holes.
$\Rightarrow$ The current stays the same across n material at the value give by [[#^66e134]].

The same thing happens with electrons in p material too.

As the diffusion currents of both holes and electrons are independent of $x$, we can strip it and multiply by junction area $A$ to find the total current

$$
\begin{aligned}
I &= A\left(J_p + J_n\right) \\
I &= A q
\left(
\frac{D_p}{L_p} p_{n0}
+
\frac{D_n}{L_n} n_{p0}
\right)
\left(\mathrm{e}^{V/V_T}-1\right)
\end{aligned}
$$

^254b55

Substitute $p_{n0}=n_i^2/N_D$ and $n_{p0}=n_i^2/N_A$ into [[#^254b55]], we have

$$
I
=
A q n_i^{2}
\left(
\frac{D_p}{L_p N_D}
+
\frac{D_n}{L_n N_A}
\right)
\left(\mathrm{e}^{V/V_T}-1\right)
$$

We can see that if $V$ is negative and of orders of magnitude of $V_T$, the resultant current is negative. From the qualitative description, we can be certain that this is equal to the drift current $I_S$.
![[Is-current-in-IV-characteristics-pn-junction.png|400]]

$$
I=I_S\left({\rm e}^{V/V_T}-1\right)
$$
Where

$$
I_S
=
A q n_i^{2}
\left(
\frac{D_p}{L_p N_D}
+
\frac{D_n}{L_n N_A}
\right)
$$

^7822a2

$I_S$ is called the *saturation current*.

>[!note]
>$I_S$ is proportional to area and $n_i^2$. And $n_i^2$ is a strong function of temperature. This mean even when reverse-bias voltage is applied, there is still a small amount of current go through.

### Reverse Breakdown
When there is reverse-bias voltage $-V$ ($V \gg V_T$) applied between pn junction, the current flows will approximately equal to $I_S$, which is very small.

As the reverse-bias voltage increases, it reaches a value of $V_Z$. This is where current increases dramatically with minimal increase in voltage. This phenomenon is called *junction breakdown*. An it is *not* a destructive phenomenon, provided that an external circuit limits the current through the junction to a safe value.

![[rapid-increase-current-breakdown-region.png|400]]

Two possible mechanisms for pn junction breakdown: the *zener effect* and *avalanche effect*.
If $V_Z$ < 5 V, the breakdown mechanism is usually zener effect.
If $V_Z$ > ~7 V, the breakdown mechanism is avalanche effect.
If 5 V < $V_Z$ < 7 V, the breakdown mechanism can be zener effect/avalanche effect/combination of the two.
#### Zener effect
*Zener breakdown* occurs when the electric field in the depletion region increases to the point it can break covalent bonds and generate electron-hole pairs.
The electrons are moved to the n region and the holes are moved to the p region, constituting a reverse current.
Once the effect starts, current can be large and *must* be controlled by a external circuit.
The reverse voltage appears between the diode terminals remain close to a specified breakdown voltage $V_Z$.
#### Avalanche effect
Avalanche breakdown occurs when minority carriers crossing the depletion region, under the influence of electric field, gain sufficient kinetic energy to break covalent bonds in atoms with which they collide.
The carriers liberated by this effect may also have sufficient energy to break other covalent bonds. This process keeps repeating in avalanche fashion.
Many carriers are created, supporting any value of reverse current, determined only by an external circuit with negligible change in voltage drop.