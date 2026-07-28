The gate capacitor can be viewed as a parallel plate capacitor: the gate on top and the channel at the bottom with a thin oxide dielectric between.

$$
C_g=C_{ox}WL
$$

The bottom plate of this capacitor is the channel. When the transistor is ON, the channel extends from the source (to the drain in unsaturated transistor, stops short in saturated transistor).
$\Rightarrow$ We approximate it as terminating at the source and call it $C_{gs}$.

Source and drain contribute parasitic capacitances which will impact circuit performance. These capacitances arise from p-n junctions with the body and are called diffusion capacitances $C_{sb}$ and $C_{db}$.

Recall the p-n junction circuit analysis from [[pn Junction (Open-Circuit)]], we can see that depletion regions are form at these junctions due to diffusion current and drift current. These depletion regions act as insulators between p- and n-type regions, creating capacitance across these junctions.

These capacitances depend on the area and perimeter of the source and drain, the depth of the diffusion, the doping levels, and the voltage.

>[!note]
>As diffusion regions has both high capacitance and high resistance. It is generally made as small as possible in the layout.

Three types of diffusion region are usually seen. See the graph below.

![[three-types-of-diffusion.png|400]]

For hand calculations, the diffusion capacitance $C_{sb}$ and $C_{db}$ of contacted source or drain is comparable to the gate capacitance. The diffusion capacitance of the uncontacted source or drain is somewhat less because the area is smaller, but usually unimportant for hand calculations.