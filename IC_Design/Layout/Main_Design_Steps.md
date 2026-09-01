The simplified process is specifications $\rightarrow$ circuit design $\rightarrow$ physical design $\rightarrow$ fabrication.
Circuit design produces a netlist/schematic. This serves as input for physical design.
Physical design is also known as *layout design*.
With physical design of digital circuits, the process is mostly automated while physical design of analog circuits requires manual work most of the time. However, there are scripts called generators which can produce various layout variants using various parameters.
The result of physical is a *layout*.
Many automated verification algorithms are available to check the layout results. These two algorithms are a must:
- Design Rule Check (DRC) ensures manufacturability. These are process technology constraints.
- Layout Versus Schematic Check (LVS) ensures specifications contained in the structural description have been correctly realized in the layout. Below are those checks:
	- Devices are properly connected electrically.
	- Correct types of devices are in the layout.
	- Devices are correctly parameterized.
The layout is sent to factory for fabrication.