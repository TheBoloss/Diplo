![](assets/Logo256.png)
# Diplo Language

----

# Principle and operation

Diplo language works with pointer and values.

- [Interpreter](Interpreter.md) creates an array of 65536 cases.
- Each case has its own value that can be changed in the program (0 by default). The pointer designates the selected case.

**Diplo is not case sensitive, so ```INSERT``` is the same as ```Insert``` or ```insert```.**

# Pointer statements

By default, pointer is initialized to 0.

Minimum value is 0 and maximum value is 65535.

Pointer statements begin with ```Ptr```.

## Increment or decrement pointer

### Add/remove 1

Use ```Ptr +``` to add 1 or ```Ptr -``` to remove 1.

```jsx
Ptr +
Ptr -
```

### Add/remove custom

Use ```Ptr +N``` to add N or ```Ptr -N``` to remove N, with N integer.

```jsx
Ptr +3
Ptr -5
```

## Set pointer to specific

Use ```Ptr N``` to set pointer to N, with N integer between 0 and 65535.

```jsx
Ptr 32
```


# Value statements

This section shows how to change the pointed value.

By default, value is initialized to 0.

Minimum value is 0 and maximum value is 255.

Value statements begin with ```Insert```.

## Increment or decrement value

### Add/remove 1

Use ```Insert +``` to add 1 or ```Insert -``` to remove 1.

```jsx
Insert +
Insert -
```

### Add/remove custom

Use ```Insert +N``` to add N or ```Insert -N``` to remove N, with N integer.

```jsx
Insert +3
Insert -5
```

## Set value to specific

Use ```Insert N``` to set value to N, with N integer between 0 and 255.

```jsx
Insert 32
```

# Console statements

## Out statement

Use ```Out```.

Prints the corresponding ASCII character of pointed value to the console.

```jsx
Insert 97
Out
```

## Get statement

Use ```Get```.

Prompt user for a character in the console.

```jsx
Get
Insert +
Out
```

# Loop statements

Loop statements are 3 parts:
- Opening with ```Begin <LoopName> [Arguments]```
- Loop content
- Closing with ```End <LoopName>```

## If

Use if loop with ```If```.

Executes content if pointed value is different from 0.

```jsx
Begin If
    Insert 0
End If
```

## If not

Use if not loop with ```IfNot```.

Executes content if pointed value is equal to 0.

```jsx
Begin IfNot
    Insert +
End IfNot
```

## Repeat

Use repeat loop with ```Repeat N```, with N positive integer.

Executes the content N times.

```jsx
Begin Repeat 10
    Insert +
    Out
End Repeat
```

## Stretch

Use stretch loop with ```Stretch N M```, with N and M positive integers.

Goes from N pointer to M pointer and execute content.

```jsx
Begin Stretch 0 5
    Out
End Stretch
```

# Beside-execution statements

Beside-execution statements start with ```#```. They are used to set parameters about program execution.

- ## ```#TITLE <Name>```
    Sets the program title to \<Name>.
    ```jsx
    #TITLE Diplo program!
    ```
- ## ```#DEBUG```
    Enables execution debug.
    ```jsx
    #DEBUG
    ```
- ## ```#DMPMEM```
    Dumps program data array to ```./diplo_dump.json``` file.
    
    **⚠️ Warning: the ```#DEBUG``` beside-execution statement has to be specified before any ```#DMPMEM```.** 
    ```jsx
    #DEBUG
    Insert +
    #DMPMEM
    ```
- ## ```#EXECTIME```
    Prints the execution time at the end of the program.
    ```jsx
    #TITLE Diplo program!
    ```

# Comments

Use ```//``` to comment your code.

```jsx
Insert 97 // 'a' in ASCII
Out // Display pointed value
```

# Program examples

- ## Print entire alphabet
    ```jsx
    Insert 97
    Begin Repeat 26
        Out
        Insert +
    End Repeat
    ```


---

2022. Eugène Villotte *([TheBoloss](https://github.com/TheBoloss))*