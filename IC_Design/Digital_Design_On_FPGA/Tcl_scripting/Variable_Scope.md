---
id: Variable_Scope
aliases: []
tags: []
---
`global` command will make a variable in a local scope (inside a procedure) to refer to the global variable of that name.
`upvar` "ties" the name of the variable in the current scope to a different scope. Commonly used to simulate pass-by-reference to `proc`s.
There is also a `variable` command which is a part of the namespace system.

Tcl uses a type of garbage collection called reference counting to automatically clean up variables when they are not used anymore. You can explicitly unset by using `unset` command.

`upvar` syntax is `upvar ?level? otherVar1 myVar1 ?otherVar2 myVar2? ... ?otherVarN myVarN?` with *myVar1* becoming reference to *otherVar1*, *myVar2* becoming reference to *otherVar2*, and so on...

By default, level is 1 which is the next level up. If a number is used, then level referecences that many levels up the stack from the current level. If the level number is preceded by a # symbol, it references that many levels down from the global scope (e.g. if the level is #0, it references the global scope).

And of course, as every other programming languages, avoid using global variables where applicable.

