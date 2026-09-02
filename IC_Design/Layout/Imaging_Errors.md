There are three types of errors:
- Overlay errors
- Diffraction effects
- Edge shifts
Overlay errors and diffraction effects occur during exposure, while edge shifts occur in subsequent structuring process steps.
## Overlay Errors
The cause of overlay errors can be:
- Mechanical tolerances
- Measurement inaccuracies
- Changes in temperature
There are also four types of overlay errors:
- Displacement
- Rotation
- Scaling
- Perspective distortion
Because wafer and photomask can move along the optical axis to adjust the depth of field. When the distances between masks, lens and wafer are changed during focusing step, the layers will be scaled relative to one another.

If the photomask is tilted with respect to the optical axis, perspective distortion occurs.

Temperature change can also make the wafer expand or shrink. The relative positions between each structure on the wafer change, hence cause the displacement and scaling errors.

The type and extent of these overlay defects cannot be predicted. And their effects are cumulative.
The maximum permissible overlay error in a semiconductor process **should not exceed the minimum feature size and is typically must less than this value.**
## Edge Shifts
Effects that occur in some technology layers can cause graphics elements on the processed wafer to be enlarged or shrunk with respect to the associated graphics elements in the layout.

The changes with these effects are *additive*. The structure's boundary lines are shift outwards (positive shift) or inwards (negative shift).

The size of these edge shifts are *layer-specific*, and they are defined for every semiconductor process.

The effect can be compensated by pre-sizing when creating the photomask geometry. For example, if an edge shift of value *k* occurs in the process, the edges of layout geometries are shifted by a value *k* before transferring to the photomask.
## Diffraction Effects
Diffraction effects occur at the structural edges of the chromium layer on the photomasks $\rightarrow$ degrades the optical resolution.

The smaller the feature size, the more the diffraction effects impact the accuracy. As feature size approach exposure wavelength, *line-end shortening* and *corner rounding* become more severe.

For average distortion, you can use *rule-based optical proximity correct* (rule-based OPC). You can add *hammer heads* to line ends if line width is approximately the same as feature size. And you can add or punch *serifs* (a square element) to the corners to get more or less light.

For more severe cases, you can use *model-based OPC* which uses models that describe the wave-optical effects to make necessary corrections to the boundary. As exposure results are also impacted by surrounding structures, these corrections must be computed for each individual structure.

## Reference to Physical Design
There are two types of errors:
- Deterministic: edge shifts and diffraction
- Stochastic: overlay errors
### Deterministic Errors
With these types, we can take preventive measures. This is automated in *layout to mask preparation process*.

But not all edge shifts occurring in the process are neutralized by pre-emptive operations. Some features on wafer will look different than in layout.

Calculations for model-based OPC are very CPU intensive, but can run in parallel.

The technological constraint caused by wave-optical properties of light used to photolithography is realized through these design rules:
- Minimum width: ensure features can be exposed on wafer (or ensure they do not "disappear")
- Minimum spacing rule: ensure features are safely separated (or ensure they do not "merge")
### Stochastic Errors
We can only ensure that the sum of all deviations does not exceed the specified limit by complying with tolerances for devices and process regulation.

Rules for overlay errors describe minimum dimensions that refer to features on *different layers*:
- **Extension** and **Intrusion** rules: two overlapping geometrical elements (ensure features overlap on wafer)
- **Enclosure** rules: one geometrical element is enclosed by the other (ensure one structure covers the other on the wafer)
- **Spacing** rules: spacing between two geometrical elements (ensure there is a clearance between two features, or at least no contact between them)