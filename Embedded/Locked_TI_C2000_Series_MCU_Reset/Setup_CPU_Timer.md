---
id: Setup_CPU_Timer
aliases: []
tags: []
---
- RPT instructions are not interruptible, meaning it can delay or block interrupts from executing. An example is the memcpy() function in a background function. To avoid this, use --no_rpt to tell the compiler not to generate RPT instructions or --rpt_threshold to limit the number of consecutive RPT instructions generated. From [this source](https://software-dl.ti.com/C2000/docs/optimization_guide/common_optimization_issues.html).
- Any global variable that is modified by both main() and ISRs must be annotated volatile.
- Example program flow: Reset -> Boot Sequence (Boot ROM) -> DSP2833x_CodeStartBranch.asm -> Initialize System Control -> Initialize GPIO -> Initialize PIE Vector Table -> Initialize Peripherals -> Application Code.
