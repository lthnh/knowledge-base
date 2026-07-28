In ideal transistor, $I_{ds}$ is independent of $V_{ds}$.
But in reality, the p-n junction between the drain and the body forms a depletion region with width $L_d$ that increases with $V_{db}$ - the voltage between the drain and the body.
![[deplet-region-shorts-channel-length.png|300]]
This reduces the channel length to
$$L_{eff}=L-L_d$$
We can assume $V_s \approx V_b$, hence $V_{ds} \approx V_{db}$.
This means increasing $V_{ds}$ will shortens the channel length, results in higher current.

> [!important]
> $I_{ds}$ increases with $V_{ds}$ in saturation.

Channel length modulation is important for analog designers as it reduces the gain of amplifiers.
It's generally unimportant for qualitatively understanding digital circuits.






