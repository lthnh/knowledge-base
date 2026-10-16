When electromagnetic fields exist in material media, the field vectors are related to each other by the constitutive relations.
## Electric Field
For a dielectric material, an applied electric field $\vec{E}$ causes the polarization of the atoms/molecules of the material to create electric dipole moments that augment the total displacement flux $\vec{D}$. This additional polarization vector is called $P_e$, the electric polarization, where

$$
\vec{D} = \epsilon_0 \vec{E} + \vec{P_e}
$$

^d3d634

In the linear medium, electric polarization is linearly related to the applied electric field as

$$
\vec{P_e} = \epsilon_0 \chi_e \vec{E}
$$

^fb4d8f

where $\chi_e$ is *electric susceptibility* (maybe complex).

From [[#^d3d634]] and [[#^fb4d8f]], we have

$$
\vec{D} = \epsilon_0 \vec{E} + \vec{P_e} = \epsilon_0 (1+\chi_e) \vec{E} = \epsilon \vec{E}
$$

where

$$
\epsilon = \epsilon' - j\epsilon'' = \epsilon_0 (1+\chi_e)
$$

is a complex permittivity of the medium.

The imaginary part of $\epsilon$ accounts for loss in the medium (heat) due to damping of the vibrating dipole moments. The loss of a dielectric material may also be considered as an equivalent conductor loss. Free space has real $\epsilon$, which is lossless.

In material with conductivity $\sigma$, a current density exists:

$$
\vec{J} = \sigma \vec{E}
$$

This is *Ohm's Law* from electromagnetic view. Combining with Maxwell's curl equation for $\vec{H}$ we have

$$
\begin{align*}
\Delta \times \vec{H} &= j\omega\vec{D} + \vec{J} \\
&= j\omega\epsilon\vec{E} + \vec{J} \\
&= j\omega\epsilon'\vec{E} + (\omega\epsilon''+ \sigma)\vec{E} \\
&= j\omega\left(\epsilon ' -j\epsilon '' - j \frac{\sigma}{\omega} \right)\vec{E}
\end{align*}
$$

We can see that the loss from dielectric damping is indistinguishable from conductivity loss. The term $we''+\sigma$ can be considered total effective conductivity.

A related quantity is *loss tangent* defined as

$$
\tan \delta = \dfrac{\omega\epsilon''+\sigma}{\omega\epsilon'}
$$

which is the ratio of the real to the imaginary part of the total displacement current.

Microwave materials are usually characterized by specifying the real relative permittivity or the *dielectric constant*, $\epsilon_r$, with $\epsilon' = \epsilon_r \epsilon_0$ and the loss tangent at certain frequencies.

When a problem is solved by assuming real $\epsilon$, loss can be introduced by replacing this $\epsilon$ with a complex $\epsilon = \epsilon' - j\epsilon'' = \epsilon'(1 - j \tan \delta) = \epsilon_0 \epsilon_r (1 - j \tan \delta)$.
### Isotropic and Anisotropic Materials
In isotropic materials, $\vec{P_e}$ is in the same direction as $\vec{E}$. But the story is not the same for anisotropic materials. The relation between $\vec{P}_e$ and $\vec{E}$, or $\vec{D}$ and $\vec{E}$ is much more complicated and is represented by

$$
\begin{bmatrix}
D_x \\
D_y \\
D_z \\
\end{bmatrix}
=
\begin{bmatrix}
\epsilon_{xx} & \epsilon_{xy} & \epsilon_{xz} \\
\epsilon_{yx} & \epsilon_{yy} & \epsilon_{yz} \\
\epsilon_{zx} & \epsilon_{zy} & \epsilon_{zz}
\end{bmatrix}

\begin{bmatrix}
E_x \\
E_y \\
E_z
\end{bmatrix}
=
\begin{bmatrix}
\epsilon
\end{bmatrix}

\begin{bmatrix}
E_x \\
E_y \\
E_z
\end{bmatrix}
$$

^401503

The most general linear relationship between these quantities takes the form of a tensor of rank two (a dyad).[^1] This means a given component of $\vec{E}$ give rises to three components of $\vec{D}$. For linear isotropic material, [[#^401503]] reduces to a diagonal matrix with elements $\epsilon$.
## Magnetic Field
An analogous situation occurs for magnetic materials. An applied magnetic field may align magnetic dipole moments in a magnetic material to produce a *magnetic polarization* or *magnetization* $\vec{P}_m$. This magnetization vector complements the existing field with

$$
\vec{B} = \mu_0 (\vec{H} + \vec{P}_m)
$$

^d919ac

For linear magnetic material, $\vec{P}_m$ is linearly related to $\vec{H}$ as

$$
\vec{P}_m = \chi_m \vec{H}
$$

^869bfc

where $\chi_m$ is the complex *magnetic susceptibility*. Combining [[#^d919ac]] and [[#^869bfc]], we have

$$
\vec{B} = \mu_0(1+\chi_m)\vec{H} = \mu \vec{H}
$$

where $\mu = \mu_0 (1+\chi_m) = \mu' - j\mu''$ is the complex permeability of the medium. As with electric field, the imaginary part of $\chi_m$ or $\mu$ accounts for the loss due to damping forces. There is no magnetic conductivity as there is no magnetic current.
### Isotropic and Anisotropic Materials
Magnetic materials can also be anisotropic. The permeability tensor can be written as

$$
\begin{bmatrix}
B_x \\
B_y \\
B_z
\end{bmatrix}
=
\begin{bmatrix}
\mu_{xx} & \mu_{xy} & \mu_{xz} \\
\mu_{yx} & \mu_{yy} & \mu_{yx} \\
\mu_{zx} & \mu_{zy} & \mu_{zz}
\end{bmatrix}

\begin{bmatrix}
H_x \\
H_y \\
H_z
\end{bmatrix}
=
\begin{bmatrix}
\mu
\end{bmatrix}

\begin{bmatrix}
H_x \\
H_y \\
H_z
\end{bmatrix}
$$

An important example of anisotropic magnetic materials in microwave engineering are *ferrites*.

If linear media is assumed ($\epsilon$, $\mu$ not depending on $\vec{E}$ or $\vec{H}$), then Maxwell's equations can be written as

$$
\begin{align*}
\Delta \times \vec{E} &= -j\omega\mu\vec{H} - \vec{M} \\
\Delta \times \vec{H} &= j\omega\epsilon\vec{E} + \vec{J} \\
\Delta \cdot \vec{D} &= \rho \\
\Delta \cdot \vec{B} &= 0
\end{align*}
$$

The constitutive relations are

$$
\begin{align*}
\vec{D} &= \epsilon\vec{E} \\
\vec{B} &= \mu\vec{H}
\end{align*}
$$

where $\epsilon$ and $\mu$ maybe complex and maybe tensors.

These relations generally can not be written in time domain form, even in linear media, because only the phasor representation can account for possible phase shifts between $\vec{D}$ and $\vec{E}$, or $\vec{B}$ and $\vec{H}$.

[^1]: Rank two means it only has maximum two independent rows and columns.
