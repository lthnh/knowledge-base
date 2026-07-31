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

