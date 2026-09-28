---
id: Data_Structures_101
aliases: []
tags: []
---
## Tcl Lists

A **list** is one of Tcl's fundamental data structures. It is an ordered collection of elements. Elements can be numbers, words, strings, or even other lists.

Tcl commands themselves have a list-like structure: the first word is the **command name**, and the remaining words are its **arguments**.

### Creating Lists

#### Directly

A variable can be assigned a valid list:

```tcl
set lst {{item 1} {item 2} {item 3}}
```

This creates a list containing three elements:

```text
item 1
item 2
item 3
```

#### `list`

```tcl
set lst [list "item 1" "item 2" "item 3"]
```

Syntax:

```tcl
list ?arg1? ?arg2? ... ?argN?
```

`list` constructs a valid Tcl list from its arguments. It automatically handles the quoting/escaping necessary to keep each argument as one list element.

#### `split`

```tcl
set lst [split "item 1.item 2.item 3" "."]
```

Result:

```tcl
{item 1} {item 2} {item 3}
```

Syntax:

```tcl
split string ?splitChars?
```

`split` breaks a string wherever any character in `splitChars` occurs. If `splitChars` is omitted, it defaults to whitespace.

Each character in `splitChars` acts as an **individual separator**. It is not treated as one multi-character delimiter.

For example:

```tcl
split "1234567" "36"
```

Both `3` and `6` are separators, producing:

```tcl
12 45 7
```

### Accessing List Elements

Use `lindex`:

```tcl
lindex $lst 0
```

Syntax:

```tcl
lindex list index
```

List indices start at **0**:

```text
index 0 → first element
index 1 → second element
index 2 → third element
```

For example:

```tcl
set lst [list apple banana cherry]

puts [lindex $lst 0]   ;# apple
puts [lindex $lst 1]   ;# banana
puts [lindex $lst 2]   ;# cherry
```

### Getting the List Length

Use `llength`:

```tcl
llength $lst
```

It returns the number of elements in the list.

```tcl
set lst [list apple banana cherry]
puts [llength $lst]
```

Output:

```text
3
```

### Iterating with `foreach`

The basic form is:

```tcl
foreach varname list {
    body
}
```

`foreach` executes `body` once for every element in the list. On each iteration, the next element is assigned to `varname`.

Example:

```tcl
set lst [list apple banana cherry]

foreach item $lst {
    puts $item
}
```

Output:

```text
apple
banana
cherry
```

### Taking Multiple Elements per Iteration

`foreach` can assign multiple elements at once:

```tcl
foreach {a b} $listOfPairs {
    # ...
}
```

For example:

```tcl
set values {a 1 b 2 c 3}

foreach {letter number} $values {
    puts "$letter = $number"
}
```

Output:

```text
a = 1
b = 2
c = 3
```

Each iteration consumes **two elements** because two variables were specified.

### Iterating Over Multiple Lists

`foreach` can also iterate through multiple lists simultaneously:

```tcl
foreach a $listOfA b $listOfB {
    # ...
}
```

For example:

```tcl
set names {Alice Bob Charlie}
set scores {90 85 95}

foreach name $names score $scores {
    puts "$name: $score"
}
```

This processes corresponding elements from the lists together.

### Quick Reference

| Command | Purpose |
|---|---|
| `list` | Construct a Tcl list from arguments |
| `split` | Split a string into a list |
| `lindex` | Retrieve an element by index |
| `llength` | Get the number of elements |
| `foreach` | Iterate through list elements |

**Key idea:** Tcl lists are structured collections of elements, not merely strings separated by spaces. Commands such as `list`, `lindex`, `llength`, and `foreach` operate according to Tcl's list syntax and preserve elements that contain spaces.

## Tcl Lists: Adding, Replacing, and Removing Elements

Tcl provides several commands for modifying lists:

| Command | Purpose |
|---|---|
| `concat` | Combine multiple lists/elements into one list |
| `lappend` | Append elements to a list variable |
| `linsert` | Insert elements at a specific position |
| `lreplace` | Replace or delete a range of elements |
| `lset` | Change an element directly |

### `concat` — Combine Lists

Syntax:

```tcl
concat ?arg1 arg2 ... argN?
```

`concat` combines its arguments into a **single list**.

If an argument is itself a list, its elements are incorporated into the resulting list rather than keeping the entire argument as one nested element.

```tcl
set a {1 2 3}
set b {4 5 6}

set result [concat $a $b]
puts $result
```

Result:

```text
1 2 3 4 5 6
```

This differs from `list`:

```tcl
list {1 2 3} {4 5 6}
```

produces a list containing **two elements**:

```text
{1 2 3} {4 5 6}
```

while:

```tcl
concat {1 2 3} {4 5 6}
```

produces a flat list containing **six elements**:

```text
1 2 3 4 5 6
```

`concat` also removes unnecessary leading/trailing whitespace and places appropriate separators between the combined arguments.

---

### `lappend` — Append Elements

Syntax:

```tcl
lappend listName ?arg1 arg2 ... argN?
```

`lappend` appends each argument as a **new list element** and modifies the specified variable.

```tcl
set numbers {1 2 3}

lappend numbers 4 5

puts $numbers
```

Result:

```text
1 2 3 4 5
```

Each argument becomes exactly one element:

```tcl
set lst {1 2}
lappend lst "hello world"
```

Result:

```text
1 2 {hello world}
```

The string `hello world` remains **one element**, despite containing a space.

---

### `linsert` — Insert Elements

Syntax:

```tcl
linsert list index arg1 ?arg2 ... argN?
```

`linsert` returns a **new list** with the supplied elements inserted **before** the specified index.

```tcl
set numbers {10 20 30 40}

set result [linsert $numbers 2 25]
```

Result:

```text
10 20 25 30 40
```

The new value `25` is inserted before the element at index `2` (`30`).

Special cases:

- `index <= 0` → insert at the beginning.
- `index >= list length` → append to the end.
- `index == end` → append to the end.

Unlike `lappend`, `linsert` does **not modify the variable automatically**:

```tcl
set lst [linsert $lst 2 newElement]
```

is needed if you want to save the result.

---

### `lreplace` — Replace or Delete Elements

Syntax:

```tcl
lreplace list first last ?arg1 ... argN?
```

`lreplace` returns a **new list** where elements from index `first` through `last` are replaced by the supplied arguments.

For example:

```tcl
set lst {A B C D E}

set result [lreplace $lst 1 3 X Y]
```

The elements:

```text
B C D
```

are replaced by:

```text
X Y
```

Result:

```text
A X Y E
```

The number of replacement elements does **not** have to equal the number of removed elements.

#### Deleting Elements

If no replacement arguments are supplied, `lreplace` effectively deletes elements:

```tcl
set lst {A B C D E}

set lst [lreplace $lst 1 2]
```

Result:

```text
A D E
```

Therefore, `lreplace` can be used for both **replacement and deletion**.

---

### `lset` — Modify an Element Directly

Syntax:

```tcl
lset varName index newValue
```

`lset` directly modifies an element of a list stored in a variable.

```tcl
set lst {A B C D}

lset lst 2 X

puts $lst
```

Result:

```text
A B X D
```

This is simpler than using `lreplace` when changing a single element.

For example:

```tcl
lset lst 2 X
```

is more convenient than:

```tcl
set lst [lreplace $lst 2 2 X]
```

---

## When to Use Tcl Lists

Use a **list** when:

- You have an arbitrary number of values.
- The **order** of those values matters.
- You want to access values by position.
- You want to iterate over the values using `foreach`.

For example:

```tcl
set registers {x0 x1 x2 x3 x4}

puts [lindex $registers 2]
```

Result:

```text
x2
```

Conceptually, Tcl lists often fill the role that **arrays/vectors** fill in languages such as C:

```c
int values[5];
values[2];
```

roughly corresponds conceptually to:

```tcl
set values {10 20 30 40 50}
lindex $values 2
```

However, a Tcl **array** means something different. Tcl arrays are **associative arrays** (key-value mappings), similar to hash tables or dictionaries, rather than C-style numerically indexed arrays.

Therefore:

```text
C array/vector             ≈ Tcl list
C hash table/map           ≈ Tcl array (or Tcl dict)
```

## Important: List Elements and Spaces

A Tcl list element can itself contain spaces:

```tcl
set lst [list "hello world" "foo bar" "test"]
```

This is a list of **three**, not five, elements:

```text
Element 0: hello world
Element 1: foo bar
Element 2: test
```

Tcl may display it as:

```text
{hello world} {foo bar} test
```

The braces indicate that the grouped characters constitute a **single list element**.

This distinction is fundamental: a Tcl list is not simply a string whose elements are separated by spaces. Tcl's list syntax determines how characters are grouped into individual elements.

## Tcl Lists: Searching, Sorting, and Extracting Ranges

Tcl provides several commands for querying and manipulating lists:

| Command | Purpose |
|---|---|
| `lsearch` | Search for an element and return its index |
| `lsort` | Sort the elements of a list |
| `lrange` | Extract a range of elements |

### `lsearch` — Search a List

Syntax:

```tcl
lsearch list pattern
```

`lsearch` searches through a list and returns the **index of the first matching element**.

If nothing matches, it returns `-1`.

```tcl
set lst {apple banana cherry banana}

puts [lsearch $lst banana]
```

Result:

```text
1
```

Only the index of the **first** match is returned.

If there is no match:

```tcl
lsearch $lst orange
```

Result:

```text
-1
```

By default, `lsearch` performs **glob-style pattern matching**, so wildcard characters can be used:

```tcl
set lst {apple banana apricot cherry}

lsearch $lst "a*"
```

Result:

```text
0
```

`a*` means "starts with `a`", so `apple` is the first match.

---

### `lsort` — Sort a List

Syntax:

```tcl
lsort list
```

`lsort` returns a **new sorted list**. By default, elements are sorted lexicographically (dictionary-like string ordering).

```tcl
set lst {banana apple cherry}

puts [lsort $lst]
```

Result:

```text
apple banana cherry
```

Importantly, `lsort` does **not modify the original variable**:

```tcl
set lst {banana apple cherry}

lsort $lst

puts $lst
```

`lst` is still:

```text
banana apple cherry
```

To update the variable, assign the result back:

```tcl
set lst [lsort $lst]
```

This pattern is common with Tcl list commands:

```tcl
set variable [command $variable ...]
```

because many list commands **return a new list rather than modifying the existing variable**.

---

### `lrange` — Extract Part of a List

Syntax:

```tcl
lrange list first last
```

`lrange` returns a new list containing elements from index `first` through index `last`, **inclusive**.

```tcl
set lst {A B C D E F}

lrange $lst 1 3
```

Result:

```text
B C D
```

because:

```text
Index:    0 1 2 3 4 5
Element:  A B C D E F
            └─────┘
             1..3
```

The special index `end` refers to the last element:

```tcl
lrange $lst 2 end
```

Result:

```text
C D E F
```

If `first <= 0`, the range starts from the beginning:

```tcl
lrange $lst -5 2
```

Result:

```text
A B C
```

If `last` is beyond the end of the list, it is treated as the last element:

```tcl
lrange $lst 3 100
```

Result:

```text
D E F
```

If `first > last`, an empty list is returned:

```tcl
lrange $lst 4 2
```

Result:

```text
{}
```

### Quick Reference

```tcl
# Search for first matching element
set index [lsearch $lst pattern]

# Sort a list and save the result
set lst [lsort $lst]

# Extract elements from index 2 through 5
set subset [lrange $lst 2 5]

# Extract from index 2 through the last element
set subset [lrange $lst 2 end]
```

**Key idea:** `lsearch` finds the position of an element, while `lsort` and `lrange` produce new lists rather than modifying the original list variable.

