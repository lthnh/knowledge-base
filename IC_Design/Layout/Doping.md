Doping can occur by implanting external atoms
- during wafer fabrication.
- when growing silicon on the wafer (epitaxy).
- from an outside source.
We will consider the last case here.

There are three techniques to do it:
- Alloying
- Diffusion
- Ion implantation
But we will focus on diffusion and ion implantation.
## Diffusion
This technique relies on concentration gradient. The concentration of dopant inside the wafer is much lower than outside $\rightarrow$ dopants diffuse into wafer. For this to happen, the wafer is heated up to 1200 $\degree$C in a diffusion furnace. The dopant is supplied through a carrier gas.

A structured oxide layer is used as a mask for specific diffusion. Dopants cannot pass through oxide. 

As dopant atoms diffuse isotropically, the impurity atoms also move sideways underneath the oxide mask. This is called *outdiffusion*. The result is an edge shift which makes the doped area expand bigger laterally than the corresponding oxide opening. 

Note that as thermal oxidation consumes silicon. It also consumes doped areas too. This is also accompanied by increased step formation at the surface. Ion implantation was developed to overcome these limitations.
## Ion Implantation
Ions are passed through an accelerator with filter to gain high kinetic energy. Then they are used to bombard the wafer areas which are expected to be doped.

The developed photoresist mask is used to selective doping. It is also called *resist masks*.

Channels are formed in the crystal lattice by the regular arrangement of the silicon atoms. If the dopant ions flow exactly between the atomic nuclei in the direction of these channels, they are only slightly slowed down and can penetrate deeper than intended into the substrate along these channels. This is *channeling effect*.

Two ways to prevent this:
- The wafers are inclined by a suitable angle with respect to the ion beam so that ions can't enter the channel.
	- Disadvantage: low asymmetric doping concentration underneath the edge of the photoresist.
- A thin oxide layer is applied to the silicon surface, causing scattering effect $\rightarrow$ ions cannot arrive in parallel streams.

Ion Implantation cause lattice structure on the surface to be slightly damaged by particle bombardment. After removing the photoresist, the wafer must be annealed at 800-1000 $\degree$C. Silicon atoms that are knocked out of the lattice and impurity atoms are embedded again in the lattice through a process so called *tempering*.

> [!info]
> Only at this point the impurity atoms are electrically activated.
>

A diffusion occurs in this process, causing outdiffusion as well. But since this is a very fast process, shift edge only occurs slightly.

> [!info]
> Wafers are exclusively doped by implantation in modern technology nodes.
> The additional costs of implantation are recouped many times over by gains in surface area.

In summary, **ion implantation provides several technological advantages over diffusion-based doping**:
- **Simpler masking:** Photoresist can be used directly, avoiding oxide masks and therefore avoiding **oxide steps** and the loss of the **heavily doped near-surface silicon region**.
- **Higher doping accuracy:** Implantation can control dopant concentration to approximately **±5%**.
- **Less outdiffusion:** Dopants remain closer to their intended profile, except when a later diffusion step is intentionally used to drive them deeper.
- **Less unwanted redistribution of existing dopants:** Because fewer high-temperature diffusion steps are needed, previously implanted impurities undergo less **post-diffusion**.
- **Greater control of doping profiles:** Reduced unwanted diffusion gives process engineers more freedom to independently tailor the **depth and concentration profiles** of different doped regions.
## Reference to Physical Design
### Edge Shifts
- **Diffusion causes edge shifts:** Dopants spread not only downward into silicon but also **laterally**, so the final doped region extends beyond the opening in the doping mask.
- The amount of lateral spreading depends on **diffusion temperature, time, and dopant species**. A typical lateral edge shift is about **70–80% of the diffusion depth**.
- Although edge shifts can theoretically be compensated using **pre-sizing**, this is **generally not done for doping layers**.
- Therefore, a drawn doping layer represents the **doping mask/opening**, **not the actual final doped region**. When creating or reading a layout, you must mentally account for the lateral outdiffusion:
    
    **drawn doping mask → diffusion → wider actual doped region**
    
- As IC dimensions have shrunk, fabrication has increasingly replaced **isotropic processes** that cause significant lateral spreading (such as wet etching and diffusion) with more **anisotropic processes** (such as dry etching and ion implantation), thereby reducing or eliminating edge shifts.

**Key takeaway:** **For diffusion-based doping, the layout shows where doping is introduced, not exactly where the dopant ultimately ends up.**
### Spacing Rules
- **Outdiffusion can require larger design-rule spacing** than would be expected from:
    - the minimum feature size for features on the **same layer**, or
    - the maximum overlay error for features on **different layers**.
- This extra spacing accounts for the fact that the **actual doped regions spread laterally beyond the doping masks**, even though this spreading is not shown in the layout.
- Doped regions may also require additional spacing for **electrical reasons**, particularly to prevent short circuits or withstand high voltages.
- In **smart power processes**, which require much higher voltage tolerance than ordinary logic CMOS, spacing between doped regions is therefore often dictated primarily by **electrical requirements rather than fabrication limitations**.

**Key takeaway:** Large spacing rules around doping layers may exist for two distinct reasons: **to accommodate outdiffusion** or **to satisfy electrical isolation/voltage requirements**.
### Vertical p–n Transitions Produced by Diffusion and Ion Implantation
- **Diffusion and ion implantation produce non-uniform doping profiles.** Dopant concentration generally decreases continuously with increasing depth rather than changing abruptly.
- Cross-sectional diagrams simplify this by showing apparently uniform **p-type and n-type regions**. In reality, each region may contain **both donors and acceptors**. The label indicates which dopant type is the **majority** at that location.
- A **p–n transition** occurs where the majority changes:
    - p-type: acceptor concentration > donor concentration
    - n-type: donor concentration > acceptor concentration
    - p–n boundary: acceptor concentration = donor concentration
	- Thus, the drawn boundary represents the point where the two concentrations become equal, not an abrupt physical change in concentration.
- Successive doping steps create the nested regions inside the original substrate, resulting in **n vertical p–n transitions**.
	- Darker colors and `+` indicate heavier doping, while lighter colors and `−` indicate lighter doping.
- The original **p⁻ substrate concentration is constant with depth** because the wafer was homogeneously doped beforehand.
- **Doping is cumulative and irreversible:** adding a new dopant does not remove the dopants already present. To change an existing region from one conductivity type to the other, it must be **redoped** with the opposite dopant at a sufficiently high concentration to become the new majority.
	- For example: **n-type region + sufficiently strong acceptor doping → p-type region** 
- Reliable redoping requires the new dopant concentration to be **noticeably greater** than the existing opposite dopant concentration. Consequently, regions subjected to repeated redoping tend to become **heavily doped**.

**Key takeaway:** The p/n regions drawn in a cross-section represent **which dopant is dominant**, not regions containing exclusively one dopant. P–n junctions arise where the continuously varying donor and acceptor concentrations cross, and changing conductivity type requires adding enough opposite dopant to **overcompensate** the existing doping.
