The way TI support answered makes me wonder if it actually works or if there is any caveat that I am not aware of. But here is how to recover it:
1. Select SCI boot using boot mode pins.
2. Power cycle the device [^1].
3. Don't send SCI data using either host or other MCU.
4. C2000 Series MCU stays in infinite loop waiting for data from the host preventing MCU (?) from access secure memories content (?).
5. Connect to C2000 device using CCS [^2].
6. Unlock the device by entering password in `0xAE0-0xAE7` memory location.
7. Erase Sector A of flash to recover the device.
## Boot mode pins
See the boot ROM section of the MCU's datasheet for more information.
## Unlock with CCS
See source #4 for more info.

Update 20/07/2026, 16:47: I think I understand what he means. He means we still need to know the password to recover the device. We need to find another way.
Now I start digging the boot loader repository Mr. Phu sent me last week, I find that it has backdoor access. But if we don't have the password, we can't erase and reprogram the flash which effectively makes this approach futile.

Update 20/07/2026, 21:36: Another person says that it's impossible to reprogram a locked MCU due to unstable power supply. Source #5 also say it's impossible to recover the device if the password is unknown.

Update 21/07/2026, 16:23: I talked to Mr. Trung this morning. Here a few main things that I took notes of:
- His plan is to load the custom bootloader into RAM then execute it from there to extract all of the firmware.
- We will use boot mode pins to determine the necessary boot mode to load this custom bootloader into RAM.
Here are my concerns:
- Can this custom bootloader access (read/write) secure memory regions (sector A)?
- We will load this custom bootloader through CAN, does this chip have default mode that support CAN? Then what type of CAN is this? FD-CAN or CAN Classic?
	- Custom boot mode requires programming the OTP.
- We have two types of boot: standalone boot and emulation boot. Emulation boot is triggered through JTAG and in turn trigger ECSL. What should we do?

Sources:
1. https://e2e.ti.com/support/microcontrollers/c2000-microcontrollers-group/c2000/f/c2000-microcontrollers-forum/1092517/tms320f28027-how-to-recover-from-csm-lock
2. https://github.com/sicrisembay/CANopenNode_C2000_bootloader
3. https://e2e.ti.com/support/microcontrollers/c2000-microcontrollers-group/c2000/f/c2000-microcontrollers-forum/721092/ccs-tms320f28035-how-do-i-unlock-c2000-mcu-when-it-s-locked
4. https://e2e.ti.com/support/microcontrollers/c2000-microcontrollers-group/c2000/f/c2000-microcontrollers-forum/721092/ccs-tms320f28035-how-do-i-unlock-c2000-mcu-when-it-s-locked
5. https://e2e.ti.com/support/microcontrollers/c2000-microcontrollers-group/c2000/f/c2000-microcontrollers-forum/1104107/tms320c2801-not-ble-to-program-the-device-device-got-locked-after-programming
6. https://www.ti.com/video/series/C2000-dual-code-security-module.html

[^1]: This means turn the device off, wait for a short time then turn it back on.

[^2]: Code Composer Studio, a TI IDE.
