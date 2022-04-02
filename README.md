<img src="assets/Banner.png" width="100%">

# Diplo Language
---

## Table of contents
- [Documentation](#documentation)
    - [Principle and operation](#principle-and-operation)
    - [Format](#format)
    - [Pointer statements](#pointer-statements)
    - [Value statements](#value-statements)
    - [Console statements](#console-statements)
    - [Exit statement](#exit-statement)
    - [Comparisons](#comparisons)
    - [Labels and jumps](#labels-and-jumps)
    - [Comments](#comments)
- [Program examples](#program-examples)
    - [Hello World](#hello-world)

# Documentation

## Principle and operation

Diplo language works with pointer and values.

- [Interpreter](Interpreter.md) creates an array of 65536 cases.
- Each case has its own value that can be changed in the program (0 by default). The pointer designates the selected case.

**Diplo is not case sensitive, so ```INSERT``` is the same as ```Insert``` or ```insert```.**

## Format

Statements can take arguments as follow:

```<Required> [Optional1|Optional2]```

```diplo
<Statement> [Arg1], [Arg2], ...
```

## Pointer statements

By default, pointer is initialized to 0.

Minimum value is 0 and maximum value is 65535.

### Syntax

```diplo
Pointer <AbsoluteValue|RelativeValue>
```

- With ```AbsoluteValue``` unsigned integer.
- With ```RelativeValue``` '+' or '-' + [unsigned integer].

### Example

```diplo
Pointer 10  // Sets pointer to 10
Pointer 0   // Set pointer to 0

Pointer +   // Adds 1 to pointer (increments pointer)
Pointer +2  // Adds 2 to pointer

Pointer -   // Removes 1 to pointer (decrements pointer)
Pointer -5  // Removes 5 to pointer
```

## Value statements

This section shows how to change the pointed value.

By default, value is initialized to 0.

Minimum value is 0 and maximum value is 255.

### Syntax

```diplo
Insert <AbsoluteValue|RelativeValue>
```

- With ```AbsoluteValue``` unsigned integer.
- With ```RelativeValue``` as follow:
    - ```+n``` to add ```n``` to value
    - ```-n``` to remove ```n``` to value
    - ```*n``` to multiply value by ```n```
    - ```/n``` to divide value by ```n``` (integer division)
    - ```%n``` to set value to value modulo ```n```

Changes the pointed value.

### Insert a list of values

```diplo
InsertL <AbsoluteValue1>, [AbsoluteValue2], [...]
```

- With ```AbsoluteValue1```, ```AbsoluteValue2```... unsigned integers.

Changes to pointed value to ```AbsoluteValue1``` and next pointed value to ```AbsoluteValue2```, etc...

### Example

```diplo
Insert 10  // Sets value to 10
Insert 0   // Sets value to 0

Insert +   // Adds 1 to value (increments value)
Insert +2  // Adds 2 to value

Insert -   // Removes 1 to value (decrements value)
Insert -5  // Removes 5 to value

Insert *2  // Multiplies pointed value by 2
Insert /2  // Divides
Insert %2  // Sets value to value%2

InsertL 97, 98, 99 // Sets pointed then next values to 'a', 'b' and 'c' -> "abc"
```

## Console statements

### ```Out``` statement

Prints the corresponding [ASCII](https://www.asciitable.com/) character of pointed value to the console.

#### Syntax

```diplo
Out
```

#### Example

```diplo
Insert 97
Out
// Prints 'a'
```

### ```Get``` statement

Prompt user for a character in the console and puts it into pointed value.

#### Syntax

```diplo
Get
```

#### Example

```diplo
Get
Out
// Prints the character user entered.
```

## Exit statement

### Syntax

```diplo
Exit <ErrorCode>
```

With ```ErrorCode``` integer corresponding to program exit code.

### Example

```diplo
Exit 0
// No error
```

## Comparisons

Compares 2 values.

Comparison result can be used in **Conditional jumps** (see below).

### Syntax

```diplo
Comp <Value1>, <Value2>
```

With ```Value1``` and ```Value2``` integers or **variables**.

### Variables

- ```$value``` returns the pointed value.
- ```$pointer``` returns the pointer value.

### Example

```diplo
Comp $value, 97
JumpGreaterEq isLetter
Exit 0

Label isLetter
// Code if is letter
```

## Labels and jumps

Labels can be defined to mark a specific place in the program and to create loops.

### Syntax

```diplo
Label <LabelName>
```

Defines the label '\<LabelName>'.

With ```LabelName``` char string containing only [a-z A-Z 0-9].

```diplo
Jump <LabelName>
```

Jumps to label '\<LabelName>'.

#### Conditional jumps

*Using ```a``` and ```b``` as arguments of last condition:*

-
    ```JumpEq <LabelName>```
    Jumps to label '\<LabelName>' if a == b.

-
    ```JumpNotEq <LabelName>```
    Jumps to label '\<LabelName>' if a != b.

-
    ```JumpGreater <LabelName>```
    Jumps to label '\<LabelName>' if a > b.

-
    ```JumpGreaterEq <LabelName>```
    Jumps to label '\<LabelName>' if a >= b.

-
    ```JumpLess <LabelName>```
    Jumps to label '\<LabelName>' if a < b.

-
    ```JumpLessEq <LabelName>```
    Jumps to label '\<LabelName>' if a <= b.


### Example

```diplo
Insert 97
Label loop
    Out
Jump loop
// Prints 'a' forever.
```

## Comments

Use ```//``` to comment your code.

### Example

```diplo
Insert 1
// This is a comment!
```

# Program examples

- ## Hello World
    ```diplo
    // Register "Hello World!"
    InsertL 72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100, 33

    // Print char until string ends (0x00)
    Label PrintLoop
        Out
        Pointer +
        Comp $value, 0
    // If string does not end, prints the next char
    JumpNotEq PrintLoop
    // Exits program properly
    Exit 0
    ```

---

<img src="assets/Logo256.png" width="50">

2022. Eugène Villotte *([TheBoloss](https://github.com/TheBoloss))*