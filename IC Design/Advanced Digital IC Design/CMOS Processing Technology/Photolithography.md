Regions of dopants, polysilicon, metal and contacts are defined using masks. Photolithogrpahy means "carving pictures in stone using light". The primary method to determine which area to keep or to carve is by the use of photoresists. The wafer is coated with photoresists and subjected to selective illumination through the use of *photomasks*. Normally, the area illuminated by the light gets hardened while other areas don't. A developer solvent is used to remove the unexposed photoresist. This is termed *negative* photoresist. There is also *positive* photoresist, which has higher resolution but is less sensitive to light $\rightarrow$ increase failure rate when feature gets smaller.

![[photo-masking-w-negative-photoresist.png]]

The wavelength of the light source and *numerical aperture* NA determines the minimum *pitch*, defined as 2b, also known as the resolution of the lens.

$$
2b=k_1\dfrac{\lambda}{\mathrm{NA}}
$$

And the numeral aperture is

$$\mathrm{NA}=n\sin{\alpha}$$

where
- $n$ is the refractive index of the medium.
- $\alpha$ is the acceptance angle of the lens.

The depth of focus is

$$\mathrm{DOF}=\dfrac{k_2\lambda}{\mathrm{NA}^2}$$

Advanced lithography systems with short wavelengths and large numerical apertures have extremely sallow DOF $\rightarrow$ the surface of the wafer must be extremity shot.

Wavelengths $\geq$ feature size can distort patterns on photoresist. *Resolution enhancement techniques* (RET) precompensate for this distortion. These techniques involve modifying the amplitude, phase, or direction of the incoming light.

*Optical proximity correction* (OPC) makes small changes to the patterns on the masks to compensate for local distortions like the ends of a line receive less light than the center causing nonuniform exposure.

*Phase shift masks* (PSM) take advantage of the diffraction grating effect of parallel lines on a mask, varying the thickness of the mask to change the phase such that light from adjacent lines are out of phase and cancel where no light is desired.

*Off-axis illumination* can improve contrast for certain types of dense, repetitive patterns.

*Double-patterning* is a sequence of two precisely aligned exposure steps with different masks for the same photoresist layer.

