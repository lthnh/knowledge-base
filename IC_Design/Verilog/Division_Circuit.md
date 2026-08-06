---
id: Division_Circuit
aliases: []
tags: []
---
For unsigned numbers, division could be implemented using series of iterative subtractors. The idea is we multiply the divisor by an mount by shifting it left. The maximum amount is determined by aligned the least significant digit of the divisor with the most significant bit of the dividend (?). In this architecture, the borrow out bit can be used to indicate the quotient. But pay attention as the borrow out is one when the subtraction result is a negative number (thus, not valid to continue). For the borrow out to be used to the quotient, an inverter is added. The borrow out can also be used as a control signal for multiplexers to decide whenever to pass the interim dividend (when quotient is 0) or the current subtraction result to the next stage (when quotient is 1). 

For division by 2, we can shift the value right. Beware of inaccuracy when trying to divide a odd number by two by shifting.

For signed numbers, a similar strategy to multiplication is adopted.

