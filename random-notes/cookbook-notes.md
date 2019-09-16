# Cookbook Notes

## Strings
* String are many bytes 
  * they can't fit in registers
  * we add them to a `.data` segment
  * refer to strings by their memory addresses (`la`)
  * they are zero terminated
* Single characters *do* fit in registers
  * so we can use `li`

## Variables + globals
* globals are stored in memory
* must declare variables in the `.data`
* to access variables you must use **load instructions** to get its value, and **store instructions** to set its value

## Choosing registers

1. if you're about to **call a function** the **arguments** got into **a** registers (start with **a0**)
2. if you're about to **return a value from a function**, the return value goes into **v0**
3. if you're about to do **a syscall**, the syscall number goes into **v0**
4. ask self: **do I need to access this value again after `jal`?**

4.1 No? --> use a **t** register
  
  * reuse them (especially `t0-t6`

4.2 Yes? --> use an **s** register 

  * common to use these as loop counters and other "local variable" tasks
  * ENSURE YOU: `push` and `pop` them as described below (writing functions)
  
## Writing Functions

1. Start with this skeleton code

```
function_name:
  push ra
  
function_name_end:
  pop ra
  jr ra
```

2. Write code **between the push and pop**
  
  * arguments are already in the **a** registers
  * to return, use **j function_name_end**
  * **DO NOT just throw `jr ra` in the middle of the function**
  * to return a value, put a value in **v0** before returning
  
 3. If you need to use any **s** registers **push them at the beginning** and pop them in reverse order at the end

```
function_name:
  push ra
  push s0
  push s1
  
  li s0, 0 
  li s1, 1 
  
  # ... blah blah...
  
function_name_end:
  # all pops in REVERSE order
  pop s1
  pop s0
  pop ra  
  
  jr ra
```
