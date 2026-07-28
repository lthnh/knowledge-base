In p-type material, a majority of carriers are holes. But due to thermal ionization, the minority of electrons also generated. This also happens to n-type material.
![[currents-in-pn-junction.png|300]]
## The Diffusion Current $I_D$
More info [[Current Flow in Semiconductors#^4858d7|here]].
## The Depletion Region
When holes get to n region, they recombine with some of the free electrons. This results in uncovered bounded positive charges, effectively creating a positive region act as a positive plate of capacitor.
The same can be said for p region. As electrons get to n region, they recombine with holes thus results in uncovered bounded negative charges, effectively creating a negative region act as a negative plate of capacitor.
Since in both cases, a part of n region and p region are devoid of free carriers. That is why it is called the *depletion region*.
## The Drift Current $I_S$ and Equilibrium
As mentioned above, a small amount of free electrons exist in p region due to thermal ionization. When they get to the edge of depletion region, the $E$ field there sweeps the free electrons into the n region.
The same thing happens in n region with holes.
Since holes and electrons associated with this current are thermal-generated. They strongly depends on temperature. They don't depends on the barrier voltage as with any value of $V_0$, conduction still happens.
In equilibrium and open-circuit conditions, the two current cancel out as
$$
I_D=I_S
$$
This equilibrium is maintained by the barrier voltage $V_0$. For example, if for some reasons $I_D$ is larger than $I_S$. This in turn widens the depletion region as more electrons and hole recombine and drives larger $I_S$ current.
In the same conditions, if $I_S$ is larger than $I_D$, this narrows the depletion region which creating less resistance to the diffusion current. Thus drives larger $I_D$ current to compensate.
## The Junction Built-in Voltage
With no external voltage applied, the barrier voltage $V_0$ across the pn junction is
$$
V_0=V_T\ln\left(\frac{N_AN_D}{n_i^2}\right)
$$
Where
- $N_A$ is doping concentration of the p side.
- $N_D$ is doping concentration of the n side.

For silicon at room temperature, $V_0$ is in the range of 0.6 V to 0.9 V.
The voltage $V_0$ across the depletion region does not appear between the junction terminals due to being cancelled out by contact voltages existing at the metal-semiconductor junctions at the terminals.
### Contact Voltage at Metal-Semiconductor Junctions
==To be researched later, when I have the time.==
## Width of and Charge Stored in Depletion Region
In practice, it's usual for one side of the junction to be more heavily doped than the other. This makes the depletion region extends into the lighter doped side more.
![[depletion-extends-almost-to-one-side.png|400]]
The width of the depletion layer can be calculated by
$$
W = x_n + x_p
=
\sqrt{
\frac{2 \varepsilon_s}{q}
\left(
\frac{1}{N_A} + \frac{1}{N_D}
\right)
V_0
}
$$

^8a397e

Where
- $\epsilon _s$ is the electrical permittivity of silicon, $\epsilon _s=11.7\epsilon_0$.
As charges on both side have the same amount, the ratio of widths in which the depletion region extends into both sides can be written as the ratio of doping concentration $N_A$ and $N_D$.
Since

$$
\begin{aligned}
\left| Q_{+} \right| &= q A x_n N_D \\
\left| Q_{-} \right| &= q A x_p N_A
\end{aligned}
$$

^065c30

With $\left| Q_{+} \right|=\left| Q_{-} \right|$, this results in

$$
\frac{x_n}{x_p} = \frac{N_A}{N_D}
$$

^09458b

Combine [[#^8a397e]] and [[#^09458b]], we obtain the expression for $x_n$ and $x_p$ in terms of $W$ as
$$
\begin{aligned}
x_n&=W\frac{N_A}{N_A+N_D}\\
x_p&=W\frac{N_D}{N_A+N_D}
\end{aligned}
$$

^85a776

We can find the charge stored on either side by combining [[#^065c30]] and [[#^85a776]].
$$
\begin{aligned}
Q_J&=\left|Q_+\right|=\left|Q_-\right|\\
Q_J&=Aq\left(\frac{N_AN_D}{N_A+N_D}\right)W
\end{aligned}
$$

^093291

Substitute $W$ from [[#^8a397e]] into [[#^093291]], we have
$$
Q_J
=
A
\sqrt{
2 \varepsilon_s q
\left(
\frac{N_A N_D}{N_A + N_D}
\right)
V_0
}
$$

^7db0cd


