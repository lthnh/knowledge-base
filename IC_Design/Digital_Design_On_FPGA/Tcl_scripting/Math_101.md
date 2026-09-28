---
id: math-101
aliases: []
tags: []
---
## Should we wrap and not wrap arguments to `expr`
Tcl command for doing math type operations is `expr`.

Many commands use `expr` behind the scenes in order to evaluate test expressions (e.g. `if`, `while` and `for` loops). All of the advice given for `expr` also holds for these commands.

Enclosing arguments to `expr` in curly braces will result in
- faster code
- safer code since wrapping argument between curly braces will prevent user input from being evaluated
## Operands
Integer values can be specified in decimal (normal case), in octal (if the first character of the operand is 0), or in hexadecimal (if the first two characters of the operand are 0x).

The way octal and hexadecimal conversion are handled is different in `expr` command than in the Tcl substitution phrase (e.g. in substitution phrase, a \\**x32** would be converted to an ascii "2" while `expr` would convert **0x32** to a decimal 50).

If the operand is not one of the integer formats, it is treated as a floating-point number if possible. Floating-point numbers can be specified in any ways accepted by an ANSI-compliant C compiler.

If no numeric interpretation is possible, it is left as a string.
It does not support number of the following forms:
- a decimal comma, instead of a decimal point
- a thousands separator
## Operators
Bit-wise NOT (~), remainder (%) may only be applied to integers.

Left shift (<<), right shift (>>), bit-wise AND (&), bit-wise exclusive OR(^), bit-wise OR (|) are valid for integer operands only.

Relation operators (< > = <= >=) can be used for strings.

We also have separate operators for string comparision (eq ne in in).
- eq: equality
- ne: inequality
- in: check if string is in a list
- ni: or not

Remainder will *always* have the same sign as the divisor.

Logical operator AND (&&) and logical OR (||) are valid for numeric operands only.

If-then-else (x ? y : z): x operand must be a numeric value.
## Math functions
|   |   |   |   |
|---|---|---|---|
| abs | acos | asin | atan |
| atan2 | bool | ceil | cos |
| cosh | double | entier | exp |
| floor | fmod | hypot | int |
| isqrt | log | log10 | max |
| min | pow | rand | round |
| sin | sinh | sqrt | srand |
| tan | tanh | wide |    |
## Type conversions
`double int wide entier` with `wide` converts a number to a "wide" integer number (has larger range). `entier` coerces a number of integer of appropriate size to hold it without truncation. Might return `int` or `wide` or int of abitrary size.
## Floating-point errors
Be careful when converting floating-point numbers to integers.
Transcendental functions like `sin` and `exp` are not standardised. We should not use them to estimate $\mu$ but specify a specific value first hand.

