---
id: Proc
aliases: []
tags: []
---
`proc` can be considered function in this language.
We can specify default values for arguments and override the default values if it's necessary.
To have a variadic function in Tcl, you can use `args` as the last element in arguments list.
As `proc` in Tcl use positional arguments, you can't have a argument without default between `args` and a argument with default value as that default value will never be used.

