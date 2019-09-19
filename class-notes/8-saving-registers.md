# Saving Registers

* both registers are trying to use t0 for different purposes (overwriting; **smashing register**) 
* a caller cannot depend on the t, a, or v registers to have the same values after a `jal` as before it
  * callees are allowed to trash those registers 
* if you want something to stick around DON'T use a temporary registers

| saved | unsaved |
|:-----:|:-------:|
| s0-s7 |  v0-v1  |
|   sp  |  a0-a3  |
|   ra  |  t0-t9  |

* functions are required to put saved registers back the way they were before they were called
* anyone can change the unsaved registers
  * after you call a function, they might have totally different values from before you called it
* the `jal` draws a line, the unsaved calls are bogus 
  * instead use an **s registers**
* **s0** should be our loop counter

## The **s register** contract
* if your function wants to use an s register, you **must save and restore** it (just like **ra**)
  * `push s0` and `pop sa`

## Dealing with a0

* in method, `push s1`, `move s1, a0`, and then at the end `pop s1`
  
```
func:
  push ra
  push s0
  push s1 # for defense
  move s1, a0
  
  
  pop s1 
  pop s0 # MUST pop in reverse order!!
  pop ra
  jr ra 

```

* note: not every label is a function
* only put pushes and pops at the beginning and the end
* you only need to use pushes and pops when `jal` appears
* you must always pop the same number of registers that you push.
* to make this simpler for yourself… make a label before the pops
  * then you can leave the function by jumping/branching there
* how to return early?
  * do not copy and paste pops, never return from entire functions use labels for the end of the function `j _end_of_argument_var`
  * do not jump from one function to another

```
my_func:
	push ra
	push s0
	...
	bge ...
	j _exit_func
	...
_exit_func: # this label only applies to this function
	pop  s0
	pop  ra
	jr   ra
```

# Pseudo-ops - an FYI
* many of the instructions, don't actually exist
   * Mars help (f1) "Extended (pseudo) instructions* 
   * they're convenient shorthand for common operations 
* the assembler translates them in real MIPS
* the **at register** never touch it



# Debugging
* 
* 
*
* 
