---
id: Vivado_Specific
aliases: []
tags: []
---
## Square Brackets
Vivado Design Suite handles square brackets differently from standard Tcl since square brackets are treated as standard characters in Verilog, SystemVerilog and VHDL names (net, instances, etc.) and usually identify one or more elements of vectors (e.g. buses or arrays of instances). In other words, in Vivado square brackets are not evaluated in a inside out manner when they are expected to be part of a netlist object name.

The follow three commands are equivalent:

```tcl
1.) set list_of_pins [get_pins transformLoop[0].ct/xOutReg_reg/CARRYOUT[*] ]
2.) set list_of_pins [get_pins {transformLoop[0].ct/xOutReg_reg/CARRYOUT[*] } ]
3.) set list_of_pins [get_pins transformLoop\[0\].ct/xOutReg_reg/CARRYOUT\[*\] ]
```

In standard Tcl, option 2) would be the most compatible without much hassle. But Vivado also supports option 1) which would elevate the ergonomics quite a bit.

## Comments
To add comment to the end of a line, ending the command with a semicolon (;) then begin the comment with a hash character (#).

```tcl
# This is a comment
puts "This is a command"; # followed by a commenttcl
```

## Getting Help
Every Vivado comman supports the `-help` command line argument that can be used anywhere in the line.

```tcl
Vivado% create_clock -help
Vivado% create_clock -name CLK1 -period 10 -help
```

In addition, there is also a `help` command. Its output is the same as `<command> -help`

The `help` command can also return a short description of the arguments using the `-args` option.

```tcl
Vivado% help create_clock -args
create_clock
Description: 
Create a clock object
Syntax: 
create_clock -period <arg> [-name <arg>] [-waveform <args>] [-add] [-quiet] [-verbose] [<objects>]
Returns: 
new clock object
Usage: 
  Name     Description
  ------------------------
  -period   Clock period: Value > 0
  [-name]   Clock name
  [-waveform] Clock edge specification
  [-add]    Add to the existing clock in source_objects
  [-quiet]   Ignore command errors
  [-verbose]  Suspend message limits during command execution
  [<objects>] List of clock source ports, pins or nets
```
A short summary of command syntax is available with the `-syntax` option.

```tcl
Vivado% help create_clock -syntax
create_clock
Syntax: 
create_clock -period <arg> [-name <arg>] [-waveform <args>] [-add] 
[-quiet][-verbose] [<objects>]
```

Executing only the `help` command will provide categories of commands or classes of objects.

```tcl
Vivado% help
ChipScope
DRC
FileIO
Floorplan
GUIControl
IPFlow
Object
PinPlanning
Power
Project
PropertyAndParameter
Report
SDC
Simulation
TclBuiltIn
Timing
ToolLaunch
Tools
XDC
```

The list of commands under each category can be listed with `-category`.

```tcl
Vivado% help -category tools
Topic      Description
link_design   Open a netlist design
list_features  List available features.
load_features  Load Tcl commands for a specified feature.
opt_design    Optimize the current netlist. This will perform the retarget,
                     propconst, and sweep optimizations by default.
phys_opt_design Optimize the current placed netlist.
place_design   Automatically place ports and leaf-level instances
route_design   Route the current design
synth_design   Synthesize a design using Vivado Synthesis and open that designtcl
```

## Simulation
### Behavioral Simulation
Gather files -> Parse using xvlog/xvhdl -> Compile and elaborate using xelab (create snapshot) -> Execute using xsim <snap shot> -> Debug on waveform.

To run behavioral simulation in Tcl script:

```tcl
launch_simulation -mode behavioral
```

### Post-Synthesis and Post-Implementation Simulations

![[post-synthesis-and-post-implementation-simulations-flow.svg]]

You can type simulation commands into a Tcl file, and reference the Tcl file with the following command:

```tcl
xsim <snapshot> -tclbatch <filename>
```

You can set a variable to represent a simulation command to quickly run frequently used simulation commands.

#### export_simulation
You can export simulation script for the target simulator in case you want to simulate outside of Vivado IDE. The generated script contains simulator commands for compiling, elaborating and simulating the design.
#### write_xsim_coverage
Use the `write_xsim_coverage` command to save the in-memory coverage data collected during a simulation run to persistant files on the disk. Once saved, the coverage databases can be used with `export_xsim_coverage` or the standalone `xcrg` tool to generate coverage reports.

> [!important]
> This command must be executed from the Tcl Console while the simulation
> session is still active. Closing the simulation discards any unsaved
> coverage data.

A single invocation writes both the functional coverage database and the code coverage database (when applicable).

Code coverage data is only available when the design has been elaborated with one or more code coverage switches in `xelab` (e.g. -cc_type sbct).

Functional coverage data is generated automatically when the design contains SystemVerilog functional coverage constructs such as covergroup and coverpoint. No additional elaboration switches are required.
#### export_xsim_coverage
This command is used to generate coverage reports from previously saved coverage databases. It reads the databases written by `write_xsim_coverage` and produces HTML/text reports for both functional coverage and code coverage.

> [!info]
> Supports merging databases from multiple simulation runs into a single
> consolidated report.

## Advanced Verification Features
### UVM Support
Vivado supports UVM in xsim. UVM ver 1.2 is precomplied and is available wiht Vivado. No need to set anything except for standealone Vivado simulator where you have to pass `-L uvm` to `xvlog` and `xelab` command.

If you want to use UVM ver 1.1, you can pass `-uvm_version 1.1` to `xvlog` and `xelab`.
### Code Coverage Support
Code coverage measures how thoroughly a testbench exercises the RTL design. When enabled, the Vivado simulator automatically collects coverage data into a coverage database.

Vivado supports four main coverage types:
- Line/Statement coverage — tracks which statements execute and how many times.
- Branch coverage — tracks paths through if/else, if/elseif/else, case/switch, and ternary operators. It can also flag missing else and missing default cases.
- Condition coverage — tracks how often conditions are evaluated and whether they evaluate to true or false.
- Toggle coverage — tracks value transitions on signals and variables, including packed/unpacked reg, bit, logic, wire, integer types, and non-dynamic structure members.

The xcrg (Xilinx Coverage Report Generator) standalone tool reads the coverage database and can:
- Generate HTML coverage reports and dashboard views.
- Show coverage by file, module, or hierarchical instance.
- Merge coverage from multiple simulation runs, allowing several test cases to contribute to an overall coverage result.

In short: Vivado collects coverage during simulation, and xcrg analyzes/report/merges the resulting coverage data to show how completely your testbench exercises the RTL.
#### Code Coverage Exclusion Support
To prevent certain signals or code sections from appearing in an **xsim coverage report**, provide an **exclusion file** to `xcrg`:

```tcl
xcrg ... -ccExclusionFile <file>
```

The exclusion file can filter several object types:
- `signal`
- `instance`
- `module`
- `directory`
- `file`

The syntax is:

```tcl
<type> -<pattern>    # Exclude matching objects
<type> +<pattern>    # Include matching objects
```

For example:

```tcl
signal -wd* +wdDataForInput
```

means:

> **Exclude all signals whose names begin with `wd`, but make an exception and include `wdDataForInput`.**

So `-` specifies **exclusion**, while `+` specifies **inclusion/re-inclusion**.

## SystemVerilog Support
### Running SystemVerilog in Standalone Mode
A new -sv flag is available with xvlog to read a SystemVerilog file, use as follows:

```tcl
xvlog -sv <Design file list>
xvlog -sv -work <LibraryName> <Design File List>
xvlog -sv -f <FileName> [Where FileName contain path of test cases]
```

### Testbench Feature
Not all testbench features are supported. For details, check the documentation from [UG900](https://docs.amd.com/r/en-US/ug900-vivado-logic-simulation/Test-Bench-Feature)
