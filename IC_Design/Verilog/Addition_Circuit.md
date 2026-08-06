---
id: Addition_Circuit
aliases: []
tags: []
---
For now, there are two types of adder circuit:
1. Ripple Carry Adder.
2. Carry Look Ahead Adder.

With RCA, the delay increases with the number of bit. But it's simple and easy to implement.
With CLA, the delay is fixed but it is met with fan-in issues due to logic functions expansion. This is the only way to make addition circuit depend only on current inputs. For more bits, additional circuit must be implement to deal with fan-in issues.

