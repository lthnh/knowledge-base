## D5.8 p. 278

![[exercise-D5.8-p.278.png|100]]

![[exercise-D5.8-p.278-1.png]]

We can calculate $R_D$ by
$$
\begin{aligned}
R_D &= \dfrac{V_{DD} - V_D}{I_D} \\
&= \dfrac{2.5 - 0.4}{0.3} \\
&= 7 \space k\ohm
\end{aligned}
$$
We find $V_{GD} < V_t$, which means the transistor is in saturation mode. Neglecting the channel-length modulation effect, we find $V_{OV}$ by
$$
\begin{aligned}
I_D &= \dfrac{1}{2} \mu_n C_{ox} \dfrac{W}{L} V_{OV}^2 \\
\rightarrow 300 &= \dfrac{1}{2} \times 60 \times \dfrac{120}{3} \times V_{OV}^2 \\
\rightarrow V_{OV} &= 0.5 \rm{V}
\end{aligned}
$$
But $V_{GS}=V_t+V_{OV}$ so $V_{GS}=1+0.5=1.5 \space \rm{V}$.
Since $V_G$ is tied to the ground $\rightarrow$ $V_S=-1.5 \space \rm{V}$.
We can then fine $R_S$ by
$$
\begin{aligned}
R_S &= \dfrac{V_S-V_{SS}}{I_D} \\
&= \dfrac{-1.5-(-2.5)}{0.3} \\
&= 3.3 \space k\ohm
\end{aligned}
$$
## D5.9 p. 279

![[exercise-d5.9-p.279.png]]

![[exercise-d5.9-p.279-1.png|200]]

We find that $V_D=V_G$, thus $Q_1$ is in saturation mode.
$V_{OV} = V_{GS} - V_{tn} = 0.7 - 0.5 = 0.2$.
The current $I_D$ is
$$
\begin{aligned}
I_D &= \dfrac{1}{2} \mu_n C_{ox} \dfrac{W}{L} V_{OV}^2 \\
&= \dfrac{1}{2} \times 0.4 \times \dfrac{0.72}{0.18} \times 0.2^2 \\
&= 0.032 \space \rm{mA}
\end{aligned}
$$
The value of $R$ is
$$
R = \dfrac{1.8 - 0.7}{0.032} = 34.4 \space \rm{k}\ohm
$$
## D5.10 p. 279-280

![[exercise-d5.10-p279-280.png]]

![[exercise-d5.10-p.279-280-1.png|300]]

Since $V_G=0.7 \space \rm{V}$, for $Q_2$ to operate at the edge of the saturation region $V_{DS}=V_{GS}-V_{tn}$.
$\rightarrow V_D=0.7-0.5=0.2$.
$\rightarrow V_{OV} = V_{GS} - V_{tn} = 0.7 - 0.5 = 0.2 \rm{V}$.

The current $I_D$ is
$$
\begin{aligned}
I_D &= \dfrac{1}{2} \mu_n C_{ox} \dfrac{W}{L} V_{OV}^2 \\
&= \dfrac{1}{2} \times 0.4 \times \dfrac{0.72}{0.18} \times 0.2^2 \\
&= 0.032 \space \rm{mA}
\end{aligned}
$$
The resistor $R_2$ is
$$R_2=\dfrac{1.8-0.2}{0.032}=50\rm{k}\ohm$$
## 5.11 p. 281

![[exercise-5.11-p.281.png]]

![[exercise-5.11-p.281-1.png]]

From the example's calculation in the book, the current $I_D$ is 0.395 mA $\approx$ 0.4 mA.
Since $R_D$ is much larger than the effective resistance between drain and source. Doubling $R_D$ will result in reducing the current by half, thus new $I_D$ $\approx$ 0.2 mA.
Now, when transistor is in triode mode, it behaves like a resistor. Assume its resistance is almost constant. Halving the current will also halve the voltage across it, thus $V_D$ $\approx$ 0.05 V.
## 5.12 p. 283

![[exercise-5.12-d5.13-p.283-2.png]]

![[exercise-5.12-p.283.png]]

![[exercise-5.12-d5.13-p.283.png|400]]

From the example we can see that $V_S$ = 3 V and $I_D$ = 0.5 mA. We also have $V_{OV}$ = $V_{GS}-V_{tn}=2-1=1$.

The largest value of $R_D$ means the current must be small enough so that the transistor is still operating in the saturation region.
$\rightarrow$ The transistor is operating at the edge of the saturation region.
$\rightarrow$ $V_{DS}$ = $V_{OV}$ = 1 V.
$\rightarrow$ $V_D$ = 4 V.

The $R_D$ value is
$$
R_D=\dfrac{10-4}{0.5}=12 \rm{k}\ohm
$$
## D5.13 p. 283

![[exercise-d5.13-p.283.png]]

$$
\begin{aligned}
R_D&=\dfrac{V_{DD}-V_D}{I_D}=\dfrac{5-3.4}{0.32}=5 \space \rm{k}\ohm \\
R_S&=\dfrac{V_S}{I_D}=\dfrac{1.6}{0.32}=5 \space \rm{k}\ohm
\end{aligned}
$$
Assume the MOSFET is operating in the saturation region, we have
$$
\begin{aligned}
I_D&=\dfrac{1}{2}\mu_nC_{ox}\dfrac{W}{L}V_{OV}^2\\
\rightarrow 0.32&=\dfrac{1}{2}\times 1\times V_{OV}^2\\
\rightarrow V_{OV}&=0.8
\end{aligned}
$$
This assumption is valid as $V_{DS}=1.8>V_{OV}$.
This means $V_{GS}=V_{tn}+V_{OV}=1+0.8=1.8$ V $\rightarrow$ $V_G=1.8+1.6=3.4$ V.
Looking at the voltage divider, we have
$$
3.4\space\rm{V}=1\space\mu\rm{A}\times R_G\rightarrow R_{G2}=3.4\space\rm{M}\ohm
$$
$$
R_{G1}=\dfrac{5-3.4}{1}=1.6\space\rm{M}\ohm
$$
## D5.14 p. 285

![[exercise-d5.14-p.285.png|600]]

We find $V_{SG}$ by
$$
V_{SG}=|V_{tp}|+|V_{OV}|=0.4+0.6=1\space\rm{V}
$$
This means $V_S$ = 1 V as $V_G$ is tied to ground.
$V_{SD}>V_{OV}$ so the transistor is in saturation mode.
We can then find $I_D$ with
$$
\begin{aligned}
I_D&=\dfrac{1}{2}k_p'\dfrac{W}{L}V_{OV}^2\\
&=\dfrac{1}{2}\times 0.1\times\dfrac{10}{0.18}\times 0.6^2\\
&=1\space\rm{mA}
\end{aligned}
$$
The value of $R$ is
$$
R=\dfrac{1.8-1}{1}=800\space\ohm
$$
## 5.15 p. 287

![[exercise-5.15-p.287.png|500]]

**When $v_i$ = 0**
Assume that both transistors are off. This means $v_o$ = 0. So $|V_{GS}|$ for both transistor are zero $\rightarrow$ both transistors are off. We can conclude this is a valid assumption.

**When $v_i$ = +2.5 V**
For positive $v_i$, we assume $Q_N$ is on and $Q_P$ is off. As $V_{DS}$ of NMOS = 0. The NMOS transistor are in saturation mode.
We obtain the current $i_{DN}$ by

$$
\begin{aligned}
i_{DN}&=\dfrac{1}{2}k_n'\dfrac{W}{L}(V_{GS}-V_{tn})^2\\
&=\dfrac{1}{2}\times 1\times (V_{GS}-1)^2
\end{aligned}
$$

^6632af

We also have $i_{DN}$ equal to

$$
i_{DN}=\dfrac{v_o}{10}=\dfrac{V_S}{10}
$$

^4a9252

Combining [[#^6632af]] and [[#^4a9252]], we have

$$
\begin{aligned}
\dfrac{V_S}{10}&=\dfrac{1}{2}\times (1.5-V_S)^2\\
\rightarrow V_S&=2.157\space\vee\space1.043
\end{aligned}
$$

For $V_S$ = 2.157, $V_{GS}$ < 1 so this value is invalid.
We find $i_{DN}$ by

$$
i_{DN}=\dfrac{1.043}{10}=0.104\space\rm{mA}
$$

We check this against our assumption, we find $V_{SG}$ = -1.46 < $|V_{pn}|$ = 1 V $\rightarrow$ the assumption is valid.

**When $v_i$ = -2.5 V**
For negative $v_i$, we assume $Q_N$ is off and $Q_P$ is on.

Redo the same analysis above, we have

$$
\begin{aligned}
\dfrac{-V_S}{10}&=\dfrac{1}{2}\times 1\times (V_S+1.5)^2\\
\rightarrow V_S&=-1.043\space\vee-2.157
\end{aligned}
$$

If $V_S$ = -2.157 V, then $V_{SG}$ < $V_{tn}$ $\rightarrow$ $Q_P$ is not on $\rightarrow$ violate our assumption.

With $V_S$ = -1.043, we recheck against our assumption and find that both $V_{GS}<V_{tn}$ and $V_{SG}>V_{tp}$. Our assumption is valid.

The current $i_{DP}$ can then be found.

$$
i_{DP}=\dfrac{-V_S}{10}=\dfrac{1.043}{10}=0.104\space\rm{mA}
$$


