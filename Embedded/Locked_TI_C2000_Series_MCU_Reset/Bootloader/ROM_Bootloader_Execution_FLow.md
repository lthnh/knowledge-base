---
id: ROM Bootloader
aliases: []
tags: []
---
## Bootloader Modes
For eCAN-A boot set the boot mode selection pins to the following, assume default BMSPs are used:

| MODE | GPIO87/XA15 | GPIO86/XA14 | GPIO85/XA13 | GPIO84/XA12 | Mode |
| ---- | ----------- | ----------- | ----------- | ----------- | ---- |
| B | 1 | 0 | 1 | 1 | eCAN-A boot |
| 3 | 0 | 0 | 1 | 1 | Branch to check boot mode |

Like before, we can't connect the JTAG debugger with a secured chip. When the emulator is trying to take control of the CPU, the CPU may start running and execute an instruction that performs access to a protected ECSL area. This cause ECSL to trip and the connection to be cut. We can try two things:
1. Select boot mode B directly.
2. Select boot mode 3 to enter boot check mode then select B mode.
## Boot ROM Execution Flow
After calling the bootloader successfully, the processor will continue execution at the entry point determined by input stream loaded by the peripheral.
## Bootloader Data Stream Structure
The first 16-bit word is the key value. It tells the bootloader the width of the incoming data. Depends on the data stream width,
- For an 8-bit data stream, it's 0x08AA.
- For an 16-bit data stream, it's 0x10AA.
If the bootloader receives invalid key, the load is aborted and entry point for FLASH memory (0x33 7FF6) will be used instead.

The next eight words are used to initialize registers values or otherwise enhancing the bootloader by passing values to it. If the bootloader doesn't use these values it discards it. Only the following peripherals bootloaders use these words to initialize the registers:
- SPI
- I2C
- parallel XINTF

The tenth and eleventh words comprise the 22-bit entry point address. Used to initialize the PC after loading. Likely the entry point of the program you have just loaded.

The twelfth word is the size of the first data block to be transferred. Defined for both 8-bit and 16-bit data stream as the number of 16-bit words in the block. Ex: to transfer a block of twenty 8-bit data, the block size would be 0x000A to indicate ten 16-bit words.

The next two words indicate the destination address of the block of data. Following it would be 16-bit words that form that block of data.

This pattern of block size/destination address is repeated for each block of data to be transferred. Once finish, a block size of 0x0000 signals to the loader that the transfer is complete. The loader will return the entry point address to the calling routine. Execution then continue at the entry point address.

>[!warning] In 8-bit mode, LSB of the word is sent first followed by MSB.

>[!warning] In 8-bit mode, 32-bit values such as a destination address have their most significant word (MSW) loaded first then least significant word (LSW).

## InitBoot Assembly Routine
InitBoot Assembly Routine is the first routine to be called after reset. It initializes the device for operation in C28x object mode and performs a dummy read of CSM password locations. If the CSM passwords are erased (all 0xFFFFs) then this has the effect of unlocking the CSM. Otherwise the CSM will remain locked and this dummy read of the password locations will have no effect.

## eCAN Boot Function
The eCAN bootloader asynchronously transfers code from eCAN-A to internal memory. The host can be *any CAN node*. The communication is first done with 11-bit standard identifiers (with a MSGID of 0x1) using two bytes per data frame. The host can download the kernel to reconfigure the eCAN if higher data throughput is desired.
The eCAN bootloader uses the following pins:
- CANRXA on GPIO30
- CANTXA on GPIO31
Bit-timing registers are programmmed to ensure valid bit-rate for different XCLKIN values as follow

| XCLKIN | SYSCLKOUT | Bit Rate |
| ------ | --------- | -------- |
| 30 MHz | 15 MHz | 500 kps |
| 15 MHz | 7.5 MHz | 250 kps |

Mailbox 1 is programmed with a standard MSGID of 0x1 for bootloader communication. The CAN host should transmit only 2 bytes at a time, LSB first and MSB next.
## Sources
1. TMS320x2833x, TMS320x2823x TRM. Literature Number: SPRUI07. March 2020.
