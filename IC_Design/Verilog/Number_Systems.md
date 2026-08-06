---
id: Number_Systems
aliases: []
tags: []
---
## Positional Number Systems
A positional number system allows the expansion of the original set of symbols to represent any arbitrarily large (or small) value.

In the formation of a number system, the first thing to be considered is the set of symbols (e.g 0, 1). The term for one of the symbols in a number system is a *numeral*. One or more numerals are used to form a *number*.
The number of numerals in a system is termed *radix* or *base*.
### Generic Structure
The *radix point* is the point within a number to which numerals to the left represent whole numbers and numerals to the left represent fractional numbers.
If a number has this radix point, we call it *fixed-point number* since it can't be moved once its location is determined.
The *position* of each numeral with respect to the radix point determines its value in a number. Starting from the radix point, the number to the left is counted from 0 and onward. The number to the right is counted from -1 and downward.
The term digit signifies that the numeral has a position. Sometime its position is denoted as a subscript of the digit itself.
### Binary Number System
A nibble consists of 4 bytes.
A byte consists of 8 bytes.
Larger groupings of bits are called words.
### Binary Arithmetic
### Addition
The largest decimal sum that can result from the addition of two binary numbers is $2(2^n-1)$.
The largest sum achievable would only require one additional bit. This means a single addition bit is sufficient to handle all possible magnitudes for binary addition.
### Subtraction
If the most significant bit requires a borrow, this event is called a *borrow in*. This is handled by a separate circuit.
### Arithmetic with Two's Complement
To ensure proper results,
- First, any carry or borrow that is generated is ignored.
- Second, always check if two's complement overflow has occurred.
	- The sum of like signs results in an answer with opposite sign.
	- The subtraction of positive number from a negative number results in a positive number.
	- The subtraction of negative number from a positive number results in a negative number.
This requires dedicated logic to monitor these signs and let the operator know if overflow has occurred.
## Negative Number Representation in Binary
The most common one is two's complement. We will complement each bit then add one. For n-bit number, this is also equivalent to take that number and subtract it from $2^n$.
$\rightarrow$ The most significant bit is still sign bit (0 = positive, 1 = negative).
$\rightarrow$ All the negative numbers are shifted up by 1 so the double 0 gap from signed magnitude representation and one's complement is eliminated.

The range of two's complement number is

$$
-2^{n-1}\leq N \leq 2^{n-1}-1
$$

For positive number, we convert to decimal like normal.
For negative number, we must first complement the number then add 1 to it.

![[example-neg-num-to-dec.png|500]]

When doing arithmetic with two's complement. We should beware of *overflow*.
This can occurs when
- The sum of like signs results in an answer with opposite sign.
- The subtraction of a positive number from a negative number results in a positive number.
- The subtraction of a negative number from a positive number results in a negative number.



[^1]: It is noteworthy that in pure logic algebra book. AND and OR have the same precedence. But in digital IC design people seem to have chosen that AND has higher precedence than OR. In pure mathematical sense, there is not settled consensus on the precedence of these operations. So it is better to add explicit parentheses to ensure that we don't misunderstand the logic function or depend on any convention.
