# MIPS
# 1.1 Instruction Set Architecture

## How do we program a processor?
 * high level language (must) -> compiler (which converts to) -> assembly code (which then translates into) -> machine code
    * assembly = instructions for the processor
    
## What does the processor do?
  * what do we have:
      * memory (big and slow)
      * current instruction
      * data registers: can hold a bit of data to work on (small and fast)
      * computations: is told by control what data (from data registers) to use 
      * control: decodes the instruction to tell the processor what to do (the brains)
      
 
# 1.2 MIPS instructions
## Format
* operation destination, source1, source2
    * e.g.:
        * `add a, b, c`  # a = b + c
        * `addi a, b, 12 ` # a = b + 12 
            * note: add immediate only needs two source registers
        * `sub a, b, c` # a = b - c
* to do complex operations, must break into steps (and use temporary registers)


## Instructions

| Function                   | Instruction        | Effect                                   |
|----------------------------|--------------------|------------------------------------------|
| add                        | `add r1, r2, r3`   | r1 = r2 + r3                             |
| subtract                   | `sub r1, r2, r3`   | r1 = r2 - r3                             |
| add immediate              | `addi r1, r2, 145` | r1 = r2 + 145                            |
| multiply                   | `mult r2, r3`      | hi, lo = r1 * r3                         |
| divide                     | `div r2, r3`       | low = r2/r3, hi = remainder              |
|----------------------------|--------------------|------------------------------------------|
| and                        | `and r1, r2, r3`   | r1 = r2 & r3                             |
| or                         | `or r1, r2, r3`    | r1 = r2 | r3                             |
| and immediate              | `and r1, r2, 145`  | r1 = r2 & 145                            |
| or immediate               | `or r1, r2, 145`   | r1 = r2 | 145                            |
| shift left logical         | `sll r1, r2, 7`    | r1 = r2 << 7                             |
| shift right logical        | `srl r1, r2, 7`    | r1 = r2 >> 7                             |
|----------------------------|--------------------|------------------------------------------|
| load word                  | `lw r1, 145(r2)`   | r1 = memory[r2 + 145]; 145 is the offset |
| store word                 | `sw r1, 145(r2)`   | memory[r2 + 145] - r1                    |
|----------------------------|--------------------|------------------------------------------|
| load upper immediate       | `lui r1, 145`      | r1 = 145 << 16                           |
| branch on equal            | `beq r1, r2, 145`  | if (r1 == r2) go to PC + 4 + 145*4       |
| brand on not equal         | `bne r1, r2, 145`  | if (r1 != r2) go to PC + 4 + 145*4       |
| set on less than           | `slt r1, r2, r3`   | if (r2 < r3) r1 = 1, else r1 = 0         |
| set on less than immediate | `slt r1, r2, 145`  | if (r2 < 145) r1 = 1, else r1 = 0        |
|----------------------------|--------------------|------------------------------------------|
| jump                       | `j 145`            | go to 145                                |
| jump register              | `jr r31`           | go to r31                                |
| jump and link              | `jal 145`          | r31 = PC + 4; go to 145                  |

## Registers in MIPS
* how many? 32
      * r0 -> r31
* how big is each? 32 bits

|     | Register file                       |
|-----|-------------------------------------|
| r0  | 0 (r0 is always zero)               |
| r1  | --MIPS registers can hold 32 bits-- |
| r2  |                                     |
| ..  |                                     |
|     |                                     |
|     |                                     |
| r29 | used for function calls             |
| r30 | used for function calls             |
| r31 |                                     |

* **values for instructions must come from the register**
* r0 is always zero (0)
* 


# 1.3 Registers and Memory














# Resource
* https://www.youtube.com/channel/UC0j4jTCkhMLmGwriVbbBtSw/playlists


