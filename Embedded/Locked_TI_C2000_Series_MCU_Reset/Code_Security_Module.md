---
id: Code Security Module
aliases: []
tags: []
---
The security features a 128-bit password which the user programs into the flash.

One CSM is used to protect the flash/OTP and the L0/L1 SRAM blocks. This prevents unauthorized user from examining the memory contents through the JTAG port or trying to **boot-load** some undesired firmware that would export the secure memory contents. To enable access to the secure blocks, the user must write the correct 128-bit KEY value that matches the value stored in the password locations within the flash.

Additionally, the emulation code security logic (ECSL) has also been implemented to prevent unauthorized users from stepping through the source code. Any code or data access to the flash, user one time programmable memory, or L0 memory while the JTAG debug probe is connected will trip the ECSL and breaks the debug probe connection.

To enable debugging, user must write the correct value into the lower 64 bits of the KEY register (KEY0 - KEY3) that matches the value in the lower 64 bits of the password locations (PWL0 - PWL3) within the flash. If the lower 64 bits of the password locations are all ones (unprogrammed), then the KEY value does not need to match.

During debug of secure code, things like single-stepping are possible but the actual contents of the secure memory cannot be seen in the CCS window.

When MCU is connected to power with attached JTAG debug probe, the CPU will begin executing and perform memory access to protected memory. This WILL trip ECSL and causes the JTAG circuitry to be deactivated. After that the host wouldn't be able to establish connection with the device. The solution is to use Wait boot mode allowing the JTAG connection is be established without tripping ECSL. Only then we can switch to other boot modes.

## Discussion
What are other boot modes for? Can we take advantage of them to recover the locked board?
