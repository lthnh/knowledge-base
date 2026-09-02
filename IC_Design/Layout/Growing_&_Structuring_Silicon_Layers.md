The process of growing silicon on the wafer is called *epitaxy*. Two types of epitaxy:
- Homoepitaxy
- Heteroepitaxy
## Homoepitaxy
### Layer Growth
New silicon atoms which are deposited on the monocrystalline silicon surface adopt the atomic structure of the silicon in the substrate. The existing silicon structure thus *propagates* to the new silicon layer. This is *homoepitaxy*.

This new layer can be doped with different dopent/concentration than the base layer.

> [!info]
> Clearly defined abrupt vertical p-n transitions that extend across the entire wafer can be created.
> Buried doped areas, or *buried layers*, can be created too by seletively doping the base layer surface before the epitaxial step.

### Structuring
Devices on wafer need to be electrically separated to ensure correct operation. As device miniaturization progresses, the relative space requirements increase and become a roadblock for increasing integration density.

*Trench isolation* methods were developed to deal with this problem.

**Trench isolation** uses deep, narrow trenches etched into silicon, typically by **reactive ion etching (RIE)**. Photoresist defines where the trenches are etched, while **etch time controls their depth** because there is no separate etch-stop material.

Two kinds of trenches:
- **Shallow Trench Isolation (STI):** The trench is completely filled with **oxide**. This can be done by:
    - thermal oxidation alone, or
    - brief thermal oxidation followed by **oxide deposition**, which consumes less silicon.
- **Deep Trench Isolation (DTI):** Only the trench walls need enough **oxide for electrical insulation**. The remaining space is often filled with **polysilicon**, whose thermal expansion is similar to monocrystalline silicon, reducing mechanical stress during temperature changes.

After filling, unwanted material remaining above the wafer surface is removed using **chemical-mechanical polishing (CMP)**. CMP simultaneously removes excess material and **planarizes (flattens) the wafer surface**.

**Limitation:** STI and DTI provide primarily **lateral/sideways isolation**. For complete dielectric isolation, the device must also be insulated from the silicon underneath.

**SOI (Silicon-on-Insulator)** solves this by providing a **buried oxide layer** beneath the device region, allowing the device to be surrounded by insulating material.

The key distinction to remember is:
- **STI/DTI → primarily sideways isolation**  
- **SOI → can provide complete dielectric isolation, including underneath the device**.
## Heteroepitaxy and Polysilicon
### Layer Growth
- **Heteroepitaxy** occurs when the deposited material differs structurally/materially from the substrate.
- When **silicon is deposited on amorphous oxide**, there is no crystal lattice to guide its orientation.
- Consequently, many small silicon crystals form independently with different orientations. As they grow, they create **polycrystalline silicon (polysilicon/poly)**, consisting of many small **grains** separated by **grain boundaries**.
- These grain boundaries can cause **leakage currents**, so polysilicon is generally unsuitable for forming useful **p–n junctions**.
- Despite this, polysilicon conducts current and is useful for structures such as **MOSFET gates, resistors, and capacitor electrodes**.

**Key idea:**  
**Silicon deposited on amorphous oxide → random crystal orientations → many grains → polysilicon.**
### Structuring
- **Polysilicon is patterned** into useful structures using **photolithography followed by etching**.
- Modern processes use **anisotropic reactive ion etching (RIE)** because it can create **precise, fine polysilicon features**.
- Polysilicon structures are fabricated **before the metal interconnect layers** and are insulated from them by oxide.
- The polysilicon layer can be deposited over:
    - **Thick field oxide (STI oxide)**, which isolates regions.
    - **Very thin gate oxide (GOX)**, which acts as a dielectric in **MOSFETs and capacitors**.
- After deposition, the polysilicon is patterned using a **photolithographically defined mask**, and unwanted polysilicon is removed by anisotropic RIE.

So the basic sequence is:
**Grow/form oxide → deposit polysilicon → photolithography → anisotropic RIE → patterned polysilicon structures.**
## Reference to Physical Design
- If polysilicon is located above the field oxide it can as well be used as an interconnect.
- Attention must be paid since polysilicon has higher ohmic resistance than metal interconnect of the same dimensions, about three orders of magnitude higher.
	- Use polysilicon as interconnect should only be considered in exceptional cases.
	- For example, connecting a device to a nearby contact.
	- Use as interconnect between devices is only recommended for very small currents and short distances.

> [!warning]
> Keep close eye on the voltage drop caused when routing with polysilicon.

