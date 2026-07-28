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

 
