---
id: Applying_&_Structuring_Errors
aliases: []
tags: []
---
## Silicon Dioxide
Silicon dioxide ($SiO_2$) has the following properties:
- Mechanically stable $\rightarrow$ suitable for layer structure
- Excellent electrical insulator
- Easy to make
- Serves as masking layer for many process steps
- Transparent: allows alignment features to be detected beneath the oxide
## Thermal Oxidation
Thermal oxidation is used to form oxide on the wafer surface. Once the oxide layer is formed, it can only grow when the oxygen atoms diffuse to the lower silicon surface and reach this silicon layer.

The oxide grows from the original silicon surface by ~44% into the silicon and ~56% outwards.
### Dry Oxidation
Wafers are heated in oxidation furnace and exposed to pure oxygen at 1000-1200 $\degree$C. The reaction is

$$
Si + O_2 \rightarrow SiO_2
$$

This produces very good quality oxide with few vacancy defects $rightarrow$ used to very thin gate oxides in FET and dielectrics in capacitors.
### Wet Oxidation
Oxygen first flows through boiling water. The wafer is exposed to steam as well. The reaction is

$$
Si + 2H_2O \rightarrow SiO_2 + 2H_2
$$

at 950-1000 $\degree$C. This reaction is much faster than dry oxidation but it's harder to control and produce lower quality dielectric. Because of this, it's widely used to produced field oxide.
## Oxidation by Deposition
If the silicon layer is covered by other layers, the oxide for additional oxide layer must be deposited. Silicon must be added from outside as well as the oxygen.
## Oxide Structuring by Etching
Material is removed selectively via chemical means. Two types: wet etching and dry etching.
### Wet Etching
Oxide is dissolved and removed by a fluid chemical etching agent. This etching agent acts isotropic (i.e. in all directions) causing unwarranted etching underneath the photoresist.

This create *undercuts*, meaning the oxide openings are always bigger than photoresist openings. The undercuts have slightly lower etching rate than vertical etching due to etching agent can't circulate properly under the photoresist. Typical value is 80% of etching depth.

> [!info]
> Wet etching is not appropriate anymore for imaging typical feature sizes in advanced processes, due to undercutting effect.
> Hence, wet etching is only used in these processes for dissolving and removing entire layers.

### Dry Etching
*Reactive ion etching (RIE)* is a technique where the etching agent is ionized and applied as plasma gas. The ions are set in oscillatory motion via an alternating electric field. This field is normal aligned to the silicon surface. The chemically active ions oscillate in this direction and etch away material veritically only.

The etching effects in this technique is a combination of two process:
- Bombard the material to be etched in a specific direction
- Chemical effect through active ions

Main advantage is no edge shift. Very fine structures can be created with RIE.
### Oxide Steps:
When growing oxide on silicon surface, the oxide grows both ways: into the silicon and out of the silicon. This means the oxidation also "eats" into the silicon. So when a silicon surface is oxidized, etched then oxidized again. Now the oxide surface will have "oxide steps" because the oxide grows at different rate on the oxide surface when compared to the silicon surface.
## Local Oxidation
Making use of silicon nitride ($Si_3Ni_4). This type of oxide acts as an insulating layer prevent silicon dioxide grow in certain regions. Hence it is call local oxidation of silicon (or LOCOS).

Silicon nitride adheres badly to silicon, so a thin layer of silicon dioxide must be put in between silicon nitride and silicon.

In standard LOCOS:
- Silicon nitride mask protects regions where oxidation is not wanted.
- The exposed silicon undergoes thermal oxidation, forming field oxide.
- Because oxidation also proceeds laterally, oxide grows underneath the edge of the nitride and lifts it, producing the tapered “bird’s beak.”
- After removing the nitride, the tapered boundary means the oxide step is only about half as high as it would be if an oxide layer were simply deposited/grown and then patterned by etching.

To reduce or eliminate even this remaining step, an extended LOCOS process lowers the silicon surface before the final oxidation. Since growing SiO₂ consumes silicon but also expands above the original silicon surface, the silicon is lowered by about 56% of the desired final oxide thickness. After oxidation, the oxide surface therefore returns approximately to the original silicon surface level.

There are two ways to create this initial depression:
- Etch the silicon directly, using nitride as the mask.
- Use two oxidation cycles: perform a first local oxidation to consume enough silicon, completely remove that first oxide by etching, leaving the silicon surface recessed, and then perform a second oxidation to grow the actual field oxide.

Advantages of this approach:
- No silicon is consumed inside the oxide openings [^1]
- Oxide step is only about half as high as one produced by thermal oxidation
- The oxide step is inclined and not steep $\rightarrow$ layers protruding over the edge of the field oxide (polysilicon, metal) cover the edge better
- The height of oxide can be reduced via LOCOS extensions $\rightarrow$ produce almost flat surface.
## Reference to Physical Design
### Edge Shifts
Field oxide is structured with wet etching $\rightarrow$ undercuts occur $\rightarrow$ oxide openings are bigger than on the masking structure.

Field oxide is structured with local oxidation $\rightarrow$ bird's peaks occur $\rightarrow$ oxide openings are smaller than on the masking structure.

Both of these effects are deterministic, meaning they can be compensated pre-emptively. Practices to deal with this issues depend on semiconductor process. Search documentation for PDK on this issue to further guidance.

Through contacts are exclusively dry etched in processes nowadays $\rightarrow$ no edge shifts.
### Oxide Steps with Through Contacts
Etching contact openings through the oxide inherently creates oxide steps. These steps make it harder to deposit metal with good coverage inside the openings and ensure reliable electrical contact with the underlying silicon.

[^1]: Growing silicon dioxide always consumes silicon. This sentence refers to the fact that since nitride silicon layer is deposited on the wafer, there is no silicon lost during that mask creation process.
