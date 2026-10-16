## Plane Waves in a Lossless Medium
In a lossless medium, $\epsilon$ and $\mu$ are real numbers. So is $k$.

Considering an electric field with only an $\hat{x}$ component and uniform in the $x$ and $y$ directions. This means $\dfrac{\partial}{\partial x} = 0$ and $\dfrac{\partial}{\partial y} = 0$. The Helmholtz equation reduces to

$$
\dfrac{\partial^2 E_x}{\partial x^2} + k^2 E_x = 0
$$

This is a homogeneous ODE. Its two independent solutions are

$$
E^+e^{-jkz} \space \text{and} \space E^-e^{jkz}
$$

where $E^+$ and $E^-$ are arbitrary amplitude constants.

The combination of the two linearly independent solutions is the "complete" solution to this ODE:

$$
E_x(z) = E^+ e^{-jkz} + E^- e^{jkz}
$$

This solution is time harmonic case at frequency $\omega$. In time domain representation:

$$
E_x(z, t) = E^+ \cos(\omega t - kz) + E^- \cos(\omega t + kz) 
$$

The first component of the solution represents is the wave travelling forward. Notice in the phasor representation, the wave amplitude decreases as $z$ increases. The opposite thing happens to the second component of the solution. The amplitude decreases as $z$ decreases. This component represents part of the wave being reflected back.

To maintain a fix point on the wave, one must move along the $z$ axis, i.e. keeping $\omega t - kz$ constant. The velocity of the wave in this sense is called the *phase velocity* as this is the velocity of a fixed phase point on the wave.

$$
v_p = \dfrac{\mathrm{d}z}{\mathrm{d}t}= \dfrac{\mathrm{d}}{\mathrm{d}t} \left( \dfrac{\omega t - \text{constant}}{k} \right) = \dfrac{\omega}{k} = \dfrac{1}{\sqrt{\mu \epsilon}}
$$

In free space, $v_p = \dfrac{1}{\sqrt{\mu \epsilon}} = c$, which is the speed of light.

The wavelength $\lambda$ is defined as the distance between successive minima or successive maxima at the fixed instant of time.

$$
(\omega t - kz) - [\omega t - k (z + \lambda)] = 2 \pi
$$

or 

$$
\lambda = \dfrac{2 \pi}{k} = \dfrac{2 \pi v_p}{\omega} = \dfrac{v_p}{f}
$$

To find the magnetic component of the wave, we can use curl equations from [[Wave_Equation#^53c086]]. Applying the first curl equation, we have $H_x = H_z = 0$ and

$$
H_y = \dfrac{j}{\omega \mu} \dfrac{\partial E_x}{\partial z} = \dfrac{1}{\eta}(E^+ e^{-jkz} - E^- e^{jkz})
$$

where $\eta = \omega\mu/k = \sqrt{\mu/\epsilon}$ is the *intrinsic impedance* of the medium. In free space, the intrinsic impedance is $\eta_0 = \sqrt{\mu_0/\epsilon_0} = 377 \space \Omega$ The ratio of the $\vec{E}$ and $\vec{H}$ field components is seen to have units of impedance, known as *wave impedance.*

For plane waves, the wave impedance is equal to the intrinsic impedance of the medium.

Note that the $\vec{E}$ and $\vec{H}$ vectors are orthogonal to each other and orthogonal to the direction of propagation ($\pm \hat{z}$). This is a characteristic of transverse electromagnetic (TEM) waves.
## Plane Waves in a General Lossy Medium
If the medium is conductive with conductivity $\sigma$, Maxwell's curl equations can be written as

$$
\begin{align*}
\Delta \times \vec{E} &= -j\omega\mu\vec{H} \\
\Delta \times \vec{H} &= j\omega\epsilon\vec{E} + \sigma\vec{E}
\end{align*}
$$

The resulting equation for $\vec{E}$ becomes

$$
\Delta^2\vec{E} + \omega^2\mu\epsilon \left(1-j\dfrac{\sigma}{\omega\epsilon}\right)\vec{E} = 0
$$

We can see the similarity with [[Wave_Equation#^a275e0]], with the difference being the quantity $k$. In lossless case, $k = \omega^2\mu\epsilon$ but in this case, $k = \omega^2\mu\epsilon[1 - j(\sigma/\omega\epsilon)]$.

The *complex propagation constant* for the medium is

$$
\gamma = \alpha + j\beta = j\omega\sqrt{\mu\epsilon}\sqrt{1-j\dfrac{\sigma}{\omega\epsilon}}
$$

where
- $\alpha$ is the *attenuation constant*
- $\beta$ is the *phase constant*

If we assume an electric field with only $\hat{x}$ component and uniform in x and y, the wave equation reduces to

$$
\dfrac{\partial^2 E_x}{\partial z^2} - \gamma^2 E_x = 0
$$

The solution to this equation is

$$
E_x(z) = E^+ e^{-\gamma z} + E^- e^{\gamma z}
$$

The positive traveling wave has the propagation factor of the form

$$
e^{\gamma z} = e^{-\alpha z} e^{-j\beta z}
$$
or

$$
e^{-\alpha z}\cos(\omega t - \beta z)
$$

From this equation, we can see that the wave is travelling in the $z$ direction with a phase velocity $v_p = \omega/\beta$, a wavelength of $\lambda = 2\pi/\beta$, and an exponential damping factor. The rate of decay with distance is given by the attenuation constant $\alpha$. The negative wave travelling along the $-z$ axis is similarly damped.

Loss can also be treated through the use of complex permittivity.

The associated magnetic field can be calculated as

$$
H_y = \dfrac{j}{\omega\mu} \dfrac{\partial E_x}{\partial z} = \dfrac{-j\gamma}{\omega\mu}(E^+ e^{-\gamma z} + E^- e^{\gamma z})
$$

^c9e2e3

The intrinsic impedance of the medium is now complex:

$$
\eta = \dfrac{j\omega\mu}{\gamma}
$$

^d51856

but is still identified as the wave impedance. This allows rewriting [[#^c9e2e3]] as

$$
H_y = \dfrac{1}{\eta} (E^+ e^-{\gamma z} - E^- e^{\gamma z})
$$

## Plane Waves in a Good Conductor
A good conductor is a special case the preceding analysis, where the conductive current is much greater than the displacement current. This means $\sigma \gg \omega\epsilon$. It also means that, in terms of a complex $\epsilon$, this condition is equivalent to $\epsilon'' \gg \epsilon'$.

Most metals can be categorized as a good conductor.

$$
\gamma = \alpha + j\beta \approx j\omega \sqrt{\mu\epsilon} \sqrt{\dfrac{\sigma}{j\omega\epsilon}} = (1+j) \sqrt{\dfrac{\omega\mu\sigma}{2}}
$$

^04f7d5

The *skin depth*, or characteristic depth of penetration, is defined as

$$
\delta_s = \dfrac{1}{\alpha} = \sqrt{\dfrac{2}{\omega\mu\sigma}}
$$

Thus the amplitude of the field will decay by an amount of $1/e$, or 36.8%, after travelling a distance of one skin depth. At microwave frequencies, this distance is very small. Thus for low-loss microwave components, only a thin plating of a good conductor (e.g. silver or gold) is necessary.

The intrinsic impedance inside a good conductor can be obtained from [[#^d51856]] and [[#^04f7d5]]: 

$$
\eta = \dfrac{j\omega\mu}{\gamma} \approx (1+j)\sqrt{\dfrac{\omega\mu}{2\sigma}} = (1+j) \dfrac{1}{\sigma\delta_s}
$$

Notice the phase angle of this impedance is 45$\degree$, a characteristic of good conductors. The phase angle of the impedance for lossless material is 0$\degree$. The phase angle of the impedance for arbitrary lossy medium is somewhere between 0$\degree$ and 45$\degree$.
## Summary of Results for Plane Wave Propagation in Various Media

| Quantity                         | Lossless ($\epsilon'' = \sigma = 0$)                       | General Lossy                                                                                             | Good Conductor ($\epsilon'' \gg \epsilon'$ or $\sigma \gg \omega\epsilon'$) |
| -------------------------------- | ---------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **Complex propagation constant** | $\gamma = j\omega\sqrt{\mu\epsilon}$                       | $\gamma = j\omega\sqrt{\mu\epsilon} = j\omega\sqrt{\mu\epsilon'}\sqrt{1-j\frac{\sigma}{\omega\epsilon'}}$ | $\gamma = (1+j)\sqrt{\frac{\omega\mu\sigma}{2}}$                            |
| **Phase constant (wave number)** | $\beta = k = \omega\sqrt{\mu\epsilon}$                     | $\beta = \operatorname{Im}\{\gamma\}$                                                                     | $\beta = \operatorname{Im}\{\gamma\} = \sqrt{\frac{\omega\mu\sigma}{2}}$    |
| **Attenuation constant**         | $\alpha = 0$                                               | $\alpha = \operatorname{Re}\{\gamma\}$                                                                    | $\alpha = \operatorname{Re}\{\gamma\} = \sqrt{\frac{\omega\mu\sigma}{2}}$   |
| **Impedance**                    | $\eta = \sqrt{\frac{\mu}{\epsilon}} = \frac{\omega\mu}{k}$ | $\eta = \frac{j\omega\mu}{\gamma}$                                                                        | $\eta = (1+j)\sqrt{\frac{\omega\mu}{2\sigma}}$                              |
| **Skin depth**                   | $\delta_s = \infty$                                        | $\delta_s = \frac{1}{\alpha}$                                                                             | $\delta_s = \sqrt{\frac{2}{\omega\mu\sigma}}$                               |
| **Wavelength**                   | $\lambda = \frac{2\pi}{\beta}$                             | $\lambda = \frac{2\pi}{\beta}$                                                                            | $\lambda = \frac{2\pi}{\beta}$                                              |
| **Phase velocity**               | $v_p = \frac{\omega}{\beta}$                               | $v_p = \frac{\omega}{\beta}$                                                                              | $v_p = \frac{\omega}{\beta}$                                                |

