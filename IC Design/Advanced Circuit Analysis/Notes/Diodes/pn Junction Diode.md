## Forward-Bias Region
The I-V relationship is

$$
i=I_S(\mathrm{e}^{v/V_T}-1)
$$

$I_S$ is proportional to junction area, as in equation [[pn Junction (with Applied Voltage)#^7822a2]]. Doubling the junction area will double the value of $I_S$. Thus doubling the forward current.

At room temperature (20 $\degree$C), the value of $V_T$ is 25.3 mV.

This relation can be expressed in logarithmic form

$$
v=V_T\ln{\dfrac{i}{I_S}}
$$

This exponential relationship of current $i$ to the voltage $v$ holds over many decades of current (as many as seven decades, or a factor of $10^7$).

Assume there are two states for the diode: when the diode voltage is $V_1$ with a corresponding $I_1$ and when the diode voltage is $V_2$ with a corresponding $I_2$.

$$
\begin{aligned}
I_1&=I_S\mathrm{e}^{V_1/V_T}\\
I_2&=I_S\mathrm{e}^{V_2/V_T}
\end{aligned}
$$

^5aba4a

Combine these [[#^5aba4a]], we have

$$
\dfrac{I_2}{I_1}=\mathrm{e}^{(V_2-V_1)/V_T}
$$

It can be rewritten as

$$
V_2-V_1=V_T\ln{\dfrac{I_2}{I_1}}
$$

or in terms of base-10 logarithms,

$$
V_2-V_1=2.3V_T\log{\dfrac{I_2}{I_1}}
$$

This means for a decade of change in current, the diode voltage drop change by 2.3$V_T$ $\approx$ 60 mV.

![[details-diode-i-v-characteristic.png|500]] ^212f29

The 0.5 V voltage in the [[#^212f29|graph]] above is referred to the *cut-in voltage*. This is a consequence of the exponential relationship. This also means the current increase exponentially with minimal increase in voltage drop, with "fully conducting" diode voltage drop falls around 0.6 V to 0.8 V.
$\Rightarrow$ This gives rise to simple fixed 0.7-V voltage drop model for diode.

>[!important]
>Diodes with different current ratings will experience 0.7-V voltage drop at different currents.

Since both $I_S$ and $V_T$ are dependent on temperature, the forward I-V characteristic varies with temperature.

![[temperature-dependence-forward-characteristic.png|400]]

At a given diode current, the voltage drop increases by approximately 2 mV for every increment of 1 $\degree$C in temperature. ^e143db

>[!note]
>[[#^e143db|The property above]] is exploited in the design of electronic thermometers.

## Reverse-Bias Region
When voltage $v$ across the diode is made negative, the diode enters reverse-bias region of operation.

When $v$ is both negative and of a few magnitude of $V_T$, the current approaches $I_S$.

$$
i \simeq -I_S
$$

Real diodes have much reverse current much larger than $I_S$. For example, a small-signal diode whose $I_S$ is on the order of $10^{-14}$ A to $10^{-15}$ A could show a reverse current of 1 nA.
The reverse current also increases somewhat with the increase in magnitude of reverse voltage.

>[!note]
>A large part of the reverse current is due to leakage effects.

These leakage currents are proportional to the junction area, just like $I_S$. But they are different in temperature dependence:
- $I_S$ doubles for every 5 $\degree$C increase in temperature.
- Reverse current doubles for every 10 $\degree$C increase in temperature. (rule of thumb)

## Breakdown Region
When reverse voltage passes through *breakdown voltage*. This is the voltage $V_{ZK}$ in the [[#^212f29|graph]] above[^1].

In the breakdown region, rapid current increase associates with minimal change in voltage drop. Current is required to be limited by the external circuit to a safe value.

The I-V characteristic in this region is almost a vertical line $\rightarrow$ enable use in voltage regulation.

[^1]: Z for Zener. K for Knee.
