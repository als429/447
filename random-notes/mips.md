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
* each register called? a word

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

# 1.3 Memory Organization (versus Register)
* MIPS is a load-store register file machine
      *  meaing: instructions computer only on data in the register file
* memory = big and slow, most of the data is stored here
* register = small (32 registers x 32 bits) and fast

## Load-store architecture
* Data must be transfered from memory to the register file to use it
* **Load**: load from from memory to the register file; `lw`
* **Store**: store data to the memory from the register; `sw`

## Memory organization
* in MIPS, memory is a large one-dimensional aray 
* each location is one byte (8 bits) ((IMPORTANT: Registers are 4 bytes, i.e., 32 bits))
* memory addresses indexes into the array 
   * for a 32-bit computer, there are 2<sup>32</sup> locations
         * largest address = 2<sup>32</sup> - 1

| Address                                | Memory                                      |
|----------------------------------------|---------------------------------------------|
| 4,294,967,295 (i.e., 2<sup>32</sup>-1) | memory holds 8 bits of data (i.e., 2 bytes) |
| 4,294,967,294                          |                                             |
| ...                                    |                                             |
| ...                                    |                                             |
| ...                                    |                                             |
| ...                                    |                                             |
| 2                                      |                                             |
| 1                                      |                                             |
| 0                                      |                                             |

## Memory vs. Registers
* it takes 4x memory addresses to fill up 1x registers (or 1x word or 32 bits)
* **4x memory addresses = 1x register**

|                                 | Memory                            | Register                     |
|---------------------------------|-----------------------------------|------------------------------|
| Locations                       | +4 billion addresses (for 32-bit) | 32 registers                 |
| Speed                           | Slow                              | Fast                         |
| Each address holds (bits)       | 8                                 | 32                           |
| Each address holds (bytes)      | 1                                 | 4 (32 bits/(8 bits / 1byte)) |
| Each address holds (hex values) | 1/2                               | 2                            |

## Viewing memory/ alignment 
* **word-aligned**: looking at data in terms of a word (numbering each based 32 bit groupings)
* **byte-addressable**: looking at data in multiples of bytes

# 1.4 Instruction Execution Model
* n/a

# 1.5 Data Operation Instructions
## Data Operations
* we have: memory, register, ALU (arithmatic logic unit) (i.e., the thing doing te mathmatic computations), and program counter
* what is the process?
      1. program counter holds the instruction address
      2. instructions are fetched from meory into the instruction register
      3. control logic decodes the instruction and tells the ALU and register file what to do
      4. ALU executes the instruction and results flow back into the register file
      5. the control logic updates the program counter for the next instruction
            * Note: the program counter must increment **4 bytes** to go to the next instruction

# 1.6 Data Transfer Instructions







# Resource
* https://www.youtube.com/channel/UC0j4jTCkhMLmGwriVbbBtSw/playlists


