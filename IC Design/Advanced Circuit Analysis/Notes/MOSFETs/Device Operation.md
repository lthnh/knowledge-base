## Operation with Zero Gate Voltage
As stated in [[Advanced Circuit Analysis/Notes/MOSFETs/Device Structure|MOSFETs' structure]], the drain and source regions form with the body two back-to-back diodes (in case of n-type MOSFET). This prevents current conduction from drain to source when $v_{ds}$ is applied.
The path between source and drain has very high resistance, on the order of $10^{12} \space \ohm$.
## Operation with Non-Zero Gate Voltage
In the case of n-type MOSFET, when there is positive voltage applied at the gate, the holes on the opposite side of the oxide layer are repelled away since they effectively are positive carriers. This leaves bounded negative charges associated with acceptor atoms. This region is called the depletion region.

As voltage increases above certain threshold $V_t$, more electrons are attracted to the opposite side of the gate. Effectively creating a channel for conduction. The induced channel is called an *inversion layer*.

>[!note]
>The gate voltage must exceed $V_t$ for a channel to form.

The voltage, or electric field, controls the amount of charge in the channel thus the current that will flow through the channel when $v_{DS}$ is applied.
$\Rightarrow$ This is the origin of the name "field-effect transistor", or FET.

The excess of $v_{GS}$ over $V_t$ is termed the *effective voltage* or the *overdrive voltage*. This is the quantity that determines the amount of charge in the channel. ^6d1d52

$$
v_{GS}-V_t \equiv v_{OV}
$$

### Applying a Small $v_{DS}$
The channel (or the transistor) acts as a linear resistance whose value is controlled by overdrive voltage $v_{OV}$, which in turn is determined by $v_{GS}$.

Increasing $v_{GS}$ above threshold $V_t$ enhances the channel, hence the names *enhancement-mode operation* and *enhancement-type MOSFET*.

>[!note]
>Current enters the drain = current leaves the source. Gate current = 0. (Ideally)

### As $v_{DS}$ Is Increased
$v_{DS}$ increases make the channel become more tapered and its resistance increases correspondingly.

## Operation with $v_{DS} > v_{OV}$
When $v_{DS}$ approaches $V_{OV}$, the channel depth at drain will reach zero. This gives rise to the term *channel pinch-off*.

>[!note]
>Increasing $v_{DS}$ above $V_{OV}$ has no effect on the channel shape and charge.

This also means the current will remain constant at the value reached for $v_{DS}=V_{OV}$.
$\Rightarrow$ The current is said to *saturate* at that value.

![[transistor-operating-modes.png|400]]

Note: this is a ideal model. Real transistors face non-ideal effects, see more at [[Nonideal I-V Effects]].
