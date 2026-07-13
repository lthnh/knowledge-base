Due to 2 physical mechanisms:
1. *Fowler-Nordheim* (FN) *tunneling*
2. *Direct tunneling*

FN tunneling is prominent at high voltage and moderate oxide thickness.
It's used to program EEPROM memories.

Direct tunneling is most important at lower voltage with thin oxides.
It's the dominant leakage component.

Direct gate tunneling current can be estimated as
$$
I_{\mathrm{gate}}
=
W A
\left(\frac{V_{DD}}{t_{ox}}\right)^{2}
\exp\!\left(-B\,\frac{t_{ox}}{V_{DD}}\right)
$$
where $A$ and $B$ are technology constants.

Transistors need good ON current through high $C_{ox}$ leads to drive in oxide thickness reduction. This in turn increase gate leakage as gate leakage increases by a factor of 2.7 or more per angstrom reduction in thickness.

Large tunneling currents impact dynamic nodes and quiescent power consumption and thus limits the (equivalent) oxide thickness to at least 10.5 $\mathring{A}$.

Tunneling current can be order of magnitude higher for nMOS than pMOS with $\mathrm{SiO}_2$ gate dielectrics cause electrons tunnel from conduction band while holes tunnel from valence band.

Different materials have different tunneling properties.
