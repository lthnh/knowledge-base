---
id: Linker Command File
aliases: []
tags: []
---

> [!warning] This is specifically for TI linker script, not apply to GCC linker.

## Basics
Linker command file can contain anything that may appear in a command line: options, object file names, library names. Global symbols can also be created.
### MEMORY Directive
Its purpose is to assign names to a range of memory. These name can be used in the `SECTIONS` directive.
Below  is an example from TI.

```ld
MEMORY
{
    SFR                     : origin = 0x0000, length = 0x0010
    PERIPHERALS_8BIT        : origin = 0x0010, length = 0x00F0
    PERIPHERALS_16BIT       : origin = 0x0100, length = 0x0100
    RAM                     : origin = 0x1C00, length = 0x0FFE
    INFOA                   : origin = 0x1980, length = 0x0080
    INFOB                   : origin = 0x1900, length = 0x0080
    INFOC                   : origin = 0x1880, length = 0x0080
    INFOD                   : origin = 0x1800, length = 0x0080
    FLASH                   : origin = 0x8000, length = 0x7F80
    INT00                   : origin = 0xFF80, length = 0x0002
    /* ... and so on */
}
```

You specify a memory region by stating the origin and the length of that memory region.
### SECTIONS Directive
This section does two things at once:
- Forms output sections from input sections
- Allocates those output sections to memory

![Sections Directive Visual](../Images/linker_primer_sections_directive.PNG)

#### Glossary
- Object file: a file contains mostly machine code (i.e 0 and 1) and has info that allows a linker to know which symbol it requires to work.
- Symbol: names of variables, functions, etc.
- Input section: one section from one object file. One section can be initialized or uninitialized. It can be either code or data. 
- Output section: a collection of more than one input sections, formed according to the SECTIONS directive.
#### Section Naming Convention
Section name doesn't tell you everything. But input sections with these names usually have these contents.

| Name | Initialized | Notes |
| ---- | ----------- | ----- |
| .text | yes | executable code |
| .bss | no | global variables |
| .cinit | yes | tables which initialize global variables |
| .data (EABI) | yes and no | initialized coming out of the assembler; changed to unitialized by the linker |
| .data (COFF EABI) | yes | initialized data |
| .stack | no | system stack |
| .heap or .sysmem | no | malloc heap |
| .const | yes | initialized global variables |
| .switch | yes | jump tables for certain switch elements |
| .init_array or .pinit | yes | table of C++ constructors called at startup |
| .cio | no | buffer for stdio functions |

Sections often begin with '.' but it is not required. The names may have some variations but they have the same meaning.
The SECTIONS directive has similar syntax as MEMORY directive.

```ld
SECTIONS
{
    /* All sections appear here. */
}
```

#### Output Sections
Shortcut is one of the most confusing aspects in SECTIONS directive code. Below is an example without shortcuts.

```ld
    output_section_name         /* Name the output section        */
    {
       file1.obj(.text)         /* List the input sections        */
       file2.obj(.text)
       file3.obj(.text)
    } > FLASH                   /* Allocate to FLASH memory range */
```

Here is a possible shortcut:

```ld
    output_section_name         /* Name the output section           */
    {
        /* Shortcut syntax for all input sections named .text        */
        *(.text)
    } > FLASH                   /* Allocate to FLASH memory range    */
```

If these sections are included together, this second section will include any .text sections aside from the .obj files above. But even this is not short enough. This example will continue from the example above.

```ld
    .text > FLASH
```
This example has only one difference: now the output_section_name has been changed to .text. The output section name and the input section names are all the same: .text.

> [!info] We should not overlook the distinction between input sections and output section which contains them.

Here is another example:

```ld
    .text : {} > FLASH
```

This example is no difference from the one above but included because that syntax pattern is common in many linker command files.
You can mix all of these shortcuts together.

```ld
    output_section_name
    {
        first.obj(.text)        /* This code must be first */
        *(.text)
    } > FLASH

```

This syntax `> FLASH` allocates the output section to FLASH memory.
You may also see hard-coded address `> 0x20000000`.
Allocations to hard-coded address are always done before allocations to a named memory range. Your linker command file may takes advantage of this.
You should watch for macro expansion like this as this is actually an allocation to a hard-coded address:

```ld
#define BASE 0x20000000

/* many lines later */

    ... > BASE
```

## Advance
### First Output Section in a Memory Range

```ld
#define BASE 0x00200000

MEMORY
{
    FLASH : origin = BASE, length = 0x0001FFD4
    ...
}

SECTIONS
{
    .intvecs > BASE    /* only section allocated to BASE */
    .text    > FLASH
    .const   > FLASH
    ...
}
```

The net effect is that .intvecs is the first output section in the FLASH memory range. Any other section can be allocated in any order in FLASH.
Define BASE is an example of using C-like preprocessor macro of linker.
### Allocation to Multiple Memory Ranges

```ld
.text > FLASH0 | FLASH1
```
This means .text section is allocated to either FLASH0 or FLASH1. FLASH0 is tried first, if it doesn't have enough space FLASH1 is tried.

[!info] The text is NOT split but stay whole in either FLASH0 or FLASH1.

### Split an Output Section Across Multiple Memory Ranges

```ld
.text : >> RAMM0 | RAML0 | RAML1
```

The `>>` means .text is split across those memory ranges. If all of .text is not fit in RAMM0 then it is split into the other memory ranges.

>[!info] The split occurs on the input section boundaries. An input section is never split.

### Pages of Memory
Are only used in C28xx linker command files.

```ld
MEMORY
{
    PAGE 0 :
        RAMM0   : origin = ...
        RAML0L1 : origin = ...

    PAGE 1 :
        RAMM1   : origin = ...
        RAML2   : origin = ...
}
```

Each page of memory is completely independent so you can reuse memory range names and *memory addresses*.
This is a bad idea:

```ld
/* DO NOT DO THIS!!! */
MEMORY
{
    PAGE 0 :
        MEM_RANGE : origin = 0x100, length = 0x100
    PAGE 1 :
        MEM_RANGE : origin = 0x100, length = 0x100
}
```

C28xx devices are descended from a long line of C2xxx devices which started in the 80s. Those early devices have separate memory buses for code and data. These buses connect to physically separate memory blocks. Thus, it was possible for a specific address on PAGE0 to have different content from the same address on PAGE1. In theory, this same separate connection of buses is possible on C28xx devices but it is almost a never used feature. You should check the TRM before proceeding.
3.

Even though nearly all C28xx devices have all the memory buses connected to all the memory. This tradition use of memory pages persists.

>[!warning] Check the documentation properly before tampering.

#### Syntax Hint
Anywhere you can write MEMORY_RANGE_NAME you can also write MEMORY_RANGE_NAME PAGE 0. Ostensibly, this is possible because we can have the same name on multiple memory pages.
If you combine a memory range name and page that don't exist, the linker will tell you.
### Nullify an Output Section

```ld
   .reset : > RESET, PAGE = 0, TYPE = DSECT    /* not used */
```

`TYPE = DSECT` means make this output section a dummy section. A dummy section takes no space in memory and the linker sliently throws away this section. You should properly check the code or data in section is being used or not before making it a dummy section.
More info on special sections like `DSECT`, refer to [[Linker Command File#source]] 3.

### Refer to ROM Code or Data

```ld
FPUmathTables : > FPUTABLES, PAGE = 0, TYPE = NOLOAD
```

This code is how to refer to a section that is already present in the system. That section is usually supplied in ROM or flash memory. The `TYPE = NOLOAD` makes this section not present in the output file. In this specific case some floating point unit must be supplied in ROM, and other code is using those tables.
In practice, there is no reference from the NOLOAD section to anything outside. But other sections can refer to the code and data inside the NOLOAD section.

More info on special sections like `NOLOAD`, refer to [[Linker Command File#source]] 3.
### Load at One Address, Run from a Different Address

```ld
 .TI.ramfuncs : LOAD = FLASHD,
                RUN = RAML0,
                LOAD_START(_RamfuncsLoadStart),
                LOAD_END(_RamfuncsLoadEnd),
                RUN_START(_RamfuncsRunStart)
```

This create an output section named .TI.ramfuncs that is composed of all input sections with the same name. It has two allocations: FLASHD for loading and RAML0 for running. This requires the application copies .TI.ramfuncs from FLASHD to RAML0 during system execution. This step is not automatic and must be explicitly implemented in the application code.

The LOAD_START, LOAD_END and RUN_START establish symbols that are used to implement the copy. The value of symbol _RamfuncsLoadStart is the starting load address, _RamfuncsLoadEnd is the ending load address, and _RamfuncsRunStart has the starting run address.
### Allocate a Single Input Section from a Library

```ld
IQmathTables3 : > IQTABLES3
{
   IQmath.lib<IQNasinTable.obj> (IQmathTablesRam)
}
```

This forms an output section named IQmathTables3 with one input section named IQmathTablesRam. This input section comes from an object file named IQNasinTable.obj,which is a member of IQmath.lib library. The output section is allocated to IQTABLES3 memory range.

Below is a variant to include all sections from a library.

```ld
sinetext : > DDR2
{
     --library=Sinewave_lib.lib(.text)
}
```

This forms an output section named sintext containing all the .text input sections from Sineware_lib.lib. This section is allocated to DDR2 memory range. Note that the linker does not bring in the files from the library but only files that are actually needed to satisfy open references from other object modules.

The `--library=` syntax has the same effects as `<>` in the previous examples.
### Allocate an Input Section from a Library to Different Load and Run Addresses.

```ld
ipcConst
{
   driverlib.lib<ipc.obj>(.const)
} LOAD = FLASH5, RUN = RAMLS0,
LOAD_START(constLoadStart),
LOAD_SIZE(constLoadSize),
RUN_START(constRunStart), ALIGN(8)
```

This combines techniques from [[Linker Command File#load-at-one-address-run-from-a-different-address]] and [[Linker Command File#allocate-a-single-input-section-from-a-library]].
For more info on the LOAD_START, LOAD_SIZE and RUN_START operators see *Address and Dimension Operators* in **Assembly Language Tools** manual for your CPU family. ALIGN(8) means the run address is aligned to a multiple of 8. For details see *Specifying Load and Run Addresses* in **Assembly Language Tools**.
### Group Output Sections Together
Suppose you need some output sections to be next to each other in order. You might write

```ld
/* This does NOT work */
output_section_1 > RAM
output_section_2 > RAM
output_section_3 > RAM
```

The linker places all of those output sections in memory range but in any order. There maybe some other section put in between them. You should use GROUP directive to allocate output sections together in certain order like

```ld
GROUP : > CTOMRAM
{
    PUTBUFFER
    PUTWRITEIDX
    GETREADIDX
}
```

The output sections are PUTBUFFER, PUTWRITEIDX, and GETREADIDX. They are allocated to the memory range CTOMRAM as a group, in that exact order. Note how the individual output sections do not have any memory allocation specification.

>[!info] The output section names are in capital. This is unwritten convention in linker command files that only memory range names like CTOMRAM are written in all capital letters.

>[!info] TI linker command files may violate this convention.

### Memory Attributes
The MEMORY directive might have lines like these

```ld
MEMORY
{
    ...
    FLASH1 (RX) : origin = 0x00204000, length = 0x1C000
    FLASH2 (RX) : origin = 0x00260000, length = 0x1FFD0
    CSM_RSVD_Z2 : origin = 0x0027FFD0, length = 0x000C
    CSM_ECSL_Z2 : origin = 0x0027FFDC, length = 0x0024
    C0 (RWX)    : origin = 0x20000000, length = 0x2000
    ...
}
```

Note `(RX)` and `(RWX)`. That syntax specifies *memory attributes* with each letter representing one attribute.
- R: Can be read
- W: Can be written
- X: Can contain executable code
- I: Can be initialized

>[!info] By default, a memory range has all four attributes.

>[!info] No TI supplied linker command files use this feature.

The documented purpose of these attributes is to support, in the SECTIONS directive, section allocation by memory attribute. Since no TI supplied linker command files use this feature, this syntax is used only as a way to document what kinds of sections usually go in that memory range.
## Sources
1. https://software-dl.ti.com/ccs/esd/documents/sdto_cgt_Linker-Command-File-Primer.html
2. https://stackoverflow.com/questions/7718299/whats-an-object-file-in-c
3. https://software-dl.ti.com/ccs/esd/documents/sdto_cgt_linker_special_section_types.html

