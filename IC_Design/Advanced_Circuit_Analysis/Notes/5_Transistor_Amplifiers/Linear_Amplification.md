## Biasing
This is to obtain almost linear amplification on both MOSFET and BJT. A dc voltage is selected to obtain a operating point Q on the [[Basics|segment AB of the VTC]]. Coordinates of point Q is $V_{GS}$ and $V_{DS}$, related by

$$
V_{DS} = V_{DD} - \dfrac{1}{2}k'_nR_D(V_{GS}-V_{t})^2
$$

Point Q is known as *bias point*, *dc operating point* or *quiescent point* (since there is no signal component present, hence it's "quite" around here).

Call $v_{gs}$ the signal component that we need to amplify. The instantaneous value of $v_{GS}$ is

$$
v_{GS}(t) = V_{GS} + v_{gs}(t)
$$

This equation in essence represents instantaneous operating point. The amplitude of signal will "move" the operating point back and forth within the segment AB. If the signal ever gets too large, it might "move" the operating point beyond the saturation region. For example, if $v_{gs}$ goes negative, the transistor may move into the cutoff region and make the output signal positive peaks clipped off. Otherwise, if $v_{gs}$ goes positive too hard, it might make the transistor go into triode/saturation (for BJT) region and make the output negative peaks flat.

This means the selection of operating point is important, and it determines the *maximum allowable signal swing at the output*.

The same is applied for BJT counterpart:

$$
V_{CE} = V_{CC} - R_CI_S\mathrm{e}^{V_{BE}/V_T}
$$

$$
I_C = I_S\mathrm{e}^{V_{BE}/V_T}
$$

Superimposing a small-signal $v_{be}$ on the dc bias voltage $V_{BE}$ is

$$
v_{BE}(t) = V_{BE} + v_{be}(t)
$$
