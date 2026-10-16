The general form of time-varying Maxwell equations written in differential forms:

$$
\begin{align*}
\Delta \times \vec{E} &= -\dfrac{\partial \vec{B}}{\partial t} - \vec{M} \\
\Delta \times \vec{H} &= \dfrac{\partial \vec{D}}{\partial t} + \vec{J} \\
\Delta \cdot \vec{E} &= \rho \\
\Delta \cdot \vec{H} &= 0
\end{align*}
$$

with
- $\vec{E}$ is the electric field (V/m)
- $\vec{H}$ is the magnetic field (A/m)
- $\vec{D}$ is the electric flux density (C/m$^2$)
- $\vec{B}$ is the magnetic flux density (Wb/m$^2$)
- $\vec{M}$ is the fictitious magnetic current density (V/m$^2$)
- $\vec{J}$ is the electric current density (A/m$^2$)
- $\rho$ is the electric charge density (C/m$^3$)

The vector quantities represent time-varying vector fields  and are real functions of $x$, $y$, $z$ and the time variable $t$.

The sources of electromagnetic field are the currents $\vec{M}$ and $\vec{J}$ and the electric density $\rho$. The magnetic current is not real since the real source of *magnetic current* is always a loop of current or some similar type of magnetic dipole, not the actual flow of magnetic charge. Since electric current is the actual flow of charge, it can be said that electric charge density $\rho$ is the ultimate source of electromagnetic field. This claim actually makes sense somewhat as the magnetic field doesn't appear when there isn't any current (with the exception of magnets). The moving of charges is what creates the magnetic field. Magnetic field appears when charged particles move really fast with its electric field.

There are simple relations between field intensities and field densities:

$$
\begin{align*}
\vec{B} &= \mu_0 \vec{H} \\
\vec{D} &= \epsilon_0 \vec{E}
\end{align*}
$$

where
- $\mu_0$ is the permeability of the free space
- $\epsilon_0$ is the permittivity of the free space 

These equations are valid only for free space.

The integral forms of Maxwell equations can be found by applying divergence theorem and Stokes' theorem:

$$
\begin{align*}
\oint_S \vec{D} \cdot \mathrm{d}\vec{s} &= \int_V \rho \mathrm{d}v = Q \\
\oint_S \vec{B} \cdot \mathrm{d}\vec{s} &= 0 \\
\oint_C \vec{E} \cdot \mathrm{d}\vec{l} &= -\dfrac{\partial}{\partial t}\int_S \vec{B} \cdot \mathrm{d}\vec{s} - \int_S \vec{M} \cdot \mathrm{d}\vec{s} \\
\oint_C \vec{H} \cdot \mathrm{d}\vec{l} &= \dfrac{\partial}{\partial t}\int_S \vec{D} \cdot \mathrm{d}\vec{s} + \int_S \vec{J} \cdot \mathrm{d}\vec{s} = \dfrac{\partial}{\partial t}\int_S \vec{D} \cdot \mathrm{d}\vec{s} + \vec{I}
\end{align*}
$$

where $\vec{I} = \int_S \vec{J} \mathrm{d}\vec{s}$ is the total current flow through the surface $S$.

The phasor form of Maxwell equations are:

$$
\begin{align*}
\Delta \times \vec{E} &= -j\omega\vec{B} - \vec{M} \\
\Delta \times \vec{H} &= j\omega\vec{D} + \vec{J} \\
\Delta \cdot \vec{D} &= \rho \\
\Delta \cdot \vec{B} &= 0
\end{align*}
$$

The Fourier transform can be used to convert the solution to Maxwell's equations for an arbitrary frequency $w$ into a solution for arbitrary time dependence.

The electric and magnetic current $\vec{J}$ and $\vec{M}$ are volume current densities. However the actual current will be in the form of a current sheet, a line current, or an infinitesimal dipole current. These special types of current distributions can always be written in the form of volume current densities through the use of delta functions.
