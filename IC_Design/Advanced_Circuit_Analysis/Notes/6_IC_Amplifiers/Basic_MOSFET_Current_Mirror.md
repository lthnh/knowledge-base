![[generic-current-mirror.png|300]]

This is a generic current mirror. $I_{REF}$ can be generated from a resistor tied to $V_{DD}$ and drain of the transistor.

In this image, transistor $Q_1$, has its drain and gate connected together, is called diode-connected. This forces $Q_1$ to operate in saturation mode ($V_{DS} = V_{GS})$. $I_{REF}$ can be calculated as

$$
I_{REF} = \dfrac{1}{2}k'_n\left(\dfrac{W}{L}\right)_1(V_{GS}-V_{tn})^2
$$

^1b0a08

If we assume $Q_2$ also operate in saturation mode, $I_O$ is then

$$
I_O = \dfrac{1}{2}k'_n\left(\dfrac{W}{L}\right)_2(V_{GS}-V_{tn})^2
$$

^a4fd8a

From [[#^1b0a08]] and [[#^a4fd8a]], we can see that $I_{REF}$ and $I_O$ is related by this equation

$$
I_O = \dfrac{{W/L}_1}{{W/L}_2} I_{REF}
$$

Hence in this circuit, ideally, the output current only depends on the ratio of geometries of transistors.
## Effects of $V_O$ on $I_O$
For this circuit to operate correctly, $V_O$ should be larger than $V_{OV}$ (just a reminder, $V_{OV} = V_{GS} - V_{tn}$) because this puts the $Q_2$ transistor in saturation mode. This means $V_O$ can be as low as a few tenths of a volt but circuit still operates correctly.

As the process technology gets smaller, [[Channel_Length_Modulation|channel length modulation]] has increasing effects on output current. To increase output resistance, people choose longer channel length.[^1] The current with channel length modulation effects taken into account is

$$
I_O = \dfrac{{W/L}_2}{{W/L}_1}I_{REF}\left(1 + \dfrac{V_O-V_{GS}}{V_{A2}}\right)
$$
with
- $V_{A2}$ is the Early voltage of $Q_2$.

[^1]: For a given process technology, Early voltage $V_A$ is proportional to the transistor channel length.
