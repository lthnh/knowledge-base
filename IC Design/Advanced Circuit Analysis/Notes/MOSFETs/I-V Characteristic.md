## The $i_D$-$v_{DS}$ Characteristics
There are three regions of operation for MOSFETs: the cutoff region, the triode region, and the saturation region.

For transistors utilized as a switch: the cutoff region and the triode region are useful.
For transistors used in amplifier design: it must operate in the saturation region.
==More details about this to be added later.==

$v_{OV}$ [^1] separates the triode region and the saturation region. If $v_{DS} > v_{OV}$, the transistor is in saturation region. Otherwise it is in triode mode.

![[n-mos-i-v-characteristic.png|500]]

Another way to check transistor's mode of operation is to check the voltage difference between gate and drain. If $v_{GD}>V{tn}$, the transistor is in triode mode. If $v_{GD} \leq V_{tn}$, the transistor is now in saturation mode.

![[n-mos-relative-levels-of-voltage-relation-with-mode.png|400]]

Each $v_{OV}$ gives different curves, as shown by the figure below.

![[n-mos-characteristic-with-different-v-ov.png|400]]

The locus of saturation points is given by this parabolic curve

$$
i_D=\dfrac{1}{2}k_n'\left(\dfrac{W}{L}\right)v_{DS}^2
$$

## The $i_D$-$v_{GS}$ Characteristic
When in saturation mode, the transistor operate like a voltage-controlled current source determined by $v_{GS}$ or more specifically, $v_{OV}$. Described by this equation

$$
\begin{aligned}
i_D &= \frac{1}{2} k_n' \left( \frac{W}{L} \right) (v_{GS} - V_{tn})^2 \\
&= \frac{1}{2} k_n' \left( \frac{W}{L} \right) v_{OV}^2
\end{aligned}
$$

^ebffcc

Note that, ideally $i_D$ is independent of $v_{DS}$ but this is not the case, see more below.

The relationship above underlines the application of MOSFET as an amplifier. But this relationship is nonlinear and need additional work to design linear amplifiers.

![[n-mos-i-vgs-characteristic.png|300]]

As MOSFET operates in the saturation region can be viewed as voltage-controlled current source, we can replace it with a equivalent circuit known as *large-signal equivalent circuit*.

![[n-mos-in-saturation-equiv-circuit.png|400]]

Note that ideal current source has infinite output resistance. Real MOSFET has finite output resistance due to nonideal effect(s) like *channel-length modulation*.
### Finite Output Resistance in Saturation

Ideally, $i_D$ is independent of $v_{DS}$. The idealization is based on the premise that once the channel is pinched off, increasing $v_{DS}$ have no effect on the channel's shape.

In reality, increasing $v_{DS}$ reduces the channel length $L$. This is [[Channel Length Modulation|channel length modulation]].
$i_{D}$ is inversely proportional to $L$ $\rightarrow$ current increase.

The voltage across the channel remains constant at $v_{OV}$, and the additional voltage applied at drain appears as a voltage drop across the depletion region. This voltage sweeps the electrons from the channel end to the drain.

![[channel-length-modulation-effect.png|400]]

This effect can be accounted for by including a factor $1 + \lambda(v_{DS}-v_{OV})$, or for simplicity, $(1 + \lambda v_{DS})$ in the equation for $i_D$.

$$
i_D = \frac{1}{2} k_n' \left( \frac{W}{L} \right) (v_{GS} - V_{tn})^2 \left( 1 + \lambda v_{DS} \right)
$$

where
- $\lambda$ is a device parameter ($V^{-1}$), depends on both the fabrication technology and the channel length that circuit designer selects. ^53796d

>[!note]
>Newer technologies $\rightarrow$ shorter channels $\rightarrow$ greatly impacted by channel-length modulation effect.

>[!important]
>For a given technology, $\lambda$ is inversely proportional to $L$.

This graph is a plot of typical $i_D$-$v_{DS}$ characteristics shown the effect of channel-length modulation.

![[i-vds-characteristic-with-channel-L-modulation.png|400]]

In the saturation region, $i_D$ is linearly dependent on $v_{DS}$ represented by the factor $(1 + \lambda v_{DS})$.
Also when the I-V characteristics are extrapolated, they intercept the $v_{DS}$ axis at $-V_A$, where $V_A >0$.
When $i_D=0$, we have

$$
V_A=\dfrac{1}{\lambda}
$$
where
- $V_A$ is a device parameter ($V$) called the *Early voltage*, proportional to the channel length that the designer selects for a MOSFET. ^7296dc

It is possible to isolate this dependence of $V_A$ on $L$ with

$$
V_A=V_A'L
$$

where
- $V_A'$ is entirely process-technology dependent ($V/ \mu m$), typically about 5 $V/ \mu m$ to 50 $V/ \mu m$.

Now, since $i_{DS}$ changes with $v_{DS}$, the output resistance is finite. Defining the output resistance $r_0$ as

$$
\begin{aligned}
r_o &\equiv \left. \left( \frac{\mathrm{\partial} i_D}{\mathrm{\partial} v_{DS}} \right)^{-1} \right|_{v_{GS}\ \text{constant}} \\
&= \left[ \lambda \frac{k_n'}{2} \frac{W}{L} (V_{GS} - V_{tn})^2 \right]^{-1} \\
&= \dfrac{1}{\lambda I_D} \\
&= \dfrac{V_A}{I_D'}
\end{aligned}
$$

where
- $I_D'$ is the drain current without channel-length modulation taken into account. Can be calculated with [[#^ebffcc]].

Now the large-signal equivalent circuit can incorporate this $r_0$ into its model.

![[nmos-better-large-signal-equiv-circuit.png|400]]


[^1]: See more in [[Device Operation#^6d1d52|overdrive voltage]].
