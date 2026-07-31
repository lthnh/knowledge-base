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


