# MIPS Instructions

## Questions
* what does [x] stand for:
  * imm = immediate
  * sxt
  * zxt
  * lo16
  * lo8
  * mfhi
  * mflo

## Arithmetic + Bitwise Instructions

| Code         | Operation | Description                                               |
|--------------|-----------|-----------------------------------------------------------|
| neg a, b     | a = -b    | gives the negative of b                                   |
| add a, b, c  | a = b + c | adds **signed** numbers                                   |
| sub a, b, c  | a = b - c | subtracts **signed** numbers                              |
| mul a, b, c  | a = b * c | give low 32 bits of signed multiplication                 |
| div a, b, c  | a = b / c | give quotient of signed division                          |
| rem a, b, c  | a = b % c | give remainder of signed division                         |
| addu a, b, c | a = b + c | adds unsigned numbers                                     |
| subu a, b, c | a = b - c | subtracts unsigned numbers                                |
| mulu a, b, c | a = b * c | give low 32 bits of unsigned multiplication               |
| divu a, b, c | a = b / c | give quotient of unsigned division                        |
| remu a, b, c | a = b % c | give remainder of unsigned division                       |
| mfhi a       | a = HI    | after mul, gives high 32 bits. after div, gives remainder |
| mflo a       | a = LO    | after mul, gives high 32 bits. after div, gives quotient  |
| not a, b     | a = ~b    | gives the bitwise complement of b (all bits flipped)      |
| and a, b, c  | a = b & c | bitwise ANDs numbers                                      |
| or a, b, c   | a = b | c | bitwise ORs numbers                                       |
| xor a, b, c  | a = b ^ c | bitwise XORs numbers                                      |

## Shift Instructions

| Code           | Operation     | Description                                                |
|----------------|---------------|------------------------------------------------------------|
| sll a, b, imm  | a = b << imm  | shift left by a constant amount                            |
| srl a, b, imm  | a = b >>> imm | shift right unsigned (logical) by a constant amount        |
| sra a, b, imm  | a = b >> imm  | shift right arithmetic by a constant amount                |
| sllv a, b, reg | a = b << reg  | shift left by the amount in a register                     |
| srlv a, b, reg | a = b >>> reg | shift right unsigned (logical) by the amount in a register |
| srav a, b, reg | a = b >> reg  | shift right arithmetic by the amount in a register         |

## Data Transfer Instructions

| Code          | Operation              | Description                                                                     |
|---------------|------------------------|---------------------------------------------------------------------------------|
| li a, imm     | a = imm                | put a constant value into a register                                            |
| la a, label   | a = &label             | put the address that a label points to in a register                            |
| move a, b     | a = b                  | copy value from one register to another                                         |
| lw t0, var    | -                      | copies a word (32-bit value) from the memory variable (var) into t0             |
| lw t0, (t1)   | -                      | copies a word from a word from the memory address given by t1 into register t0  |
| lw t0, 4(t1)  | -                      | copies a word from the memory address given by t1 + 4 into register t0          |
| lw reg, addr  | reg = MEM[addr]        | loads the 4 bytes at addr as a 32-bit value into reg                            |
| lh reg, addr  | reg = sxt(MEM[addr])   | loads the 2 bytes at address as a signed 16-but value into reg                  |
| lb reg, addr  | reg = sxt(MEM[addr])   | loads the 1 byte at addr as a signed 8-bit value into reg                       |
| lhu reg, addr | reg = zxt(MEM[addr])   | loads the 2 bytes at addr as an unsigned 16-bit value into reg                  |
| lbu reg, addr | reg = zxt(MEM[addr])   | loads the 1 byte at addr as an unsigned 8-bit value into reg                    |
| sw reg, addr  | MEM[addr] = reg        | stores the value of reg into memory as 4 bytes starting at addr                 |
| sh reg, addr  | MEM[addr] = lo16(reg)  | stores the low 16 bits of reg into memory as 2 bytes starting at addr           |
| sb reg, addr  | MEM[addr] = lo8(reg)   | stores the low 8 bits of reg into memory as 1 byte at addr                      |
| push ra       | sp -= 4; MEM[sp] = reg | pushes the value of reg onto the call stack                                     |
| pop reg       | reg = MEM[sp]; sp+=4   | pops the top call stack value and puts it into reg                              |

## Unconditional Control Flow
These always change the PC to a new location.

| Code      | Operation               | Description                                               |
|-----------|-------------------------|-----------------------------------------------------------|
| j label   | PC = label              | goes to the instruction at label                          |
| jal label | ra = PC + 4; PC = label | function call to label, stores return address in ra       |
| jr reg    | PC = reg                | goes to the instruction whose address is in reg, often ra |
| syscall   | -->                     | runs the system call function whose number is in v0       |

## Conditional Control Flow
b can be a register or a constant.

| Code             | Operation                 | Description                                       |
|------------------|---------------------------|---------------------------------------------------|
| beq a, b, label  | if(a == b) { PC = label } | if a is equal to b, goes to label                 |
| bne a, b, label  | if(a != b) { PC = label } | if a is NOT equal to b, goes to label             |
| blt a, b, label  | if(a < b) { PC = label }  | if a is less than to b, goes to label             |
| ble a, b, label  | if(a <= b) { PC = label } | if a is less than or equal to b, goes to label    |
| bgt a, b, label  | if(a > b) { PC = label }  | if a is greater than b, goes to label             |
| bge a, b, label  | if(a >= b) { PC = label } | if a is greater than or equal to b, goes to label |
| bltu a, b, label | if(a < b) { PC = label }  | same as above, but does an unsigned comparison    |
| bleu a, b, label | if(a <= b) { PC = label } | same as above, but does an unsigned comparison    |
| bgtu a, b, label | if(a > b) { PC = label }  | same as above, but does an unsigned comparison    |
| bgeu a, b, label | if(a >= b) { PC = label } | same as above, but does an unsigned comparison    |


## Resource
https://jarrettbillingsley.github.io/teaching/classes/2201/cs0447/guides/instructions.html
