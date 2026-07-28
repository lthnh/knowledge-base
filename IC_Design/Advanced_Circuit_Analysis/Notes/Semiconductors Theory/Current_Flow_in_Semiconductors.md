There are 2 distinct mechanisms for current flow in semiconductors: drift and diffusion.
## Drift current
Drift current appears when there is an electric field applied to the semiconductor crystal.
The velocity holes and electrons acquired are
$$
\begin{aligned}[t]
v_{p-drift}=\mu_pE \\
v_{n-drift}=-\mu_nE
\end{aligned}
$$
Where
- $\mu_p$ is hole mobility.
- $\mu_n$ is electron mobility.

![[currents-in-semi.png|300]] ^83a0b0

By convention, the direction of current flow must be positive. In the [[#^83a0b0|image]] above, electrons flow in the opposite direction of $E$. Therefore there is a positive current flow created by electrons from left to right.
The current densities associated with holes and electrons are
$$
\begin{align*}
J_p &= q p \mu_p E \\
J_n &= q n \mu_n E
\end{align*}
$$
The total drift current density is
$$
J=J_p+J_n=q(p\mu _p+n\mu _n)E
$$
with
$$
\sigma=\frac{1}{\rho}=q(p\mu _p+n\mu _n)
$$
## Diffusion current

^4858d7

Like ink drops diffuse into a water tank, holes/electrons diffuse from regions of high concentration into regions of low concentration.
The diffusion currents of holes and electrons are
$$
\begin{align*}
J_p
&=
- q D_p \frac{\mathrm{d}p(x)}{\mathrm{d}x} \\
J_n
&=
q D_n \frac{\mathrm{d}n(x)}{\mathrm{d}x}
\end{align*}
$$

^7c2386

Where
- $D_p$/$D_n$ is the diffusion constant of holes/electrons.
- $p(x)$/$n(x)$ is the concentration of holes/electrons depends on the $x$ direction.

>[!Einstein relationship]
>$$
>\frac{D_n}{\mu _n}=\frac{D_p}{\mu _p}=V_T
>$$
>Where $V_T$ is the *thermal voltage*.

$V_T$ is a constant, given by

$$
V_T=\dfrac{kT}{q}
$$

where
- $k$ is Boltzmann's constant.
- $T$ is absolute temperature in kelvins.
- $q$ is the magnitude of electronic charge.

