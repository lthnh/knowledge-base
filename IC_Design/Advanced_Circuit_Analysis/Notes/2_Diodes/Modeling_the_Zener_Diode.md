![[zener-diode-operating-region.png|400]]

The manufacturer usually specifies the diode voltage $V_Z$ at test current $I_{ZT}$.
These values determine the operating point $Q$.
As the current through the diode changes, its voltage will change slightly.

$$
\Delta V=r_z \Delta I
$$

where
- $r_z$ is the inverse of the slope of almost-linear I-V curve at point Q, known as *incremental resistance* or *dynamic resistance*. It is in the range of a few ohms to a few tens of ohms.

>[!note]
>$r_z$ the lower, the better it is in the design of voltage regulator.

>[!important]
>While $r_z$ is low or almost constant over a wide range of current. Its value increases considerably in the vicinity of the knee
>$\Rightarrow$ Avoid operating the zener in this low-current region.

Aside from $V_z$, $I_{ZT}$ and $I_{ZK}$, the manufacturer also specifies the maximum power dissipation the device can handle.

Due to almost-linear I-V curve, the device can be modeled like this figure below:

![[zener-model-above-knee.png|200]]

$V_{Z0}$ denoted the voltage in which the straight line tangent to I-V curve at the operating point intersecting with the voltage axis.

In practice, $V_{Z0} \approx V_{ZK}$.

The equivalent circuit model is

$$
V_Z=V_{Z0}+r_z I_Z
$$

and valid only for $I_Z > I_{ZK}$, $V_Z > V_{Z0}$.

==There is design example in the book p. 204.==
## Temperature Effects
Zener voltage $V_Z$ dependence on temperature is characterized through a quantity called *temperature coefficient TC*, or *temco*, expressed in mV/$\degree$C.
For a given diode, TC also varies with diode current.
$V_Z < 5$: negative TC.
$V_Z > 5$: positive TC.
$V_Z \approx 5 V$: can be zero at some at some operating current.

Commonly used technique to create reference voltage with low temperature coefficient is combine zener diode with positive temco of about 2 mV/$\degree$C in series with forward conducting diode. Forward conducting diode has voltage drop $\simeq$ 0.7 V and negative temco about -2 mV/$\degree$C.
$\Rightarrow$ This combination have temco about zero.

