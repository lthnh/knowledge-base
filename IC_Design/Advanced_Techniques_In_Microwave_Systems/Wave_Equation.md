## The Helmholtz Equation
In a source-free, isotropic, homogeneous region, Maxwell's curl equations in phasor form are

$$
\begin{align*}
\Delta \times \vec{E} &= -j\omega\mu\vec{H} \\
\Delta \times \vec{H} &= j\omega\epsilon\vec{E}
\end{align*}
$$

^53c086

There are two equations with two unknowns. We can solve it by taking the curl of both equations:

$$
\begin{align*}
\Delta \times \Delta \times \vec{E} &= -j\omega\mu \Delta \times \vec{H} = \omega^2\mu\epsilon\vec{E} \\
\Delta \times \Delta \times \vec{B} &= j\omega\epsilon \Delta \times \vec{E} = \omega^2\mu\epsilon\vec{H}
\end{align*}
$$
Applying vector identity $\Delta \times \Delta \vec{A} = \Delta(\Delta \cdot \vec{A}) - \Delta^2 \vec{A}$ with the fact that this is a source free region ($\Delta \cdot \vec{A} = 0$), we have

$$
\begin{align*}
\Delta^2\vec{E} + \omega^2\mu\epsilon\vec{E} &= 0 \\
\Delta^2\vec{H} + \omega^2\mu\epsilon\vec{H} &= 0 \\
\end{align*}
$$

^a275e0

Note that the vector identity above is valid for rectangular components of an arbitrary vector $\vec{A}$.

These equations [[#^a275e0]] are called the *wave equation* for $\vec{E}$ and $\vec{H}$.

The constant called *propagation constant* of a medium is defined as

$$
k = \omega\sqrt{\mu\epsilon}
$$

with $k$ is also called the *phase constant* or *wave number* with its units are 1/m.
