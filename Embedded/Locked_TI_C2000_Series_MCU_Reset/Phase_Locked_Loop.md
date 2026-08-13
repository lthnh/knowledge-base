---
id: Phase_Locked_Loop
aliases: []
tags: []
---
## Fundamentals
### Basic configuration
In its most simple form, PLL consists of:
- Error Detector: implemented as phase detector
- Loop Filter: implemented as low-pass filter
- Voltage Controlled Oscillator: can be Voltage Controlled Crystal Oscillator
- Feedback Divider: implemented as divide-by-N counter

PLL compares the phase of the reference signal to the phase of the adjustable feedback signal. If the frequency and phase of both signals are matched, the PLL is said to be locked.

## Sources
1. https://www.analog.com/en/resources/analog-dialogue/articles/phase-locked-loop-pll-fundamentals.html

