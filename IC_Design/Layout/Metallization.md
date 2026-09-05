## Fundamentals
- **FEOL (Front-End-of-Line):** The fabrication stage where individual devices such as **transistors, capacitors, and resistors** are formed.
- **BEOL (Back-End-of-Line):** The subsequent stage where those devices are **electrically interconnected according to the circuit nets**.
- BEOL is constructed by alternately stacking:
    - **Oxide layers** → electrical insulation.
    - **Metal layers** → interconnect wiring.
    - **Through contacts/vias** → vertical connections between layers.
- For each metallization level, layout generally needs **two types of layers**:
    1. A layer defining the **through contacts/vias** in the oxide.
    2. A layer defining the **metal interconnect tracks** above that oxide.
- Designing these interconnect structures is called **routing**.

In short:
**FEOL = fabricate the devices → BEOL = wire the devices together → routing = layout design of those connections.**
### Routing Layers
Modern ICs require **many metallization layers** to route their large number of nets.
- **BEOL layer names are relatively standardized**, unlike FEOL layer names, which vary significantly between processes and manufacturers.
- Metal layers are numbered **from bottom to top in fabrication order**:  
    **Metal1 → Metal2 → Metal3 → ...**
- Vertical connections have two different names:
    - **Contact** → connects the **silicon/device level to Metal1**.
    - **Via[n]** → connects **Metal[n] to Metal[n+1]**.
- Therefore, each routing level is associated with a pair of layout layers:
    - **Contact + Metal1**
    - **Via1 + Metal2**
    - **Via2 + Metal3**
    - and so on.

A useful mental picture is:

Metal3
  │
 Via2
  │
Metal2
  │
 Via1
  │
Metal1
  │
Contact
  │
Silicon / devices

So the key distinction is: **contacts connect Metal1 to the devices; vias connect one metal layer to another.**
### Materials
A good metallization material must be **easy to fabricate**, adhere well to oxide, and provide high conductivity, high current capacity, reliable contacts, corrosion/mechanical resistance, and support for multilayer routing.
#### Aluminum
**Aluminum (Al)** was historically the preferred interconnect material because it satisfies these requirements well. Alloys such as **AlSiCu** improve some of its properties.

However, as feature sizes shrink:
- Interconnect cross-sectional area decreases.
- Aluminum's **parasitic resistance becomes increasingly problematic**.
- **Electromigration** limits the current density that small aluminum wires can reliably carry.
#### Copper
Modern processes increasingly replaced aluminum with **copper (Cu)** because:
- Copper has roughly **half the specific resistance** of pure aluminum.
- It suffers **less electromigration**, allowing higher current densities.
- Consequently, copper interconnects can have **smaller cross-sections**.
- Smaller interconnects also reduce **parasitic capacitance per unit length**, reducing crosstalk.
- Lower resistance and capacitance reduce the interconnect **RC delay**, enabling faster circuits.

So, in simplified form:
**Cu → lower R + smaller wires → lower C → lower RC delay + less crosstalk**

Copper nevertheless introduces substantial fabrication difficulties:
- It **diffuses readily into surrounding oxide**, causing contamination.
- It **corrodes easily**.
- Therefore, protective/barrier coatings are required.
- Copper is **difficult to dry etch**, requiring different structuring techniques.
- Consequently, copper metallization is **more complex and expensive to fabricate** than aluminum.

The transition from aluminum to copper occurred roughly across the **350 nm to 90 nm technology nodes**, so both materials can be found in this range. Some smart-power processes even combine them: **thin aluminum layers for ordinary routing and a thick top copper layer for very high-current interconnects**.

There are two broad metallization approaches: **with intermediate planarization** and **without intermediate planarization**.
## Metallization Structures Without Planarization
Older processes, particularly from the aluminum era, often omitted planarization. Modern submicron processes require planarization because otherwise surface unevenness accumulates from layer to layer.

For the older **non-planarized aluminum process**, each metal level is fabricated using four basic steps:
1. Deposit an **insulating oxide**.
2. Etch **contacts/vias** through the oxide.
3. Deposit **aluminum** over the surface and into the openings.
4. Selectively etch the aluminum to form the **interconnects**.

This sequence is repeated for each additional metal layer.
### Main problem: increasing surface topography
Because there is **no planarization**, every etched oxide and metal feature creates steps. As more layers are added, these steps accumulate:
**Device structures → Oxide → Metal 1 → Oxide → Metal 2 → ...**

This creates problems with **step coverage**. Aluminum deposited mainly from above may not adequately coat the vertical or steep sidewalls of contact/via holes. A thin metal region at the edge of a via becomes an electrical weak point and can eventually cause an open circuit.

The problem becomes particularly severe with **stacked vias**—vias placed directly above each other. Without planarization, the underlying topography adds together, producing an increasingly large step that the next metal layer must cover. Consequently, stacked vias were often prohibited in these processes.
### Methods used to improve contact reliability
Several techniques were developed:
- **Beveled via edges:** Sloped rather than vertical sidewalls improve metal coverage, but consume more area and therefore conflict with miniaturization.
- **Sputtering instead of vapor deposition:** Improves deposition on vertical surfaces, but filling increasingly small contact/via holes remains difficult.
- **Tungsten plugs:** Contact holes are first filled with tungsten using **CVD (chemical vapor deposition)**. Excess tungsten is removed, leaving a tungsten plug inside the opening. Aluminum is then deposited over the plugs to form the interconnects.

The tungsten-plug approach effectively separates the problems of **filling the contact hole** and **forming the aluminum interconnect**, producing more reliable contacts while allowing aluminum wiring to be finely patterned using dry etching.

The core idea is:

> **Without planarization, topographical steps accumulate with every metal layer, making reliable metal coverage of contacts/vias increasingly difficult. Tungsten plugs and improved deposition techniques were developed to mitigate this problem.**
## Metallization Structures with Planarization
### Additive Processes
Additive processes **reduce surface steps by adding material into recessed areas**, improving the surface for later metallization.
- **Reflow technology:** Uses doped glass that softens/liquefies at high temperature and flows preferentially into recesses. It is suitable mainly for smoothing **polysilicon structures**, because the required temperature is too high for aluminum.
- **Spin-on glass (SOG):** A silicon-oxide-containing solution applied at room temperature and hardened below aluminum’s melting temperature, allowing it to smooth **aluminum features**.
- **Limitation:** Because these glass materials have relatively **high viscosity**, they mainly smooth **local surface irregularities**. They reduce step-coverage problems but **cannot produce complete planarization**.

**In short:**  
**Reflow → smooths poly; SOG → smooths aluminum; both reduce steps but do not fully eliminate surface topography.**
### The Damascene Process with CMP
**Chemical-mechanical polishing (CMP)** is a **subtractive planarization process** used to eliminate surface steps across the entire wafer.
- It combines **chemical etching** with **mechanical polishing**.
- The wafer is pressed against a rotating polishing surface supplied continuously with **etching chemicals and polishing material**.
- Raised regions are preferentially removed until the wafer surface becomes **flat and planar**.
- CMP can also be used to **partially or completely remove specific material layers**.

**Key idea:** Unlike additive smoothing methods such as SOG, CMP can achieve **wafer-wide planarization**, rather than merely reducing local surface irregularities.
#### Damascene technique
The **Damascene process** is a BEOL technique particularly suited to **copper interconnects**. Unlike conventional subtractive metallization, where metal is deposited everywhere and then selectively etched, Damascene **first creates recesses in an insulating layer and then fills those recesses with metal**.

This is necessary because CMP would remove conventional metal interconnects protruding above the wafer surface. With Damascene, the desired metal is **embedded inside the insulator**, so CMP removes only the excess metal above the surface.

The basic sequence is:
1. **Etch holes/trenches into the insulating layer** for vias/contacts or interconnects.
2. Deposit a conductive **barrier/liner** such as Ta, TaN, or TiN to prevent copper diffusion and oxidation.
3. For electrochemical copper deposition, deposit a thin **copper seed layer**.
4. Deposit copper, completely filling the holes or trenches.
5. Use **CMP to remove excess copper** from the surface, leaving copper only inside the recesses.
6. Deposit a **protective dielectric barrier** over the copper.

For a complete **metallization layer pair**, this sequence is performed **twice**:
**Via/contact formation → CMP → interconnect formation → CMP**

The key distinction from conventional metallization is therefore:

> **Conventional:** deposit metal → pattern/etch metal  
> **Damascene:** pattern/etch insulator → fill with metal → CMP excess metal

Damascene is especially useful for **copper because copper is largely unsuitable for dry etching**. It also allows the insulating material to be a **low-k dielectric** rather than ordinary $SiO_2$, reducing parasitic coupling capacitance between nearby interconnects.

For copper metallization, **vias can also be copper**. However, according to the excerpt, at the first metallization level where copper would contact silicon, **tungsten separates the copper from the silicon**.

**Key idea:** Damascene essentially reverses the conventional approach—the **empty space for the wire is fabricated first, then copper is put into that space**, and CMP makes the surface flat again.
#### Dual-Damascene process flow
The **dual-Damascene process** is an improved Damascene technique used for copper BEOL metallization. Its main advantage is that the **metal interconnect trench and its associated via are formed and filled with copper together**, so only **one copper deposition and one CMP step** are needed.

Different variations are in used. One possible sequence is as follows:
1. **Deposit the first oxide layer** — this insulating layer will ultimately contain the **via**.
2. **Deposit a nitride layer** — the nitride acts as an intermediate mask/etch-control layer.
3. **Pattern the nitride using the via mask** — openings in the nitride mark where the vias will eventually be formed.
4. **Deposit the second oxide layer** — this layer will contain the **new metal interconnect trenches**.
5. **Etch using the metal mask** — trenches are etched into the upper oxide. At locations where the previously patterned nitride has openings, etching can continue downward, beginning formation of the **via holes**.
6. **Etch the remaining nitride** — this completes the combined **trench + via-hole structure**.
7. **Deposit a diffusion barrier and copper seed layer** — the barrier prevents copper diffusion into surrounding materials; the seed facilitates subsequent copper deposition.
8. **Deposit copper** — copper fills **both the trenches and via holes simultaneously**.
9. **CMP** removes excess copper from the surface and planarizes it. Copper remains only inside the trenches and vias.
10. **Deposit a nitride cap** — this protects the copper against **diffusion and oxidation**.

So the essential idea is:
**pattern via locations → create trenches + via holes → fill both with Cu at once → CMP**

The resulting structure simultaneously provides the **horizontal metal routing** and the **vertical vias connecting it to the previous metal layer**.
## Reference to Physical Design
### Spacing Rules for Interconnect Layouts without Planarization Technology
In **non-planarized metallization processes**, stacking vias directly on top of each other is generally prohibited because it creates **steep surface steps**, making reliable metal coverage difficult.

As a result:
- **Via stacks are forbidden**, so vias on different metal levels must be laterally offset.
- Design rules specify not only **same-layer via spacing**, but also **spacing between vias on different layers**, making routing more complicated.
- With each additional metal layer, the wafer surface becomes **increasingly uneven**.
- This unevenness reduces **photolithography image sharpness/focus** on upper layers.
- Therefore, **higher metal layers require larger minimum widths and spacings** to maintain reliable fabrication.

**Core idea:** Poor planarization → increasing surface topography → harder metal coverage and lithography → stricter via placement and larger geometry rules on upper layers.
### Density Rules
The **Damascene technique** provides excellent surface planarity, allowing many finely patterned metal layers to be fabricated. This makes routing easier and supports automated routing in complex digital ICs.

Its main layout drawback comes from **CMP (Chemical Mechanical Planarization)**. CMP removes different materials at different rates, so an uneven distribution of materials such as metal and oxide can cause surface defects such as **indentations or hillocks**.

To prevent this, **density rules** require the amount of each material within a given area to remain within specified density limits. Meeting these rules can require:
- **Too little material:** add electrically inactive **dummy/fill structures**.
- **Too much material:** introduce **slots** in wide interconnects or increase spacing between structures, potentially increasing layout area.

Because fixing density violations late in physical design can be costly, **density rules should be considered early**, even though complete density verification can only be performed near the end. Efficiently satisfying them often requires substantial layout experience.

**Key idea:**  
**Damascene → excellent planarity and multilayer routing, but CMP → density-dependent surface variation → density rules → metal fill/slotting and careful early layout planning.**
### Current Carrying Capacity
Metal interconnects, contacts, and vias must be sized to **carry their required current reliably for the entire chip lifetime**.
- **Contacts and vias are particularly vulnerable** because older processes may have poor metal coverage around oxide edges, while in newer processes vias are typically among the smallest interconnect structures.
- Making the **metal wire wide enough is not sufficient**.
- When current moves between metal layers, the layout should use **multiple vias in parallel** when necessary rather than relying on a single via.
- More vias distribute the current among several paths, improving the reliability of the inter-layer connection.

In short:

> **Current-carrying capacity requires both sufficiently wide metal tracks and a sufficient number of contacts/vias for the expected current.**
### Via Doubling
As modern ICs contain extremely large numbers of vias, the probability that **at least one via is defective** increases. Because a single failed via can create an open connection and cause the entire chip to fail, reducing manufacturing yield, designers use **redundant vias**.

Instead of using one via:

```text
Metal 2
─────●─────
     │ via
─────●─────
Metal 1
```

two or more vias are placed in parallel:

```text
Metal 2
────●──●────
    │  │
────●──●────
Metal 1
```

This is **via doubling**. Even when **one via is sufficient for the required current**, using at least two means that if one via fails to make proper electrical contact, the other can maintain the connection.

So there are two related but distinct reasons for using multiple vias:

- **Current carrying capacity:** enough vias are needed to safely carry the required current.
    
- **Via redundancy:** additional vias are deliberately added **beyond what current capacity requires** to improve reliability and manufacturing yield.

The key idea is:

> **Via doubling introduces redundancy so that a single defective via does not cause the interconnect—and potentially the entire chip—to fail.**
### Metal–Semiconductor Contact
When a **metal contacts a semiconductor**, their different electronic band structures naturally create a **depletion region** at the interface. This region acts as an energy barrier, producing a **diode-like (Schottky) contact** rather than the desired linear connection.

To avoid this, the semiconductor immediately underneath the contact is **heavily doped**. Heavy doping makes the depletion region extremely thin, allowing carriers to **quantum-mechanically tunnel through the barrier**.

The result is an **ohmic contact**, meaning approximately:

$$I \propto V$$ 

so current can flow readily in either direction rather than behaving like a diode.

For IC layout, the key takeaway is:

> **Any silicon region that is contacted by metal must be sufficiently heavily doped to obtain a low-resistance, ohmic contact.**

A typical individual contact has a resistance in the **single- to double-digit ohm range** according to the excerpt.
### The Number of Metal Layers as an Optimization Goal
Choosing the number of metallization layers is a **trade-off between routability and manufacturing cost**:
- **“As many as needed”** — enough metal layers must be available to route every required interconnection while satisfying design rules.
- **“As few as possible”** — each additional metal layer increases fabrication complexity and cost, so unnecessary layers should be avoided.
- Removing a metal layer may be technically possible, but it can require **more layout effort and/or a larger chip area**, potentially eliminating the cost savings.
- **Mixed-signal processes** typically use about **3–5 metal layers**.
- **Smart-power processes** often have a **thick top-metal layer** for high-current routing. Because of its thickness and intended use, it may have larger minimum width and spacing rules.
- **Modern digital CMOS** generally provides more metal layers because highly complex circuits require very high routing density.
- Overall, the required number of metal layers is driven primarily by **circuit complexity and routing demand**.

**Key idea:** More metal layers improve routing capability and can reduce required chip area, but they increase manufacturing cost. Physical design therefore seeks the **minimum number of layers that can route the circuit efficiently and reliably**.