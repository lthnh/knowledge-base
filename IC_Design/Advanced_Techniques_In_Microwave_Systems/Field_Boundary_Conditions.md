## Fields at a General Material Interface
Consider a plane interface between two media, Maxwell's equations integral form can be used to find the conditions involving the normal and tangential fields at this surface.

From the diagram above, we have

$$
\oint_S \vec{D} \cdot \mathrm{d}s = \int_V \rho \mathrm{d}v
$$

^82eb55

In the limit as $h \rightarrow 0$, the contribution of $D_{\mathrm{tan}}$ through the sidewalls goes to zero, so [[#^82eb55]] reduces to

$$
\Delta S D_{2n} - \Delta S D_{1n} = \Delta S p_s
$$

or

$$
D_{2n} - D_{1n} = \rho_s
$$

where $p_s$ is the surface charge density on the interface. In vector form,

$$
\hat{n} \cdot (\vec{D}_2-\vec{D}_1) = \rho_s
$$

^ba9723

Applying similar argument for $\vec{B}$, we have

$$
\hat{n} \cdot \vec{B}_2 = \hat{n} \cdot \vec{B}_1
$$

^1976f3

because there is no free magnetic charge.

![[closed-contour-c.png]]

For the tangential components of the electric field, we use the phasor form of

$$
\oint_C \vec{E} \cdot \mathrm{d}\vec{l} = -j \omega \int_S \vec{B} \cdot \mathrm{d} \vec{s} - \int_S \vec{M} \cdot \mathrm{d}\vec{s}
$$

^4a23e2

As $h \rightarrow 0$, the surface integral for $\vec{B}$ vanishes because $S = h \Delta l$ vanishes. The contribution from the surface integral of $\vec{M}$ may be nonzero if a magnetic surface current density $\vec{M}_s$ exists on the surface. The Dirac delta function can then be used:

$$
\vec{M} = \vec{M}_s \delta(h)
$$

where $h$ is the coordinate measured normal from the interface. [[#^4a23e2]] becomes

$$
\Delta l E_{t1} - \Delta l E_{t2} = -\Delta l M_s
$$

or

$$
E_{t1} - E_{t2} = -M_s
$$

which can be generalized in vector form as

$$
(\vec{E}_2 - \vec{E}_1) \times \hat{n} = \vec{M}_s
$$

^659531

Applying similar argument for magnetic field results in

$$
\hat{n} \times (\vec{H}_2 - \vec{H}_1) = \vec{J}_s
$$

^428eef

where $\vec{J}_s$ is an electric surface current density that may exist at the interface.

These equations [[#^ba9723]], [[#^1976f3]], [[#^659531]], and [[#^428eef]] are the most general expressions for the boundary conditions at an arbitrary interface of materials and/or surface currents.
## Fields at a Dielectric Interface
At an interface between two lossless dielectric materials, no charge or surface current densities will ordinarily exist. Four equations [[#^ba9723]], [[#^1976f3]], [[#^659531]], and [[#^428eef]] reduce to

$$
\begin{align*}
\hat{n} \cdot \vec{D}_1 &= \hat{n} \cdot \vec{D}_2 \\
\hat{n} \cdot \vec{B}_1 &= \hat{n} \cdot \vec{B}_2 \\
\hat{n} \times \vec{E}_1 &= \hat{n} \times \vec{E}_2 \\
\hat{n} \times \vec{H}_1 &= \hat{n} \times \vec{H}_2
\end{align*}
$$

^286ca1

The equations above state that the normal components of $\vec{D}$ and $\vec{B}$ are continuous across the interface, and the tangential components of $\vec{E}$ and $\vec{H}$ are continuous across the interface.

Since Maxwell's equations are not all linearly independent, the boundary conditions are not all independent either. The satisfaction of four tangential components from the last two equations in [[#^286ca1]] will force satisfaction of equations for continuity of the normal components.
## Fields at the Interface with a Perfect Conductor (Electric Wall)
Many problems in microwave engineering involving boundaries with good conductors (e.g. metals), which is often assumed to be lossless $\sigma \rightarrow \inf$.

In the case of perfect conductor, all field components *must be zero* inside the conducting region. This can be seen by considering conductor with finite conductivity ($\sigma < \inf$) and noting that the skin depth[^1] goes to zero as $\sigma \rightarrow \inf$. If we also assume $\vec{M}_s$ =  0 (would only happened if the perfect conductor filled all the space on one side of the boundary), [[#^286ca1]] will reduce to

$$
\begin{align*}
\hat{n} \cdot \vec{D} &= \rho_s \\
\hat{n} \cdot \vec{B} &= 0 \\
\hat{n} \times \vec{E} &= 0 \\
\hat{n} \times \vec{H} &= \vec{J}_s
\end{align*}
$$

where $\rho_s$ and $\vec{J}_s$ are the electric surface charge density and current density, respectively, on the interface, and $\hat{n}$ is the normal unit vector pointing out of the perfect conductor. This boundary is known as *electric wall* because the tangential components of $\vec{E}$ are shorted out and must vanish at the surface of the conductor.

Electric wall boundary condition is analogous to the voltage and current at the end of a short-circuited transmission line.
## The Magnetic Wall Boundary Condition
Dual to above boundary condition is the *magnetic wall*, where the tangential components of $\vec{H}$ must vanish.

This problem doesn't really exist in practice but maybe approximated by a corrugated surface or in certain planar transmission line problems.

$\hat{n} \times \vec{H} = 0$ at the interface is a convenient simplification.

Magnetic wall boundary condition is analogous to the relations between the voltage and current at the end of an open-circuited transmission line. Thus is useful in several cases of practical interest.

The fields at the magnetic wall satisfy the following conditions:

$$
\begin{align*}
\hat{n} \cdot \vec{D} &= 0 \\
\hat{n} \cdot \vec{B} &= 0 \\
\hat{n} \times \vec{E} &= -\vec{M}_s \\
\hat{n} \times \vec{H} &= 0
\end{align*}
$$

where $\hat{n}$ is the normal vector pointing out of the magnetic wall region.
## The Radiation Condition
In problems with one or more infinite boundaries, e.g. plan waves in an infinite medium, infinitely long transmission lines, a condition on the fields at infinity must be enforced and is called *radiation condition*. This is a result of energy conservation. It states that, at an infinite distance from the source, the fields must either be vanishingly small (i.e. zero) or propagating in an outward direction.

Incoming waves (from infinity) of finite amplitude would then require an infinite source at infinity and so are disallowed.

[^1]: The depth to which most of the microwave power penetrates.
