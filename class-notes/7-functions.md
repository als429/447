# Functions

## What's a calling convention? 
* we need rules for humans
* it ensures our programs don't trip over their own feet
* every function in your program must share the same registers
* how machine language functions call one another
  * how arguments are passed (a-registers)
  * how return values are returned (v-registers)
  * how control flows into/out of the function
  * what contracts exist between the caller and callee


## Program Counter (PC)
* a programs instructions are in memory, so they have addresses
* the PC holds the address of the **next instruction to run**
* each instructions are 4 bytes, one word
* 0, 4, 8, C <- multiples of 4 in bits

* side note: if a branch instruction is false, it just goes to the next instruction

### MIPS ISA
* `jal`: jump and link; what we use for f(x) calls
* a jump is just assigning a different address value in **pc** register
  * we still have to remember where we are... (we use the ra register to remember what instruction we need to run after the instruction)
* links back to the old one in the **ra** (return address) register



# Questions
* How do we keep track of a0?
* 
