## Positional Number Systems

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
## Combinational Logic Design
### Boolean Algebra
There are two valid states (true or false) and three core operations (conjunction $\wedge$ equivalent to AND, disjunction $\vee$ equivalent to OR, and negation $\neg$ equivalent to NOT).
We also use +, $\cdot$, ' instead of the symbol above.
#### Axioms
1. Logical Values: A variable can only take one of two values, 0 or 1 $\rightarrow$ A = 0 or A = 1.
2. Definition of Logical Negation: If A = 0 then A' = 1 and vice versa.
3. Definition of Logical Product: A$\cdot$B = 1 if A = B = 1 and A$\cdot$B = 0 and A$\cdot$B = 0 otherwise.
4. Definition of Logical Sum: A+B = 1 if A = 1 or B = 1 and A+B = 0 otherwise.
5. Logical Precedence: NOT precedes AND, and AND precedes OR unless explicitly stated using parentheses.[^1]
#### Theorems

**De Morgan's Theorem of Duality**
Duality states that an algebraic equality will remain true if all 0's and 1's are interchanged and all AND and OR operations are interchanged.
$\Rightarrow$ This is why Boolean algebra theorems are almost always given in pairs.

When using duality, we should take note of the order of precedence follows original function. For example, with expression $F=A\cdot B+C$. Then the dual of this expression is $F_D=(A+B)\cdot C$.

**Identity**
An identity operation is one that when performed will yield itself regardless of variable's value.

Any variable OR with logic 0 with yield the original variable, likewise when you AND a variable with logic 1.
$\Rightarrow$ Useful for reducing circuitry.

**Null Element**
A null element operation is the one that, when performed on a constant value, will yield that same constant value regardless of any variables within the same operation.

For example, OR'ing any variable with a logic 1 will always yield a logic 1. AND'ing any variable with a logic 0 will always yield a logic 0.
$\Rightarrow$ Useful for both reducing circuitry and change value of a storage element.

**Idempotent**
An idempotent operation is one that has no effect on the input, regardless of the number of times the operation is applied.

OR'ing a variable with itself will result in itself. The same goes for AND.

**Complements**
OR'ing a variable with its complement produce a logic 1. AND'ing a variable with its complement produce a logic 0.
$\Rightarrow$ Useful for reducing circuitry.

**Involution**
Basically double negation.

**Commutative Property**
Changing the order of variables in an OR/AND operation does not change the result.

**Associative Property**
The grouping of variables doesn't impact the result of an OR/AND operation.
Which means

$$
\begin{aligned}
(A+B)+C&=A+(B+C)\\
(A\cdot B)\cdot C&=A\cdot (B\cdot C)
\end{aligned}
$$
$\Rightarrow$ Can be used to address fan-in limitations of a logic family.

**Distributive Property**
An operation on a parenthesized operation(s), or higher precedence operator, will distribute through each term.

$$
\begin{aligned}
A\cdot (B+C)&=A\cdot B+A\cdot C\\
A+(B\cdot C)&=(A+B)\cdot(A+C)
\end{aligned}
$$

$\Rightarrow$ Can be used to put a logic expression in a form suitable for direct circuit synthesis or to reduce the number of gates necessary.

**Absorption**
When a term within a logic expression produces the same output(s) as another term, the second term can be removed without affecting the result.

It is called this way because the remaining term *absorb* the functionality of the eliminated term.

**Uniting**
Also called *combining* or *minimization*.

When a variable (B) and its complement (B') appear in multiple product terms with a common variable (A) within a logical OR operation, the variable B does not have any effect on the result and can be removed.

$$
\begin{aligned}
A\cdot B+A\cdot B'&=A\\
(A+B)\cdot(A+B')&=A
\end{aligned}
$$

**De Morgan's Theorem**
An OR operation with both inputs inverted is equivalent to an AND operation with output inverted.
An AND operation with both inputs inverted is equivalent to an OR operation with output inverted.

$$
\begin{aligned}
A'+B'&=(A\cdot B)'\\
A'\cdot B'&=(A+B)'
\end{aligned}
$$

We can take advantage of this theorem to turn a *sum of products (SOP)* into one that uses only NAND gates. We can also turn a *product of sums (POS)* into one that uses only NOR gates.

#### Functionally Complete Operation Sets
A set of Boolean operators is said to be *functionally complete* when the set can implement all possible logic functions.
The set of operators {AND, OR, NOT} is functionally complete because every other operation can be implemented using these three operators.
De Morgan's theorem shows that AND and OR can be replaced by NAND and NOR.

>[!important]
>NAND and NOR by themselves are functionally complete since they can also implement NOT function.

## Combinational Logic Synthesis
### Canonical Sum of Products
Based on minterms. A minterm must include all literals and will produce a 1 when the input is matched.
This form is often unminimized, and is a starting point for minimization using Boolean algebra.
### Canonical Product of Sums
Based on maxterms. A maxterm must include all literals and will produce a 0 when the input is matched.
This approach is complementary to the sum of products approach. It will produce 0 for each maxterm but 1 for others.
This form is often unminimized, and is a starting point for minimization using Boolean algebra.
## Logic Minimization


[^1]: It is noteworthy that in pure logic algebra book. AND and OR have the same precedence. But in digital IC design people seem to have chosen that AND has higher precedence than OR.
