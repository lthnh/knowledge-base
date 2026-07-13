The p-n junctions between diffusion regions and the substrate or well form diodes.
The well-to-substrate junctions is another diode.
![[subtrate-to-diffusion-diodes-cmos.png|500]]
As the substrate or well needs to tie to GND or $V_{DD}$ to ensure these diodes does not conduct in normal operation, we effectively *reverse bias* the diodes.
Reverse-biased diodes still conduct a small amount of current
$$
I_D
=
I_S
\left(
\mathrm{e}^{\frac{V_D}{v_T}}
-
1
\right)
$$
Where
- $I_S$ depends on doping levels and on the area and perimeter of the diffusion region.
- $V_D$ is the diode voltage.
When the junction is reverse biased by significantly more than the thermal voltage, the leakage is $-I_S$.
It's in the range of 0.1-0.01 fA/$\mu m^2$, which is negligible compared to other leakage mechanisms.
## BTBT and GIDL
Heavily doped drains also subject to *band-to-band tunneling* (BTBT) and *gate-induced drain leakage* (GIDL).
### BTBT

^7b13e9

*BTBT* occurs at the source/drain and body junction when the junction is reverse-biased.
It's a function of reverse bias and doping levels.
High halo doping used to increase $V_t$ to alleviate subthreshold current instead causes BTBT to grow $\rightarrow$ most of the leakage occurs along the sidewall closest to the channel where the doping level is the highest.
*Trap-assisted tunneling* (TAT) makes this type of leakage worse. This is caused by defects in the silicon lattice called traps reduce the distance that carriers must tunnel.
$$
I_{BTBT}
=
W X_j A
\frac{E_j}{E_g^{0.5}}
V_{DD}\,
\exp\!\left(
- B\,\frac{E_g^{1.5}}{E_j}
\right)
$$
Where
- $X_j$ is the junction depth of the diffusion.
- $E_g$ is the band gap voltage.
- $A$ and $B$ are technology constants.
- $E_j$ is electric field along the junction at the reserve bias of $V_{DD}$.
$E_j$ is calculated as follow
$$
E_j
=
\sqrt{
\frac{2 q\, N_{halo} N_{sd}}
{\varepsilon \left( N_{halo} + N_{sd} \right)}
\left(
V_{DD}
+
v_T \ln\!\left(
\frac{N_{halo} N_{sd}}{n_i^{2}}
\right)
\right)
}
$$
### GIDL
This effect occurs where the gate overlaps the drain.
It's most pronounced when the drain is at a high voltage and the gate is at a low voltage.
GIDL proportional to gate-drain overlap (hence to transistor width) and drain-to-gate voltage (it's a strong function of electric field[^1]).
*Normally insignificant at* $\left| V_{gd} \right| \le V_{DD}$, but not when the gate is driven outside the rails (in an attempt to cut off subthreshold current).

[^1]: This means the gate leakage increases rapidly with voltage.
