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
*


















# Resource
* https://www.youtube.com/channel/UC0j4jTCkhMLmGwriVbbBtSw/playlists


