The use of transistor in amplification depends on the fact that MOSFET is a voltage-controlled current source in the saturation region. The drain current of the MOSFET is determined via

$$
i_D = \dfrac{1}{2}k'_n(v_{GS}-V_{tn})^2
$$

Similarly, when a BJT is operated in the active region, its current is determined via

$$
i_C = I_S\exp(v_{BE}/V_T)
$$

In both first-order models, the drain/collector current does not depend on the $v_{DS}$/$v_{CE}$. For MOSFET, this is caused by channel cutoff. For BJT, this is resulted from collector-base being reversed-bias, thus isolating the collector.

For MOSFET to enter saturation mode, the usual rule applies: $v_{DS} > V_{OV}$.
For BJT to enter active mode, CBJ must be reversed-bias. Since CBJ is also a pn junction, it isn't effectively conductive until $v_{CB} < -0.4\space\mathrm{V}$. Also, $v_{BE}$ of conducting junction lies around 0.7 $\mathrm{V}$. So $V_{CE}$ must be larger than 0.3 $\mathrm{V}$.

Transistor is a transconductance amplifier: the input is a voltage and the output is a current. We can convert this current into voltage by putting in a resistor. To maintain common reference between the input and output, the drain voltage is measured with respect to ground:

$$
v_{DS} = V_{DD}-i_DR_D
$$
and in case of BJT,

$$
v_{CE} = V_{DD} - i_CR_C
$$

![[nmos-transistor-amplifier-vtc.png]]This is VTC of an NMOS amplifier. Notice that as $V_{GS}$ creeps up, the transistor starts conducting. At first, $V_{DD}$ is still much larger than $V_{OV}$. But as $V_{GS}$ gets larger, so do the drain current. The drain current causes drain voltage to drop. This happens until the drain voltage is equal to the gate voltage minus the threshold voltage.

Same situation for BJT amplifier:
![[npn-transistor-amplifier-vtc.png]]Notice that in the saturation/active region, the VTC is steep hence suitable for amplification applications. But in VTC equation is nonlinear. To obtain linear amplification, we need first to bias the transistor to a point between A and B.