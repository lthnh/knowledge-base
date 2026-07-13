![[bjt-active-mode.png|500]]

We use two external voltage sources to establish the required bias conditions for active-mode operation. $V_{BE}$ causes EBJ to be forward-biased, $V_{CE}$ causes CBJ to be reverse-biased.

The forward bias on the EBJ will causes current to flow across this junction.
Current consists of two components: electrons injected from the emitter into the base, and holes injected from the base into the emitter.

>[!note]
>Highly desirable to have the electrons component higher than the holes component.
>$\Rightarrow$ Can be accomplished by fabricating the device with heavily doped emitter and a lightly doped base.

The current flows across EBJ is $i_E$. The direction of this current is "out of " the emitter lead, i.e. in the direction of positive-charge flow.

Emitter have highest electron concentration $\rightarrow$ diffuses from the emitter through the base toward the collector. Here they recombine with holes during their journey through the base. But base is thin and lightly doped $\rightarrow$ large portion of electrons pass through successfully. Since the collector is more positive than the base $\rightarrow$ successful electrons are swept across CBJ into the collector $\rightarrow$ constitute current $i_C$.
## The Collector Current

$$
i_C=I_S\mathrm{e}^{v_{BE}/V_T}
$$
$I_S$ is the saturation current.
## The Base Current
The base current has two components:
- $i_{B1}$ due to holes injected from the base region into the emitter region.
- $i_{B2}$ due to holes injected from the external circuit to the base region in order to replace the holes which are lost in the recombination process $\rightarrow$ proportional to the number of electrons injected into the base.
Total base current $i_B=i_{B1}+i_{B2}$ will be proportional to the collector current $i_C$.

$$
i_B=\dfrac{i_C}{\beta}
$$

^46ea1b

$$
i_B=\left(\dfrac{I_S}{\beta}\right)\mathrm{e}^{v_{BE}/V_T}
$$
where
- $\beta$ is **common-emitter current gain.

$\beta$ is highly influenced by two factors: the width of the base region, $W$, and the relative doping of the base region the emitter region, $N_A/N_D$. To obtain high $\beta$, the base should be thin ($W$ small) and lightly doped and the emitter highly doped (making $N_A/N_D$ small).
## The Emitter Current

$$
i_E=i_C+i_B
$$

From [[#^46ea1b]], we have

$$
i_E=\dfrac{\beta+1}{\beta}i_C
$$
We can also set

$$
\alpha=\dfrac{\beta}{\beta+1}
$$

where
- $\alpha$ is **common-base current gain**.

If we have $\alpha$, we can also calculate $\beta$ with

$$
\beta=\dfrac{\alpha}{1-\alpha}
$$
From this equation we can see, small change in $\alpha$ causes large change in $\beta$. This mathematical observation also manifests itself physically.
## Minority-Carrier Distribution

![[profiles-of-minority-carriers-concentrations.png]]

The doping concentration in the emitter, $N_D$, is much higher than the doping concentration in the base, $N_A$. Thus the concentration of electrons injected from the emitter to base, $n_p(0)$, is much larger than the concentration of holes injected from the base to the emitter, $p_n(0)$.

Because the base is very thin $\rightarrow$ concentration of excess electrons decays *almost* linearly (as opposed to the usual decay for excess holes in the emitter region). The reverse bias on the CBJ also causes the concentration of excess electrons at the collector side to be zero.

The tapered minority-carrier concentration profile causes electrons injected into the base to diffuse through the base region toward the collector.

The current of electron diffusion is

$$
\begin{aligned}
I_n&=A_EqD_n\dfrac{\mathrm{d}n_p(x)}{\mathrm{d}x}\\
&=A_EqD_n\left(-\dfrac{n_p(0)}{W}\right)
\end{aligned}
$$

where
- $A_E$ is the cross-sectional area of the EBJ.
- $D_n$ is the electron diffusivity in the base.
- $W$ is the effective width of the base.

But in reality, recombination cause this concentration gradient line to take a slightly concave shape. The slope of the concentration profile at EBJ is slightly higher than that at CBJ to account for the small amount of electrons lost in the base region due to recombination process.

The parameter $I_S$ is given by

$$
I_S=A_EqD_nn_{p0}/W
$$
with $n_{p0}=n_i^2/N_A$, we have

$$
I_S=\dfrac{A_EqD_nn_i^2}{N_AW}
$$
We can see that $I_S$ is inversely proportional to the base width $W$ and directly proportional to EBJ area $A_E$.

>[!important]
>Twice the area will give the transistor twice the current.

The concept above is frequently employed in IC design.
## Summary and Equivalent-Circuit Models
==To do.==
