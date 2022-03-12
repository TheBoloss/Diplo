![](Logo256.png)
# Diplo Language

----

# Principle and operation

Diplo language works with pointer and values.

- [Interpreter](Interpreter.md) creates an array of 65536 cases.
- Each case has its own value that can be changed in the program (0 by default). The pointer designates the selected case.

# Pointer statements

By default, pointer is initialized to 0.

Minimum value is 0 and maximum value is 65535.

Pointer statements begin with ```PTR```.

## Increment or decrement pointer

### Add/remove 1

Use ```PTR +``` to add 1 or ```PTR -``` to remove 1.

```jsx
PTR +
PTR -
```

### Add/remove custom

Use ```PTR +N``` to add N or ```PTR -N``` to remove N, with N integer.

```jsx
PTR +3
PTR -5
```

## Set pointer to specific

Use ```PTR N``` to set pointer to N, with N integer between 0 and 65535.

```jsx
PTR 32
```


# Value statements

This section shows how to change the pointed value.

By default, value is initialized to 0.

Minimum value is 0 and maximum value is 255.

Value statements begin with ```INSERT```.

## Increment or decrement value

### Add/remove 1

Use ```INSERT +``` to add 1 or ```INSERT -``` to remove 1.

```jsx
INSERT +
INSERT -
```

### Add/remove custom

Use ```INSERT +N``` to add N or ```INSERT -N``` to remove N, with N integer.

```jsx
INSERT +3
INSERT -5
```

## Set value to specific

Use ```INSERT N``` to set value to N, with N integer between 0 and 255.

```jsx
INSERT 32
```

# Console statements

## Out statement

Use ```OUT```.

Prints the corresponding ASCII character of pointed value to the console.

```jsx
INSERT 97
OUT
```

## Get statement

Use ```GET```.

Prompt user for a character in the console.

```jsx
GET
INSERT +
OUT
```

# Loop statements

Loop statements are 3 parts:
- Opening with ```BEGIN <LoopName> [Arguments]```
- Loop content
- Closing with ```END <LoopName>```

## If

Use if loop with ```IF```.

Executes content if pointed value is different from 0.

```jsx
BEGIN IF
    INSERT 0
END IF
```

## If not

Use if not loop with ```IFNOT```.

Executes content if pointed value is equal to 0.

```jsx
BEGIN IFNOT
    INSERT +
END IFNOT
```

## Repeat

Use repeat loop with ```REPEAT N```, with N positive integer.

Executes the content N times.

```jsx
BEGIN REPEAT 10
    INSERT +
    OUT
END REPEAT
```

## Stretch

Use stretch loop with ```STRETCH N M```, with N and M positive integers.

Goes from N pointer to M pointer and execute content.

```jsx
BEGIN STRETCH 0 5
    OUT
END STRETCH
```