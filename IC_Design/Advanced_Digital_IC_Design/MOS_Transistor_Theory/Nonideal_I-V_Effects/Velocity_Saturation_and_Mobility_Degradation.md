When there is a strong lateral field applied $\rightarrow$ the carrier collides more often with the silicon lattice. The technical term is *collisions with optical phonons* $\rightarrow$ velocity saturation.

When there is a strong vertical field applied $\rightarrow$ the carriers collide more often with the oxide layer $\rightarrow$ mobility degradation.

Mobility degradation can be modeled by replacing $\mu$ with smaller $\mu _{eff}$ that is a function of $V_{gs}$.
$$\begin{aligned}
\mu_{\mathrm{eff}-n}
&=
\frac{540\,\mathrm{cm}^2/(\mathrm{V}\cdot\mathrm{s})}
{1+\left(\dfrac{V_{gs}+V_t}{0.54\,\mathrm{V/nm}\; t_{ox}}\right)^{1.85}}
\qquad
\mu_{\mathrm{eff}-p}
=
\frac{185\,\mathrm{cm}^2/(\mathrm{V}\cdot\mathrm{s})}
{1+\left|\dfrac{V_{gs}+1.5V_t}{0.338\,\mathrm{V/nm}\; t_{ox}}\right|}
\end{aligned}$$
Accounting for these effects, a new expression to approximate velocity is
$$v =
\begin{cases}
\dfrac{\mu_{\mathrm{eff}}\,E}{1+\dfrac{E}{E_c}}, & E < E_c \\[6pt]
v_{\mathrm{sat}}, & E \ge E_c
\end{cases}$$
with the *critical electric field*
$$E_c=\frac{2v_{sat}}{\mu _{eff}}$$
and the *critical voltage*
$$V_c=E_cL$$

And with the new equation for velocity, we can modify the equations for linear and saturation currents to
$$
I_{ds} =
\begin{cases}
\dfrac{\mu_{\mathrm{eff}}}{1+\dfrac{V_{ds}}{V_c}}\,
C_{ox}\,\dfrac{W}{L}\,
\left( V_{GT}-\dfrac{V_{ds}}{2} \right)V_{ds},
& V_{ds} < V_{dsat} \quad \text{(Linear)} \\[10pt]
C_{ox}\,W\left( V_{GT}-V_{dsat} \right)v_{sat},
& V_{ds} > V_{dsat} \quad \text{(Saturation)}
\end{cases}
$$

^264b36

Note $\mu_{eff}$ is a decreasing function of $V_{gs}$ because of mobility degradation
If we equate the two equation at $V_{ds}=V_{dsat}$, we have
$$V_{dsat}=\frac{V_{GT}V_c}{V_{GT}+V_c}$$
Substitute this equation into $I_{ds}$ equation, we have a simplified expression for saturation current
$$I_{dsat}
=
W C_{ox} v_{sat}\,
\frac{V_{GT}^{2}}{V_{GT}+V_c},
\qquad
V_{ds} > V_{dsat}$$

If $V_{GT} \ll V_c$, then velocity saturation effect is negligible and the transistor is operating in linear regime. This is called *long-channel regime*.
$$I_{dsat}
\approx
W C_{ox} v_{sat}\,
\frac{V_{GT}^{2}}{V_c},
\qquad
V_{ds} > V_{dsat}$$

If $V_{GT} \gg V_c$, then equation [[#^264b36]] becomes
$$I_{dsat} \approx W C_{ox} v_{sat} V_{GT},
\qquad V_{ds} > V_c$$
We can observe that the current in long channel regime is quadratically dependent on the voltage and linearly dependent when saturated.

Though more accurate, this model is hard to apply by hand in practice. There is a simpler $\alpha$-*power law model* which fits well at $V_{ds}=V_{DD}$ across the full range of $V_{gs}$.

At low fields, the mobility of holes is much lower than that of electrons. Hence these holes experience less velocity saturation effect for a given $V_{DD}$.

As $I_{ds}$ grows linearly with $V_{gs}$ when the transistor is strongly ON. We can approximate saturation current with a straight line.
$$I_{ds}=k(V_{gs}-V^*_t)$$
With $V^*_t$ is the x-intercept.
![[sat-i-linear-approx.png|200]]
