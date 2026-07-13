In real transistors, current does not abruptly cut off below threshold. Rather it drops off exponentially. 
![[iv-characteristics-65nm-nmos-70-degrees.png|300]]
This regime where $V_{gs}<V_t$ is called *weak inversion*.
The *subthreshold leakage current* increases significantly with $V_{ds}$ because of [[Drain-Induced Barrier Lowering|DIBL]].
There is a lower limit on $I_{ds}$ set by drain junction leakage that is exacerbated by the negative gate voltage.
$$
I_{ds}
=
I_{ds0}\,
\exp\!\left(
\frac{V_{gs}-V_{t0}+\eta V_{ds}-k_{\gamma}V_{sb}}{n v_T}
\right)
\left(
1-\exp\!\left(-\frac{V_{ds}}{v_T}\right)
\right)
$$

^668fef

Where
- $I_{ds0}$ is current at threshold, dependent on the process and device geometry. Can be extracted from stimulation or be calculated from[^1]
$$
I_{ds0} = \beta v_T^{2} e^{1.8}
$$
- $n$ is process-dependent term affected by the depletion region characteristics, 1.3 ~ 1.7 for CMOS processes.
In [[#^668fef]], the final term indicates that leakage is 0 when $V_{ds}=0$, but increases to its full value when $V_{ds}$ is a few multiples of the thermal voltage $v_T$.
The $\eta V_{ds}$ term is used to model [[Drain-Induced Barrier Lowering|DIBL]].
The $k_\gamma V_{sb}$ is used to model [[Body Effect|body effect]].

> [!tip]
> We can take advantage of subthreshold conduction in very low-power circuits

>[!important]
>This effect must be taken into account when designing dynamic circuits and DRAMs, which depends on the storage of charge on a capacitor.
>To counter this effect, the capacitor must be either *refreshed periodically* or *use a trickle of current* to counter the leakage.

**Subthreshold leakage increases exponentially as $V_t$ decreases or as temperature rises.**

The inverse of the slope of subthreshold current fits as a straight line on a semilog plot. It's called *subthreshold slope* $S$ with
$$
S
=
\left[
\frac{\mathrm{d}\!\left(\log_{10} I_{ds}\right)}{\mathrm{d}V_{gs}}
\right]^{-1}
=
n v_T \ln 10
$$
Typical value of $S$ is 100 mV/decade at room temperature.
Equation [[#^668fef]] can be rewritten using $S$ as
$$
I_{ds}
=
I_{off}\,
10^{\dfrac{V_{gs}+\eta\!\left(V_{ds}-V_{DD}\right)-k_{\gamma}V_{sb}}{S}}
\left(
1-\mathrm{e}^{-\dfrac{V_{ds}}{v_T}}
\right)
$$
with $I_{off}$ is the subthreshold current at $V_{gs}=0$, $V_{ds}=V_{DD}$ and $V_{sb}=0$.

[^1]: $e^{1.8}$ term is found empirically.
