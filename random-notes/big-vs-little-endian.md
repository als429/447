# General
* 8 bits = 1 byte, per memory address
* 0x = hexadecimal

* 0x 00c0ffee <- want to assign into a memory address

    |   |   |   |   |   |
    |---|---|---|---|---|
    | 0 | 1 | 2 | 3 | 4 |

**Big Endian**

    | 00 | c0 | ff | ee |   |
    |----|----|----|----|---|
    |  0 |  1 |  2 |  3 | 4 |

**Little Endian**

    | ee | ff | c0 | 00 |   |
    |----|----|----|----|---|
    |  0 |  1 |  2 |  3 | 4 |

* So long as your computer knows what order the numbers are in, you can store either way
* How do you store values greater than one byte

# Why have two systems
* It doesn't matter, so long as people know
* Problem is when you have two computers are communicating
  * They must agree on whether big or little endian stand is being used
  * Translation will happen within software

## Big Endian
* Start at the first address, and move down
* L-> R reading style
* Most significant byte stored first
* Used by: IBM

    | a | b | c | d |
    |:-:|:-:|:-:|:-:|

## Little Endian
* R -> L reading style
* Least significant byte stored first
* Hardware may be easier to design
* Used by: AMD

    | c | d | a | b |
    |:-:|:-:|:-:|:-:|

# Side Note
* A reference to Gulvers Travels within Egg wars

# Resources
* https://youtu.be/NcaiHcBvDR4
