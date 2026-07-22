## Combinatoric Logic Design
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

We can convert between positive logic and negative logic using duality. The precedence must follow the original precedence of the function.

Formal definition: An algebraic equality will remain true if all 0's and 1's are interchanged, and all AND and OR operations are interchanged. Taking the dual of a positive logic function will produce the equivalent function using negative logic if the original order of precedence is preserved.

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

Any sum of products that is implemented with only AND/OR gates can be replaced by a NAND-only equivalent circuit.
Any product of sums that is implemented with only AND/OR gates can be replaced by a NOR-only equivalent circuit.
#### Functionally Complete Operation Sets
A set of Boolean operators is said to be *functionally complete* when the set can implement all possible logic functions.
The set of operators {AND, OR, NOT} is functionally complete because every other operation can be implemented using these three operators.
De Morgan's theorem shows that AND and OR can be replaced by NAND and NOR.

>[!important]
>NAND and NOR by themselves are functionally complete since they can also implement NOT function.

## Combinatoric Logic Synthesis
### Canonical Sum of Products
Based on minterms. A minterm must include all literals and will produce a 1 when the input is matched.
This form is often unminimized, and is a starting point for minimization using Boolean algebra.
### Canonical Product of Sums
Based on maxterms. A maxterm must include all literals and will produce a 0 when the input is matched.
This approach is complementary to the sum of products approach. It will produce 0 for each maxterm but 1 for others.
This form is often unminimized, and is a starting point for minimization using Boolean algebra.
## Logic Minimization
We can do this with Karnaugh maps to find either sum of products or product of sums.
### Timing hazards and Glitches
There are two types:
- Static hazard
	- Static 0 timing hazard is when input switches between two input codes that both yield an output of 0 but momentarily switches to 1.
	- Static 1 timing hazard is when input switches between two input codes that both yield an output of 1 but momentarily switches to 0.
- Dynamic hazard: when input switches between two input codes that results output transition but momentarily glitches before reaching its final value.
Can add additional circuitry to avoid these timing problems. One example of this would be adding non-prime essential prime implicant (i.e. use complete sum instead of minimal sum).[^1]

[^1]: A complete sum is an expression that includes every possible prime implicants.
