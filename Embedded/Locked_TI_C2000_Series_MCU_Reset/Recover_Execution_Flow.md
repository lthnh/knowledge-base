---
id: Execution Flow
aliases: []
tags: []
---
From last Saturday (25/07/2026), he told me about his ideas for unlocking this chip. I will list it down here:
1. Configure the boot mode pins to load our firmware (bootloader) through CAN bus.
2. Load [CANopenNode_C2000_bootloader](https://github.com/sicrisembay/CANopenNode_C2000_bootloader) into RAM.
3. Backup the FLASH, ROM.
4. Write new FLASH, ROM into it.

I think what we need is a *flash kernel*, not a full-blown bootloader.
Here is the general execution flow with a flash kernel:
1. Reset the device and use the intended boot mode.
2. Transfer the flash kernel from the host to the device via the bootloader in the boot ROM.
3. The flash kernel takes control after the ROM bootloader is complete.
4. Kernel configures a connection with host and receive the new application code using the intended peripheral communications protocol.
5. The kernel can either backup or erase the old application code from flash memory on the controller.
6. Kernel writes the newly received application code to flash memory and transfers control to the application.
7. Newly received code from host executes.

The hex utility supports the creation of the [[ROM_Bootloader_Execution_FLow#bootloader-data-stream-structure|ROM bootloader table]] required for CAN and other peripheral loaders. The actual file format required by the host (ASCII, binary, hex, etc.) differs between applications and some additional conversion must be applied. We can check the TMS320C28x Assembly Language Tools User's Guide for options used to generate boot table.

We must include the Flash API by linking it.

## Problems
Several control registers are protected from spurious CPU writes by the EALLOW protection mechanism. Can be check by using the EALLOW bit in CPU status register 1 (ST1). The states are as followed:

| EALLOW bit | CPU Writes | CPU Reads | JTAG Writes | JTAG Reads |
| ---------- | ---------- | --------- | ----------- | ---------- | 
| 0 | Ignored | Allowed | Allowed[^1] | Allowed |
| 1| Allowed| Allowed| Allowed| Allowed | 

[^1]: The EALLOW bit is overridden via JTAG port, allowing full access to EALLOW protected registers during debug with CCS interface.

