---
id: Multiplication_Circuit
aliases: []
tags: []
---
For any multiplication of n-bit inputs, the product is going to be 2*n bits.

When handling signed numbers with unsigned circuit, we need to convert negative number to positive first before doing multiplication. Then depending on the signs of both operands, we either keep the result or take the two's complement of it. 

