Boot loader is a small piece of software that lies in a flash sector.
It must be in a separate sector as the flash can only erase a sector at a time.
If you use Code Security Module, you can must ensure the bootloader is correctly linked and HAS the ability to unlock the device before flashing.
Source: https://www.ti.com/video/3871889296001