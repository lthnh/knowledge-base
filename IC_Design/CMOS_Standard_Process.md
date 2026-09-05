## Process Options
CMOS requires both **p-type and n-type bulk/backgate regions** so that NMOS and PMOS transistors can be fabricated. Starting from a p-doped substrate, these regions can be produced using several well structures.

|Process|Structure|Main characteristic|
|---|---|---|
|**Single-well**|NMOS uses the original p-substrate; PMOS is placed in a fabricated n-well|Simple, but threshold voltages are naturally asymmetric|
|**Twin-well**|NMOS is placed in a p-well and PMOS in an n-well|Independent optimization of both transistor bulk doping|
|**Triple-well**|One well is formed inside another well|Provides additional electrical isolation and independent body potentials|

**Single-well process:** With a p-doped starting wafer, the NMOS can use the original p-substrate directly, while an **n-well must be created for the PMOS** by redoping part of the substrate. Because a redoped region must have a sufficiently high dopant concentration to overcome the original doping, the n-well ends up more heavily doped than the original p-substrate. Consequently, the NMOS and PMOS naturally have different threshold-voltage magnitudes, with the PMOS having the higher threshold in the example.

A **threshold-adjust implantation** can compensate for this mismatch by implanting acceptors into a thin surface layer across the wafer until the NMOS and PMOS threshold voltages are approximately symmetrical. A disadvantage is that the additional dopant atoms reduce hole mobility in the PMOS.

**Twin-well process:** A better approach is to start with a **weakly doped substrate** and deliberately fabricate both a **p-well for NMOS** and an **n-well for PMOS**. Their doping concentrations can therefore be independently selected to obtain the desired transistor characteristics. This extra flexibility makes twin-well processes widely used, despite requiring an additional mask.

**Triple-well process:** One transistor's well is placed **inside another oppositely doped well**, creating a _well-in-a-well_. For example, with the p-substrate shown:
**p-substrate → deep n-well → p-well → NMOS**

while the PMOS remains in a separate n-well. This arrangement creates isolating p–n junctions between the transistor backgates and the original substrate. When these junctions are reverse-biased, the **NMOS and PMOS backgate/body potentials can be controlled more independently**. This extra degree of freedom is particularly useful in applications such as high-voltage electronics.

The progression can therefore be remembered as:

**Single-well → simplest, but limited doping control**  
**Twin-well → independent doping optimization**  
**Triple-well → independent doping + greater body-potential/isolation flexibility**