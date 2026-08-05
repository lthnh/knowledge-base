---
id: Memory
aliases: []
tags: []
---
## What is memory?
Memory is a system with the ability to store digital information. For IC, it's called *solid-state memory* since it has no moving parts.
## Memory Map Model
The information stored in memory is called **data**. The action to store information in memory is called a **write**. The aciton to access information in memory is called a **read**. To access data in memory, an **address** is used.

To reduce the number of addresses needed, individual bits are grouped into N-bit words. The number of address locations is described using a variable called M. Then the overall size of memory is typically stated as "MxN". For example, if we have a system with 16x8 memory, that means we have 16 address locations with each capable of storing a byte. This memory would have the capacity of 16 x 8 = 128 bits. 

Since addresses are implemented using binary code. The address lines determine the number of address locations that the memory system will have.
## Volatile vs. Nonvolatile Memory
Depends on whenever it can hold data when power is removed.
- Nonvolatile memory is memory that holds data even after power is removed.
- Volatile memory is memory that can't hold data after power is removed.

Historically, volatile memory is able to run much faster than nonvolatile so it's often used while a system is running. Nonvolatile memory is used to store startup instructions, operating systems, and applications.
## Read Only vs. Read/Write Memory
Depends on how the data is accessed.
- **Read Only Memory (ROM)** is a memory that can not be written to during normal operation. Useful to hold critical device info and programs that should not be modified while the system is running.
- **Read/Write Memory** is a memory that can be read or written to during normal operation. Used to store temporary data and variables.
## Random Access vs. Sequential Access
- **Random Access Memory (RAM)** is memory in which any location in the system can be accessed at any time.
- **Sequential Access Memory** is memory in which not all address location are immediately available.

Most semiconductor memory in modern systems is random access.
## Nonvolatile Memory Technology
### ROM Architecture
An address decoder is used to access individual data words within the memory. The decoder asserts one and only one *word line* (WL) for each unique binary address that is present on its input. The operation is identical to a binary-to-one-hot decoder. Historically, the word lines run horizontally across the memory array, thus they are called the *row lines*. And the word line decoder is often called the *row decoder*.

*Bit lines* (BL) run perpendicular to the memory array to provide individual bit access at the intersection of bit and word lines. These lines typically run vertically through the memory array, thus they are called *column lines*.

The output is obtained by providing the word address then reading the word from a buffered versions of the BLs.

When memory provides individual bit access to a role or access to multiple data words sharing the row line, a column decoder is used to route the appropriate BLs to the data output port.

In a traditional ROM array, each BL contains a pull-up network for $V_{CC}$ which provides the ability to store a 1. To store a 0, a NMOS transisor is added to pull BL down to GND. This NMOS will have its drain connected to bit line, its gate connected to word line and its source connected to GND. When reading data, the word line is asserted and this makes the NMOS turn on. The NMOS then pulls the bit line down to 0, effectively outputs a 0. If the NMOS is excluded, the bit line will be pull up to 1.

This memory can be either asynchronous or synchronous. The term *latency* describes the delay between when the input is sent to memory (an address in case of asynchronous and the clock in case of synchronous memory) and when the data is available.
### Mask Read Only Memory
With this memory type, all the features necessary for a memory are fabricated, with the exception of the final connections between NMOS transistors and the word and BLs. This state is said to be "unprogrammed". Once the desired information to be stored is provided by the customer, the fabrication process is completed by adding the connections between certain NMOS transistors and the word/BLs in order to create a logic 0's. This state is said to be "programmed".
### Programmable Read Only Memory
A PROM is created in manner similar to an MROM, except that the programming is accomplished post-fabrication through the use of fuses and anti-fuses. A fuse is an electrical connection that is normally conductive. After a certain amount of current passes through it, it melts and creates an open circuit. The anti-fuse operates in the manner opposite of fuse. Normally, anti-fuse is non-conductive. After a certain amount of current is forced through it, the insulating material breaks down and creates a conduction path. A PROM uses fuses or anti-fuses in order to connect/disconnect the NMOS transistors in the ROM array to the word/BLs.

A PROM programmer is used to burn the fuses or anti-fuses.
### Erasable Programmable Read Only Memory
This is a interesting type of ROM. Its based on floating-gate conductor. It works by adding an additional gate on top of the already existing gate of the transistor. This modifies the transistor threshold level such that it's impossible to turn on with normal CMOS levels. This threshold can be changed by apply large electric field between the two metal conductors. The charges from the metal will tunnel through the oxide layer due to a phenomenon called Fowler–Nordheim tunneling. This causes the oxide to turn into a conductive layer and reduces the threshold voltage, making the transistor impossible to turn off with normal CMOS levels.

To erase this type of ROM, the memory must be subjected to UV light source to knock charges off the oxide layer, turn it once again into a insulating layer.
### Electrically Erasable Programmable Read Only Memory
This is an improvement over the previous ROM type. With this ROM type, additional circuitry is added to generate large electric field to apply across the oxide layer. This removes the charges reside inside the oxide and effectively erases memory. EEPROM doesn't need an external programmer and it also doesn't need to leave the system to be programmed.
### FLASH Memory
One of the early drawbacks of EEPROM is the additional circuitry that provides the ability to program and erase individual bits also adds to the size of each individual storage element. FLASH EEPROM attempted to improve that by programming and erasing large groups of data, or *blocks*. This allowed individual storage cells to shrink and provide higher memory density. This new architecture is called *NAND FLASH*. Today, NAND FLASH is used in nearly all devices.

To provide individual word access, NOR FLASH was introduced. This architecture provides faster read times than NAND FLASH but the additional circuitry causes the write and erase times to be slower and the individual storage cell has to be larger.

Due to NAND FLASH has faster write times and higher density, it is seeing higher adoption than NOR FLASH. NOR FLASH is considered RAM, while NAND is typically not.
## Volatile Memory Technology
### Static Random-Access Memory
SRAM stores information using a cross-coupled inverter feedback loop. In basic SRAM storage cell, two access transistors are used to read from and write the storage cell. The cell has two complementary port BL and BL'. Due to the interving functionality, these two ports always complements each other. This is advantageous to determine the data value because the signal effectively has double strength.

This configuration takes 6 transistor to be implemented and is often called 6 T configuration. Its simple configuration makes it very fast. Thus SRAM cells are often used for cache memory in computer.

To build an SRAM memory, cells are arranged in an array pattern. Word lines are shared horizontally across the array to provide addressing capability. An address decoder is used to convert binary address into appropriate word-line assertion. N storage cells mean the data word is N-bit long. BLs are shared vertically across the array to provide data access (either read or write). A data line controller handles data read or write based on external write enable signal.

The data line controller also handles determining the correct logic value read from the cells by comparing BL to BL'. As more cells are added to BLs, the signal magnitude being driven by storage cells diminishes due to loading effect from other cells. This is where complementary data signals are useful. The comparison of BL to BL' is handled by an differential amplifier to determine storage cell outputs even when the incoming signals are very small.
### Dynamic Random-Access Memory
DRAM stores information using a capacitor. In a basic DRAM cell, there are a transistor and a capacitor. This is referred to as 1T1C configuration. Just like SRAM, word lines are used to access the storage elements. The term *digit line* (DL) is used to describe the vertical connection to the storage cells.

DRAM storage element requires less area than SRAM. This allows DRAM to have higher memory density than SRAM. But there are a few caveats you should know:
1. Charge in capacitor will slowly dissipate over time.
2. The voltage of the wordline must be larger than $V_{CC}$ in order to turn on the access transistor.
3. Charge sharing phenomenon.

For the first caveat, DRAM must have a dedicated circuit to refresh the contents of the storage cell. A refresh cycle involves periodically reading the value stored in the cell then writing back the same value at full strength.

In DRAM, the source terminal of the access transistor is connected to a capacitor. If the capacitor is storing a 1, the gate voltage of the transistor must be larger than or equal to $V_{CC} + V_T$ in order to turn on the transistor. This requires a *charge pump* to create this voltage on word lines. The process of charging takes time, thus affects the maximum of DRAM.

When the access transistor is closed, the charge sharing phenomenon appears. This makes the charge stored in the capacitors cannot develop a full voltage level across DL when the transistor is closed. In practice, the capacitance of DL is much larger than that of capacitor due to having a larger area and being connected to other storage cells. The resulting voltage on DL is much smaller then the original voltage stores on a cell. This creates issues cause the voltage on word lines is not large enough to be detected by standard logic gate or latch. To overcome this, modern DRAM arrays use complementary storage cells and sense amplifiers. The complementary cells store data and its complement. Two DLs (DL and DL') are used to read the contents of the cells. DL and DL' are precharged to exactly $\frac{V_{CC}}{2}$. When the access transistors are closed, their capacitors share charges with DLs and move them slightly from $\frac{V_CC}{2}$ in different directions. This allows TWICE voltage difference to be developed during a read. A sense amplifier is then used to boost this small voltage deviations from $\frac{v_{CC}}{2}$ on DL and DL' to full logic levels.

The sense amplifier sits between DL and DL' and has two complementary networks: the N-sense amplifier and P-sense amplifier. The N-sense amplifier is used to pull a signal that is below $\frac{V_{CC}}{2}$ (either DL or DL') to GND. A control signal (N-Latch) is used to turn on this network. The P-sense amplifier is used to pull a signal that is above $\frac{V_{CC}}{2}$ up to $V_{CC}$. The two networks are activated in sequence, with the N-sense network activating first.

A DRAM write operation occurs as followed. First the access transistors to complementary cells are open. Then the precharge drivers are disabled. Finally, data-in line driver writes full logic level signals to the storage cells.
## Modelling Memory with Verilog

